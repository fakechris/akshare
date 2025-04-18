# [AKShare](https://github.com/akfamily/akshare) 数据说明

## 专栏介绍

本专栏主要目的是提示数据使用的风险，包括但不限于股票、期货、期权、债券、基金、外汇等数据。

## 股票数据

### stock_zh_a_hist

接口：stock_zh_a_hist

问题描述：股票 `600734` 后复权数据的开高低收字段出现负值

代码复现：

```python
import akshare as ak

stock_zh_a_hist_df = ak.stock_zh_a_hist(
    symbol="600734",
    period="daily",
    start_date="20050501",
    end_date="20050520",
    adjust="hfq"
)
print(stock_zh_a_hist_df)
```

结果复现：

```shell
      日期    开盘    收盘    最高    最低  ...  成交额     振幅    涨跌幅   涨跌额   换手率
0  2005-05-09 -0.13 -0.53  0.00 -0.53  ...  1571616.0   407.69 -507.69 -0.66  0.60
1  2005-05-10 -0.53 -0.50 -0.36 -0.79  ...  1150869.0   -81.13    5.66  0.03  0.45
2  2005-05-11 -0.50 -0.30 -0.20 -0.69  ...  1651719.0   -98.00   40.00  0.20  0.63
3  2005-05-12 -0.33 -0.20  0.00 -0.43  ...  2175707.0  -143.33   33.33  0.10  0.81
4  2005-05-13 -0.33 -0.13  0.07 -0.40  ...  1569427.0  -235.00   35.00  0.07  0.58
5  2005-05-16 -0.30 -0.10  0.10 -0.40  ...  2324469.0  -384.62   23.08  0.03  0.85
6  2005-05-17 -0.10  0.04  0.13 -0.23  ...  2682900.0  -360.00  140.00  0.14  0.96
7  2005-05-18  0.00  0.20  0.27 -0.13  ...  2261494.0  1000.00  400.00  0.16  0.81
8  2005-05-19  0.10  0.07  0.17 -0.06  ...  1589463.0   115.00  -65.00 -0.13  0.57
9  2005-05-20  0.07  0.00  0.13 -0.03  ...  1355000.0   228.57 -100.00 -0.07  0.48
[10 rows x 11 columns]
```
