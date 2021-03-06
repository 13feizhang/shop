# 后台
+ 2019年2月20日
    + 子产品经销商初始化
    + 产品颜色初始化
    
+ 2019年3月01日

    + 主产品列表查询接口
    + 主产品新增接口
    + 主产品修改接口
    + 主产品删除接口
    + 主产品中品牌查询接口
    + 主产品通过id查询详情接口
    
+ 2019年3月04日
    + 子产品新增接口
    + 子产品修改接口
    + 子产品删除接口
    + 查询后台子产品的相关信息接口
+ 2019年3月11日
    + 用户收藏列表接口 
+ 2019年3月12日   
    + 分类新增接口
    + 分类修改接口
    + 分类删除接口
    + 分类通过名字模糊查询接口
    + 分类通过parentId查询其下的所有分类
+ 2019年3月14日 
    + 后台子产品通过产品ID得到子产品列表
+ 2019年3月21日 
    + 增加价格来源接口

## 经销商管理
### 增加 [POST] /dealer
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN
    
+ Request (application/json) 

      {
    	 "data":{
            "dealerName": "米星",
            "dealerTel": "18331931952",
            "dealerEmail": "850770722@qq.com",
            "dealerAddress": "山西",
            "dealerMainBrand": "米星品牌"
    	 }
      }

Response (application/json)

    {
        "data": {
            "id": 1,
            "type": "dealer"
        }
    }

### 修改 [PATCH] /dealer/{id}

+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN

+ Request (application/json)
    
      {
    	 "data":{
            "dealerName": "米星1",
            "dealerTel": "18331931952",
            "dealerEmail": "850770722@qq.com",
            "dealerAddress": "山西",
            "dealerMainBrand": "米星品牌"
    	 }
      }

+ Response 200

### 列表[GET] /dealer?page[number]=1&page[size]=5
+ Parameters
  + id 
  + sort -modified(从新到旧) | modified(从旧到新)
+ Request (application/json)
        
        {
            "meta": {
                "totalPages": 4,
                "totalElements": 17,
                "size": 5,
                "number": 1,
                "numberOfElements": 5,
                "first": true,
                "last": false,
                "sort": null
            },
            "links": {
                "self": "/dealer?page[number]=1&page[size]=5",
                "first": "/dealer?page[number]=1&page[size]=5",
                "next": "/dealer?page[number]=2&page[size]=5",
                "last": "/dealer?page[number]=4&page[size]=5"
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
                    "id": 3,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "created": "2019-02-14 15:02:14",
                    "modified": "2019-02-14 15:02:14",
                    "dealerName": "安恒利国际",
                    "dealerTel": "13811111111",
                    "dealerEmail": "1234567891@qq.com",
                    "dealerAddress": "北京",
                    "dealerMainBrand": "越享生活"
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
                },
                {
                    "id": 5,
                    "enabled": 1,
                    "creator": 0,
                    "modifier": 0,
                    "dealerName": "易科国际11"
                }
            ]
        }
      
### 删除 [DELETE] /dealer/{id}

+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN
+ Response 204  



## 颜色管理
### 增加 [POST] /colour
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN
    
+ Request (application/json) 

        {
        "data": {
    	"colourName":"桃红色",
    	"colourPicture":"https://static.mifanxing.com/article/image/88/87/5724231.jpg?w=320&h=180"
        }
        }

Response201 (application/json)

        {
        "data": {
            "id": 13,
            "type": "colour"
        }
        }
    
Response400 (application/json)

        {
         "errors": [
            {
            "status": "400",
            "title": "Bad Request",
            "detail": "此颜色已存在！！"
            }
        ]
        }


### 修改 [PATCH] /colour/{id}

+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN

+ Request (application/json)
    
      {
        "data": {
    	"colourName":"桃红色1",
    	"colourPicture":"https://static.mifanxing.com/article/image/88/87/5724231.jpg?w=320&h=180"
        }
        }

+ Response 200

### 列表[GET] /colour
+ Parameters
  + id 
  + title
     + 查询示例：filter[colourName:like]=%25红%25 （'%25'为'%'的转义） 
  + sort -modified(从新到旧) | modified(从旧到新)
+ Request (application/json)
       
      {
        "meta": {
            "totalPages": 1,
            "totalElements": 7,
            "size": 10,
            "number": 1,
            "numberOfElements": 7,
            "first": true,
            "last": true,
            "sort": null
        },
        "links": {
            "self": "/colour?page[number]=1&page[size]=10",
            "first": "/colour?page[number]=1&page[size]=10",
            "last": "/colour?page[number]=1&page[size]=10"
        },
        "data": [
            {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-02-20 11:08:46",
                "modified": "2019-02-20 11:08:50",
                "colourName": "红色",
                "colourPicture": "http://img.alicdn.com/imgextra/i4/804206007/TB2vBDgxxlmpuFjSZPfXXc9iXXa_!!804206007.jpg_40x40q90.jpg"
            },
            {
                "id": 2,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-02-24 21:28:01",
                "modified": "2019-02-24 21:28:03",
                "colourName": "黑色",
                "colourPicture": "http://img.alicdn.com/imgextra/i4/804206007/TB2vBDgxxlmpuFjSZPfXXc9iXXa_!!804206007.jpg_40x40q90.jpg"
            },
            {
                "id": 3,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-02-24 21:28:06",
                "modified": "2019-02-24 21:28:09",
                "colourName": "蓝色",
                "colourPicture": "http://img.alicdn.com/imgextra/i4/804206007/TB2vBDgxxlmpuFjSZPfXXc9iXXa_!!804206007.jpg_40x40q90.jpg"
            },
            {
                "id": 4,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-02-27 11:32:09",
                "modified": "2019-02-27 11:32:09",
                "colourName": "白色",
                "colourPicture": "http://img.alicdn.com/imgextra/i4/804206007/TB2vBDgxxlmpuFjSZPfXXc9iXXa_!!804206007.jpg_40x40q90.jpg"
            },
            {
                "id": 5,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-02-27 11:32:30",
                "modified": "2019-02-27 11:33:00",
                "colourName": "绿色",
                "colourPicture": "http://img.alicdn.com/imgextra/i4/804206007/TB2vBDgxxlmpuFjSZPfXXc9iXXa_!!804206007.jpg_40x40q90.jpg"
            },
            {
                "id": 6,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-02-27 11:43:09",
                "modified": "2019-02-27 11:43:09",
                "colourName": "黑红色",
                "colourPicture": "http://img.alicdn.com/imgextra/i4/804206007/TB2vBDgxxlmpuFjSZPfXXc9iXXa_!!804206007.jpg_40x40q90.jpg"
            },
            {
                "id": 12,
                "enabled": 1,
                "creator": 1037,
                "modifier": 1037,
                "created": "2019-02-28 17:45:08",
                "modified": "2019-02-28 17:45:52",
                "colourName": "粉红色"
            }
        ]
      }
       

