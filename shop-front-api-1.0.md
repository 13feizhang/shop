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
        + type (Integer) - 类型(0：视频  1：音频  2:文件 3:相关视频)
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
        + orderNo (Integer) - 360图展示顺序
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
     + mainProductId 主产品id 
     + products 主产品 
     + pictures 子产品图片
     + specifications 主产品下所有规格
     + colours 主产品下所有的颜色 
     + brands 品牌
     + accessories 附件参数
     + subProductsList 子产品集合(通过子产品集合里specification与colour确定子产品id，唯一值{id}进行查询)
     + categories 子产品所属分类
     + availableSpecifications 当前子产品<颜色>下有的规格数据
     + availableColours 当前子产品<规格> 下有的颜色数据
     + shopUrl 购买链接
     + imageRotation 是否有360图片
     + rotations 360图存放list
 
+ Response 200 (Application/json)

      {
        "data": {
        "id": 1,
        "mainProductId": 1,
        "specification": "6GB+64GB",
        "colour": 1,
        "thumbsUp": 17,
        "thumbsDown": 9,
        "pictures": [
            {
                "pictureurl": "//static.mifanxing.com/wx/image/29/15/990601.jpg",
                "title": "TestPicTURE2",
                "groupId": 1,
                "orderNo": 0
            },
            {
                "pictureurl": "//static.mifanxing.com/wx/image/29/15/990604.jpg",
                "title": "TestPicTURE",
                "groupId": 1,
                "orderNo": 0
            },
            {
                "pictureurl": "//static.mifanxing.com/wx/image/29/15/990602.jpg",
                "title": "TestPicTURE",
                "groupId": 1,
                "orderNo": 0
            },
            {
                "pictureurl": "//static.mifanxing.com/wx/image/29/15/990603.jpg",
                "title": "TestPicTURE2",
                "groupId": 1,
                "orderNo": 0
            }
        ],
        "shopUrl": "https://item.jd.com/1234567890",
        "products": {
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-03-01 11:14:48",
            "modified": "2019-03-01 11:15:20",
            "categoryId": 3,
            "title": "小米8",
            "briefDescription": "【品质特惠】骁龙845处理器，成交价2399！红外人脸解锁，AI变焦双摄，AI语音助手！推荐购买白色",
            "description": "小米公司最新款手机",
            "brandId": 1,
            "specifications": [
                "6GB+64GB",
                "x86",
                "8GB+222GB",
                "8GB+128GB"
            ],
            "colours": [
                {
                    "id": 1,
                    "colourName": "红色",
                    "colourPicture": "http://img.alicdn.com/imgextra/i4/804206007/TB2vBDgxxlmpuFjSZPfXXc9iXXa_!!804206007.jpg_40x40q90.jpg"
                },
                {
                    "id": 2,
                    "colourName": "黑色",
                    "colourPicture": "http://img.alicdn.com/imgextra/i4/804206007/TB2vBDgxxlmpuFjSZPfXXc9iXXa_!!804206007.jpg_40x40q90.jpg"
                },
                {
                    "id": 3,
                    "colourName": "蓝色",
                    "colourPicture": "http://img.alicdn.com/imgextra/i4/804206007/TB2vBDgxxlmpuFjSZPfXXc9iXXa_!!804206007.jpg_40x40q90.jpg"
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
                "type": 2,
                "filename": "https://static.mifanxing.com/yyren/image/week/20171110/1/Snare-1_1inchabove.mp3",
                "title": "文件",
                "description": "文件下载",
                "filesize": 0,
                "duration": 0
            },
            {
                "type": 1,
                "filename": "https://static.mifanxing.com/yyren/image/week/20171110/1/Snare-1_1inchabove.mp3",
                "title": "音频",
                "description": "音频",
                "filesize": 0,
                "duration": 11
            },
            {
                "type": 3,
                "title": "相关视频",
                "content": "m0508lpjej4",
                "description": "相关视频",
                "filesize": 0,
                "duration": 0
            },
            {
                "type": 3,
                "filename": "",
                "title": "相关视频1",
                "content": "m0508lpjej4",
                "description": "相关视频1",
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
            },
            {
                "id": 12,
                "specification": "x86",
                "colour": 1
            },
            {
                "id": 13,
                "specification": "x86",
                "colour": 1
            },
            {
                "id": 15,
                "specification": "x86",
                "colour": 1
            }
        ],
        "availableSpecifications": [
            "6GB+64GB",
            "x86",
            "8GB+128GB"
        ],
        "availableColours": [
            1,
            2
        ],
        "imageRotation": true,
        "rotations": [
            {
                "pictureurl": "//static.mifanxing.com/wx/image/29/15/990605.jpg",
                "title": "TestPicTURE",
                "groupId": 36,
                "orderNo": 1
            },
            {
                "pictureurl": "//static.mifanxing.com/wx/image/29/15/990601.jpg",
                "title": "TestPicTURE",
                "groupId": 36,
                "orderNo": 2
            }
         ]
       }
      }

### 查询子产品价格详情(客户端) [GET] /price/subProduct/{id}
+ Parameters
     +  id 子产品id
+ Description 
    +  [MUST] Authenticated
    + subProductId 子产品ID
    + tbProductId 淘宝表ID
    + tbItemId 实际淘宝id
    + reservePrice 子产品淘宝价格
    + subCurrency 币别名称
    + sourceName 来源名称
    + sourceLogo 来源logo
+ Response 200 (Application/json)

       {
        "data": [
            {
                "id": 3,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-02-22 10:19:27",
                "modified": "2019-02-22 10:19:27",
                "subProductId": 3,
                "tbProductId": 3,
                "tbItemId": 10003,
                "source": 1,
                "currency": 1,
                "isInland": 1,
                "isManual": 0,
                "reservePrice": "325",
                "subCurrency": "¥",
                "sourceName": "淘宝",
                "sourceLogo": "http://static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg",
                "salesVolume": 10758
            },
            {
                "id": 5,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "subProductId": 3,
                "tbProductId": 16,
                "tbItemId": 11111,
                "source": 13,
                "currency": 2,
                "isInland": 0,
                "isManual": 0,
                "reservePrice": "2959.01",
                "subCurrency": "$",
                "sourceName": "亚马逊",
                "sourceLogo": "http://static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg",
                "salesVolume": 22
            }
        ]
      }

### 子产品赞踩(客户端) [GET] /subProducts/thumbs/{id}?thumbsUp=1
+ Parameters
     +  id 子产品id
     +  thumbsUp 当请求为<点赞>添加子产品的点赞数
     +  thumbsDown 当请求为<踩>添加此子产品的踩数
+ Response 200 (Application/json)
    
### 子产品收藏(客户端) [POST] /collects
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
      
### 查询子产品经销商详情(客户端) [GET] /dealer/mainProduct?productId={id}
+ Parameters
     +  id 子产品id
+ Description 
    + dealerName 经销商名称
    + dealerTel 经销商电话
    + dealerEmail 经销商邮件
    + dealerAddress 经销商地址
    + dealerMainBrand 经销商主营品牌

+ Response 200 (Application/json)

       {
        "meta": {
            "totalPages": 1,
            "totalElements": 3,
            "size": 10,
            "number": 1,
            "numberOfElements": 3,
            "first": true,
            "last": true,
            "sort": null
        },
        "links": {
            "self": "/dealer/mainProduct?productId=1&page[number]=1&page[size]=10",
            "first": "/dealer/mainProduct?productId=1&page[number]=1&page[size]=10",
            "last": "/dealer/mainProduct?productId=1&page[number]=1&page[size]=10"
        },
        "data": [
            {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-02-14 15:02:14",
                "modified": "2019-02-27 10:39:45",
                "dealerName": "米饭星1",
                "dealerTel": "1",
                "dealerEmail": "850770722@qq.com",
                "dealerAddress": "山西",
                "dealerMainBrand": "德力风根"
            },
            {
                "id": 2,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-02-14 15:02:14",
                "modified": "2019-02-14 15:02:14",
                "dealerName": "宝迪",
                "dealerTel": "13911111111",
                "dealerEmail": "1253619833@qq.com",
                "dealerAddress": "北京",
                "dealerMainBrand": "品质生活"
            },
            {
                "id": 4,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-02-14 15:02:14",
                "modified": "2019-02-14 15:02:14",
                "dealerName": "易科国际",
                "dealerTel": "18811111111",
                "dealerEmail": "1234511111@qq.com",
                "dealerAddress": "深圳市",
                "dealerMainBrand": "最新服务"
            }
        ]
      }
