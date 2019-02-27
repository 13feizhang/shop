# 前台
## 子产品模块
+ 2019年02月20日
    + API初始化 
+ Data
    + products 主产品表
        + id (Long) - ID
        + categoryId (Long) - 分类ID
        + title (String) - 产品名称
        + briefDescription (String) - 简述
        + description (String) - 描述
        + brandId (Long) - 品牌ID
        + mainFeature (String) - 主参数
     + accessory 附件表
        + id (Long) - ID
        + type (Integer) - 类型(0：视频  1：音频  2:文件)
        + filename (String) - 存放文件的URL，如果是视频为空
        + extesion (String) - 扩展名
        + title (String) - 名称
        + content (String) - 品牌ID
        + description (String) - 主参数
        + filesize (Integer) - 文件大小
        + duration (Long) - 描述
        + enabled (int) - 使能 0禁止 1启用
        + creator (long) - 创建人
        + modifier (long) - 修改人
        + created (date) - 创建时间
        + modified (date) - 修改时间 
    + SubProducts 子产品表
        + id (Long) - ID
        + mainProductId (Long) - 主产品ID
        + subFeature (String) - 自参数
        + keyWords (String) - 淘宝关键字
        + specification (String) - 规格
        + colour (Long) - 颜色ID
        + thumbsUp (Integer) - 赞
        + thumbsDown (Integer) - 踩
        + isShow (Integer) - 是否展示
        + enabled (int) - 使能 0禁止 1启用
        + creator (long) - 创建人
        + modifier (long) - 修改人
        + created (date) - 创建时间
        + modified (date) - 修改时间 
    + pictures 产品图片表
        + id (Long) - ID
        + pictureurl (String) - 图片链接
        + extension (String) - 扩展名
        + title (String) - 名称属性
        + description (String) - 图片描述
        + extra (String) - 其它信息
        + md5 (String) - md5值
        + groupId (Integer) - 1为正常图；36为360图
        + orderNo (Integer) - 引用
        + enabled (int) - 使能 0禁止 1启用
        + creator (long) - 创建人
        + modifier (long) - 修改人
        + created (date) - 创建时间
        + modified (date) - 修改时间 
    + dealers 经销商表
        + id (Long) - ID
        + dealerName (Long) - 名称
        + dealerTel (String) - 电话
        + dealerEmail (String) - 邮件
        + dealerAddress (String) - 地址
        + dealerMainBrand (String) - 主营品牌
        + enabled (int) - 使能 0禁止 1启用
        + creator (long) - 创建人
        + modifier (long) - 修改人
        + created (date) - 创建时间
        + modified (date) - 修改时间 
    + prices 价格表
        + id (Long) - ID
        + subProductId (Long) - 子产品ID
        + tbProductId (Long) - 淘宝id
        + tbItemId (Long) - 实际淘宝id
        + source (String) - 来源
        + currency (Integer) - 币别ID
        + isInland (Integer) - 是否国内 1：国内，0：国外
        + enabled (int) - 使能 0禁止 1启用
        + creator (long) - 创建人
        + modifier (long) - 修改人
        + created (date) - 创建时间
        + modified (date) - 修改时间 
    + pictures 淘宝产品表
        + id (Long) - ID
        + subProductId (Long) - 商品id
        + itemid (String) - 商品id
        + title (String) - 名称
        + description (String) - 描述
        + reservePrice (String) - 一口价
        + zkFinalPrice (String) - 折扣价
        + isCoupon (Integer) - 是否有劵
        + volume (Integer) - 30天销量
        + itemUrl (String) - 商品详情页链接
        + couponClickUrl (String) - 优惠劵链接
        + couponInfo (String) - 优惠卷信息
        + couponRemainCount (Long) - 优惠劵剩余数量
        + couponTotalCount (Long) - 优惠劵数量
        + couponStartTime (Date) - 优惠劵开始时间
        + couponEndTime (Date) - 优惠劵结束时间
        + enabled (int) - 使能 0禁止 1启用
        + created (date) - 创建时间

### 查询子产品详情(客户端) [GET] /subProducts/{id}
+ Parameters
     +  id 子产品id
+ Description 
     + products 主产品 
     + specifications 主产品下所有规格
     + colours 主产品下所有的颜色 
     + brands 品牌
     + accessories 附件参数
     + subProductsList 子产品集合(通过子产品集合里specification与colour确定子产品id，唯一值{id}进行查询)
     + categories 子产品所属分类
     + availableSpecifications 当前子产品<颜色>下有的规格数据
     + availableColours 当前子产品<规格> 下有的颜色数据
 
