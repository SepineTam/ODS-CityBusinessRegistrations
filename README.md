# ODS-CityBusinessRegistrations

Open Data Series: China's Annual City-Level Enterprise and Individual Business Registrations.

开源数据系列：中国城市年度企业与个体工商户注册量。

Data maintenance:

- [Song Tan](https://github.com/sepinetam)

## About the data

本项目整理城市年度企业注册量与个体工商户注册量，提供统一英文表头的 CSV 文件。以下统计基于当前文件，覆盖范围不代表各年完整、可比的全国统计口径。

| 项目 | 内容 |
| --- | --- |
| 年份范围 | 2000—2023 年 |
| 省级代码数 | 31 个 |
| 城市代码数 | 369 个，不等同于 369 个地级市 |
| 记录数 | 8,851 行 |
| 记录单位 | 城市代码—年份 |
| 文件编码 | UTF-8 |

## Files

```text
.
├── README.md
└── city_business_registrations.csv
```

### `city_business_registrations.csv`

| 字段 | 含义 |
| --- | --- |
| `year` | 年份 |
| `province_name` | 省级行政区名称 |
| `province_code` | 六位省级行政区代码 |
| `city_name` | 城市或对应行政单元名称，保留现有数据表述 |
| `city_code` | 六位城市行政区代码 |
| `enterprise_registration_count` | 该年度企业注册量，单位：户；具体主体范围有待来源资料确认 |
| `individual_business_registration_count` | 该年度个体工商户注册量，单位：户；空值表示缺失 |

## Usage

### Python

```python
import pandas as pd

registrations = pd.read_csv(
    "city_business_registrations.csv",
    encoding="utf-8-sig",
    dtype={"province_code": "string", "city_code": "string"},
)
```

### Stata

```stata
import delimited using "city_business_registrations.csv", clear varnames(1) encoding("utf-8") stringcols(3 5)
isid city_code year
```

Excel 如直接打开出现乱码，请通过“数据 → 从文本/CSV”导入，并选择 UTF-8 编码。

## Related ODS projects

本说明的组织结构参考以下项目：

- [ODS-RuralTourismKeyVillages](https://github.com/SepineTam/ODS-RuralTourismKeyVillages)
- [ODS-ECommerceIntoRuralAreas](https://github.com/SepineTam/ODS-ECommerceIntoRuralAreas)
- [ODS-BroadbandChina](https://github.com/SepineTam/ODS-BroadbandChina)
