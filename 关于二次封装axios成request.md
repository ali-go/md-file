在request.js处输入下面代码：

```js
//导入axios
import axios from 'axios'

//导出request
export function request() {
    const instance = axios.create() //创建axios实例
    instance.defaults.baseURL = 'http://127.0.0.1:8888/api/private/v1/'  //设置公共地址
    return instance  //注意此处返回的是一个不执行的函数
}
```



在main.js代码如下：

```js
// 导入封装aixos后的request文件
import { request } from './network/request'

// 把网络请求request添加到Vue的原型对象上，$http
Vue.prototype.$http = request()  //注意此处要调用request（）
```

