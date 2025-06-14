# 自我评价
张子泰 42233009 数据科学与大数据
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
### 花了很多时间，一开始觉得操作繁琐，熟悉之后能适应
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
这些内容掌握不是很好，扣两分
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
- 内连接	只返回两表中匹配的行	INNER JOIN 或 JOIN
- 左外连接	返回左表所有行，右表不匹配的显示NULL	LEFT JOIN 或 LEFT OUTER JOIN
- 右外连接	返回右表所有行，左表不匹配的显示NULL	RIGHT JOIN 或 RIGHT OUTER JOIN
- 全外连接	返回两表所有行，不匹配的部分显示NULL	FULL JOIN 或 FULL OUTER JOIN
- 交叉连接	返回两表的笛卡尔积	CROSS JOIN
- 自然连接	自动按相同列名连接（不推荐使用）	NATURAL JOIN
### 感觉连接操作很复杂，掌握各种连接类型和连接条件的正确使用后，能编写高效SQL查询
## 第九周：PostgreSQL 数据类型
### 日期和时间类型
```
SELECT CURRENT_DATE, CURRENT_TIME, CURRENT_TIMESTAMP;

SELECT 
    CURRENT_TIMESTAMP + INTERVAL '1 hour' AS in_one_hour,
    CURRENT_DATE - INTERVAL '2 days' AS two_days_ago;
```
### 自定义数据类型
- PostgreSQL 允许创建用户定义的数据类型，增强数据抽象能力。
### 小数精度处理
| 类型                | 描述                     | 推荐场景               |
|---------------------|--------------------------|-----------------------|
| `NUMERIC(p,s)`      | 精确小数，p为总位数，s为小数位 | 财务计算、需要精确值的场景 |
| `DECIMAL(p,s)`      | 同NUMERIC                | 同NUMERIC             |
| `REAL`             | 4字节浮点数，约6位小数精度  | 科学计算，性能优先      |
| `DOUBLE PRECISION`  | 8字节浮点数，约15位小数精度 | 大多数科学计算         |
### SERIAL 自增主键
- PostgreSQL 有3种 SERIAL 类型：

| 类型          | 范围               | 存储大小 | 适用场景               |
|--------------|--------------------|----------|-----------------------|
| `SMALLSERIAL` | 1到32,767         | 2字节    | 小型表                 |
| `SERIAL`      | 1到2,147,483,647  | 4字节    | 大多数表(最常用)        |
| `BIGSERIAL`   | 1到9,223,372,036,854,775,807 | 8字节 | 超大型表               |
## 第十周：函数与过程
### 自定义函数和存储过程的编写
这一章学起来比较困难，对自定义函数的理解不够深入，实操也不是很熟练，需要借助ai完成内容，给自己扣了两分
## 第十一周：SQL注入原理
### 学习从外部调用sql，体会到数据库安全的重要性
- 常用连接方式有：
  Python: psycopg2 Java: JDBC	高性能，直接连接	需手动防注入
### SQL注入原理与防护
- SQL注入典型场景
```
-- 危险! 拼接SQL示例
SELECT * FROM users WHERE username = 'admin'--' AND password = '';
-- 实际执行(注释掉了密码验证)
SELECT * FROM users WHERE username = 'admin'
```
## 第十二周：ER图
- 这一章理解的很好，就是关系图，分清实体、属性、联系就好了
- 把 ER 图转化为关系模式有点难度
## 第十三周：理论
### 函数依赖基本概念
- 函数依赖定义

函数依赖(Functional Dependency, FD)是关系数据库中描述属性间依赖关系的核心概念。记作 X → Y，表示：
X（决定因素）唯一确定 Y（被决定因素）
即对于X的每个值，都有唯一的Y值与之对应
- 范式级别详解
1. 第一范式(1NF)
定义：所有属性都是原子性的，不可再分

特点：

每列都是最小数据单元

没有重复的组或数组

每行有唯一标识（主键）


2. 第二范式(2NF)
前提：已满足1NF

定义：消除非主属性对主键的部分函数依赖

判断步骤：

找出所有候选键

检查非主属性是否完全依赖于整个候选键

