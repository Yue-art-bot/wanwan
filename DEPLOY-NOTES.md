# 部署说明（个人维护版）

## 站点

- 生产地址：https://wanwan-yue.netlify.app
- 源码仓库：https://github.com/Yue-art-bot/wanwan（fork 自 wanonewan/wanwan）
- 部署方式：Netlify 连接 GitHub 仓库，推送到 `main` 自动发布
- Netlify 设置：Publish directory 填 `.`，base 与 build command 留空

## 访问口令（公开部署后的入口收敛）

`index.html` 顶部有一段口令校验脚本：

```js
var WANWAN_ACCESS_PIN = 'wanwan';   // 改成你自己的口令；设为 '' 即关闭
```

- 默认口令为 `wanwan`，首次输入后会记住在当前浏览器（localStorage）
- 换成自己的口令：改上面这一行，提交推送即可
- 不想用口令：把它改成空字符串 `''`
- 说明：这是纯前端门槛，能挡住随手打开网页的人，但挡不住会看源码的人；要真正的私有化需用 Netlify 的付费 Password protection

## 静态资源已全部本地化

| 资源 | 原位置 | 现在 |
|---|---|---|
| 7 张背景/头像图 | img2.tofaka.com 图床 | `img/external/`（bg-01/03/04/05、phb-1/2、imessage-default） |
| Font Awesome 7.2.0 | cdn.jsdelivr.net | `vendor/fontawesome/` |
| 4 套 Flaticon UIcons | cdn-uicons.flaticon.com | `vendor/uicons/` |
| Dexie 4.4.3 | 3 个 CDN 轮询 | `vendor/dexie.min.js`（CDN 仅作兜底） |
| JSZip 3.10.1 | cdn.jsdelivr.net | `vendor/jszip.min.js`（CDN 仅作兜底） |

PWA 图标已按真实尺寸重建在 `img/icons/`（192 / 512 / maskable 512）。

## 密钥相关

仓库内不含任何 API Key。所有 API Key 均由使用者在应用设置里自行填写，只保存在其本机浏览器的 IndexedDB 中，不会上传。因此把站点公开不会泄露或消耗作者的额度。

## Android APK

APK 是 WebView 壳，加载的就是上面这个网址，站点更新后无需重新打包。
