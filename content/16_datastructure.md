# 数据结构

## 供应商

供应商数据表，记录供应商相关的数据。

```sql
DROP TABLE IF EXISTS `supplier`;
CREATE TABLE `supplier` (
  `code` varchar(255) DEFAULT '' COMMENT '供应商编号',
  `name` varchar(255) DEFAULT '' COMMENT '供应商名称',
  `contact` varchar(255) DEFAULT '' COMMENT '联系人',
  `phone` varchar(255) DEFAULT '' COMMENT '联系电话',
  `create_time` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '创建时间',
  `creator` varchar(255) DEFAULT '' COMMENT '创建人',
  `address` varchar(255) DEFAULT '' COMMENT '地址',
  `area` varchar(255) DEFAULT '' COMMENT '区域',
  `email` varchar(255) DEFAULT '' COMMENT '邮箱',
  `status` varchar(255) DEFAULT '' COMMENT '状态',
  `collect_name` varchar(255) DEFAULT '' COMMENT '首款名称',
  `bank_name` varchar(255) DEFAULT '' COMMENT '开户行名称',
  `bank_account_number` varchar(255) DEFAULT '' COMMENT '银行账户',
  `remark` varchar(255) DEFAULT '' COMMENT '备注'
) ENGINE=InnoDB DEFAULT CHARSET=utf8;


```

## 供应商拜访记录

供应商的每一次拜访需要记录。

```sql
DROP TABLE IF EXISTS `supplier_visit`;
CREATE TABLE `supplier_visit` (
  `visit_date` date DEFAULT '0000-00-00' COMMENT '拜访日期',
  `visit_object` varchar(255) DEFAULT NULL,
  `company_distribution` varchar(255) DEFAULT '' COMMENT '公司分布情况',
  `company_scale` varchar(255) DEFAULT '' COMMENT '公司规模',
  `company_asset` varchar(255) DEFAULT '' COMMENT '公司资产',
  `dicision_process` varchar(255) DEFAULT '' COMMENT '决策流程',
  `data_clean` varchar(255) DEFAULT '' COMMENT '数据清除',
  `optitude` varchar(255) DEFAULT '' COMMENT '资质',
  `contract` varchar(255) DEFAULT '' COMMENT '合同',
  `invoice` varchar(255) DEFAULT '' COMMENT '发票',
  `rent` varchar(255) DEFAULT '' COMMENT '租赁',
  `intention` varchar(255) DEFAULT '' COMMENT '意向',
  `other` varchar(255) DEFAULT '' COMMENT '其他'
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='供应商拜访记录';
```

## 采购单

```sql
DROP TABLE IF EXISTS `purchase`;
CREATE TABLE `purchase` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `purchase_code` varchar(255) DEFAULT '' COMMENT '采购编号',
  `client_purchase_code` varchar(255) DEFAULT '' COMMENT '客户采购编号',
  `company` varchar(255) DEFAULT '' COMMENT '所属公司',
  `repository` varchar(255) DEFAULT '' COMMENT '所属仓库',
  `create_time` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '创建时间',
  `creator` varchar(255) DEFAULT '' COMMENT '创建人',
  `belong` varchar(255) DEFAULT '' COMMENT '项目归属： 常规业务',
  `strategy_center` varchar(255) DEFAULT '' COMMENT '战略中心',
  `evaluation` decimal(15,2) DEFAULT '0.00' COMMENT '采购估价',
  `deal_price` decimal(15,2) DEFAULT '0.00' COMMENT '成交总价',
  `include_tax` tinyint(1) DEFAULT '0' COMMENT '是否含税',
  `tax_rate` double(6,2) DEFAULT '0.00' COMMENT '税率',
  `pay_type` varchar(255) DEFAULT '' COMMENT '付款方式： 线下转账',
  `settlement_type` varchar(255) DEFAULT '' COMMENT '结算方式： 后付',
  `sale_price` decimal(15,2) DEFAULT '0.00' COMMENT '销售金额',
  `cost_price` decimal(15,2) DEFAULT '0.00' COMMENT '销售成本',
  `sale_profit` decimal(15,2) DEFAULT '0.00' COMMENT '销售利润',
  `supplier` varchar(255) DEFAULT '' COMMENT '供应商',
  `recipient` varchar(255) DEFAULT '' COMMENT '承接人',
  `pickup_time` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '提货时间',
  `delivery_type` varchar(255) DEFAULT '' COMMENT '配送方式',
  `conclude_performance` tinyint(1) DEFAULT '0' COMMENT '是否计入业绩',
  `offer_code` varchar(255) DEFAULT '' COMMENT '报价单编号',
  `scrap_reason` varchar(255) DEFAULT '' COMMENT '报废原因',
  `remark` varchar(255) DEFAULT '' COMMENT '备注信息',
  `status` int(11) DEFAULT '0' COMMENT '记录状态',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='采购单数据表';
```