### 删除 [DELETE] /colour/{id}

+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN
+ Response 204 

+ 2019年03月01日
     + API初始化

     
## 商城管理 -主产品
+ Data
    + id (Long) - ID
    + categoryId (Long) -分类ID
    + title (String) - 产品名
    + briefDescription (String) - 产品简述
    + description (String)  -产品描述
    + brandId (Long) - 品牌ID
    + mainFeature (String)  公共参数
    + creator (Long) 创建人
    + modifier (Long) 修改人
    + created (Date) - 创建时间
    + modified (Date) - 修改时间    

### 查询主产品列表 [GET]  /products  
+ Parameters
    + page[number] (int)  页码  -非必填
    + page[size]  (int)   页尺  -非必填
    + filter[id]  (int)   产品ID  -非必填
    + filter[categoryId]  分类id  -非必填
    + filter[productName] (String)  产品名字  -非必填（模糊查询）
     
    
+ Response 200 (application/json)

        {
        "meta": {
        "totalPages": 1,
        "totalElements": 8,
        "size": 10,
        "number": 1,
        "numberOfElements": 8,
        "first": true,
        "last": true,
        "sort": null
        },
        "links": {
        "self": "/products?page[number]=1&page[size]=10",
        "first": "/products?page[number]=1&page[size]=10",
        "last": "/products?page[number]=1&page[size]=10"
        },
        "data": [
        {
            "id": 1,
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
            "brands": {
                "id": 1,
                "name": "小米",
                "logo": "/static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
            }
            },
         {
            "id": 2,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-03-01 11:15:17",
            "modified": "2019-03-01 11:15:22",
            "categoryId": 1,
            "title": "小米台灯",
            "briefDescription": "小米台灯简单描述",
            "description": "小米台灯描述",
            "brandId": 1,
            "brands": {
                "id": 1,
                "name": "小米",
                "logo": "/static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
            }
        },
        {
            "id": 4,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-03-01 11:14:55",
            "modified": "2019-03-01 11:15:29",
            "categoryId": 3,
            "title": "小米台灯33",
            "briefDescription": "小米台灯简单描述331",
            "description": "小米台灯描述333",
            "brandId": 1,
            "mainFeature": "{\"颜色\":\"红色\"}",
            "brands": {
                "id": 1,
                "name": "小米",
                "logo": "/static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
            }
        },
        {
            "id": 8,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-03-01 11:15:09",
            "modified": "2019-03-01 11:15:44",
            "categoryId": 3,
            "title": "小米台灯33",
            "briefDescription": "小米台灯简单描述331",
            "description": "小米台灯描述333",
            "brandId": 1,
            "mainFeature": "{\"颜色\":\"红色\"}",
            "brands": {
                "id": 1,
                "name": "小米",
                "logo": "/static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
            }
        }
        ]
        }


### 增加 [POST] /products
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
        + type (Integer) - 类型(0：视频  1：音频  2:文件,3相关视频)
        + filename (String) - 存放文件的URL，如果是视频为空
        + extesion (String) - 扩展名
        + title (String) - 名称
        + content (String) - 品牌ID
        + description (String) - 主参数
        + filesize (Integer) - 文件大小
        + duration (Long) - 描述
        + enabled (int) - 使能 0禁止 1启用
+ Description
  + [MUST] authenticated
  + [MUST] ROLE_ADMIN

+ Parameters
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
        + type (Integer) - 类型(0：视频  1：音频  2:文件,3相关视频)
        + filename (String) - 存放文件的URL，如果是视频为空
        + extesion (String) - 扩展名
        + title (String) - 名称
        + content (String) - 品牌ID
        + description (String) - 主参数
        + filesize (Integer) - 文件大小
        + duration (Long) - 描述
        + enabled (int) - 使能 0禁止 1启用
+ Request  (application/json)

        {
          "data": {
          "categoryId": 3,
          "title": "小米WIFI",
          "briefDescription": "小米WIFI",
          "description": "小米WIFI0",
          "brandId": "1",
          "mainFeature":"{\"颜色\":\"红色\"}",
          "accessories":[
          	{ "type": 0,
                "filename": "https://jdvodoss.jcloudcache.com/vodtransgzp1251412368/7447398156451886582/v.f30.mp4?dockingId=aee5a279-b858-4e06-a8e6-3accdc3f8014&storageSource=3",
                "title": "小米WIFI视频",
                "description": "小米WIFI视频",
                "filesize": 0,
                "duration": 0},
                {
                "type": 1,
                "filename": "https://static.mifanxing.com/yyren/image/week/20171110/1/Snare-1_1inchabove.mp3",
                "title": "音频8888",
                "description": "音频8888",
                "filesize": 0,
                "duration": 0
                }
          	],
          "dealers":[
          	{"dealerName":"汇丰音响",
          	 "dealerTel":"18331931900",
          	 "dealerEmail":"1253619800@qq.com",
          	 "dealerAddress":"广州市",
          	 "dealerMainBrand":"mifanxing"
          	},{"dealerName":"诚信建业",
          	 "dealerTel":"18331931900",
          	 "dealerEmail":"1253619800@qq.com",
          	 "dealerAddress":"湖北省",
          	 "dealerMainBrand":"mifanxing"
          	}
          	]	
          }
        }
+ Response 200 


