# Telco_Customer_Churn_Data_Analysis
电信企业客户流失数据分析
- [Telco_Customer_Churn_Data_Analysis](#telco_customer_churn_data_analysis)
- [相关背景与分析目的](#相关背景与分析目的)
- [数据情况](#数据情况)
  - [数据集概览](#数据集概览)
  - [数据基本分析](#数据基本分析)
  - [流失率与其他变量之间的关系](#流失率与其他变量之间的关系)
  - [用户流失数据情况拆分](#用户流失数据情况拆分)
    - [用户分类](#用户分类)
      - [按用户使用服务时间划分](#按用户使用服务时间划分)
      - [根据用户行为数据使用聚类模型细分流失用户群体](#根据用户行为数据使用聚类模型细分流失用户群体)
    - [用户的生命周期价值](#用户的生命周期价值)
    - [用户流失影响因素分析](#用户流失影响因素分析)
- [可能的解决措施与策略](#可能的解决措施与策略)
  - [预防流失机制](#预防流失机制)
    - [分析流失征兆](#分析流失征兆)
    - [建立流失预警机制](#建立流失预警机制)
    - [进行干预引导](#进行干预引导)
  - [流失召回机制](#流失召回机制)
    - [判断用户是否有回流可能性](#判断用户是否有回流可能性)
    - [六十用户找回方案设计](#六十用户找回方案设计)
- [结论汇总](#结论汇总)
- [附件](#附件)


# 相关背景与分析目的
根据网络服务电信企业给定的用户服务数据集，分析用户流失的主要原因并给出针对性的解决措施以降低用户流失率。

# 数据情况
## 数据集概览
+ 数据集规模: (7032, 21)
  
+ 数据集特征涵盖以下内容
  +  用户个人信息
     +  性别，是否退休，是否有配偶，是否有监护人
  +  用户账户情况
     +  支付方式，月度消费，总消费，合约类型，使用时长，是否流失
  +  用户使用的服务类别

+ 缺失值情况与处理：共11行缺失总消费金额，删去涵盖缺失值的行

## 数据基本分析
+ 用户使用公司服务的时间分布情况
  + 横坐标：用户使用时长(月)，纵坐标：用户数(户)
  + 整体呈双峰分布，使用1-3个月的用户人数最多，超过1200户，使用35-45个月的用户数最少，使用67-70个月及以上的用户较多，接近800户。

![用户使用公司服务的时间分布情况](charts/usage_time_Distribution.jpg)

+ 用户使用公司服务签订的合同类型对应的用户使用时长分布
  + 按月签订合约的用户最多，为3875户，按一年/两年签订合约的用户为1685/1472户
  

![用户使用公司服务签订的合同类型对应的用户使用时长分布](charts/tenure_constract_type.jpg)

+ 各项服务的使用情况

![各项服务的使用情况](charts/Distribution_Services.jpg)

+ 用户个人信息基本统计：
  + 性别：男性50.5% 女性49.5%
  + 是否退休：未退休：83.8% 退休：16.2%
  + 配偶情况：无配偶：51.7% 有配偶：48.3%
  + 监护人情况：无监护人：70.2% 有监护人：29.8%

+ 给定数据集中的总用户流失率为26.6%

## 流失率与其他变量之间的关系
+ 用户流失情况与服务使用时间的关系
  + 流失用户的使用时长主要集中在1-30个月内，平均时长10月左右，未流失用户的使用时长范围更广，平均时长38月左右
  
![用户流失情况与服务使用时间的关系](charts/Churn_Tenure.jpg)

+ 不同合同类型对应的流失率情况
  + 按月付费的合同流失率最高，为43%，而按一年和两年签订合约的流失率分别为11%和3%
  
![不同合同类型对应的流失率情况](charts/Churn_ContractType.jpg)

+ 退休情况与流失率之间的关系
  + 退休用户的流失率为42%，远高于未退休用户的24%
  
![退休情况与流失率之间的关系](charts/Churn_Seniority.jpg)

+ 月度收费与流失率之间的关系
  + 更高的月度收费通常伴随着较高的流失率
  
![月度收费与流失率之间的关系](charts/Churn_MonthlyCharge.jpg)

+ 总收费与流失率之间的关系
  
![总收费与流失率之间的关系](charts/Churn_TotalCharge.jpg)

## 用户流失数据情况拆分

### 用户分类
#### 按用户使用服务时间划分
通过产品生命周期及产品本身的特性，算出产品的新老用户明确界限
+ 新用户I - 引入期，接触适应 （1-6月）
+ 新用户II - 成长期，探索成长 （7-24月）
+ 老用户I - 成熟期，追求体验  （25-50月）
+ 老用户II - 疲惫期 （51月及以上）

|用户类别|用户使用期限|流失数量|留存数量|总数量|流失率|
|--------|--------|--------|--------|--------|--------|
|新用户I|1-6个月|784|686|1470|53.3%|
|新用户II|7-24个月|547|1182|1729|31.6%|
|老用户I|25-50个月|350|1378|1728|20.2%|
|老用户II|51个月及以上|188|1917|2105|8.9%|

+ 不同用户类别对应的基础信息情况：较为均衡
  
![不同用户类别对应的基础信息分布](charts/parallelplot_userinfo.png)
  
+ 不同用户类别对应的月度消费金额最小值/平均值/最大值
  + 按使用时间分类的用户类别月度消费金额呈逐步上升的趋势
  
![不同用户类别对应的月度消费金额最小值/平均值/最大值](charts/MonthlyCharges_Each_User_Category.jpg)



#### 根据用户行为数据使用聚类模型细分流失用户群体
+ 模型
  + 特征：用户使用的网络服务与交易方式，合约类型
  + KMeans
  + 簇数：4

+ 模型分类后各类别用户的数量

![模型分类后各类别用户的数量](charts/numberofeachCategoryKMneas.jpg)

+ 各类别用户的平均使用时长，平均月度消费金额与平均总消费金额
![各类别用户的平均使用时长，平均月度消费金额与平均总消费金额](charts/Tenure_MonthlyCharges_TotalCharges_Category.jpg)

+ 四类客户提供的总收入贡献占比
![四类客户提供的总收入贡献占比](charts/total_charges_of_each_category.jpg)

+ 依据各类别用户的使用时长，平均月度消费金额，平均总消费金额进行定性归类
  + 一类用户 序号0
    + 特征：数量占比第三，平均使用时长12月左右，月度消费金额


### 用户的生命周期价值

### 用户流失影响因素分析

# 可能的解决措施与策略
## 预防流失机制
### 分析流失征兆
### 建立流失预警机制
### 进行干预引导

## 流失召回机制
### 判断用户是否有回流可能性
### 六十用户找回方案设计


# 结论汇总

# 附件