## 提货单

```sql
CREATE TABLE `purchase_pick_up` (
  `purchase_code` varchar(255) DEFAULT '' COMMENT '采购单编号',
  `client_purchase_code` varchar(255) DEFAULT '' COMMENT '客户端采购编号',
  `supplier` varchar(255) DEFAULT '' COMMENT '供应商',
  `store` varchar(255) DEFAULT '' COMMENT '仓库',
  `technician` varchar(255) DEFAULT '' COMMENT '技术员',
  `pickup_time` datetime DEFAULT '0000-00-00 00:00:00',
  `pickup_info` varchar(255) DEFAULT '' COMMENT '提货信息',
  `create_time` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '提货时间',
  `status` varchar(255) DEFAULT '' COMMENT '提货状态： 待提货，提货中，已完成',
  `remark` varchar(255) DEFAULT '' COMMENT '备注',
  `creator` varchar(255) DEFAULT '' COMMENT '创建人',
  `operator` varchar(255) DEFAULT '' COMMENT '承接人'
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='采购提货单';
```

## 收获通知单

```sql
CREATE TABLE `good_receiving` (
  `code` varchar(255) DEFAULT '' COMMENT '收获通知单',
  `purchase_code` varchar(255) DEFAULT '' COMMENT '订单编号（采购单编号）',
  `client_purchase_code` varchar(255) DEFAULT '' COMMENT '客户采购单编号',
  `type` varchar(255) DEFAULT '' COMMENT '收货单类型：采购收货，退款收获，调拨收获',
  `store` varchar(255) DEFAULT '' COMMENT '仓库',
  `status` varchar(255) DEFAULT '' COMMENT '收货单状态： 待收货，已入库，部分入库，已签收，生产完成，已作废',
  `logistics_code` varchar(255) DEFAULT '' COMMENT '物流单号',
  `receive_time` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '提货时间',
  `remark` varchar(255) DEFAULT '' COMMENT '备注',
  `deliver_type` varchar(255) DEFAULT '' COMMENT '配送方式： 物流快递，上门提货，无',
  `create_time` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '创建时间',
  `creator` varchar(255) DEFAULT '' COMMENT '创建人',
  `trade_client` varchar(255) DEFAULT '' COMMENT '供应商/销售客户',
  `company` varchar(255) DEFAULT '' COMMENT '公司'
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='收获通知单';
```

## 资产表

```sql
DROP TABLE IF EXISTS `asset`;
CREATE TABLE `asset` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `asset_type` varchar(255) DEFAULT '' COMMENT '资产类型： 整机设备，手机平板，其他设备， 配件',
  `sn_code` varchar(255) DEFAULT '' COMMENT '条形码/SN码',
  `purchase_code` varchar(255) DEFAULT '' COMMENT '采购单编号',
  `client_purchase_code` varchar(255) DEFAULT '' COMMENT '客户采购编号',
  `type` varchar(255) DEFAULT '' COMMENT '针对于asset_type有自己的子类型： 笔记本',
  `brand` varchar(255) DEFAULT '' COMMENT '品牌： 联想',
  `model` varchar(255) DEFAULT '' COMMENT '型号： T46OS',
  `location` varchar(255) DEFAULT '' COMMENT '所在位置：上海回收舱',
  `cpu` varchar(255) DEFAULT '' COMMENT 'cpu',
  `struction` varchar(255) DEFAULT '' COMMENT '产品结构',
  `memory` int(11) DEFAULT '8' COMMENT '内存',
  `display_card` varchar(255) DEFAULT '' COMMENT '显卡',
  `hard_disk` varchar(255) DEFAULT '' COMMENT '硬盘',
  `purchase_price` decimal(15,2) DEFAULT '0.00' COMMENT '采购价格',
  `sale_price` decimal(15,2) DEFAULT '0.00' COMMENT '销售价格',
  `refund_amount` decimal(15,2) DEFAULT '0.00' COMMENT '退款金额',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='资产数据表，用于存储采购回来的资产的记录归档，包括整机设备，手机/平板，配件和其他';
```

