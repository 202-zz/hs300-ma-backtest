# 沪深300双均线策略回测

使用 Python/pandas/numpy/matplotlib/akshare 对沪深300指数进行 MA5/MA20 双均线回测。

## 数据
- 来源：akshare `stock_zh_index_daily(symbol="sh000300")`
- 实际运行中有 akshare 连接重试/RemoteDisconnected 提示，最终成功读取：`stock_zh_index_daily(sh000300)`
- 样本区间：2002-01-04 ~ 2026-09-04
- 行数：5986
- 字段示例：`date`, `close`

示例头部数据：

text

date        close

2002-01-04  1316.455

2002-01-07  1302.084

2002-01-08  1292.714

2002-01-09  1272.645

2002-01-10  1281.261

## 策略
- 快线：MA5
- 慢线：MA20
- 金叉买入/持仓，死叉空仓/卖出
- 双边手续费假设：千分之一

## 结果
- 样本区间：2002-01-04 ~ 2026-09-04
- 策略年化收益：0.0795
- 夏普比率：0.4702
- 最大回撤：-0.4873
- 策略最终净值：4.6936

## 文件
- `backtest_ma.ipynb`：回测代码
- `hs300.csv`：指数数据
- `backtest_ma_result.png`：结果图，由 `plt.savefig("backtest_ma_result.png", dpi=120)` 保存

## 运行
安装依赖：
bash

pip install pandas numpy matplotlib akshare
启动：
bash

jupyter notebook backtest_ma.ipynb

注：运行时出现 `UserWarning: Glyph ... Sans` 是 matplotlib 中文字体显示警告，不影响数值结果和图片保存；图中中文标题/图例可能字体回退。

