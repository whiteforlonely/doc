# 销售客户管理

## 客户

```sql
CREATE TABLE `client` (
  `code` varchar(255) NOT NULL DEFAULT '' COMMENT '客户编号',
  `type` varchar(255) DEFAULT '' COMMENT '客户类型： 个人，企业',
  `name` varchar(255) DEFAULT '' COMMENT '名称',
  `contact` varchar(255) DEFAULT '' COMMENT '联系人',
  `contact_way` varchar(255) DEFAULT '' COMMENT '联系方式',
  `product_type` varchar(255) DEFAULT '' COMMENT '主营品类',
  `company` varchar(255) DEFAULT '' COMMENT '所属公司',
  `salesman` varchar(255) DEFAULT '' COMMENT '业务员',
  `order_time` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '首次下单时间',
  `creator` varchar(255) DEFAULT '' COMMENT '创建人',
  `create_time` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '创建时间',
  `force_verified` tinyint(1) DEFAULT '0' COMMENT '证件是否必传',
  `client_source` varchar(255) DEFAULT '' COMMENT '客户来源',
  `delivery_address` varchar(255) DEFAULT '' COMMENT '收货地址',
  PRIMARY KEY (`code`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='销售客户，即购买仓库资产的客户。';
```

### 操作

1. **添加**

2. **查询客户列表**

3. **导出客户列表**

4. **客户资料上传**

5. **编辑客户**

6. **删除客户**

7. **修改业务员**

8. **客户资料上传设置**