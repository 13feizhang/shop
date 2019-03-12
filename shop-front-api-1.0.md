# 前台
## 子产品模块
+ 2019年02月20日
    + API初始化 
     
    
+ 2019年03月05日
    + 添加逛一逛接口 
+ 2019年03月07日
    + 在子产品查询接口添加是否有优惠券判断
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
        + type (Integer) - 类型(0：产品视频  1：音频  2:文件 3:相关视频)
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
     + coupon 是否有券
 
+ Response 200 (Application/json)

        {
        "data": {
        "id": 2,
        "mainProductId": 1,
        "specification": "8GB+128GB",
        "colour": 1,
        "thumbsUp": 8,
        "thumbsDown": 2,
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
        "shopUrl": "//s.click.taobao.com/t?e=m%3D2%26s%3DHpflsm941igcQipKwQzePOeEDrYVVa64r4ll3HtqqoxyINtkUhsv0ELduV78cHqXBO4jgj4QPfnFplEiCvCZ5tg0f9hkTsUBriOItY53i0EeQ4ho2CZ9o9oUVTgpC4THSBaygToy7XlHV8A77VHf6dPpLLmw2lzkjB7r%2B0aDb9GM3h%2FwNLE3G3NpyAJV9wj%2FND4oVtUG3oTGDmntuH4VtA%3D%3D&scm=null&pvid=100_11.178.152.226_69594_3711551941185636933&app_pvid=59590_11.175.105.51_675_1551941185632&ptl=floorId:2836;pvid:100_11.178.152.226_69594_3711551941185636933;app_pvid:59590_11.175.105.51_675_1551941185632&xId=kD8KnOB9YuTssESUeooqpOYzhil5pKJ2zrnjpeFkSTyZ2tRHtBTNdIwo2VT0dDjao52NcXC57OxEdKEfmhK2hd&union_lens=lensId:0baf6933_0c04_16956e7308c_451a",
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
            "mainFeature": "{\"影像传感器\": { \"传感器类型\": \"Exmor Rs\", \"有效哦像素\": \"2420\" }, \"对焦系统\": {\"对焦点\": \"683各个想问点\"}, \"液晶屏\": { \"尺寸\": \"3.tt\", \"总箱数\": \"111\" } }",
            "specifications": [
                "6GB+64GB",
                "经典",
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
            ],
            "accessories": [
                {
                    "id": 1,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2019-02-20 11:08:21",
                    "modified": "2019-02-20 11:08:24",
                    "type": 0,
                    "filename": "https://jdvodoss.jcloudcache.com/vodtransgzp1251412368/7447398156451886582/v.f30.mp4?dockingId=aee5a279-b858-4e06-a8e6-3accdc3f8014&storageSource=3",
                    "title": "小米8展示视频",
                    "description": "小米8展示视频",
                    "filesize": 0,
                    "duration": 0
                },
                {
                    "id": 2,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2019-02-22 10:30:05",
                    "modified": "2019-02-22 10:30:05",
                    "type": 2,
                    "filename": "https://static.mifanxing.com/yyren/image/week/20171110/1/Snare-1_1inchabove.mp3",
                    "title": "文件",
                    "description": "文件下载",
                    "filesize": 0,
                    "duration": 0
                },
                {
                    "id": 3,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "type": 1,
                    "filename": "https://static.mifanxing.com/yyren/image/week/20171110/1/Snare-1_1inchabove.mp3",
                    "title": "音频",
                    "description": "音频",
                    "filesize": 0,
                    "duration": 11
                },
                {
                    "id": 4,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2019-02-28 16:44:03",
                    "modified": "2019-02-28 16:44:06",
                    "type": 3,
                    "filename": "https://static.mifanxing.com/article/image/254/86/5701313.jpg",
                    "title": "相关视频",
                    "content": "m0508lpjej4",
                    "description": "相关视频",
                    "filesize": 0,
                    "duration": 0
                },
                {
                    "id": 5,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2019-03-01 14:43:27",
                    "modified": "2019-03-01 14:43:27",
                    "type": 3,
                    "filename": "https://static.mifanxing.com/article/image/254/86/5701313.jpg",
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
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2019-03-07 15:52:38",
                    "modified": "2019-03-07 15:52:38",
                    "mainProductId": 1,
                    "subFeature": "[\"影像传感器\": { \"传感器类型\": \"Exmor Rs\", \"有效哦像素\": \"2420\" }, \"对焦系统\": {\"对焦点\": \"683各个想问点\"}, \t\"液晶屏\": { \"尺寸\": \"3.tt\", \"总箱数\": \"111\" } ]",
                    "keyWords": "小米8",
                    "specification": "6GB+64GB",
                    "colour": 1,
                    "thumbsUp": 31,
                    "thumbsDown": 9,
                    "isShow": 1,
                    "coupon": false
                },
                {
                    "id": 2,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2019-02-26 11:27:02",
                    "modified": "2019-02-26 11:27:02",
                    "mainProductId": 1,
                    "keyWords": "blue,yeti",
                    "specification": "8GB+128GB",
                    "colour": 1,
                    "thumbsUp": 8,
                    "thumbsDown": 2,
                    "isShow": 1,
                    "coupon": false
                },
                {
                    "id": 3,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2019-02-20 11:05:22",
                    "modified": "2019-02-20 11:05:25",
                    "mainProductId": 1,
                    "keyWords": "Shure,舒尔,SM58S",
                    "specification": "6GB+64GB",
                    "colour": 2,
                    "thumbsUp": 1,
                    "thumbsDown": 1,
                    "isShow": 1,
                    "coupon": false
                },
                {
                    "id": 4,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2019-02-20 11:05:18",
                    "modified": "2019-02-20 11:05:14",
                    "mainProductId": 1,
                    "keyWords": "Shure,舒尔,SM58S",
                    "specification": "8GB+128GB",
                    "colour": 3,
                    "thumbsUp": 1,
                    "thumbsDown": 1,
                    "isShow": 1,
                    "coupon": false
                },
                {
                    "id": 5,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "mainProductId": 1,
                    "keyWords": "JBL,GO2",
                    "specification": "8GB+222GB",
                    "colour": 3,
                    "thumbsUp": 1,
                    "thumbsDown": 1,
                    "isShow": 1,
                    "coupon": false
                },
                {
                    "id": 12,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2019-02-27 15:51:07",
                    "modified": "2019-02-27 15:51:07",
                    "mainProductId": 1,
                    "subFeature": "{\"品质\":\"另类\"}",
                    "keyWords": "小米91",
                    "specification": "x86",
                    "colour": 1,
                    "thumbsUp": 0,
                    "thumbsDown": 100,
                    "isShow": 1,
                    "coupon": false
                },
                {
                    "id": 13,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2019-02-27 15:53:52",
                    "modified": "2019-02-27 15:53:52",
                    "mainProductId": 1,
                    "subFeature": "{\"品质\":\"另类\"}",
                    "keyWords": "小米91",
                    "specification": "x86",
                    "colour": 1,
                    "thumbsUp": 0,
                    "thumbsDown": 100,
                    "isShow": 1,
                    "coupon": false
                },
                {
                    "id": 15,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2019-02-27 15:56:48",
                    "modified": "2019-02-27 15:56:48",
                    "mainProductId": 1,
                    "subFeature": "{\"品质\":\"另类\"}",
                    "keyWords": "小米91",
                    "specification": "x86",
                    "colour": 1,
                    "thumbsUp": 0,
                    "thumbsDown": 100,
                    "isShow": 1,
                    "coupon": false
                },
                {
                    "id": 16,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2019-03-04 14:00:09",
                    "modified": "2019-03-04 14:00:09",
                    "mainProductId": 1,
                    "subFeature": "{\"拆字\"\":\"松木\"}",
                    "keyWords": "小米,插板",
                    "specification": "经典",
                    "colour": 1,
                    "thumbsUp": 0,
                    "thumbsDown": 0,
                    "isShow": 1,
                    "coupon": false
                },
                {
                    "id": 17,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2019-03-04 14:03:46",
                    "modified": "2019-03-04 14:28:11",
                    "mainProductId": 1,
                    "subFeature": "{\"拆字\"\":\"黄松木\"}",
                    "keyWords": "小米1,插板1",
                    "specification": "经典",
                    "colour": 1,
                    "thumbsUp": 0,
                    "thumbsDown": 0,
                    "isShow": 1,
                    "coupon": false
                }
            ]
        },
        "accessories": [
            {
                "created": "2019-02-20 11:08:21",
                "type": 0,
                "filename": "https://jdvodoss.jcloudcache.com/vodtransgzp1251412368/7447398156451886582/v.f30.mp4?dockingId=aee5a279-b858-4e06-a8e6-3accdc3f8014&storageSource=3",
                "title": "小米8展示视频",
                "description": "小米8展示视频",
                "filesize": 0,
                "duration": 0
            },
            {
                "created": "2019-02-22 10:30:05",
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
                "created": "2019-02-28 16:44:03",
                "type": 3,
                "filename": "https://static.mifanxing.com/article/image/254/86/5701313.jpg",
                "title": "相关视频",
                "content": "m0508lpjej4",
                "description": "相关视频",
                "filesize": 0,
                "duration": 0
            },
            {
                "created": "2019-03-01 14:43:27",
                "type": 3,
                "filename": "https://static.mifanxing.com/article/image/254/86/5701313.jpg",
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
                "colour": 1,
                "coupon": false
            },
            {
                "id": 2,
                "specification": "8GB+128GB",
                "colour": 1,
                "coupon": false
            },
            {
                "id": 3,
                "specification": "6GB+64GB",
                "colour": 2,
                "coupon": false
            },
            {
                "id": 4,
                "specification": "8GB+128GB",
                "colour": 3,
                "coupon": false
            },
            {
                "id": 5,
                "specification": "8GB+222GB",
                "colour": 3,
                "coupon": false
            },
            {
                "id": 12,
                "specification": "x86",
                "colour": 1,
                "coupon": false
            },
            {
                "id": 13,
                "specification": "x86",
                "colour": 1,
                "coupon": false
            },
            {
                "id": 15,
                "specification": "x86",
                "colour": 1,
                "coupon": false
            },
            {
                "id": 16,
                "specification": "经典",
                "colour": 1,
                "coupon": false
            },
            {
                "id": 17,
                "specification": "经典",
                "colour": 1,
                "coupon": false
            }
        ],
        "availableSpecifications": [
            "6GB+64GB",
            "经典",
            "x86",
            "8GB+128GB"
        ],
        "availableColours": [
            1,
            3
        ],
        "imageRotation": true,
        "rotations": [
            {
                "pictureurl": "//static.mifanxing.com/wx/image/29/15/990601.jpg",
                "title": "TestPicTURE",
                "groupId": 36,
                "orderNo": 3
            },
            {
                "pictureurl": "//static.mifanxing.com/wx/image/29/15/990601.jpg",
                "title": "TestPicTURE",
                "groupId": 36,
                "orderNo": 4
            }
        ],
        "coupon": false
        }
        }