+ Response 200 (Application/json)

      {
        "data": {
            "mainProductId": 1,
            "specification": "8GB+128GB",
            "colour": 1,
            "thumbsUp": 8,
            "thumbsDown": 2,
            "products": {
                "id": 1,
                "categoryId": 3,
                "title": "小米8",
                "briefDescription": "【品质特惠】骁龙845处理器，成交价2399！红外人脸解锁，AI变焦双摄，AI语音助手！推荐购买白色",
                "description": "小米公司最新款手机",
                "brandId": 1,
                "specifications": [
                    "6GB+64GB",
                    "8GB+222GB",
                    "8GB+128GB"
                ],
                "colours": [
                    {
                        "id": 1,
                        "colourName": "红色"
                    },
                    {
                        "id": 3,
                        "colourName": "蓝色"
                    },
                    {
                        "id": 2,
                        "colourName": "黑色"
                    }
                ],
                "brands": {
                    "name": "小米",
                    "logo": "/static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
                },
                "categoryses": [
                    {
                        "id": 1,
                        "parentId": 0,
                        "title": "麦克风",
                        "leaf": 0
                    },
                    {
                        "id": 2,
                        "parentId": 1,
                        "title": "无线麦克风",
                        "leaf": 0
                    },
                    {
                        "id": 3,
                        "parentId": 2,
                        "title": "BLUE无线麦克风",
                        "leaf": 1
                    }
                ]
            },
            "accessories": [
                {
                    "type": 0,
                    "filename": "https://jdvodoss.jcloudcache.com/vodtransgzp1251412368/7447398156451886582/v.f30.mp4?dockingId=aee5a279-b858-4e06-a8e6-3accdc3f8014&storageSource=3",
                    "title": "小米8展示视频",
                    "description": "小米8展示视频",
                    "filesize": 0,
                    "duration": 0
                },
                {
                    "type": 1,
                    "filename": "https://jdvodoss.jcloudcache.com/vodtransgzp1251412368/7447398156451886582/v.f30.mp4?dockingId=aee5a279-b858-4e06-a8e6-3accdc3f8014&storageSource=3",
                    "title": "小米8展示音频",
                    "description": "小米8展示音频",
                    "filesize": 0,
                    "duration": 0
                }
            ],
            "subProductsList": [
                {
                    "id": 1,
                    "specification": "6GB+64GB",
                    "colour": 1
                },
                {
                    "id": 2,
                    "specification": "8GB+128GB",
                    "colour": 1
                },
                {
                    "id": 3,
                    "specification": "6GB+64GB",
                    "colour": 2
                },
                {
                    "id": 4,
                    "specification": "8GB+128GB",
                    "colour": 3
                },
                {
                    "id": 5,
                    "specification": "8GB+222GB",
                    "colour": 3
                }
            ],
            "availableSpecifications": [
                "6GB+64GB",
                "8GB+128GB"
            ],
            "availableColours": [
                1,
                3
            ]
        }
      }

### 查询子产品价格详情(客户端) [GET] /price/{id}
+ Parameters
     +  id 子产品id
+ Description 
    +  [MUST] Authenticated
    + [MUST] ROLE_ADMIN
+ Response 200 (Application/json)

       {
        "data": {
            "id": 2,
            "creator": 0,
            "modifier": 0,
            "created": "2019-02-22 10:19:27",
            "modified": "2019-02-22 10:19:27",
            "subProductId": 2,
            "tbProductId": 2,
            "tbItemId": 10002,
            "source": "224",
            "currency": 1,
            "isInland": 1,
            "reservePrice": "224",
            "shopUrl": "https://item.jd.com/4586925.html#crumb-wrap",
            "subCurrency": "¥"
        }
      }

### 产品赞踩 [GET] /subProducts/thumbs/{id}?thumbsUp=1
+ Parameters
     +  id 子产品id
     +  thumbsUp 当请求为<点赞>添加子产品的点赞数
     +  thumbsDown 当请求为<踩>添加此子产品的踩数
+ Response 200 (Application/json)
    
### 产品收藏 [POST] /collects
+ Parameters
     +  mainProductId 主产品id
+ Description 
    +  [MUST] Authenticated
    + [MUST] ROLE_ADMIN
+ Request（application/json）

      {
    	 "data":{
    		"mainProductId":1
    	  }
      }

+ Response 200 (Application/json)

      {
        "data": {
            "id": 1,
            "type": "collects"
        }
      }
