<!--
 * @Autor        : Pat
 * @Description  : 
 * @Email        : gouqingping@yahoo.com
 * @Date         : 2020-07-31 15:23:05
 * @LastEditors  : Pat
 * @LastEditTime : 2020-12-30 20:32:11
-->
<div align="center">
	<div style="width:128px;height:128px;line-height:128px;font-size:36px;border-radius:50%;text-align:center;color:white;background-color:#d43544;box-shadow: 0 0 10px 0 rgba(0,0,0,.4);margin-bottom:15px;border:6px solid rgba(255,0,0,0.6)">AmbFs</div>
	<h2 style="margin:0;padding:0">AmbFs.js</h2>
	<span style="height:60px;border-radius:2px 0 0 2px;background-color: #000;color:white;padding:0 5px;font-size:12px;">PatGp</span>
	<span style="height:60px;border-radius: 0 2px 2px 0;background-color: #d43544;color:white;padding:0 5px;font-size:12px;margin-left:-5px;">v1.0.61</span>
</div>


系统配置文件生成器（解决多余IP暴露引起的安全性问题）

### 如何使用 
+ 根目录创建amb与api文件夹
+ amb文件夹添加环境配置参数,如：
	在文件目录中添加 `modele.dist.js`
	```js
	// modele.dist.js

	// 所有配置皆为自定义
	module.exports = {
		moduleName: "测试",
		moduleEname: "Test",
		mock: true,
		logo: "./favicon.ico",
		appGuid: "b91b93789e5c42318bdd8b2eb77db19b"
	};
	```
+ api文件夹添加环境配置接口IP,如：
	在文件目录中添加 `modele.api.js`
	```js
	// modele.api.js

	// ambName用于关联amb文件夹下面的文件
	const ambName = "modele.dist";
	// 所有配置皆为自定义
	module.exports = {
		requestUrl: `http://10.51.100.133:4399`
	};
	```
+ 在 `webpack` 中
	```js
	// webpack.config.js
	
	const ambfs = require("p.fs.amb"),
		SRC = "./src/init";
	ambfs(SRC);
	module.exports = {
		……
	};
	```

+ 在 `nodeJs` 中

	```js
	const ambfs = require("p.fs.amb"),
		SRC = "./src/init";
	ambfs(SRC);
	```

+ `package.json` 中 `'scripts'` 
	- `--mode ENV_TYPE=dev ` 设置当前环境,关联`amb.js`、`api.js`（可自定义）
	- `--mode SYS_TYPE=enterprise"` 自定义参数扩展，关联`sys.js`（可自定义）
	
	如：
	```js
  "scripts": {
    "dev": "vue-cli-service serve  --mode ENV_TYPE=dev  --mode SYS_TYPE=enterprise",
    "build:dev": "vue-cli-service build  --mode ENV_TYPE=dev  --mode SYS_TYPE=enterprise",
    "build": "vue-cli-service build",
    "lint": "eslint --fix --ext .js,.vue src"
  },
	```


+ 在 `nodeJs` 中

	```js
	const ambfs = require("p.fs.amb"),
		SRC = "./src/init";
	ambfs(SRC);
	```


+ 结果 `./src` 文件夹内

	- src/
		- init/
			- amb.js ```环境配置参数 ```
			- api.js ```环境Api接口配置 ```
			- sys.js ```自定义参数扩展 ```


### 问题反馈
在使用中有任何问题，欢迎反馈给我，可以用以下联系方式跟我交流

* 邮箱: [gouqingping@yahoo.com](https://gouqingping@yahoo.com)
* github: [PatGp](https://github.com/gouqingping)