**pandas_dataframe_visualization：基于pandas的内置可视化**
* 基本绘图：df.plot()
* 条形图: df.plot.bar()/df.plot.barh() stacked=True:堆积条形图
* 直方图：df.plot.hist()/df.hist()
* 箱形图: df.plot.box()
* 区域块图: df.plot.area()
* 散点图: df.plot.scatter()
* 饼状图: df.plot.pie(subplots=True) 绘制带图例的饼图
	
**matplotlib_visualization: [matplotlib可视化手册](https://matplotlib.org/api/pyplot_api.html)**	

**matplotlib_cases:**
1. 关联分析、数值比较：散点图、曲线图（带置信区间、双坐标）
2. 分布分析：灰度图、密度图、直方图（堆叠）
3. 涉及分类的分析：柱状图（堆积、分组）、箱式图

* 获取网络数据（urllib）
* 文件解压缩（zipfile）
* matplotlib基本参数配置如下：
```
from __future__ import division, print_function # 引入3.x版本的除法和打印
from matplotlib import pyplot as plt
import pandas as pd
import numpy as np
# 在notebook中显示绘图结果
%matplotlib inline

# 设置一些全局的资源参数，可以进行个性化修改
import matplotlib
# 设置图片尺寸 14" x 7"
# rc: resource configuration
matplotlib.rc('figure', figsize = (14, 7))
# 设置字体 14
matplotlib.rc('font', size = 14)
# 不显示顶部和右侧的坐标线
matplotlib.rc('axes.spines', top = False, right = False)
# 不显示网格
matplotlib.rc('axes', grid = False)
# 设置背景颜色是白色
matplotlib.rc('axes', facecolor = 'white')
```

**visualization_seaborn_distribution：**

单变量分布：
- 直方图（灰度图）：sns.distplot(x, kde=True, bins=20)
- 核密度估计：sns.kdeplot(x)

双变量分布：

- 散点图：sns.jointplot(x="x", y="y", data=df)
- 核密度估计：sns.jointplot(x="x", y="y", data=df, kind="kde")


**movie_analysis:**
* 每部电影打分的人数
* 每部电影的平均分，以及有多少人打分
* 脏数据处理，把字符串id转化为int
* merge
* sort_values(排序)
	
**bike_analysis：**
* dropna默认是删掉行, axis=1删除列，any是只要有一个就删除,all是所有的都是NaN才删除
* 对于缺失的数据，我们未必要直接删除，可以考虑用fillna把这一行的平均数填上
* 一周当中每天Berri 1的数量分布
* 一周当中每天总共有多少自行车通过
	
**stock_analysis：**
* index_col=0：将第一列作为索引，无行号，默认为None
* concat
* 月K线图

**lianjia_data_analysis：**
* 找到最近更新信息的20套房子
* 平均看房人数
* 房龄最小的20套房子的平均看房人数、平均面积（nsmallest）
* 房子价格的分布(平均，方差，中位数)
* 最受欢迎的朝向(平均看房人数)
* 最受欢迎的房型
* 最受关注的小区
* 房型数量分布
* 房子的平均租房价格(按平米算)
* 出租房源最多的小区
* 集中供暖和非集中供暖的有多少家，平均价格是多少
* 不同房型的平均/最大/最小面积
* 哪个地铁口附近的房子最多
* 地铁附近的房子平均价格 比 非地铁的高多少
* 地铁附近的房源离地铁平均距离
* 最多的在租楼层
* 直接看房的房子比例