### 修改 [PATCH] /products/{id}
+ Description
  + [MUST] authenticated
  + [MUST] ROLE_ADMIN

+ Parameters
    + id (Long) - ID
        + categoryId (Long) - 分类ID
        + title (String) - 产品名称
        + briefDescription (String) - 简述
        + description (String) - 描述
        + brandId (Long) - 品牌ID
        + mainFeature (String) - 主参数
     + accessory 附件表
        + id (Long) - ID
        + type (Integer) - 类型(0：视频  1：音频  2:文件,3相关视频)
        + filename (String) - 存放文件的URL，如果是视频为空
        + extesion (String) - 扩展名
        + title (String) - 名称
        + content (String) - 品牌ID
        + description (String) - 主参数
        + filesize (Integer) - 文件大小
        + duration (Long) - 描述
        + enabled (int) - 使能 0禁止 1启用
    

+ Request (application/json)
 
        {
          "data": {
          "categoryId": 3,
          "title": "1小米WIFI",
          "briefDescription": "1小米WIFI",
          "description": "小米WIFI0",
          "brandId": "1",
          "mainFeature":"{\"颜色\":\"红色\"}",
          "accessories":[
          	{ "type": 0,
                "filename": "https://jdvodoss.jcloudcache.com/vodtransgzp1251412368/7447398156451886582/v.f30.mp4?dockingId=aee5a279-b858-4e06-a8e6-3accdc3f8014&storageSource=3",
                "title": "小米WIFI视频",
                "description": "小米WIFI视频",
                "filesize": 0,
                "duration": 0},
                {
                "type": 1,
                "filename": "https://static.mifanxing.com/yyren/image/week/20171110/1/Snare-1_1inchabove.mp3",
                "title": "1音频8888",
                "description": "音频8888",
                "filesize": 0,
                "duration": 0
                }
          	],
          "dealers":[
          	{"dealerName":"汇丰音响1",
          	 "dealerTel":"18331931900",
          	 "dealerEmail":"1253619800@qq.com",
          	 "dealerAddress":"广州市",
          	 "dealerMainBrand":"mifanxing"
          	},{"dealerName":"诚信建业1",
          	 "dealerTel":"18331931900",
          	 "dealerEmail":"1253619800@qq.com",
          	 "dealerAddress":"湖北省",
          	 "dealerMainBrand":"mifanxing"
          	}
          	]	
          }
        }

+ Response 200 

### 删除 [DELETE] /products/{id}
+ Description
  + [MUST]  Authenticated
  + [MUST] ROLE_ADMIN 
+  Response 204


### 查询品牌 [GET] /products/brand
主要是在主产品添加的时候，模糊查询相关品牌的时候使用
+ Parameters
    + filter[brandName]  品牌名字（模糊查询） 
    
+ Request (application/json)
       
        {
        "data": [
        {
            "id": 3,
            "name": "ev",
            "logo": "/static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
        },
        {
            "id": 4,
            "name": "ev1",
            "logo": "/static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
        },
        {
            "id": 34,
            "name": "ev2",
            "logo": "/static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
        },
        {
            "id": 33,
            "name": "ev3",
            "logo": "/static.mifanxing.com/iyyren/image/201806/06/1638/347865732702420992.jpg"
        }
        ]
        }

### 查询主产品详情 [GET] /products/{id}
主产品通过id查询详情接口
+ Parameters
    + id 
    
+ Request 200  (application/json)
       
       {
        "data": {
        "id": 1,
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
                "created": "2019-03-15 10:05:43",
                "modified": "2019-03-15 10:05:43",
                "mainProductId": 1,
                "subFeature": "[\"影像传感器\": { \"传感器类型\": \"Exmor Rs\", \"有效哦像素\": \"2420\" }, \"对焦系统\": {\"对焦点\": \"683各个想问点\"}, \t\"液晶屏\": { \"尺寸\": \"3.tt\", \"总箱数\": \"111\" } ]",
                "keyWords": "小米8",
                "specification": "6GB+64GB",
                "colour": 1,
                "thumbsUp": 6,
                "thumbsDown": 0,
                "isShow": 1,
                "coupon": false
            },
            {
                "id": 2,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-03-08 18:56:20",
                "modified": "2019-03-08 18:56:20",
                "mainProductId": 1,
                "keyWords": "blue,yeti",
                "specification": "8GB+128GB",
                "colour": 1,
                "thumbsUp": 4,
                "thumbsDown": 1,
                "isShow": 1,
                "coupon": false
            },
            {
                "id": 3,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-03-08 18:56:48",
                "modified": "2019-03-08 18:56:48",
                "mainProductId": 1,
                "keyWords": "Shure,舒尔,SM58S",
                "specification": "6GB+64GB",
                "colour": 2,
                "thumbsUp": 3,
                "thumbsDown": 1,
                "isShow": 1,
                "coupon": false
            },
            {
                "id": 4,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-03-08 18:56:17",
                "modified": "2019-03-08 18:56:17",
                "mainProductId": 1,
                "keyWords": "Shure,舒尔,SM58S",
                "specification": "8GB+128GB",
                "colour": 3,
                "thumbsUp": 3,
                "thumbsDown": 1,
                "isShow": 1,
                "coupon": false
            },
            {
                "id": 5,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-03-08 17:20:42",
                "modified": "2019-03-08 17:20:42",
                "mainProductId": 1,
                "keyWords": "JBL,GO2",
                "specification": "8GB+222GB",
                "colour": 3,
                "thumbsUp": 2,
                "thumbsDown": 1,
                "isShow": 1,
                "coupon": false
            },
            {
                "id": 12,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-03-11 16:53:46",
                "modified": "2019-03-11 16:53:46",
                "mainProductId": 1,
                "subFeature": "{\"品质\":\"另类\"}",
                "keyWords": "小米91",
                "specification": "x86",
                "colour": 1,
                "thumbsUp": 3,
                "thumbsDown": 0,
                "isShow": 1,
                "coupon": false
            },
            {
                "id": 13,
                "enabled": 0,
                "creator": 0,
                "modifier": 0,
                "created": "2019-03-08 15:01:54",
                "modified": "2019-03-19 16:29:25",
                "mainProductId": 1,
                "subFeature": "{\"品质\":\"另类\"}",
                "keyWords": "小米91",
                "specification": "x86",
                "colour": 1,
                "thumbsUp": 1,
                "thumbsDown": 1,
                "isShow": 1,
                "coupon": false
            },
            {
                "id": 15,
                "enabled": 0,
                "creator": 0,
                "modifier": 0,
                "created": "2019-03-08 15:02:49",
                "modified": "2019-03-19 10:35:31",
                "mainProductId": 1,
                "subFeature": "{\"品质\":\"另类\"}",
                "keyWords": "小米91",
                "specification": "x86",
                "colour": 1,
                "thumbsUp": 2,
                "thumbsDown": 0,
                "isShow": 1,
                "coupon": false
            },
            {
                "id": 44,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-03-20 18:06:31",
                "modified": "2019-03-20 19:27:10",
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
                "id": 46,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-03-20 19:29:16",
                "modified": "2019-03-20 19:29:16",
                "mainProductId": 1,
                "subFeature": "{\"拆字\"\":\"松木\"}",
                "keyWords": "小米,插板",
                "specification": "经典",
                "colour": 1,
                "thumbsUp": 0,
                "thumbsDown": 0,
                "isShow": 1,
                "coupon": false
            }
        ],
        "brandTitle": "小米",
        "categoryTitle": "BLUE无线麦克风"
        }
        } 
        
