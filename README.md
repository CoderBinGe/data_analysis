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

**visualization_seaborn_distribution（单维度与关联维度分析）：**

单变量分布：
- 直方图（灰度图）：sns.distplot(x, kde=True, bins=20)
- 核密度估计：sns.kdeplot(x)

双变量分布：

- 散点图：sns.jointplot(x="x", y="y", data=df)
- 核密度估计：sns.jointplot(x="x", y="y", data=df, kind="kde")

**visualization_seaborn_regression（连续变量关联分析）：**

- 绘制线性回归模型：sns.lmplot()
- 拟合不同模型
- 变量间的条件关系摸索
- 控制图片的大小和形状

**visualization_seaborn_statEstimation（离散变量分析）：**

- 散点图：sns.stripplot(x="day", y="total_bill", data=tips)
- 箱图：sns.boxplot(x="day", y="total_bill", hue="time", data=tips)
- 统计柱状图：sns.barplot(x="sex", y="survived", hue="class", data=titanic, ci=None)
- 灰度柱状图：sns.countplot(x="deck", data=titanic)


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

**students_sales_data_analysis：**

学生数据和销售数据做分析：

```
# 两张表按字段做连接
pd.merge(df_info, df_score, on="ID", how="inner")

# 按性别统计各科目的平均分
df.groupby('sex').agg({'G1':np.mean,'G2':np.mean,'G3':np.mean})

# 按年龄统计各科目平均分，并柱状图展示
result=df.groupby('age')['G1','G2','G3'].agg(np.mean)
result.plot(kind='bar')
```

**data_visualization_case1（seaborn库绘图）：**
1. 航班乘客变化
- 分析年度乘客总量变化情况（折线图）
- 分析乘客在一年中各月份的分布（柱状图）

2. 鸾尾花花型尺寸分析
* 载入iris数据集
* 萼片（sepal）和花瓣（petal）的大小关系（散点图）
- 不同种类鸢尾花萼片和花瓣大小的分布情况（柱状图或者箱式图）
* 不同种类（species）鸢尾花萼片和花瓣的大小关系（分类散点子图）

3. 餐厅小费情况分析
* 载入tips数据集
* 小费和总消费之间的关系（散点图）
* 男性顾客和女性顾客，谁更慷慨（分类箱式图）
* 抽烟与否是否会对小费金额产生影响（分类箱式图）
* 工作日和周末，什么时候顾客给的小费更慷慨（分类箱式图）
* 午饭和晚饭，哪一顿顾客更愿意给小费（分类箱式图）
* 就餐人数是否会对慷慨度产生影响（分类箱式图）
* 性别+抽烟的组合因素对慷慨度的影响（分组柱状图）

4. 泰坦尼克号海难幸存状况分析
* 不同仓位等级中幸存和遇难的乘客比例（堆积柱状图）
* 不同性别的幸存比例（堆积柱状图）
* 幸存和遇难乘客的票价分布（分类箱式图）
* 幸存和遇难乘客的年龄分布（分类箱式图）
* 不同上船港口的乘客仓位等级分布（分组柱状图）
* 幸存和遇难乘客堂兄弟姐妹的数量分布（分类箱式图）
* 幸存和遇难乘客父母子女的数量分布（分类箱式图）
* 单独乘船与否和幸存之间有没有联系（堆积柱状图或者分组柱状图）
```
# dataframe创建
data = {"city" : ["Beijing", "Tianjin", "Shanghai"],
        "remuneration" : [3496.57, 1383.36, 3756.56],
        "tax" : [1161.55, 775.09, 1623.36],
        "depreciation" : [1251.09, 595.09, 1730.51],
        "surplus" : [1961.07, 1605.61, 3255.94]}
GDP_data = pd.DataFrame(data).set_index('city')

# 分组柱状图
GDP_data.T.plot.bar()

# 堆叠柱状图
GDP_data.T.plot.bar(stacked=True)

# 饼图
GDP_data.T.loc['remuneration'].plot.pie(subplots=True)
```
