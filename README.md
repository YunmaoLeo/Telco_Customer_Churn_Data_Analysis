# Telco_Customer_Churn_Data_Analysis
电信企业客户流失数据分析
- [Telco_Customer_Churn_Data_Analysis](#telco_customer_churn_data_analysis)
- [相关背景与分析目的](#相关背景与分析目的)
- [数据情况](#数据情况)
  - [数据集概览](#数据集概览)
  - [数据基本分析](#数据基本分析)
- [数据拆分](#数据拆分)
  - [基于用户使用的网络服务项目进户行分析](#基于用户使用的网络服务项目进户行分析)
  - [用户流失数据情况拆分](#用户流失数据情况拆分)
    - [用户分类](#用户分类)
      - [按用户使用服务时间划分](#按用户使用服务时间划分)
      - [按用户消费能力与消费意愿进行划分](#按用户消费能力与消费意愿进行划分)
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
<br>
  
![用户使用公司服务的时间分布情况](charts/usage_time_Distribution.jpg)


+ 给定数据集中的总用户流失率为26.6%

###

# 数据拆分

## 基于用户使用的网络服务项目进户行分析

## 用户流失数据情况拆分

### 用户分类
#### 按用户使用服务时间划分
通过产品生命周期及产品本身的特性，算出产品的新老用户明确界限
+ 新用户I - 引入期，接触适应
+ 新用户II - 成长期，探索成长
+ 老用户I - 成熟期，追求体验
+ 老用户II - 疲惫期，流失隐患中


#### 按用户消费能力与消费意愿进行划分

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