+ Request 400  （查询为空）





+ 2019年03月04日
     + API初始化
 
## 商城管理 -子产品
+ Data
    + SubProducts 子产品表
        + id (Long) - ID
        + mainProductId (Long) - 主产品ID
        + subFeature (String) - 自参数
        + keyWords (String) - 淘宝关键字
        + specification (String) - 规格
        + colour (Long) - 颜色ID
        + thumbsUp (Integer) - 赞
        + thumbsDown (Integer) - 踩
        + shopUrl （String） -购买链接
        + couponUrl （String）-优惠券链接
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
        + enabled (Integer) - 使能 0禁止 1启用
        + creator (long) - 创建人
        + modifier (long) - 修改人
        + created (date) - 创建时间
        + modified (date) - 修改时间 
    + prices 价格表
        + subProductId  (long)  - 子产品的id
        + tbProductId   (long)  - 淘宝表的产品id
        + tbItemId   (long)   - 实际淘宝产品的id
        + source   (Integer)   - 来自淘宝，京东，亚马逊
        + currency  (Integer)  - 币别的id
        + isInland  (Integer)  - 是否国内   1为国内  0为国外
        + isManual  (Integer)  - 是否人工   1 为人工  0为机器
        + manualCouponClickUrl  (String)  -人工输入的优惠券链接（目前保留字段）
        + manualPurchaseLink  (String) -人工输入的购买链接（目前保留字段）
        + manualPrice  (Float)  - 人工输入的价格

### 增加 [POST] /subProducts
+ Data
   
+ Description
  + [MUST] authenticated
  + [MUST] ROLE_ADMIN

+ Parameters
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
    + prices 价格表
        + subProductId  (long)  - 子产品的id
        + tbProductId   (long)  - 淘宝表的产品id
        + tbItemId   (long)   - 实际淘宝产品的id
        + source   (Integer)   - 来自淘宝，京东，亚马逊
        + currency  (Integer)  - 币别的id
        + isInland  (Integer)  - 是否国内   1为国内  0为国外
        + isManual  (Integer)  - 是否人工   1 为人工  0为机器
        + manualCouponClickUrl  (String)  -人工输入的优惠券链接（目前保留字段）
        + manualPurchaseLink  (String) -人工输入的购买链接（目前保留字段）
        + manualPrice  (Float)  - 人工输入的价格
        
+ Request  (application/json)

        {
        "data": {
        "mainProductId": 1,
        "subFeature": "{\"拆字\"\":\"松木\"}",
        "keyWords": "小米,插板",
        "specification": "经典",
        "colour": 1,
        "isShow": 1,
        "shopUrl": "购买链接",
        "couponUrl": "http://优惠券链接",
        "manualInfo": [        //来源价格的保存
            {
                "tbProductId": 1111,
                "tbItemId": 0,
                "source": 1,
                "currency": 1,
                "isInland": 1,
                "manualPrice": 13.5,
                "manualCouponClickUrl": "http://ceshi1",
                "manualPurchaseLink": "http://ceshi1"
            },
            {
                "tbProductId": 1211,
                "tbItemId": 0,
                "source": 1,
                "currency": 2,
                "isInland": 1,
                "manualPrice": 14.5,
                "manualCouponClickUrl": "http://ceshi1",
                "manualPurchaseLink": "http://ceshi1"
            }
        ],
        "pictures": [
            {
                "pictureurl": "//1static.mifanxing.com/wx/image/29/15/990601.jpg",
                "title": "TestPicTURE2",
                "groupId": 1,
                "orderNo": 0
            },
            {
                "pictureurl": "//2static.mifanxing.com/wx/image/29/15/990601.jpg",
                "title": "TestPicTURE2",
                "groupId": 1,
                "orderNo": 0
            },
            {
                "pictureurl": "//3static.mifanxing.com/wx/image/29/15/990601.jpg",
                "title": "TestPicTURE2",
                "groupId": 36,
                "orderNo": 0
            },
            {
                "pictureurl": "//4static.mifanxing.com/wx/image/29/15/990601.jpg",
                "title": "TestPicTURE2",
                "groupId": 36,
                "orderNo": 0
            }
            ]
        }
        }
+ Response 200 

        {
        "data": {
        "id": 17,
        "type": "subProducts"
        }
        }


### 修改 [PATCH] /subProducts/{id}
+ Description
  + [MUST] authenticated
  + [MUST] ROLE_ADMIN

+ Parameters
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
    