### 查询子产品价格详情(客户端) [GET] /price/subProduct/{id}
+ Parameters
     +  id 子产品id
+ Description 
    +  [MUST] Authenticated
    +  marketPrice 市场价格
    +  priceSource 价格来源
    + subProductId 子产品ID
    + tbProductId 淘宝表ID
    + tbItemId 实际淘宝id
    + reservePrice 子产品淘宝价格
    + subCurrency 币别名称
    + sourceName 来源名称
    + sourceLogo 来源logo
    + salesVolume 30天销量
+ Response 200 (Application/json)

       {
        "data": {
            "marketPrice": [
                {
                    "district": "国外",
                    "currency": "$",
                    "pricesRange": "5.3~54.0"
                },
                {
                    "district": "国内",
                    "currency": "¥",
                    "pricesRange": "200.5~2649.01"
                }
            ],
            "priceSource": [
                {
                    "id": 1,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2019-02-22 10:19:27",
                    "modified": "2019-02-22 10:19:27",
                    "subProductId": 1,
                    "tbProductId": 1,
                    "tbItemId": 10001,
                    "source": 1,
                    "currency": 1,
                    "isInland": 1,
                    "isManual": 0,
                    "reservePrice": "200.5",
                    "subCurrency": "¥",
                    "sourceName": "淘宝",
                    "sourceLogo": "http://static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
                },
                {
                    "id": 2,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2019-02-22 10:19:27",
                    "modified": "2019-02-22 10:19:27",
                    "subProductId": 1,
                    "tbProductId": 2,
                    "tbItemId": 10002,
                    "source": 2,
                    "currency": 1,
                    "isInland": 1,
                    "isManual": 1,
                    "manualPurchaseLink": "是多少",
                    "reservePrice": "224",
                    "subCurrency": "¥",
                    "sourceName": "京东",
                    "sourceLogo": "http://static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
                },
                {
                    "id": 6,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2019-03-08 18:30:46",
                    "subProductId": 1,
                    "tbProductId": 17,
                    "tbItemId": 577823242934,
                    "source": 3,
                    "currency": 1,
                    "isInland": 1,
                    "isManual": 0,
                    "reservePrice": "2649.01",
                    "subCurrency": "¥",
                    "sourceName": "苏宁",
                    "sourceLogo": "http://static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg",
                    "salesVolume": 54
                },
                {
                    "id": 7,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2019-03-08 18:37:46",
                    "subProductId": 1,
                    "tbProductId": 21,
                    "tbItemId": 556614091011,
                    "source": 14,
                    "currency": 2,
                    "isInland": 0,
                    "isManual": 0,
                    "reservePrice": "54.0",
                    "subCurrency": "$",
                    "sourceName": "洋码头",
                    "sourceLogo": "http://static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg",
                    "salesVolume": 48
                },
                {
                    "id": 8,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2019-03-08 18:40:09",
                    "subProductId": 1,
                    "tbProductId": 23,
                    "tbItemId": 576583014190,
                    "source": 15,
                    "currency": 2,
                    "isInland": 0,
                    "isManual": 0,
                    "reservePrice": "5.30",
                    "subCurrency": "$",
                    "sourceName": "windelnde",
                    "sourceLogo": "http://static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg",
                    "salesVolume": 10758
                },
                {
                    "id": 9,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2019-03-08 18:41:37",
                    "subProductId": 1,
                    "tbProductId": 31,
                    "tbItemId": 563969168235,
                    "source": 13,
                    "currency": 2,
                    "isInland": 0,
                    "isManual": 0,
                    "reservePrice": "13.01",
                    "subCurrency": "$",
                    "sourceName": "亚马逊",
                    "sourceLogo": "http://static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg",
                    "salesVolume": 23
                }
            ]
        }
      }