## 销售客户

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

## 销售单

```sql
CREATE TABLE `sale` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `sale_code` varchar(255) DEFAULT '' COMMENT '销售单编号',
  `company` varchar(255) DEFAULT '' COMMENT '所属公司',
  `sale_channel` varchar(255) DEFAULT '' COMMENT '销售渠道',
  `creator` varchar(255) DEFAULT '' COMMENT '创建人',
  `create_time` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '创建时间',
  `sale_time` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '销售时间',
  `offer_code` varchar(255) DEFAULT '' COMMENT '竞价单编号',
  `salesman` varchar(255) DEFAULT '' COMMENT '业务员',
  `client` varchar(255) DEFAULT '' COMMENT '客户名称',
  `consignee_info` varchar(255) DEFAULT '' COMMENT '收货信息',
  `deliver_type` varchar(255) DEFAULT '' COMMENT '配送方式',
  `total_price` decimal(15,2) DEFAULT '0.00' COMMENT '总价',
  `refund_amount` decimal(15,2) DEFAULT '0.00' COMMENT '退款金额',
  `order_price` decimal(15,2) DEFAULT '0.00' COMMENT '订单金额',
  `conclude_tax` tinyint(1) DEFAULT '0' COMMENT '是否含税',
  `tax_rate` double(6,2) DEFAULT '0.00' COMMENT '税率',
  `pay_type` varchar(255) DEFAULT '' COMMENT '付款方式',
  `payer` varchar(255) DEFAULT '' COMMENT '付款人名称',
  `settlement_type` varchar(255) DEFAULT '' COMMENT '结算方式',
  `pay_cert` varchar(255) DEFAULT '' COMMENT '付款凭证',
  `outbound_deliver_cert` varchar(255) DEFAULT '' COMMENT '出库凭证',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='销售数据表';


```

## 销售物流

```sql
CREATE TABLE `sale_logistics` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `sale_code` varchar(255) DEFAULT '' COMMENT '销售单编号',
  `location` varchar(255) DEFAULT '' COMMENT '所在仓库位置',
  `deliver_company` varchar(255) DEFAULT '' COMMENT '快递公司',
  `create_time` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '物流生成时间',
  `code` varchar(255) DEFAULT '' COMMENT '物流单号',
  PRIMARY KEY (`id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='销售物流信息';


