#### 流程

##### 一、基础结构搭建

1. 创建文件夹，自定义（包名）；

2. 创建入口文件index.js;

3. npm init（或者`npm init -y` 直接默认选择） 初始化package.json文件；

4. 为了让终端输入某个命令能执行某个文件，类似node index.js，我们需要配置一些东西；

5. 在package.json配置bin信息，大概如下，我们配置了一个`ali`的命令，指定终端输入`ali`时能执行index.js入口文件；

   ```js
   {
     "name": "learn_cli",
     "version": "1.0.0",
     "description": "",
     "main": "index.js",
     "bin": {
       "ali": "index.js"
     },
     "scripts": {
       "test": "echo \"Error: no test specified\" && exit 1"
     },
     "keywords": [],
     "author": "",
     "license": "ISC"
   }
   ```

6. 到这一步，我们在终端输入`ali`时，还是会报错，因为终端并不会识别这个命令，即node不识别这个命令，我们需要让终端输入这个命令时去关联node，让node去执行这个命令对应的需要执行的文件；

7. 我们需要在入口文件index.js中的最顶部写一段Shebang代码，考虑到不同用户安装node路径不一样，因此指定从环境变量中用node执行脚本;

   ```js
   #!/usr/bin/env node
   ```

8. 但是仅仅是这样，在终端输入`ali`时依旧会报错，还是不识别命令，我们上面所有的操作都是为了让node执行`ali`命令但，是`ali`这个命令并不是全局的命令，正常我们终端能执行某些全局命令是因为安装了依赖，此时我们没有也没法安装我们正在开发的依赖包，所以需要使用工具去帮助，去模拟，让终端输入的ali命令指向到我们正在开发的依赖，因此我们在终端输入npm link，建立连接：

   ```js
   npm link
   ```

   具体说明可参考[某博主的文章](https://blog.csdn.net/weixin_47359038/article/details/123988900)。

9. 如此一来，我们就配置好这个命令了，即终端输入`ali`能够执行我们指定的index.js入口文件，达到了和node index.js一样的效果；

##### 二、commander实现可选参数options

使用该插件，获取终端的输入参数，根据参数去执行某些代码逻辑，同时扩展内置的options选项来延展功能。

commander插件安装后默认只有两个参数：-v或--version，表示版本；-h或--help，表示帮助；

1.index.js输入如下代码：

```js
#!/usr/bin/env node

// 导入commander插件
const program = require("commander");
// 获取版本
// program.version(require("./package.json").version); //获取版本信息，默认选项名称是-V和--version，此处可自定义
program.version(require("./package.json").version, "-v,--version", "this is description of version"); //此处自定义名称并加描述
// 解析参数
program.parse(process.argv);

console.log("入口文件index");
```

2.终端输入如下代码及效果：

```js
//终端输入
ali -v  或 ali --version

//终端输出
1.0.0

//终端输入
ali -h  或 ali --help

//终端输出
Usage: index [options]

Options:
  //默认情况：-V, --version  output the version number
  //修改过version后：
  -v,--version  this is description of version
  -h, --help     display help for command
```

说明：

- 根据前面提到的输入ali会执行index.js的文件，后面跟了参数-v或者--version时，commander插件会内部parse解析参数，解析到-v或--version时，就会获取program.version()函数传递的参数，即1.0.0；
- 同理，检测到参数-h或--help时，内部会输出内置的两个options；

##### 三、commander实现可选参数

```js
  program.option("-a --ali", "a ali cli"); //描述-a或--ali选项为脚手架
  program.option("-d --dest <dest>", "a destination folder 例如：-d /src/components"); //-d或--dest后面跟目标路径
  program.option("-f --framework <framework>", "your framework"); // -f或--framework表示当前框架

  // 可以对可选参数进行监听，进而处理一些自定义的逻辑
  // program.on("--help", function () {
  program.on("option:dest", function () {
    // console.log("");
    // console.log("Other:");
    // console.log("	other options~");
    // console.log(this);
    // console.log(this.opts().dest);
  });

说明：
1.-d --dest为可选参数名称，中间也可用逗号分隔，--表示指令名称的结尾
2.后面紧跟的<dest>是该可选参数的自定义参数，[属性]：0 或 1 个参数; <属性...>：至少 1 个参数；[属性...]：0 或多个参数，如果是多个参数则会存在数组中
3.第二个参数是描述
4.下面的on函数可以注册可选参数的监听事件
```



##### 四、commander实现command指令

```js
program
    .command("addcpn <name>")
    .description("add vue component，例如：coderali addcpn HelloWorld [-d src/components]")
    .action((name) => {
      //回调逻辑
    });

说明：
1.command函数添加命令addcpn，<name>表示后面必须接一个参数。
2.description内写该指令的描述信息，在--help会输出所有指令、可选参数对应的信息
3.action的回调函数中执行该指令的行为，可自行定义。
```

