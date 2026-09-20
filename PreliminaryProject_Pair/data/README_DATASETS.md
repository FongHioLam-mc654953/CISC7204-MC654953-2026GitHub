# CISC7204 Assignment 01 — 真实数据集采集汇总（data 目录）

采集完成时间：2026-09-19
保存根目录：C:\Users\07viv\Desktop\cisc7204-Assgn01-2026-mc653748\data\
说明：仅新增文件，未修改或删除任何既有文件。

## ① data.gov.mo 巴士路线资料数据集
- 来源页面：https://data.gov.mo/Detail?id=e7b2e84d-3333-42f0-b676-64ce95306f0d （交通事务局）
- 原始下载包（zip）：data\data.gov.mo_bus_route_data.zip（779,945 字节）
- 解压目录：data\data.gov.mo_bus_route_shp\ExportShapeFile20260919\
  - BUS_POLE.shp / .dbf(1,412,270) / .shx / .prj / .cpg（巴士站）
  - ROUTE_NETWORK.shp(567,100) / .dbf(760,383) / .shx / .prj / .cpg（路线网络）
  - BUS_ROUTE_SEQ.xls（5,896,192 字节，巴士路线顺序）
- 直接下载端点规律：https://api.data.gov.mo/document/download/{datasetId}?fileId={fileId}&isNeedFile=1&lang=TC
  （必须带 Accept-Encoding: identity，否则返回 31 字节内部错误 JSON）
- 站内检索清单：
  - data\data.gov.mo_all_datasets.csv （data.gov.mo 全量数据集 1,376 条：名称/ID/部门/是否可下载）
  - data\gov_mo_datasets_manifest.csv （关键词命中 86 条中的可下载项清单）
  - data\gov_mo_datasets\ （59 个已下载文件，1,928,336 字节；含巴士路线、公共巴士站总数、巴士数量、新能源/低地台巴士、酒店穿梭巴士、陆路口岸跨境汽车流量、出入境人数、区域旅游数据 dst_visitor_01~05、按时段及统计分区旅客人次等 xlsx/xml）

## ② DSEC 访澳旅客统计（id=402）
- 来源页面：https://www.dsec.gov.mo/en-US/Statistic?id=402
- 时间序列数据库 API（月度，官方原始 JSON）：
  https://www.dsec.gov.mo/TimeSeriesApi/App/KeyIndicatorv3/1/en-US/{KeyIndicatorID}
  - data\dsec_timeseries\DSEC_KeyIndicator_27.json（79,559 字节，Visitor arrivals 月度总量，2008 起）
  - data\dsec_timeseries\DSEC_KeyIndicator_28.json（81,663 字节）
  - data\dsec_timeseries\DSEC_KeyIndicator_127.json（79,609 字节）
- 月度统计表 Excel（含旅客入境统计表）：
  - data\dsec\DSEC_MonthlyBulletin_Stats_2026_M08.xlsx（1,385,626 字节）
  - data\dsec\DSEC_MonthlyBulletin_Stats_2026_M07.xlsx（1,347,778 字节）
- 获取路径：https://www.dsec.gov.mo/en-US/Home/Publication/MonthlyBulletinOfStatistics → 选月份 → Statistical Tables
  实际附件端点：https://www.dsec.gov.mo/getAttachment/{guid}/E_BME_PUB_{YYYY}_M{MM}.aspx

## ③ MGTO Data+ 按时段及统计分区旅客人数
- 来源页面：https://dataplus.macaotourism.gov.mo/Publication/StatisticalTables?lang=E
- 下载目录：data\mgtodataplus\ （41 个月度 Excel，共 16,972,713 字节）
  命名：MacaoDistrictTourismData_YYYYMM_en.xlsx（2025-08 至 2026-07 全月份）
  直链规律：https://dataplus.macaotourism.gov.mo/document/ENG/Report/MacaoDistrictTourismData/{YYYY}/MacaoDistrictTourismData_{YYYYMM}_en.xlsx
- 同主题的 data.gov.mo 版本：data\gov_mo_datasets\dst_visitor_01_stats.xlsx（145,407 字节）

## ④ figshare MOPubBus 数据集（DOI 10.6084/m9.figshare.29578121.v1）
- 状态：figshare 站点与 API 对本机网络返回 HTTP 403（doi.org 跳转、figshare.com 页面、api.figshare.com/v2/articles/29578121、ndownloader 均 403），无法直接下载原站文件。
- 已获取的元数据（经 DataCite 公开元数据接口）：
  data\figshare\figshare_29578121_datacite_metadata.json
  标题 Macao Public Bus (MOPubBus) figShare；作者 Kim, SongKyoo；2025；总大小 4,234,737 Bytes；关联仓库 https://github.com/amangkim/MOPubBus
- 文件清单（63 条 path + size + 下载链接）：data\figshare\figshare_29578121_filelist.csv
- 替代下载（作者关联 GitHub 仓库镜像）：data\mopubbus\（11 文件，968,075 字节）
  - 3_grandprix_test.csv(45,644)、AP1_grandprix_test.csv(53,281)、3_normal_test.csv(240,238)、AP1_normal_test.csv(215,492)、3_grandprix_train.csv(183,009)、AP1_grandprix_train.csv(213,265)、weather_types.csv(183) 及 4 个 README
  - 其余大文件（>1MB）清单与链接见 filelist.csv

## ⑤ GitHub macau-bus-data（巴士路线/站点/班次 GeoJSON）
- 仓库：https://github.com/ngsiolei/macau-bus-data （默认分支 master）
- 下载目录：data\github_macau-bus-data\macau-bus-data-master\（186 文件，4,108,111 字节）
  - routes.json（818,093 字节，路线）
  - stops.json（106,798 字节，站点）
  - geojson\*.json（路线/站点空间数据）

## 清单文件
- data\_MANIFEST_all_files.csv：data 目录全部文件（相对路径 / 字节数 / 修改时间）
