##Webpack dev server
npm install webpack-dev-server -g

webpack-dev-server --content-base public/

output: {
    ...
    publicPath: "/assets/",
}

--content-base
Using this config webpack-dev-server will serve the static files in your public folder

###Dev server and iframe automatic refresh

http://localhost:8080/webpack-dev-server - Menu
    bundle.js - source code of bundle file in the memory (http://localhost:8080/assets/bundle.js)
    bundle (magic html for bundle.js) (webpack-dev-server) - http://localhost:8080/webpack-dev-server/assets/bundle
http://localhost:8080/webpack-dev-server/assets - Files list
http://localhost:8080/webpack-dev-server/assets/bundle - execute bundle file in the iframe and reload it automatically after any file saving
http://localhost:8080 - execute bundle file but not in iframe. Will be automatically reload only in --inline mode

###Inline automatic refresh

webpack-dev-server --content-base public/ --inline

"refresh client" is added to bundle file (webpack-dev-server/client/index.js).

"refresh client" connects to dev server using socket connection  

###Hot module replacement

webpack-dev-server --content-base public/ --inline --hot (or HotModuleReplacementPlugin in the webpack config)

"hot loader" is added to bundle file (webpack/hot/dev-server.js).

API https://webpack.github.io/docs/hot-module-replacement.html

npm install webpack webpack-dev-server -g
npm install webpack css-loader style-loader
webpack-dev-server ./entry --hot --inline --module-bind "css=style!css"