+ Request (application/json)
 
        {
        "data": {
        "mainProductId": 1,
        "subFeature": "{\"拆字\"\":\"松木\"}",
        "keyWords": "小米,插板",
        "specification": "经典",
        "colour": 1,
        "isShow": 1,
        "shopUrl": "购买链接",
        "couponUrl": "http://优惠券链接",
        "manualInfo": [
            {
                "id": 35,
                "tbProductId": 1111,
                "tbItemId": 0,
                "source": 1,
                "currency": 2,
                "isInland": 1,
                "manualPrice": 122.5,
                "manualCouponClickUrl": "http://ceshi1",
                "manualPurchaseLink": "http://ceshi1"
            },
            {
                "tbProductId": 1111,
                "tbItemId": 0,
                "source": 1,
                "currency": 1,
                "isInland": 1,
                "manualPrice": 13.5,
                "manualCouponClickUrl": "http://ceshi1",
                "manualPurchaseLink": "http://ceshi1"
            },
            {
                "id": 36,
                "tbProductId": 1222221,
                "tbItemId": 0,
                "source": 1,
                "currency": 2,
                "isInland": 1,
                "manualPrice": 222.5,
                "manualCouponClickUrl": "http://ceshi1",
                "manualPurchaseLink": "http://ceshi1"
            }
        ],
        "pictures": [
            {
                "pictureurl": "//1static.mifanxing.com/wx/image/29/15/990601.jpg",
                "title": "TestPicTURE2",
                "groupId": 1,
                "orderNo": 0
            },
            {
                "pictureurl": "//2static.mifanxing.com/wx/image/29/15/990601.jpg",
                "title": "TestPicTURE2",
                "groupId": 1,
                "orderNo": 0
            },
            {
                "pictureurl": "//3static.mifanxing.com/wx/image/29/15/990601.jpg",
                "title": "TestPicTURE2",
                "groupId": 36,
                "orderNo": 0
            },
            {
                "pictureurl": "//4static.mifanxing.com/wx/image/29/15/990601.jpg",
                "title": "TestPicTURE2",
                "groupId": 36,
                "orderNo": 0
            }
        ]
        }
        }

+ Response 200 

### 删除 [DELETE] /subProducts/{id}
+ Description
  + [MUST]  Authenticated
  + [MUST] ROLE_ADMIN 
+  Response 204


### 查询后台子产品的相关信息 [GET] /subProducts/admin/{id}
查询出子产品的信息
+ Parameters
    + id  子产品的id
    
+ Request (application/json)
       
        {
        "data": {
        "id": 49,
        "enabled": 1,
        "creator": 0,
        "modifier": 0,
        "created": "2019-03-27 09:54:36",
        "modified": "2019-03-27 10:39:19",
        "mainProductId": 1,
        "subFeature": "{\"拆字\"\":\"松木\"}",
        "keyWords": "小米,插板",
        "specification": "经典",
        "colour": 1,
        "thumbsUp": 0,
        "thumbsDown": 0,
        "couponUrl": "http://优惠券链接",
        "shopUrl": "购买链接",
        "isShow": 1,
        "pictures": [
            {
                "id": 11,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-03-27 10:39:09",
                "modified": "2019-03-27 10:39:09",
                "pictureurl": "//1static.mifanxing.com/wx/image/29/15/990601.jpg",
                "title": "TestPicTURE2",
                "md5": "0",
                "groupId": 1,
                "orderNo": 0
            },
            {
                "id": 76,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-03-27 10:39:10",
                "modified": "2019-03-27 10:39:10",
                "pictureurl": "//2static.mifanxing.com/wx/image/29/15/990601.jpg",
                "title": "TestPicTURE2",
                "md5": "0",
                "groupId": 1,
                "orderNo": 0
            }
        ],
        "imageRotation": true,
        "rotations": [
            {
                "id": 77,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-03-27 10:39:10",
                "modified": "2019-03-27 10:39:10",
                "pictureurl": "//3static.mifanxing.com/wx/image/29/15/990601.jpg",
                "title": "TestPicTURE2",
                "md5": "0",
                "groupId": 36,
                "orderNo": 0
            },
            {
                "id": 78,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-03-27 10:39:11",
                "modified": "2019-03-27 10:39:11",
                "pictureurl": "//4static.mifanxing.com/wx/image/29/15/990601.jpg",
                "title": "TestPicTURE2",
                "md5": "0",
                "groupId": 36,
                "orderNo": 0
            }
        ],
        "colourClass": {
            "id": 1,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-02-20 11:08:46",
            "modified": "2019-02-20 11:08:50",
            "colourName": "红色",
            "colourPicture": "https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1552893543223&di=625a3ffdc859589fd6526c0b7a0dc4a7&imgtype=0&src=http%3A%2F%2Fimg010.hc360.cn%2Fm6%2FM01%2FFC%2FBE%2FwKhQoVbs__CEfumYAAAAABd0L1M127.jpg"
        },
        "manualInfo": [
            {
                "id": 37,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-03-27 10:39:19",
                "modified": "2019-03-27 10:39:19",
                "subProductId": 49,
                "tbProductId": 1111,
                "tbItemId": 0,
                "source": 1,
                "currency": 1,
                "isInland": 1,
                "isManual": 1,
                "manualCouponClickUrl": "http://ceshi1",
                "manualPurchaseLink": "http://ceshi1",
                "manualPrice": 13.5
            }
        ],
        "coupon": false
        }
        }

+ Request 400  （查询为空）


### 后台子产品通过产品ID得到子产品列表 [GET] subProducts/admin/productid/{productId}
+ Parameters
     +  productId 主产品ID
+ Description 
    + id  Long  子产品ID
    + enabled 禁用为0 启用为1
    + creator  Long 创建人
    + modifier Long 修改人
    + created  Date 创建时间
    + modified Date 修改时间
    + mainProductId  Long 主产品id
    + subFeature  String 子特征
    + keyWords     String  淘宝关键词
    + specification  String 规格
    + colour      Long 颜色
    + colourClass Colour 颜色类
    + thumbsUp    Integer  点赞
    + thumbsDown  Integer 踩
    + isShow      Integer 是否展示（1为展示 0为不展示）
    + coupon      Boolean  是否有优惠券
    
