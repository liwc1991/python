# python
python项目


# 用户模块
## 用户表设计
```
create table user
(
  id int auto_increment primary key,      -- 自增id  主键
	phone_num char(11) NOT NULL,            -- 用户手机号
	device_id varchar(20) NOT NULL,         -- 用户注册设备号
	create_time timestamp NOT NULL,         -- 注册时间
	user_token varchar(50),           -- token(用户的唯一私钥)
	user_id char(32),                       -- 用户唯一标识userid
	user_password varchar(20),              -- 密码
	last_login_time timestamp,              -- 上次登录时间
	user_name varchar(20)                   -- 用户名
);
```

## 业务流程

## 接口
### 获取验证码接口

### 验证验证码接口


### 注册接口


# 商品模块
## 商品类别表设计
```
create table product_category
(
	id int auto_increment primary key,       -- 自增id  主键       
	name varchar(20),                        -- 分类名称
	code varchar(20),                        -- 分类编码
	category_order varchar(50),              -- 分类排序（order与数据库关键字冲突）
	parent_id int,                           -- 父级分类id 0父类 其他子类
	show_in_nav char(1)                      -- 是否显示在导航内 y显示 n不显示
);
```

## 商品表设计
```
create table product
(
	id int auto_increment primary key,      -- 自增id  主键       
	status tinyint,                         -- 商品状态 1 新增 2 已上架 3 已下架
	category_id int,                        -- 商品类别id
	name varchar(50),               		-- 商品名称
	introduction varchar(50),               -- 商品简介
	price decimal(6,2),                     -- 商品定价
	now_price decimal(6,2),                  -- 商品现价
	picture varchar(50),                    -- 商品图片
	create_time timestamp,                  -- 商品创建时间
	sale int,                               -- 商品销售数量
	stock int                               -- 商品库存
);
```

