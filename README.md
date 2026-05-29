# 地图定位示例

这是一个最小静态页面示例，支持腾讯地图和高德地图。

页面使用浏览器 `navigator.geolocation` 获取当前位置，在所选地图上居中并添加标记，同时调用对应地图服务做逆地址解析。

示例源码不内置地图 Key。页面运行时可在输入框填写 Key，也可使用 URL 参数传入：

```text
http://localhost:5173/?provider=tencent&tencentKey=你的腾讯地图Key
http://localhost:5173/?provider=amap&amapKey=你的高德地图Key
```

高德 JS API 2.0 的新 Key 可能还需要安全密钥，可在页面的“高德安全密钥”输入框填写，或通过 URL 参数传入：

```text
http://localhost:5173/?provider=amap&amapKey=你的高德地图Key&amapSecurityJsCode=你的高德安全密钥
```

## 运行

定位能力需要在 `localhost` 或 HTTPS 环境下运行。当前目录可直接执行：

```powershell
python -m http.server 5173
```

浏览器打开：

```text
http://localhost:5173/
```

## 文件

- `index.html`：完整示例页面，运行时选择腾讯地图或高德地图并填写 Key 后加载地图。

## 官方文档

- 腾讯位置服务文档：https://lbs.qq.com/docs-square/
- 高德 Web 服务 API：https://lbs.amap.com/api/webservice/summary
- 高德地图 JS API 2.0：https://lbs.amap.com/api/javascript-api-v2
