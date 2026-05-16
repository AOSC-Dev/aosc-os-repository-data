# repository-data 字段定义

## attributes
该字段定义了镜像站的一些属性，用以调度。
* tracking 准实时镜像
* full 全量内容镜像
* dual-stack 双栈接入
* cdn CDN镜像
* redir 仅按特定规则跳转
* no-images 不同步安装镜像
* no-debug 不同步调试符号包
* ipv4-only 仅提供IPv4接入
* ipv6-only 仅提供IPv6接入

## location.region
该字段定义了镜像站物理所在地理区域，精确到一级行政区。
### 字段格式
**"AA-BB-CC"**
* AA表示最顶级地理分区，一般为大洲。如AS（亚洲）、EU（欧洲）、NA（北美洲）等。
* BB表示顶级地理分区下的国家或地区。如CN（中国）、US（美国）等。此部分代号大体遵循ISO 3166-1规范。
* CC表示BB所下属一级行政区。如BJ（北京）、HA（河南）、CA（加利福尼亚州）等。此部分代号大体遵循ISO 3166-2规范。
### 字段一般定义
**AA字段代号列表**
* AS 亚洲
* EU 欧洲
* NA 北美（含中美和加勒比诸岛）
* SA 南美
* AF 非洲
* PAC 太平洋诸岛群（含澳新）
### 字段特例定义
* 如镜像为全球CDN或Anycast CDN，则使用 `GLOBAL` 代号。
* 港澳台分别定义为， `AS-CN-HK` 、 `AS-CN-MO` 、 `AS-CN-TW` 。
* 美国、英法等国的海外属地、托管地等，按所在顶级地理分区处理，CC部分直接重复BB部分代号。
* 夏威夷州按北美洲归属处理。
* 俄罗斯联邦以乌拉尔联邦管区为界，以西（包括乌拉尔联邦管区）归属EU，以东归属AS。

## location.code
该字段按一个稍大的地理区域划分，用于repo镜像站地理重定向。
### 字段格式
**"XX-YYY"**
* XX表示顶级分区，按主要地理区域和互联网路由情况划分，如AS（亚洲）、CN（中国）、USA（美国）、CIS（独联体国家）等。
* YYY表示次级分区，在XX分区下按区域距离和路由情况再次划分，如AS-JAPAN、CN-EAST、USA-WEST、CIS-WEST等。
### 字段一般定义
* CN 中国
* AS 亚洲
* EU 欧洲
* USA 美国
* CIS 独联体国家
* AM 美洲（除美国以外其余美洲国家和地区）
* AF 非洲
* PAC 太平洋诸岛群（含澳新）
* CLD 大型全球云服务商
* ZZ 其余定义

#### CN 中国
<details>

* CN-EAST 华东地区
* CN-NORTH 华北地区
* CN-NORTHEAST 东三省
* CN-WEST 华西和西北地区
* CN-CENTR 华中地区
* CN-SOUTH 华南地区
* CN-HMT 港澳台

</details>

#### AS 亚洲
<details>

* AS-JAPAN 日本
* AS-KOREA 韩国
* AS-SEA 东南亚
* AS-SOUTH 南亚次大陆
* AS-IRAN 伊朗
* AS-GULF 阿拉伯海湾诸国
* AS-LEVANT 黎凡特地区诸国

</details>

#### EU 欧洲
<details>

* EU-WEST 西欧
* EU-NORDIC 北欧
* EU-SOUTH 南欧
* EU-BALKAN 巴尔干地区
* EU-CE 中东欧

</details>

#### USA 美国
<details>

* USA-EAST 东海岸
* USA-WEST 西海岸
* USA-MID Mid-West地区
* USA-SOUTH 南方各州
* USA-ALASKA 阿拉斯加
* USA-HAWAII 夏威夷

</details>

#### AM 美洲
<details>

* AM-CAD 加拿大
* AM-CRB 加勒比诸岛
* AM-MID 中美洲
* AM-ARG 阿根廷
* AM-BRZ 巴西
* AM-ANDES 安第斯山区
* AM-NOSAM 南美北部区域

</details>

#### CIS 独联体国家
<details>

* CIS-WEST 西部区域
* CIS-CENTRAL 中亚五国
* CIS-SIBIR 西伯利亚
* CIS-FAREST 远东地区

</details>

#### AF 非洲
* TBD... 

#### PAC 太平洋诸岛
<details>

* PAC-AUS 澳大利亚
* PAC-NZ 新西兰
* PAC-ISLANDS 太平洋岛群

</details>

#### CLD 大型全球云服务商
<details>

* CLD-AZURE
* CLD-AWS
* CLD-ALIYUN
* CLD-TENCENT
* ...

</details>

#### ZZ 其余定义
<details>

* ZZ-UKN 未知分区、未分区
* ZZ-TOR Tor网络
* ZZ-DOD （谁家偷了DoD的段出来广播啊？）
* ZZ-AMPR 业余无线电网络

</details>

### 字段特例定义
* 如无法判断大区内具体位置，则使用 `UNKNOWN` 作为次级代号。
* 如镜像为全球CDN或Anycast CDN，则使用 `GLOBAL` 代号。