```

## 发货单

```sql
CREATE TABLE `dispatch` (
  `code` varchar(255) DEFAULT '' COMMENT '发货单编号',
  `sale_code` varchar(255) DEFAULT '' COMMENT '销售单编号',
  `type` varchar(255) DEFAULT '' COMMENT '发货单类型： 销售发货，调拨发货，采购退货发货',
  `creator` varchar(255) DEFAULT '' COMMENT '创建人',
  `create_time` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '创建时间',
  `sale_time` date DEFAULT '0000-00-00' COMMENT '销售日期',
  `client` varchar(255) DEFAULT '' COMMENT '客户名称',
  `receive_info` varchar(255) DEFAULT '' COMMENT '收货信息',
  `deliver_type` varchar(255) DEFAULT '' COMMENT '配送方式',
  `company` varchar(255) DEFAULT '' COMMENT '所属公司',
  `store` varchar(255) DEFAULT '' COMMENT '仓库',
  `remark` varchar(255) DEFAULT '' COMMENT '备注',
  `status` varchar(255) DEFAULT '' COMMENT '发货状态：代发货 ，已发货'
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='发货单';


```

## 销售竞价

```sql
CREATE TABLE `sales_biding` (
  `code` varchar(255) DEFAULT '' COMMENT '竞价单编号',
  `company` varchar(255) DEFAULT '' COMMENT '所属公司',
  `remark` varchar(255) DEFAULT '' COMMENT '备注信息',
  `bid_deadline` date DEFAULT '0000-00-00',
  `standard_price` decimal(15,2) DEFAULT NULL,
  `participants` varchar(255) DEFAULT '' COMMENT '竞价参与人',
  `creator` varchar(255) DEFAULT '' COMMENT '创建人',
  `warehouse` varchar(255) DEFAULT '' COMMENT '所属仓库',
  `product_type` varchar(255) DEFAULT '' COMMENT '精品类别',
  `offline_time` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '段标落地时间',
  `bid_participation` varchar(255) DEFAULT '' COMMENT '竞价参与度',
  `device_count` int(11) DEFAULT '0' COMMENT '竞价设备总数',
  `purchase_price` decimal(15,2) DEFAULT '0.00' COMMENT '采购成本价',
  `set_standard_price` tinyint(1) DEFAULT '0' COMMENT '是否设置标准价',
  `bid_price` decimal(15,2) DEFAULT '0.00' COMMENT '中标金额',
  `bid_winner` varchar(255) DEFAULT '' COMMENT '中标人',
  `profit` decimal(15,2) DEFAULT '0.00' COMMENT '利润',
  `status` varchar(255) DEFAULT '' COMMENT '状态： 待发布，竞价中，已结束',
  `bid_continue` tinyint(1) DEFAULT '0' COMMENT '是否需单',
  `create_time` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '创建时间'
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='销售竞价单';

```

## 审核任务

```sql
CREATE TABLE `audit_task` (
  `code` varchar(255) NOT NULL DEFAULT '' COMMENT '订单编号',
  `order_code` varchar(255) DEFAULT '' COMMENT '订单编号',
  `type` varchar(255) DEFAULT '' COMMENT '审核类型： 采购单，销售单，调拨单，退货单，合同管理了，工单',
  `client` varchar(255) DEFAULT '' COMMENT '客户名称',
  `handler` varchar(255) DEFAULT '' COMMENT '处理人',
  `create_time` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '创建时间',
  `handle_time` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '任务处理时间',
  `creator` varchar(255) DEFAULT '' COMMENT '创建人',
  `status` varchar(255) DEFAULT '' COMMENT '状态： 待办，已办',
  `workflow` varchar(255) DEFAULT '' COMMENT '工作流名称',
  `task_name` varchar(255) DEFAULT '' COMMENT '当前任务名称',
  `diagram` varchar(255) DEFAULT '' COMMENT '流程图片',
  `task_id` varchar(255) DEFAULT '' COMMENT '任务ID',
  `audit_action` varchar(255) DEFAULT '' COMMENT '审批动作： 提交审批',
  `remark` varchar(255) DEFAULT '' COMMENT '备注',
  `attachment` varchar(255) DEFAULT '' COMMENT '附件信息',
  PRIMARY KEY (`code`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='审核任务';


```

## 报价单

```sql
CREATE TABLE `offer` (
  `code` varchar(255) NOT NULL DEFAULT '' COMMENT '报价单编号',
  `supplier` varchar(255) DEFAULT '',
  `creator` varchar(255) DEFAULT '',
  `create_time` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '创建时间',
  `deadline` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '报价截止时间',
  `lefttime` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '报价剩余时间',
  `period` int(11) DEFAULT '0' COMMENT '有效期',
  `wintime` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '中标时间',
  `status` varchar(255) DEFAULT '' COMMENT '状态： 待提交，报价中，已报价，已取消',
  `bid_status` varchar(255) DEFAULT '' COMMENT '中标状态： 未中标，已中标，仅询价，未处理，部分中标',
  `bid` tinyint(4) DEFAULT '0' COMMENT '是否投标',
  `bid_record` varchar(255) DEFAULT '' COMMENT '投标记录',
  `remark` varchar(255) DEFAULT '' COMMENT '备注',
  `offer_amount` decimal(10,0) DEFAULT '0' COMMENT '报价总金额',
  `bid_amount` decimal(10,0) DEFAULT '0' COMMENT '中标金额',
  `off_bid_amount` decimal(10,0) DEFAULT '0' COMMENT '失标金额',
  `order_source` varchar(255) DEFAULT '' COMMENT '订单来源',
  `project_belong` varchar(255) DEFAULT '' COMMENT '项目归属',
  `strategy_center` varchar(255) DEFAULT '' COMMENT '战略中心',
  `offer_time` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '报价时间',
  PRIMARY KEY (`code`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='报价单';


```

## 销售竞价单

```sql
CREATE TABLE `sales_biding` (
  `code` varchar(255) DEFAULT '' COMMENT '竞价单编号',
  `company` varchar(255) DEFAULT '' COMMENT '所属公司',
  `remark` varchar(255) DEFAULT '' COMMENT '备注信息',
  `bid_deadline` date DEFAULT '0000-00-00',
  `standard_price` decimal(15,2) DEFAULT NULL,
  `participants` varchar(255) DEFAULT '' COMMENT '竞价参与人',
  `creator` varchar(255) DEFAULT '' COMMENT '创建人',
  `warehouse` varchar(255) DEFAULT '' COMMENT '所属仓库',
  `product_type` varchar(255) DEFAULT '' COMMENT '精品类别',
  `offline_time` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '段标落地时间',
  `bid_participation` varchar(255) DEFAULT '' COMMENT '竞价参与度',
  `device_count` int(11) DEFAULT '0' COMMENT '竞价设备总数',
  `purchase_price` decimal(15,2) DEFAULT '0.00' COMMENT '采购成本价',
  `set_standard_price` tinyint(1) DEFAULT '0' COMMENT '是否设置标准价',
  `bid_price` decimal(15,2) DEFAULT '0.00' COMMENT '中标金额',
  `bid_winner` varchar(255) DEFAULT '' COMMENT '中标人',
  `profit` decimal(15,2) DEFAULT '0.00' COMMENT '利润',
  `status` varchar(255) DEFAULT '' COMMENT '状态： 待发布，竞价中，已结束',
  `bid_continue` tinyint(1) DEFAULT '0' COMMENT '是否续单',
  `create_time` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '创建时间'
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='销售竞价单';


```

## 销售报价单

```sql
CREATE TABLE `sale_offer` (
  `code` varchar(255) NOT NULL DEFAULT '' COMMENT '编号',
  `bid_code` varchar(255) DEFAULT '' COMMENT '竞价单编号',
  `creator` varchar(255) DEFAULT '' COMMENT '创建者',
  `create_time` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '创建时间',
  `deadline` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '报价截止时间',
  `lefttime` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '报价剩余时间',
  `publish_time` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '结果公布时间',
  `status` varchar(255) DEFAULT '' COMMENT '状态： 待提交，报价中，已报价，已取消',
  `bid_status` varchar(255) DEFAULT '' COMMENT '竞价单状态',
  `bid` tinyint(4) DEFAULT '0' COMMENT '是否投标',
  `remark` varchar(255) DEFAULT '' COMMENT '备注',
  `bid_amount` decimal(10,0) DEFAULT '0' COMMENT '中标金额',
  `create_order` tinyint(1) DEFAULT '0' COMMENT '是否建单',
  `in_order` tinyint(1) DEFAULT '0' COMMENT '竞价参与度',
  PRIMARY KEY (`code`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='销售报价单';


```

## 竞拍客户保证金

```sql
CREATE TABLE `margin` (
  `code` varchar(255) DEFAULT '' COMMENT '流水号',
  `type` varchar(255) DEFAULT '' COMMENT '保证金类型',
  `opr_type` varchar(255) DEFAULT '' COMMENT '操作类型： 价款，冻结，退还，扣款，申请退款',
  `amount` decimal(10,0) DEFAULT '0' COMMENT '发生额',
  `description` varchar(255) DEFAULT '' COMMENT '资金描述',
  `channel` varchar(255) DEFAULT '' COMMENT '渠道',
  `client` varchar(255) DEFAULT '' COMMENT '客户名称',
  `offer_code` varchar(255) DEFAULT '' COMMENT '关联竞价单',
  `opr_time` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '操作时间',
  `status` varchar(255) DEFAULT '' COMMENT '状态'
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='保证金数据表';


```

## 保证金充值

```sql
CREATE TABLE `margin_recharge` (
  `code` varchar(255) DEFAULT '' COMMENT '流水号',
  `collect_company` varchar(255) DEFAULT '' COMMENT '收款公司',
  `collect_account_number` varchar(255) DEFAULT '' COMMENT '收款账户',
  `bank_name` varchar(255) DEFAULT '' COMMENT '银行名称',
  `account` varchar(255) DEFAULT '' COMMENT '户名',
  `pay_account_number` varchar(255) DEFAULT '' COMMENT '付款账号',
  `amount` decimal(10,0) DEFAULT NULL,
  `margin_type` varchar(255) DEFAULT '' COMMENT '保证金类型',
  `client` varchar(255) DEFAULT '' COMMENT '销售客户名称',
  `status` varchar(255) DEFAULT '' COMMENT '状态',
  `pay_time` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '付款时间',
  `auditor` varchar(255) DEFAULT '' COMMENT '审核人',
  `pay_certification` varchar(255) DEFAULT '' COMMENT '付款凭证'
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='保证金充值数据表';


```

## 调拨单

```sql
CREATE TABLE `scheduler` (
  `code` varchar(255) NOT NULL DEFAULT '' COMMENT '编号',
  `type` varchar(255) DEFAULT '' COMMENT '调拨单类型： 正常调拨',
  `company` varchar(255) DEFAULT '' COMMENT '所属公司',
  `source_store` varchar(255) DEFAULT '' COMMENT '原仓库',
  `dest_store` varchar(255) DEFAULT '' COMMENT '目标仓库',
  `status` varchar(255) DEFAULT '' COMMENT '调拨单状态： 待提交；审核中；待发货；待受货；已完成；已取消',
  `creator` varchar(255) DEFAULT '' COMMENT '创建人',
  `create_time` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '创建时间',
  `remark` varchar(255) DEFAULT '' COMMENT '备注',
  `mode` varchar(255) DEFAULT '' COMMENT '调拨方式： 物流配送；自提',
  PRIMARY KEY (`code`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='调拨单';

```

## 合同

```sql
CREATE TABLE `contract` (
  `code` varchar(255) NOT NULL COMMENT '合同编号',
  `name` varchar(255) DEFAULT '' COMMENT '合同名称',
  `type` varchar(255) DEFAULT '' COMMENT '合同类型',
  `client_purchase_code` varchar(255) DEFAULT '' COMMENT '客户采购单编号',
  `first_party` varchar(255) DEFAULT '' COMMENT '甲方',
  `second_party` varchar(255) DEFAULT '' COMMENT '乙方',
  `third_party` varchar(255) DEFAULT '' COMMENT '丙方',
  `fourth_party` varchar(255) DEFAULT '' COMMENT '丁方',
  `operator` varchar(255) DEFAULT '' COMMENT '负责人',
  `deadline` date DEFAULT '0000-00-00' COMMENT '合同到期日',
  `attachment` varchar(255) DEFAULT '' COMMENT '合同附件',
  `introduction` varchar(255) DEFAULT '' COMMENT '合同简介',
  `create_time` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '合同创建时间',
  `status` varchar(255) DEFAULT '' COMMENT '合同状态',
  PRIMARY KEY (`code`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='合同';


```

## 消息

```sql
CREATE TABLE `message` (
  `topic` varchar(255) DEFAULT '' COMMENT '主题',
  `content` varchar(255) DEFAULT '' COMMENT '内容',
  `read` tinyint(4) DEFAULT '0' COMMENT '是否已读',
  `to` varchar(255) DEFAULT '' COMMENT '收件人',
  `from` varchar(255) DEFAULT '' COMMENT '发件人',
  `create_time` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '发送时间，创建时间'
) ENGINE=InnoDB DEFAULT CHARSET=utf8;


```

## 工单

```sql
CREATE TABLE `work_order` (
  `code` varchar(50) NOT NULL COMMENT '工单编号',
  `type` varchar(255) DEFAULT '' COMMENT '工单类型',
  `supplier` varchar(255) DEFAULT '' COMMENT '供应商',
  `contact` varchar(255) DEFAULT '' COMMENT '联系人姓名',
  `phone` varchar(255) DEFAULT '' COMMENT '联系电话',
  `addresss` varchar(255) DEFAULT '' COMMENT '地址',
  `door_time` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '上门时间',
  `device_list_attachment` varchar(255) DEFAULT '' COMMENT '设备清单附件',
  `handler` varchar(255) DEFAULT '' COMMENT '承接人',
  `strategy_center` varchar(255) DEFAULT '' COMMENT '战略中心',
  `offer_code` varchar(255) DEFAULT '' COMMENT '报价单编号',
  `running_handler` varchar(255) DEFAULT NULL,
  `operator` varchar(255) DEFAULT '' COMMENT '运营负责人',
  `remark` varchar(255) DEFAULT '' COMMENT '备注',
  `create_time` datetime DEFAULT '0000-00-00 00:00:00' COMMENT '工单创建时间',
  `status` varchar(255) DEFAULT '' COMMENT '工单状态',
  PRIMARY KEY (`code`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COMMENT='工单数据表';


```
