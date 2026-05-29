# 地图定位示例

这是一个最小静态页面示例，支持腾讯地图和高德地图。

页面使用浏览器 `navigator.geolocation` 获取当前位置，在所选地图上居中并添加标记，同时调用对应地图服务做逆地址解析。

定位已做三点优化：

- 连续高精度采样，最多采样 8 次或 15 秒，取误差半径最小的一次。
- 页面显示原始坐标、地图坐标和误差半径，便于判断偏差来源。
- 坐标模式默认使用 WGS84 -> GCJ-02 转换，避免国内地图底图上的系统性偏移。

示例源码不内置地图 Key。页面运行时可在输入框填写 Key，也可使用 URL 参数传入：

```text
http://localhost:5173/?provider=tencent&tencentKey=你的腾讯地图Key
http://localhost:5173/?provider=amap&amapKey=你的高德Web端JSAPIKey
http://localhost:5173/?provider=amap&coordinate=raw&amapKey=你的高德Web端JSAPIKey
```

坐标模式参数：

- `coordinate=gcj`：把原始坐标按 WGS84 -> GCJ-02 转换后再落到地图上，当前默认值。
- `coordinate=raw`：使用浏览器返回的原始坐标，用于对照诊断。

高德地图展示必须使用“Web端(JS API)”平台的 Key，不能使用“Web服务 API”平台的 Key。出现 `USERKEY_PLAT_NOMATCH` 时，含义就是当前 Key 与 JS API 平台不匹配。

高德 JS API 2.0 的新 Key 通常还需要安全密钥，可在页面的“高德安全密钥”输入框填写，或通过 URL 参数传入：

```text
http://localhost:5173/?provider=amap&amapKey=你的高德Web端JSAPIKey&amapSecurityJsCode=你的高德安全密钥
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
