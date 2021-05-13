# uni-app

## uni-app中使用小程序原生云开发

1. 修改`manifest.json`的配置

   ```json
   "mp-weixin": {
       /* 微信小程序特有相关 */
       "appid": "",/* 自己的appid*/
       /* 云函数路径 */
       "cloudfunctionRoot": "cloudfunctions/",
       "setting": {
           "urlCheck": false
       },
       "usingComponents": true
   }
   ```

2. 在`src`下创建***`cloudfunctions`*** 不能为空，否则会影响待会儿的拷贝，我先随便加个`xxx.js`

3. 在 **app.js** 的 **onLanuch** 生命周期中初始化云开发:

   ```javascript
   if (!wx.cloud) {
       console.error("请使用 2.2.3 或以上的基础库以使用云能力");
   } else {
       wx.cloud.init({
           traceUser: true,
           env: "", //写自己云环境配置的后台环境
       });
   }
   ```

4. 首先在项目根目录创建vue.config.js文件，并做如下配置：

   ```javascript
   const path = require("path");
   const CopyWebpackPlugin = require("copy-webpack-plugin");
   
   module.exports = {
     configureWebpack: {
       plugins: [
         new CopyWebpackPlugin([
           {
             from: path.join(__dirname, "src/cloudfunctions"),
             to: path.join(
               __dirname,
               "dist",
               process.env.NODE_ENV === "development" ? "dev" : "build",
               process.env.UNI_PLATFORM,
               "cloudfunctions"
             ),
           },
         ]),
       ],
     },
   };
   ```

5. **安装 copy-webpack-plugin**

   ```shell
   npm install -save copy-webpack-plugin
   ```

   > 2020/05/27更正：copy-webpack-plugin 6.1.1版本的官方配置方法有改动，导致上面的配置会在最新的依赖下会报错！请按官方文档重新配置（反正我没配置成功。。），或是就用5.1.1版本的依赖
   > npm install -save copy-webpack-plugin@5.1.1

