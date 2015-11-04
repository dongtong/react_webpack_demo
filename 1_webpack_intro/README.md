##webpack 介绍

###使用webpack基础构建

Webpack扩展require,允许用户使用加载器(loader)自定义行为。同样也可以运用于CSS中的@import。Webpack为运行任务提供了一套插件,
如minifying, localization, hot loading等等。

为什么使用Webpack? 

1. webpack解决了一些打包困难。
2. 支持热模块替换(Hot Module Replacement <HMR>), 
   这个特性在react-hot-loader有使用到。LiveReload,Browsersync这些工具可以监控文件变化刷新浏览器，HMR更深入一步，可以使React程    序保持状态。看似简单，但是实际中确实解决大问题。
3. 打包具有扩展性。可以将打包分开，在程序需要的时候加载
4. 可以住人hash key到打包文件名上。

* CLI

	1. 安装(全局安装): 可以在全局环境下使用webpack cli命令
			
		  npm install -g webpack
		  
	2. 直接使用cli命令编译文件
	
		  xxx:1_webpack_intro mac$ webpack ./javascripts/app.js ./javascripts/bundle.js
		  
              Hash: 0dd0c78d058276548c46
              Version: webpack 1.12.1
              Time: 45ms
                    Asset     Size  Chunks             Chunk Names
                    bundle.js  1.47 kB                  0  [emitted]  main
                    [0] ./javascripts/app.js 80 bytes {0} [built]


* 配置文件

	1. 在项目工程目录下面添加一个配置文件webpack.config.js. webpack使用的是CommonJS的方式配置文件。添加以下内容:
	
		  module.exports = {
             entry: './javascripts/app.js',
             output: {
    	         filename: './javascripts/bundle.js'
             }
         }
         
    2. 在项目目录下运行构建任务webpack
    
    	   $ webpack

* 开发服务器

	1. 开发过程中经常不希望因为刷新浏览器而中断思维，这时可以开启webpack的watch模式，有两种方式:
		
		  $ webpack --watch
		  
	   另一种方式，修改配置文件
	   
	      module.exports = {
             entry: './javascripts/app.js',
             output: {
    	         filename: './javascripts/bundle.js'
             },
             watch: true
          }
          
       运行 webpack, 修改文件，但是浏览器不会自动刷新，因为你没有一个http server帮助你reload页面。webpack有一个内建的开发http服务器，但是需要安装:
       
          $ npm install -g webpack-dev-server
          
       运行
          
          $ webpack-dev-server
          
       最后打开浏览器访问 http://localhost:8080/webpack-dev-server/ 或者开启inline模式
       
          $ webpack-dev-server --inline
       
       然后访问 http://localhost:8080. 这样如果修改html, js, css，http server会自动reload页面...

* 加载器
* 产品构建