+ Response 200 (Application/json)
    
        {
        "data": [
        {
            "id": 1,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-03-08 18:48:38",
            "modified": "2019-03-08 18:48:38",
            "mainProductId": 1,
            "subFeature": "[\"影像传感器\": { \"传感器类型\": \"Exmor Rs\", \"有效哦像素\": \"2420\" }, \"对焦系统\": {\"对焦点\": \"683各个想问点\"}, \t\"液晶屏\": { \"尺寸\": \"3.tt\", \"总箱数\": \"111\" } ]",
            "keyWords": "小米8",
            "specification": "6GB+64GB",
            "thumbsUp": 5,
            "thumbsDown": 0,
            "isShow": 1,
            "colourClass": {
                "id": 1,
                "colourName": "红色",
                "colourPicture": "http://img.alicdn.com/imgextra/i4/804206007/TB2vBDgxxlmpuFjSZPfXXc9iXXa_!!804206007.jpg_40x40q90.jpg"
            },
            "coupon": false
        },
        {
            "id": 2,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-03-08 18:56:20",
            "modified": "2019-03-08 18:56:20",
            "mainProductId": 1,
            "keyWords": "blue,yeti",
            "specification": "8GB+128GB",
            "thumbsUp": 4,
            "thumbsDown": 1,
            "isShow": 1,
            "colourClass": {
                "id": 1,
                "colourName": "红色",
                "colourPicture": "http://img.alicdn.com/imgextra/i4/804206007/TB2vBDgxxlmpuFjSZPfXXc9iXXa_!!804206007.jpg_40x40q90.jpg"
            },
            "coupon": false
        },
        {
            "id": 3,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-03-08 18:56:48",
            "modified": "2019-03-08 18:56:48",
            "mainProductId": 1,
            "keyWords": "Shure,舒尔,SM58S",
            "specification": "6GB+64GB",
            "thumbsUp": 3,
            "thumbsDown": 1,
            "isShow": 1,
            "colourClass": {
                "id": 2,
                "colourName": "黑色",
                "colourPicture": "http://img.alicdn.com/imgextra/i4/804206007/TB2vBDgxxlmpuFjSZPfXXc9iXXa_!!804206007.jpg_40x40q90.jpg"
            },
            "coupon": false
        },
        {
            "id": 4,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-03-08 18:56:17",
            "modified": "2019-03-08 18:56:17",
            "mainProductId": 1,
            "keyWords": "Shure,舒尔,SM58S",
            "specification": "8GB+128GB",
            "thumbsUp": 3,
            "thumbsDown": 1,
            "isShow": 1,
            "colourClass": {
                "id": 3,
                "colourName": "蓝色",
                "colourPicture": "http://img.alicdn.com/imgextra/i4/804206007/TB2vBDgxxlmpuFjSZPfXXc9iXXa_!!804206007.jpg_40x40q90.jpg"
            },
            "coupon": false
        },
        {
            "id": 5,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-03-08 17:20:42",
            "modified": "2019-03-08 17:20:42",
            "mainProductId": 1,
            "keyWords": "JBL,GO2",
            "specification": "8GB+222GB",
            "thumbsUp": 2,
            "thumbsDown": 1,
            "isShow": 1,
            "colourClass": {
                "id": 3,
                "colourName": "蓝色",
                "colourPicture": "http://img.alicdn.com/imgextra/i4/804206007/TB2vBDgxxlmpuFjSZPfXXc9iXXa_!!804206007.jpg_40x40q90.jpg"
            },
            "coupon": false
        },
        {
            "id": 12,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-03-11 16:53:46",
            "modified": "2019-03-11 16:53:46",
            "mainProductId": 1,
            "subFeature": "{\"品质\":\"另类\"}",
            "keyWords": "小米91",
            "specification": "x86",
            "thumbsUp": 3,
            "thumbsDown": 0,
            "isShow": 1,
            "colourClass": {
                "id": 1,
                "colourName": "红色",
                "colourPicture": "http://img.alicdn.com/imgextra/i4/804206007/TB2vBDgxxlmpuFjSZPfXXc9iXXa_!!804206007.jpg_40x40q90.jpg"
            },
            "coupon": false
        },
        {
            "id": 13,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-03-08 15:01:54",
            "modified": "2019-03-08 15:01:54",
            "mainProductId": 1,
            "subFeature": "{\"品质\":\"另类\"}",
            "keyWords": "小米91",
            "specification": "x86",
            "thumbsUp": 1,
            "thumbsDown": 1,
            "isShow": 1,
            "colourClass": {
                "id": 1,
                "colourName": "红色",
                "colourPicture": "http://img.alicdn.com/imgextra/i4/804206007/TB2vBDgxxlmpuFjSZPfXXc9iXXa_!!804206007.jpg_40x40q90.jpg"
            },
            "coupon": false
        },
        {
            "id": 15,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-03-08 15:02:49",
            "modified": "2019-03-08 15:02:49",
            "mainProductId": 1,
            "subFeature": "{\"品质\":\"另类\"}",
            "keyWords": "小米91",
            "specification": "x86",
            "thumbsUp": 2,
            "thumbsDown": 0,
            "isShow": 1,
            "colourClass": {
                "id": 1,
                "colourName": "红色",
                "colourPicture": "http://img.alicdn.com/imgextra/i4/804206007/TB2vBDgxxlmpuFjSZPfXXc9iXXa_!!804206007.jpg_40x40q90.jpg"
            },
            "coupon": false
        },
        {
            "id": 16,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-03-08 18:55:25",
            "modified": "2019-03-08 18:55:25",
            "mainProductId": 1,
            "subFeature": "{\"拆字\"\":\"松木\"}",
            "keyWords": "小米,插板",
            "specification": "经典",
            "thumbsUp": 2,
            "thumbsDown": 1,
            "isShow": 1,
            "colourClass": {
                "id": 1,
                "colourName": "红色",
                "colourPicture": "http://img.alicdn.com/imgextra/i4/804206007/TB2vBDgxxlmpuFjSZPfXXc9iXXa_!!804206007.jpg_40x40q90.jpg"
            },
            "coupon": false
        },
        {
            "id": 17,
            "enabled": 1,
            "creator": 0,
            "modifier": 0,
            "created": "2019-03-08 15:03:05",
            "modified": "2019-03-08 15:03:05",
            "mainProductId": 1,
            "subFeature": "{\"拆字\"\":\"黄松木\"}",
            "keyWords": "小米1,插板1",
            "specification": "经典",
            "thumbsUp": 1,
            "thumbsDown": 0,
            "isShow": 1,
            "colourClass": {
                "id": 1,
                "colourName": "红色",
                "colourPicture": "http://img.alicdn.com/imgextra/i4/804206007/TB2vBDgxxlmpuFjSZPfXXc9iXXa_!!804206007.jpg_40x40q90.jpg"
            },
            "coupon": false
        }
        ]
        }

