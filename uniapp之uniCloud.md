uniCloud是uniapp的云服务，可用于操作云数据库。

### 1、uniCloud基础操作

#### (1)、利用云函数执行云数据库简单的增删改查

```js
// 1、这是最初的模板
// 'use strict';
// exports.main = async (event, context) => {
// 	//event为客户端上传的参数
// 	console.log('event : ', event)

// 	//返回数据给客户端
// 	return event
// };

// 2、测试event和context
// (1)、event为调用该云函数传递的参数
// (2)、context为执行该云函数的上下文信息，包括请求、环境等等
// (3)、注意云函数的处理是异步的，得用async和await处理同步
// (4)、由于客户端是直接从云端获取的云函数，因此此处改了云函数必须得上传部署到云端
// 'use strict';
// exports.main = async (event, context) => {
// 	//event为客户端上传的参数
// 	console.log('event : ', event)
// 	console.log('context : ', context)
// 	//返回数据给客户端
// 	return event
// };

// 3、操作数据库--增加数据
// 'use strict';
// // (1)、链接数据库
// const db = uniCloud.database();
// //（2）、获取数据表集合并根据数据表名获取对应数据表(我们云服务建的数据表user)
// const collection = db.collection('user')
// exports.main = async (event, context) => {
// 	// (3)、给数据表增加数据(单条可直接对象，多条可数组对象)
// 	let res = await collection.add([{
// 			name: "加1",
// 			age: 19
// 		},
// 		{
// 			name: 'vue',
// 			type: 'html'
// 		}
// 	])
// 	console.log('res',JSON.stringify(res));
// 	//event为客户端上传的参数,context为请求的上下文信息
// 	console.log('event : ', event)
// 	console.log('context : ', context)
// 	//返回数据给客户端
// 	return {
// 		code: 200,
// 		message: "这是返回的数据",
// 		data: `姓名为${event.name}，年龄是${event.age}`
// 	}
// };

// 4、操作数据表--删除指定数据
// 'use strict';
// // (1)、链接数据库
// const db = uniCloud.database();
// //（2）、获取数据表集合并根据数据表名获取对应数据表(我们云服务建的数据表user)
// const collection = db.collection('user')
// exports.main = async (event, context) => {
// 	// (3)、根据doc获取指定id的数据，并移除
// 	const res = await collection.doc('619651fda1eb050001431b52').remove();
// 	console.log('res',JSON.stringify(res));
// 	//event为客户端上传的参数,context为请求的上下文信息
// 	console.log('event : ', event)
// 	console.log('context : ', context)
// 	//返回数据给客户端
// 	return {
// 		code: 200,
// 		message: "这是返回的数据",
// 		data: `姓名为${event.name}，年龄是${event.age}`
// 	}
// };

// // 5、操作数据表--更新指定数据
// 'use strict';
// // (1)、链接数据库
// const db = uniCloud.database();
// //（2）、获取数据表集合并根据数据表名获取对应数据表(我们云服务建的数据表user)
// const collection = db.collection('user')
// exports.main = async (event, context) => {
// 	// (3)、根据doc获取指定id的数据，并更新对应的数据（update和set都可以）
// 		// 区别：update只能更新存在的记录，set如果记录存在就更新，不存在就新建一条
// 	// const res = await collection.doc('6195d36f6cf30a00014bf702').update({
// 	const res = await collection.doc('6195d36f6cf30a00014bf702').set({
// 		name:"xixi"
// 	});
// 	console.log('res',JSON.stringify(res));
// 	//event为客户端上传的参数,context为请求的上下文信息
// 	// console.log('event : ', event)
// 	// console.log('context : ', context)
// 	//返回数据给客户端
// 	return {
// 		code: 200,
// 		message: "这是返回的数据",
// 		data: `姓名为${event.name}，年龄是${event.age}`
// 	}
// };


// 6、操作数据表--查询数据
'use strict';
// (1)、链接数据库
const db = uniCloud.database();
//（2）、获取数据表集合并根据数据表名获取对应数据表(我们云服务建的数据表user)
const collection = db.collection('user')
exports.main = async (event, context) => {
	// (3)、使用doc获取id记录并调用get方法查询到该数据，或者使用where传入对象参数来指定字段用get方法查询到该数据
	// const res = await collection.doc('6195d36f6cf30a00014bf702').get();
	const res = await collection.where({
		name:event.name
	}).get();
	console.log('res',JSON.stringify(res));
	return {
		code:200,
		message:"请求成功",
		data:res.data
	}
};

```

#### (2)、uniapp中调用云函数

```js
// 1、uniCloud.callFunction方法调用云函数
// 2、接收对象参数，对象第一个属性为云函数名称键值对，第二个是data参数传递自定义参数，第三个是成功的回调，第四个失败的回调
uniCloud.callFunction({
	name: "get_list",
	data: {
		name: "xixi",
		age: 18
	},
	success(res) {
		console.log(res)
	},
	fail(err) {
		console.log(err)
	}
})
```

#### (3)、uniapp中选择图片并上传至云存储

```js
uploadImg() {
	let that = this;
	// (1)、调用选择图片的内置api
	uni.chooseImage({
		count: 1, //限制传一张
		// 图片处理成功执行回调
		success(res) {
			const tempPath = res.tempFilePaths[0]; //文件bloburl的地址
			// (2)、调用上传文件到服务器的api
			uniCloud.uploadFile({
				filePath: tempPath, //上传的文件bloburl地址
				cloudPath: 'a.jpg', //绝对路径及文件名，具体可参考官网解释。必填
				// 上传成功的回调
				success(res) {
					that.src = res.fileID; //存储的路径可复制给本地展示
				},
				fail(err) {
					console.log(err)
				}
			})
		},
		fail(err) {
			console.log(err);
		}
	})
},

```

#### (4)、uniapp中删除云数据库云存储中的图片资源

```js
deleteImg() {
    //调用云函数删除文件的api
	uniCloud.deleteFile({
		// 需要删除的文件在服务器中的地址,此处为数组表示可多条
		fileList: [
			"https://vkceyugu.cdn.bspapp.com/VKCEYUGU-dbcb6ad0-9bc8-4aaf-add6-5211ed639d60/b202d411-206a-4af3-b128-6b56a4c852ff.jpg"
		],
		success(res) {
			console.log(res)
		},
		fail(err) {
			console.log(err)
		}
	})
}

```