### 子产品赞踩(客户端) [GET] /subProducts/thumbs/{id}?thumbsUp=1
+ Parameters
     +  id 子产品id
     +  thumbsUp 当请求为<点赞>添加子产品的点赞数
     +  thumbsDown 当请求为<踩>添加此子产品的踩数
+ Response 200 (Application/json)
    
### 子产品收藏(客户端) [POST] /collects
+ Parameters
     +  subProductId 主产品id
+ Description 
    +  [MUST] Authenticated
    + [MUST] ROLE_ADMIN
+ Request（application/json）

      {
    	 "data":{
    		"subProductId":1
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




+ 2019年03月05日
    + 添加逛一逛接口 
+ Data
    + products 主产品表
        + productName (String) - 产品名字
        + volume (Integer) - 30天销量
        + price (String) - 产品价格
        + briefDescription (String) - 简述
        + shopUrl (String) - 购买链接
        + brands (Brands) - 品牌
        + subProductPricesSource (SubProductPricesSource) - 产品价格来源
    + Brands 品牌表
        + name (String) 品牌评测
        + logo (String) logo
    + SubProductPricesSource 产品价格来源表
        + sourceName  (String) 来源商城名字
        + sourceUrl (String) 来源logo
    

### 查询逛一逛详情 [GET] /subProducts/gyg/{id}
+ Parameters
     +  id 子产品id
+ Description 
    

+ Response 200 (Application/json)

       {
        "data": [
        {
            "id": 1,
            "productName": null,
            "price": "200.5",
            "volume": null,
            "shopUrl": "https://item.jd.com/1234567890",
            "subProductPricesSource": {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-02-20 11:08:46",
                "modified": "2019-02-20 11:08:50",
                "sourceName": "淘宝",
                "sourceUrl": "http://static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
            },
            "brands": {
                "id": 1,
                "name": "小米",
                "logo": "/static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
            }
        },
        {
            "id": 6,
            "productName": "Blue yeti studio雪怪 电脑游戏手机直播电容麦克风USB话筒设备",
            "price": "1899",
            "volume": 0,
            "shopUrl": "https://s.click.taobao.com/t?e=m%3D2%26s%3DhN8MLNseDVocQipKwQzePOeEDrYVVa64r4ll3HtqqoxyINtkUhsv0H1AekX3rfvuxs%2FqIRTwxIbFplEiCvCZ5tg0f9hkTsUBriOItY53i0EeQ4ho2CZ9o9oUVTgpC4THSBaygToy7Xl%2FwZDSR6sFqbvATCsySvvEjB7r%2B0aDb9GM3h%2FwNLE3G8rFue86m8FG6TXn7WzmDZ4hhQs2DjqgEA%3D%3D&scm=null&pvid=100_11.178.152.226_33234_531551348464066413&app_pvid=59590_11.186.136.22_14508_1551348464058&ptl=floorId:2836;pvid:100_11.178.152.226_33234_531551348464066413;app_pvid:59590_11.186.136.22_14508_1551348464058&xId=SxIpIYkgSXFx35byfh4jilm0mfPlIQKz8h2kUvyPKnVeKyzCx6d30SCk4vxwD354CLzsI2CFHlrjcGacbB1GBK&union_lens=lensId:0bba8816_0c6d_1693392f9e4_65db",
            "subProductPricesSource": {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-02-20 11:08:46",
                "modified": "2019-02-20 11:08:50",
                "sourceName": "淘宝",
                "sourceUrl": "http://static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
            },
            "brands": {
                "id": 1,
                "name": "小米",
                "logo": "/static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
            }
        },
        {
            "id": 7,
            "productName": "Blue yeti雪怪专业电容话筒麦克风K歌录音直播USB直插MIC原装进口",
            "price": "1298",
            "volume": 0,
            "shopUrl": "https://s.click.taobao.com/t?e=m%3D2%26s%3DduXnt4IYtrkcQipKwQzePOeEDrYVVa64r4ll3HtqqoxyINtkUhsv0H1AekX3rfvuxs%2FqIRTwxIbFplEiCvCZ5tg0f9hkTsUBriOItY53i0EeQ4ho2CZ9o9oUVTgpC4THSBaygToy7XluaWh2wOcFsvewEqIJmYQDjB7r%2B0aDb9GM3h%2FwNLE3G8%2B9ZyxvICI1vit6BeTR7PshhQs2DjqgEA%3D%3D&scm=null&pvid=100_11.178.152.226_33234_531551348464066413&app_pvid=59590_11.186.136.22_14508_1551348464058&ptl=floorId:2836;pvid:100_11.178.152.226_33234_531551348464066413;app_pvid:59590_11.186.136.22_14508_1551348464058&xId=iCvD15fsuZLaj5m3yPFMBPbEBw4qEpSs77MB0VhHRtYwNZCUvAtLVwpRKejdBwn7gzRsl81351yyuxEBO3SUfk&union_lens=lensId:0bba8816_0c6d_1693392f9e4_65dc",
            "subProductPricesSource": {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-02-20 11:08:46",
                "modified": "2019-02-20 11:08:50",
                "sourceName": "淘宝",
                "sourceUrl": "http://static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
            },
            "brands": {
                "id": 1,
                "name": "小米",
                "logo": "/static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
            }
        },
        {
            "id": 8,
            "productName": "Blue yeti studio雪怪网络全民K歌录音手机直播电容麦克风USB话筒",
            "price": "1899",
            "volume": 0,
            "shopUrl": "https://s.click.taobao.com/t?e=m%3D2%26s%3DcunVR0JXax0cQipKwQzePOeEDrYVVa64r4ll3HtqqoxyINtkUhsv0H1AekX3rfvuxs%2FqIRTwxIbFplEiCvCZ5tg0f9hkTsUBriOItY53i0EeQ4ho2CZ9o9oUVTgpC4THSBaygToy7XknopNk5QTPVmKNqjg6OUcpjB7r%2B0aDb9GM3h%2FwNLE3GzQdi%2FB65lCsod2aSEi32o0hhQs2DjqgEA%3D%3D&scm=null&pvid=100_11.178.152.226_33234_531551348464066413&app_pvid=59590_11.186.136.22_14508_1551348464058&ptl=floorId:2836;pvid:100_11.178.152.226_33234_531551348464066413;app_pvid:59590_11.186.136.22_14508_1551348464058&xId=JKdZ0SmF3IzFZC6LnxjIC232RzEizAIPFo0TpBmTLHzSTZYW9pNehDkJij7cD5QMFxkiiKOhKWESPBNxoKA81P&union_lens=lensId:0bba8816_0c6d_1693392f9e4_65dd",
            "subProductPricesSource": {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-02-20 11:08:46",
                "modified": "2019-02-20 11:08:50",
                "sourceName": "淘宝",
                "sourceUrl": "http://static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
            },
            "brands": {
                "id": 1,
                "name": "小米",
                "logo": "/static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
            }
        },
        {
            "id": 9,
            "productName": "茂圣六堡茶 广西特产黑茶 梧州六堡茶 8年陈250g小米沱茶罐装",
            "price": "160.00",
            "volume": 2,
            "shopUrl": "https://uland.taobao.com/coupon/edetail?e=uTZRXOL5BkUGQASttHIRqa5nxu1JJg1Y%2BOQpvI6u%2FglYomNqLX%2FiF4eUz%2BRdYNAYSetzlAO%2B5xP51BRCmRu94DqMnsqGwilcbd76m3V5xpbgNMiuZHn6%2Ffs69hmQwiAFZ%2FuyoioKit2EZI8OxySlHAMFTfGLA%2FdyQ8Bi9zs%2FsPJg%2FBV7tG3PlBdOOR5C4gXnQS0Flu%2FfbSog%2BeE%2BjpQFGFLajOROSSHlUpLf3IbvQCCEnEzHOnSRZA%3D%3D&traceId=0b0b142d15513512381457522e",
            "subProductPricesSource": {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-02-20 11:08:46",
                "modified": "2019-02-20 11:08:50",
                "sourceName": "淘宝",
                "sourceUrl": "http://static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
            },
            "brands": {
                "id": 1,
                "name": "小米",
                "logo": "/static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
            }
        },
        {
            "id": 10,
            "productName": "小米8青春版手机壳小米8SE保护皮套小米8青春版翻盖式小米8全包探索版边软壳小米8指纹版防摔套se男女",
            "price": "15.80",
            "volume": 60,
            "shopUrl": "https://uland.taobao.com/coupon/edetail?e=z5FDjIfGwQ0GQASttHIRqRvOVvLdZWu6uUYIi%2BZOEJem%2FPqYSC%2BIlvdi9EaqWe%2FC%2B6Mggn6Qv%2FmfApc1Bmp5bMltBTQQ%2Fns7bd76m3V5xpbgNMiuZHn6%2Ffs69hmQwiAFZ%2FuyoioKit2EZI8OxySlHAMFTfGLA%2FdyQ8Bi9zs%2FsPIFapBA7XjoiCZ6Y%2FpkHtT5QS0Flu%2FfbSp4QsdWMikAalS0HdanV%2B6vYeQx8Om%2B1iI%3D&traceId=0b0b142d15513512381457522e",
            "subProductPricesSource": {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-02-20 11:08:46",
                "modified": "2019-02-20 11:08:50",
                "sourceName": "淘宝",
                "sourceUrl": "http://static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
            },
            "brands": {
                "id": 1,
                "name": "小米",
                "logo": "/static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
            }
        },
        {
            "id": 11,
            "productName": "小米8青春版手机壳小米8SE保护套翻盖式皮套八周年纪念版小米6x全包边软",
            "price": "15.80",
            "volume": 35,
            "shopUrl": "https://uland.taobao.com/coupon/edetail?e=0sB3%2FZC8N3QGQASttHIRqerFC4Hj4tMENrr2CgYVVnGm%2FPqYSC%2BIlvdi9EaqWe%2FC%2B6Mggn6Qv%2FmfApc1Bmp5bMltBTQQ%2Fns7bd76m3V5xpbgNMiuZHn6%2Ffs69hmQwiAFZ%2FuyoioKit2EZI8OxySlHAMFTfGLA%2FdyQ8Bi9zs%2FsPIFapBA7XjoiCZ6Y%2FpkHtT5QS0Flu%2FfbSp4QsdWMikAalS0HdanV%2B6vYeQx8Om%2B1iI%3D&traceId=0b0b142d15513512381457522e",
            "subProductPricesSource": {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-02-20 11:08:46",
                "modified": "2019-02-20 11:08:50",
                "sourceName": "淘宝",
                "sourceUrl": "http://static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
            },
            "brands": {
                "id": 1,
                "name": "小米",
                "logo": "/static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
            }
        },
        {
            "id": 12,
            "productName": "无线充电器苹果专用原装8plus小米6三星无线充type-c手机通用华为",
            "price": "59.00",
            "volume": 0,
            "shopUrl": "https://uland.taobao.com/coupon/edetail?e=%2BRGG3J6vVE8GQASttHIRqS4Z698vI3KZeIG8W1%2BEkZ%2Fyi1aSyqbpmpxprDZKF0z1ty3wSATn%2BU2DLZnGB%2BaaZmB1gIYhu1R9bd76m3V5xpbgNMiuZHn6%2Ffs69hmQwiAFZ%2FuyoioKit2EZI8OxySlHAMFTfGLA%2FdyQ8Bi9zs%2FsPJg%2FBV7tG3PlBdOOR5C4gXnQS0Flu%2FfbSog%2BeE%2BjpQFGFLajOROSSHlUpLf3IbvQCCEnEzHOnSRZA%3D%3D&traceId=0b0b142d15513512381457522e",
            "subProductPricesSource": {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-02-20 11:08:46",
                "modified": "2019-02-20 11:08:50",
                "sourceName": "淘宝",
                "sourceUrl": "http://static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
            },
            "brands": {
                "id": 1,
                "name": "小米",
                "logo": "/static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
            }
        },
        {
            "id": 13,
            "productName": "新款小米8手机壳真皮翻盖小米8手机套全包防摔保护皮套轻薄商务壳",
            "price": "138.00",
            "volume": 0,
            "shopUrl": "https://uland.taobao.com/coupon/edetail?e=NdQtS2HqnbwGQASttHIRqQA1%2B9fkH6cbnkwe8HWpltlUm%2Fg8xRLmNq6XJ17Tl5BdiA4ubl2b%2B4Iks8bJitH8ilj4A3rjSH0kbd76m3V5xpbgNMiuZHn6%2Ffs69hmQwiAFZ%2FuyoioKit2EZI8OxySlHAMFTfGLA%2FdyQ8Bi9zs%2FsPJg%2FBV7tG3PlBdOOR5C4gXnQS0Flu%2FfbSog%2BeE%2BjpQFGFLajOROSSHlUpLf3IbvQCCEnEzHOnSRZA%3D%3D&traceId=0b0b142d15513512381457522e",
            "subProductPricesSource": {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-02-20 11:08:46",
                "modified": "2019-02-20 11:08:50",
                "sourceName": "淘宝",
                "sourceUrl": "http://static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
            },
            "brands": {
                "id": 1,
                "name": "小米",
                "logo": "/static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
            }
        },
        {
            "id": 14,
            "productName": "无线充电器苹果专用iPhonex原装QI快充note9小米2s充电器8万能充",
            "price": "79.00",
            "volume": 0,
            "shopUrl": "https://uland.taobao.com/coupon/edetail?e=78QDZIMu5N0GQASttHIRqS7%2BjsRU3AdVlHnee4yrke3yi1aSyqbpmpxprDZKF0z1ty3wSATn%2BU2DLZnGB%2BaaZmB1gIYhu1R9bd76m3V5xpbgNMiuZHn6%2Ffs69hmQwiAFZ%2FuyoioKit2EZI8OxySlHAMFTfGLA%2FdyQ8Bi9zs%2FsPJg%2FBV7tG3PlBdOOR5C4gXnQS0Flu%2FfbSog%2BeE%2BjpQFGFLajOROSSHlUpLf3IbvQCCEnEzHOnSRZA%3D%3D&traceId=0b0b142d15513512381457522e",
            "subProductPricesSource": {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-02-20 11:08:46",
                "modified": "2019-02-20 11:08:50",
                "sourceName": "淘宝",
                "sourceUrl": "http://static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
            },
            "brands": {
                "id": 1,
                "name": "小米",
                "logo": "/static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
            }
        }
        ]
        }
