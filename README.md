# 剑门关 · 徒步

[打开路线页面](https://joker-outdoor.github.io/JianmenPass-hike-2026-11-08/) · [下载公开 GPX](https://joker-outdoor.github.io/JianmenPass-hike-2026-11-08/data/route.gpx) · [源码](https://github.com/joker-outdoor/JianmenPass-hike-2026-11-08)

剑门关徒步的 3D 卫星地形与路线地图，支持沿线飞行、联动海拔剖面、独立景点定位，以及统一 / 海拔 / 速度着色。手机可最大化地图并恢复面板，飞行进度、暂停状态与倍速保持不变；[2D 俯视图](https://joker-outdoor.github.io/JianmenPass-hike-2026-11-08/?view=2d) 可直接查看地标。

3D 展示来自真实 DEM 的地形和卫星影像贴图，不含景点建筑精模。地形高度初始为 **1×**，可用页面滑条调整。沿线飞行是按轨迹距离推进的模拟镜头，1 / 2 / 4 倍速不代表实际步行速度。本项目未制作新视频。

## 轨迹与统计口径

累计爬升约 **553 m**、下降约 **547 m**，均为裁剪后轨迹估算，不是设备原始汇总。按轨迹距离每 10 m 分箱取海拔中位数，保留首尾海拔；从首点开始，当前海拔与上次计入值相差至少 5 m 时累计相应升降，末端余量计入。滤波参数会影响结果，避免将原始海拔噪声累加成正式爬升。缺少可靠数据的主统计项直接隐藏。

- 活动与页面日期：2026-11-08。坐标、海拔来自运动健康 GPS 的裁剪后徒步轨迹。
- 保留 **10,296 点**，几何距离 **6.687247 km**，保留轨迹的起止跨度约 **2 小时 51 分 35 秒**，未扣除停留。
- 已在返回起点附近截断，回归点之后的 **1,106 点**已删除，不包含后续驾车尾段。整场 **12.35 km / 643 m** 不用于本页面的距离或爬升统计。
- 没有与裁剪段匹配的可靠爬升、下降和暂停汇总，这些字段保留 `null`；不把 GPS 海拔噪声累加为正式爬升，不推算运动时间或平均配速。`route.config.json` 与生成数据中的 `statsSource` 说明同一口径。
- 逐点速度由相邻坐标与时间差推算，并非设备实测速度。间隔超过 30 秒不计速度，低于 0.5 m/s 标记为停留；局部停留标记不替代暂停汇总。速度配色由红（慢）经黄到绿（快）。
- 公开 `data/route.gpx` 只保留轨迹名、坐标和海拔；`data/route.json` 保留路线几何、相对速度及汇总，不含逐点绝对时间。原始输入、未裁剪私人 JSON、健康 UUID、设备信息与照片均不入库。照片仅用于对照地名。

## 12 处独立景点

景点名称参照现场导游图，位置使用已核对的 OpenStreetMap 原始数据，读取日期为 2026-11-08。所有景点均启用 `preservePosition:true`，保留自身经纬度，不吸附到徒步线；梁山寺等离线景点仍显示实际位置。关联里程与剖面位置采用最近轨迹点，不表示此次徒步经过全部景点。景点海拔由 Mapzen DEM 网格双线性取高，和轨迹记录海拔分别注明来源。

原始数据范围：[OSM API 地图数据](https://api.openstreetmap.org/api/0.6/map?bbox=105.55,32.21,105.59,32.24)。英文名 **Jianmen Pass** 来自 [OSM node/5128924024](https://www.openstreetmap.org/node/5128924024) 的 `name:en`。

| 景点 | WGS84 经度、纬度 | OSM 对象与定位口径 |
| --- | --- | --- |
| 剑门关地质博物馆 | 105.56233505, 32.22499175 | [way/1024636873（轮廓节点平均代表位置；2026-11-08读取）](https://www.openstreetmap.org/way/1024636873) |
| 五丁坪 | 105.56226350, 32.22172950 | [node/9448222337（原始节点坐标；2026-11-08读取）](https://www.openstreetmap.org/node/9448222337) |
| 钟会故垒 | 105.56488324, 32.22756832 | [way/1024636861（轮廓节点平均代表位置；2026-11-08读取）](https://www.openstreetmap.org/way/1024636861) |
| 小穿洞 | 105.57126810, 32.22526910 | [way/1037626362（路径中段节点，标记代表整段步道，并非入口；2026-11-08读取）](https://www.openstreetmap.org/way/1037626362) |
| 大穿洞 | 105.57246700, 32.22396220 | [way/1037626360（路径中段节点，标记代表整段步道，并非入口；2026-11-08读取）](https://www.openstreetmap.org/way/1037626360) |
| 鸟道 | 105.57370890, 32.22777530 | [way/1037626391（路径中段节点，标记代表整段步道，并非入口；2026-11-08读取）](https://www.openstreetmap.org/way/1037626391) |
| 猿猱道 | 105.57461680, 32.22963130 | [way/1073535925（路径中段节点，标记代表整段步道，并非入口；2026-11-08读取）](https://www.openstreetmap.org/way/1073535925) |
| 梁山寺 | 105.57849190, 32.23211625 | [way/1037626371（轮廓节点平均代表位置；2026-11-08读取）](https://www.openstreetmap.org/way/1037626371) |
| 翠屏峰 | 105.58624680, 32.23154850 | [node/9557944664（原始节点坐标；2026-11-08读取）](https://www.openstreetmap.org/node/9557944664) |
| 剑门关关楼 | 105.56350963, 32.21503407 | [way/1024636859（轮廓节点平均代表位置；2026-11-08读取）](https://www.openstreetmap.org/way/1024636859) |
| 关楼观景台 | 105.56416120, 32.21576290 | [node/9448222316（原始节点坐标；2026-11-08读取）](https://www.openstreetmap.org/node/9448222316) |
| 天梯峡栈道 | 105.56921750, 32.21618460 | [way/1037626379（路径中段节点，标记代表整段步道，并非入口；2026-11-08读取）](https://www.openstreetmap.org/way/1037626379) |

各项原始说明完整保存在 `route.config.json` 和 `data/route.json` 的 `positionSource`。轮廓节点平均值是代表位置；步道中段节点代表整段步道，不当作入口。景点数据 © [OpenStreetMap contributors](https://www.openstreetmap.org/copyright)，按 [ODbL 1.0](https://opendatacommons.org/licenses/odbl/1-0/) 使用。

## 底图、地形与代码来源

- 卫星影像：[Esri World Imagery](https://server.arcgisonline.com/ArcGIS/rest/services/World_Imagery/MapServer)，全景使用 z16 源瓦片，局部高清使用 z17 原生瓦片，全部生成到本地 `data/`。Imagery © Esri, Maxar, Earthstar Geographics, and the GIS User Community；影像版权归相应提供者。
- 地形：[Tilezen / Mapzen Terrain Tiles](https://github.com/tilezen/joerd)，z14 Terrarium DEM，Terrain · Mapzen; SRTM / GMTED2010 courtesy of USGS。参见 [数据署名与许可](https://github.com/tilezen/joerd/blob/master/docs/attribution.md)。地形网格与轨迹海拔可能不同；3D 路线贴合地形，剖面保留轨迹海拔。
- 渲染与生成器：[route-visualization-template](https://github.com/joker-outdoor/route-visualization-template)，采用已合入 main 的 commit **`3fba4a79c8cea48ce87be5e266056f695c2e3c13`**。`app.js`、`route-style.js`、`video.js` 与 `scripts/` 原样同步；唯一测试适配是把 CPU 场景测试的演示数据读取路径改到 `examples/fixtures/demo/`，保留全部断言。没有另写渲染器，也没有修改共享 app 的默认逻辑；1× 初值仅配置在本路线 `index.html`。
- Three.js 0.160.0 官方原文件，MIT，见 `vendor/LICENSE`。

浏览器仅加载仓库内的地图数据，无需地图 API key。z17 高清覆盖轨迹走廊；远景、2D 与走廊外景点使用全景影像，不把全景插值当作高清。

## 重新生成与本地检查

依赖见 `requirements.txt`，优先使用已有 Python 环境。将裁剪后的私有 GPX 保留在仓库外，使用当前配置与模板生成器生成真实数据，不加 `--demo`：

```sh
python3 scripts/build_data.py /path/to/jianmen-hike-trimmed.gpx --config route.config.json --output data
python3 scripts/check_data.py
python3 -m unittest discover -s scripts -p 'test_*.py'
node --check app.js
node --check route-style.js
node --check video.js
node --check scripts/render_video.mjs
node --test scripts/test_route_style.mjs
python3 -m http.server 8080 --bind 127.0.0.1
```

打开 `http://localhost:8080` 或 `http://localhost:8080/?view=2d`。生成阶段通过网络取得底图与 DEM，瓦片缓存位于系统临时目录下的 `joker-outdoor-tile-cache`。`examples/fixtures/demo/` 仅供 CPU 场景回归使用，其合成路线和地形不进入正式 `data/`。

检查覆盖数据投影、DEM、独立景点、公开 GPX 隐私、高清分块、速度配色、沿线飞行与最大化/恢复。CPU 场景测试不替代真实浏览器的 WebGL、手机布局与视觉验收。发布由宿主流程执行，GitHub Pages 使用 main 分支、根目录 `/`，上线后再检查最终页面。

## 仙峰观与金城山绝壁

新增第13处景点“仙峰观 · 金城山绝壁”。标记采用百度地图仙峰观 POI（UID `69da4a3d04011a633310af8b`，2026-11-08读取）经 BD09MC → BD09 → GCJ02 → WGS84 转换的位置：105.54276085°E、32.22131165°N。用山顶道观位置代表其下绝壁，不表示完整崖壁边界，也不表示本次徒步经过此处。名称与照片参照[四川画报·剑门关仙峰观](https://sj.scpo.cn/detail/467242)及四川省林草局剑门关景区详细规划。西侧底图和地形同步扩展，原徒步坐标与统计不变。