### 查询用户收藏列表(客户端) [GET] /collects?filter[creator]=id
+ Parameters
     +  id 用户id
+ Description 
    + subProductId 子产品ID
    + isShow 是否展示 0：不展示 1：展示
    + pictures 子产品图片
    + subProductTitle 产品标题
    + forumName 类别
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
            "self": "/collects?filter[creator]=1037&page[number]=1&page[size]=10",
            "first": "/collects?filter[creator]=1037&page[number]=1&page[size]=10",
            "last": "/collects?filter[creator]=1037&page[number]=1&page[size]=10"
        },
        "data": [
            {
                "id": 2,
                "creator": 1037,
                "created": "2019-02-28 17:27:43",
                "subProductId": 2,
                "isShow": 1,
                "pictures": [
                    {
                        "pictureurl": "//static.mifanxing.com/wx/image/29/15/990601.jpg"
                    },
                    {
                        "pictureurl": "//static.mifanxing.com/wx/image/29/15/990604.jpg"
                    },
                    {
                        "pictureurl": "//static.mifanxing.com/wx/image/29/15/990602.jpg"
                    },
                    {
                        "pictureurl": "//static.mifanxing.com/wx/image/29/15/990603.jpg"
                    }
                ],
                "subProductTitle": "小米8 8GB+128GB 红色",
                "forumName": "商城"
            },
            {
                "id": 7,
                "creator": 1037,
                "created": "2019-03-07 17:49:20",
                "subProductId": 1,
                "isShow": 1,
                "pictures": [
                    {
                        "pictureurl": "//static.mifanxing.com/wx/image/29/15/990601.jpg"
                    },
                    {
                        "pictureurl": "//static.mifanxing.com/wx/image/29/15/990604.jpg"
                    },
                    {
                        "pictureurl": "//static.mifanxing.com/wx/image/29/15/990602.jpg"
                    },
                    {
                        "pictureurl": "//static.mifanxing.com/wx/image/29/15/990603.jpg"
                    }
                ],
                "subProductTitle": "小米8 6GB+64GB 红色",
                "forumName": "商城"
            },
            {
                "id": 68,
                "creator": 1037,
                "created": "2019-03-11 17:45:44",
                "subProductId": 4,
                "isShow": 1,
                "subProductTitle": "小米8 8GB+128GB 蓝色",
                "forumName": "商城"
            }
        ]
      }
      



## 分类管理
### 增加 [POST] /category
顶级分类parentId为0
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN
    
+ Request (application/json) 

      {
        "data": {
        "enabled": 1,
        "parentId": 0,
        "title": "录音2",
        "leaf": 0,
        "origin":"http://static.mifanxing.com/yyren/image/241/14/979421.jpg?w=400"
        }
        }

Response200 (application/json)

    {
    "data": {
        "id": 5,
        "type": "category"
    }
    }
Response400 (application/json)

    {
        "errors": [
        {
            "status": "400",
            "title": "Bad Request",
            "detail": "请不要在叶子节点再加入新的分类！"
        }
        ]
    }
Response400 (application/json)

    {
        "errors": [
        {
            "status": "400",
            "title": "Bad Request",
            "detail": "上级分类不存在，无法正常保存！"
        }
    ]
    }


### 修改 [PATCH] /category/{id}

+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN

+ Request (application/json)
    
      {
        "data": {
    	"id":4,
        "enabled": 1,
        "parentId": 0,
        "title": "录音444",
        "leaf": 0,
        "origin":"http://static.mifanxing.com/yyren/image/241/14/979421.jpg?w=400"
        }
        }

+ Response 200

### 删除 [DELETE] /category/{id}

+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN
+ Response 204 



### 查询通过模糊查询分类 [GET] /category/leaf
例如：http://192.168.1.138:8299/category/leaf?filter[categoryName]=无


+ Parameters
    + filter[categoryName] (String)   分类名称  -必填
    + filter[leaf]  不填写为分类都查，当为1的时候，为叶子节点，当为0的时候，查询的非叶子节点  -非必填
    
+ Response200(application/json)

        {
        "data": [
        {
            "id": 2,
            "title": "无线麦克风",
            "leaf": 0
        },
        {
            "id": 3,
            "title": "BLUE无线麦克风",
            "leaf": 1
        }
        ]
        }


### 通过parentId得到分类
例如：http://192.168.2.138:8299/category/byparentid

+ Parameters
    + filter[parentId]   (int)   -非必填 默认是0

    
+ Response200(application/json)

        {
        "data": [
        {
            "id": 2,
            "title": "无线麦克风",
            "leaf": 0
        },
        {
            "id": 6,
            "title": "k&m",
            "leaf": 0
        }
        ]
        }

## 价格来源管理
+ Data
    + id (Long) - ID
    + sourceName (String) - 来源名称
    + source (Long) - 是否国内 1为国内 0为国外
    + sourceUrl (String) - 来源url
    + enabled (int) - 0禁用 1启用
    + creator (Long) - 创建人
    + modifier (Long) - 修改人
    + created (date) - 创建时间
    + modified (date) - 修改时间

### 增加 [POST] /subProductPricesSource
+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN
    
+ Request (application/json) 

      {
          "data":{
        	"sourceName":"国美",
        	"source":"1",
        	"sourceUrl":"https://ss0.bdstatic.com/-0U0bnSm1A5BphGlnYG/tam-ogel/894ba013323b89b6391baa06da7629b7_222_222.jpg"
          } 
        }

