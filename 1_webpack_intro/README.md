##webpack 介绍

###使用webpack基础构建

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