3. 第三范式(3NF)
前提：已满足2NF

定义：消除非主属性对主键的传递函数依赖

判断标准：

不存在非主属性A → 非主属性B的情况（除非A是超键）

4. BC范式(BCNF/Boyce-Codd NF)
强化版3NF：消除所有属性对候选键的传递依赖

判断标准：

对于所有函数依赖X → Y，X必须包含候选键

与3NF的区别：

3NF允许主属性对候选键的传递依赖

BCNF不允许任何属性（包括主属性）对候选键的传递依赖
## 第十三周、十四周：存储、索引、查询及事务
### PostgreSQL 核心功能

### 一、存储结构

### 表空间与存储管理

| 对象类型 | 描述 | 存储特性 |
|---------|------|---------|
| **表(Table)** | 数据的主要存储形式 | 分为堆文件(Heap File)存储 |
| **TOAST表** | 处理大字段的附属表 | 自动为超过2KB的字段创建 |
| **索引** | 加速数据访问的结构 | 与表数据分离存储 |
| **序列** | 自增序列生成器 | 小型的特殊表结构 |

```sql
-- 查看表存储空间
SELECT pg_size_pretty(pg_total_relation_size('table_name'));
```

### 二、索引类型

### PostgreSQL 主要索引对比

| 索引类型 | 适用场景 | 特点 | 创建语法 |
|---------|---------|------|---------|
| **B-tree** | 默认索引，适合范围查询 | 高度平衡树结构 | `CREATE INDEX idx_name ON table(col)` |
| **Hash** | 等值查询 | 仅支持=操作，无范围查询 | `CREATE INDEX idx_name ON table USING HASH(col)` |
| **GiST** | 地理数据、全文搜索 | 通用搜索树框架 | `CREATE INDEX idx_name ON table USING GIST(col)` |
| **GIN** | 多值类型(数组、JSON) | 倒排索引 | `CREATE INDEX idx_name ON table USING GIN(col)` |
| **BRIN** | 大型表有序数据 | 块范围索引 | `CREATE INDEX idx_name ON table USING BRIN(col)` |

```sql
-- 创建多列索引
CREATE INDEX idx_employee_name ON employees(last_name, first_name);

-- 查看索引使用情况
SELECT * FROM pg_stat_all_indexes WHERE relname = 'table_name';
```

### 三、查询优化

### 查询执行计划分析

| 执行计划节点 | 描述 | 性能提示 |
|-------------|------|---------|
| **Seq Scan** | 全表扫描 | 对大表性能差，考虑加索引 |
| **Index Scan** | 索引扫描 | 良好的选择性时高效 |
| **Bitmap Heap Scan** | 位图索引扫描 | 适合多条件组合查询 |
| **Nested Loop** | 嵌套循环连接 | 小表驱动大表时高效 |
| **Hash Join** | 哈希连接 | 内存充足时高效 |
| **Merge Join** | 合并连接 | 已排序数据时最佳 |

```sql
-- 分析查询计划
EXPLAIN ANALYZE SELECT * FROM orders WHERE customer_id = 100;

-- 强制使用索引(不推荐生产使用)
SET enable_seqscan = off;
```

### 四、事务处理

### 事务特性与隔离级别

| 隔离级别 | 脏读 | 不可重复读 | 幻读 | 描述 |
|---------|------|-----------|------|------|
| **Read Uncommitted** | 可能 | 可能 | 可能 | PostgreSQL 实际实现为Read Committed |
| **Read Committed** | 不可能 | 可能 | 可能 | 默认级别 |
| **Repeatable Read** | 不可能 | 不可能 | 可能 | 快照隔离 |
| **Serializable** | 不可能 | 不可能 | 不可能 | 完全串行化 |

```sql
-- 事务控制示例
BEGIN;
  -- SQL语句
  SAVEPOINT savepoint1;
  -- 更多SQL
  ROLLBACK TO savepoint1;
COMMIT;

-- 设置隔离级别
BEGIN TRANSACTION ISOLATION LEVEL REPEATABLE READ;
```
这一部分内容较多，未能深入理解，扣两分
## 第十五周：进行了期末复习，开始准备项目
## 第十六周：完成自我评价