Response (application/json)

    {
      "data": {
        "id": 17,
        "type": "subProductPricesSource"
     }
    }

### 修改 [PATCH] /subProductPricesSource/{id}

+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN

+ Request (application/json)
    
      {
       "data":{
    	 "sourceName":"国美1",
    	 "source":"1",
    	 "sourceUrl":"https://ss0.bdstatic.com/-0U0bnSm1A5BphGlnYG/tam-ogel/894ba013323b89b6391baa06da7629b7_222_222.jpg"
       } 
      }

+ Response 200

### 列表[GET] /subProductPricesSource
+ Parameters
  + id 
  + title
     + 查询示例：filter[sourceName]=%25来源%25 （'%25'为'%'的转义） 
  + sort -modified(从新到旧) | modified(从旧到新)
+ Request (application/json)
       
      {
        "meta": {
            "totalPages": 2,
            "totalElements": 11,
            "size": 10,
            "number": 1,
            "numberOfElements": 10,
            "first": true,
            "last": false,
            "sort": null
        },
        "links": {
            "self": "/subProductPricesSource?page[number]=1&page[size]=10",
            "first": "/subProductPricesSource?page[number]=1&page[size]=10",
            "next": "/subProductPricesSource?page[number]=2&page[size]=10",
            "last": "/subProductPricesSource?page[number]=2&page[size]=10"
        },
        "data": [
            {
                "id": 1,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-02-20 11:08:46",
                "modified": "2019-02-20 11:08:50",
                "sourceName": "淘宝",
                "source": 1,
                "sourceUrl": "https://gss2.bdstatic.com/9fo3dSag_xI4khGkpoWK1HF6hhy/baike/c0%3Dbaike150%2C5%2C5%2C150%2C50/sign=948e7f7076d98d1062d904634056d36b/5fdf8db1cb134954b37001e85c4e9258d0094ad4.jpg"
            },
            {
                "id": 2,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-02-24 21:28:01",
                "modified": "2019-02-24 21:28:03",
                "sourceName": "京东",
                "source": 1,
                "sourceUrl": "https://gss1.bdstatic.com/-vo3dSag_xI4khGkpoWK1HF6hhy/baike/c0%3Dbaike116%2C5%2C5%2C116%2C38/sign=57d5eca73f2ac65c73086e219a9bd974/7dd98d1001e939014c6dbdf971ec54e737d1968d.jpg"
            },
            {
                "id": 3,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-02-24 21:28:06",
                "modified": "2019-02-24 21:28:09",
                "sourceName": "苏宁",
                "source": 1,
                "sourceUrl": "https://gss2.bdstatic.com/9fo3dSag_xI4khGkpoWK1HF6hhy/baike/c0%3Dbaike150%2C5%2C5%2C150%2C50/sign=da3a0820943df8dcb23087c3ac7819ee/9f510fb30f2442a773c6fb72da43ad4bd0130218.jpg"
            },
            {
                "id": 4,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-02-27 11:32:09",
                "modified": "2019-02-27 11:32:09",
                "sourceName": "网易考拉",
                "source": 1,
                "sourceUrl": "https://gss0.bdstatic.com/-4o3dSag_xI4khGkpoWK1HF6hhy/baike/c0%3Dbaike272%2C5%2C5%2C272%2C90/sign=e00da6a4c6ef7609280691cd4fb4c8a9/cf1b9d16fdfaaf511f272386815494eef11f7ac7.jpg"
            },
            {
                "id": 5,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-02-27 11:32:30",
                "modified": "2019-02-27 11:33:00",
                "sourceName": "微信",
                "source": 1,
                "sourceUrl": "https://gss3.bdstatic.com/7Po3dSag_xI4khGkpoWK1HF6hhy/baike/c0%3Dbaike92%2C5%2C5%2C92%2C30/sign=a2970c419a2397ddc274905638ebd9d2/d53f8794a4c27d1e15b40e6210d5ad6edcc43881.jpg"
            },
            {
                "id": 6,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-02-27 11:43:09",
                "modified": "2019-02-27 11:43:09",
                "sourceName": "拼多多",
                "source": 1,
                "sourceUrl": "https://gss3.bdstatic.com/-Po3dSag_xI4khGkpoWK1HF6hhy/baike/c0%3Dbaike150%2C5%2C5%2C150%2C50/sign=75fba791376d55fbd1cb7e740c4b242f/14ce36d3d539b600699fc4f8e350352ac65cb728.jpg"
            },
            {
                "id": 13,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-02-28 19:51:11",
                "modified": "2019-02-28 19:51:14",
                "sourceName": "亚马逊",
                "source": 0,
                "sourceUrl": "https://gss2.bdstatic.com/9fo3dSag_xI4khGkpoWK1HF6hhy/baike/c0%3Dbaike80%2C5%2C5%2C80%2C26/sign=46afe7aa242eb938f86072a0b40bee50/d043ad4bd11373f0904a8bd4af0f4bfbfbed0407.jpg"
            },
            {
                "id": 14,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-03-08 18:21:32",
                "modified": "2019-03-08 18:21:35",
                "sourceName": "洋码头",
                "source": 0,
                "sourceUrl": "https://gss2.bdstatic.com/9fo3dSag_xI4khGkpoWK1HF6hhy/baike/c0%3Dbaike80%2C5%2C5%2C80%2C26/sign=fd9875b3b299a9012f3853647cfc611e/4ec2d5628535e5dd05b90c787cc6a7efcf1b6284.jpg"
            },
            {
                "id": 15,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-03-08 18:24:01",
                "modified": "2019-03-08 18:24:04",
                "sourceName": "windelnde",
                "source": 0,
                "sourceUrl": "https://static.windeln.com.cn/content/1000.WPnB3DauMSatzNMj/windeln-cn-2x.png"
            },
            {
                "id": 16,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-03-19 10:58:00",
                "modified": "2019-03-19 10:58:03",
                "sourceName": "k&m",
                "source": 0,
                "sourceUrl": "https://images.static-thomann.de/pics/herstlogos/k_und_m.gif"
            }
        ]
      }
       

### 删除 [DELETE] /subProductPricesSource/{id}

+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN
+ Response 204  
