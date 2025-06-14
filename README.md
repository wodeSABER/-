# 我将自己的评价分为三个板块
包括数据库知识的学习，作业与实践课，同学交流与ai使用情况

# 一：知识的学习（18/20分）

## 第一周：初步了解数据库
- 在老师和助教的指导下安装了数据库软件DataGrip、Postgres
## 第二周：深入了解数据库
### 数据库的主要特点：
- 结构化存储：数据按照特定的数据模型组织
- 集中管理：统一存储和管理相关数据
- 共享访问：支持多用户并发访问
- 减少冗余：通过规范化设计减少数据重复
- 数据独立性：数据与应用程序相对独立
### 数据库几乎应用于所有需要数据管理的领域：
-企业信息系统：ERP、CRM、SCM等
-金融服务：银行交易系统、证券交易系统
-电子商务：在线购物平台、支付系统
## 第三周：SQL 的 DDL和 DQL基本用法
### DDL数据定义语言
- 创建表
```
CREATE TABLE table_name (
    column1 datatype [constraints],
    column2 datatype [constraints],
    ...
    [table_constraints]
);
```
### DQL数据查询语言 主要用于从数据库中查询数据
- 基本 SELECT 查询
```
--查询所有列
SELECT * FROM table_name;

-- 查询特定列
SELECT column1, column2 FROM table_name;

-- 使用别名
SELECT column1 AS alias_name FROM table_name;
SELECT column1 alias_name FROM table_name;  -- AS 可省略
```
## 第四周：实验课 
### 本周安装并配置了 PostgreSQL，并在DATAGRIP软件中运行，成功搭建了环境
-完成实践课作业
## 第五周：SQL字符串函数
### SQL字符串函数应用：文本处理与模糊查询
- 连接字符串CONCAT
```
-- CONCAT 连接多个字符串
SELECT CONCAT(first_name, ' ', last_name) AS full_name FROM employees;

-- 使用连接符(CONCAT_WS)
SELECT CONCAT_WS('-', '2023', '05', '20') AS formatted_date;  -- 结果: 2023-05-20
```
- 截取字符串SUBSTRING
```
-- SUBSTRING/SUBSTR 截取子串
SELECT SUBSTRING('Hello World', 1, 5) AS result;  -- 结果: Hello
SELECT SUBSTR('Hello World', 7) AS result;       -- 结果: World

-- LEFT/RIGHT 从左右截取
SELECT LEFT('Hello World', 5) AS left_part;      -- 结果: Hello
SELECT RIGHT('Hello World', 5) AS right_part;    -- 结果: World
```
## 第六周：NULL 的含义、聚集函数、分组聚集
### NULL 的特殊性
### NULL 表示"未知"或"不存在"的值，具有以下特点：
- 不是0，也不是空字符串
- 任何与NULL的比较运算结果都是UNKNOWN
- 需要使用IS NULL或IS NOT NULL进行判断
### 聚集函数对值集计算返回单个值，自动忽略NULL值
### 分组聚集 (GROUP BY)
- 基本分组语法
```
SELECT 
    dept_id,
    COUNT(*) AS employee_count,
    AVG(salary) AS avg_salary
FROM employees
GROUP BY dept_id;
```
## 第七周：增、删、改操作
- INSERT 语句 - 精确数据插入
- UPDATE 语句 - 精确数据更新
- DELETE 语句 - 精确数据删除
## 第八周：连接操作
- 
