[English](README_EN.md)
### 修改后端（服务端）
- 复制`src\Emby.CustomCssJS.dll`到`system\plugins`

### 修改前端（服务端和客户端）
- 服务端
  - 复制`src\CustomCssJS.js`到`system\dashboard-ui\modules`
  - 修改`system\dashboard-ui\app.js`
    - 函数`start()`中`Promise.all(list.map(loadPlugin))`前新增`list.push("./modules/CustomCssJS.js"),`  

      ```
      list.push("./modules/CustomCssJS.js"),
      Promise.all(list.map(loadPlugin))
      ```
- 客户端
  - 复制`src\CustomCssJS.js`到`electronapp\www\modules`
  - 修改`electronapp\www\modules\app.js`
    - 函数`start()`中`Promise.all(list.map(loadPlugin))`前新增`list.push("./modules/CustomCssJS.js"),`  

      ```
      list.push("./modules/CustomCssJS.js"),
      Promise.all(list.map(loadPlugin))
      ```
***
- 服务端脚本启用信息储存在`localStorage`，键值为`customcssServerConfig_${sercerID}`和`customjsServerConfig_${sercerID}`
- 本地脚本启用信息储存在`localStorage`，键值为`customcssLocalConfig`和`customjsLocalConfig`
- 如启用脚本后，无法进入emby，删除`localStorage`中相应数据即可