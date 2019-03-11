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
    	"data":{
    		"colourName":"粉红色"
    	}
      }

Response (application/json)

    {
        "data": {
            "id": 1,
            "type": "colour"
        }
    }

### 修改 [PATCH] /colour/{id}

+ Description
    + [MUST] authenticated
    + [MUST] ROLE_ADMIN

+ Request (application/json)
    
      {
        	"data":{
        		"colourName":"粉红色1"
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
		"title": "小米插座1",
		"briefDescription": "小米插座1",
		"description": "小米插座1",
		"brandId": "1",
		"mainFeature":"{\"颜色\":\"红色\"}",
		"accessories":[
			{ "type": 0,
              "filename": "https://jdvodoss.jcloudcache.com/vodtransgzp1251412368/7447398156451886582/v.f30.mp4?dockingId=aee5a279-b858-4e06-a8e6-3accdc3f8014&storageSource=3",
              "title": "小米插座视频",
              "description": "小米插座视频",
              "filesize": 0,
              "duration": 0},
              {
              "type": 1,
              "filename": "https://static.mifanxing.com/yyren/image/week/20171110/1/Snare-1_1inchabove.mp3",
              "title": "音频22",
              "description": "音频22",
              "filesize": 0,
              "duration": 0
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
        "id": 19,
        "categoryId": 3,
        "title": "小米插座19",
        "briefDescription": "小米插座19",
        "description": "小米插座19",
        "brandId": "1",
        "mainFeature": "{\"颜色\":\"绿色\"}",
        "access": "{\"颜色\":\"红色\"}",
        "accessories": [
            {
                "id": 22,
                "type": 0,
                "filename": "https://jdvodoss.jcloudcache.com/vodtransgzp1251412368/7447398156451886582/v.f30.mp4?dockingId=aee5a279-b858-4e06-a8e6-3accdc3f8014&storageSource=3",
                "title": "小米插座视1频",
                "description": "小米插座视频1",
                "filesize": 0,
                "duration": 0
            },
            {
                "id": 25,
                "type": 1,
                "filename": "https://static.mifanxing.com/yyren/image/week/20171110/1/Snare-1_1inchabove.mp3",
                "title": "音频111123422",
                "description": "音频212",
                "filesize": 0,
                "duration": 0
            },
            {
                "type": 1,
                "filename": "https://static.mifanxing.com/yyren/image/week/20171110/1/Snare-1_1inchabove.mp3",
                "title": "音频211112",
                "description": "音频2211",
                "filesize": 0,
                "duration": 0
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
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-03-04 10:15:22",
                "modified": "2019-03-04 10:15:22",
                "mainProductId": 1,
                "keyWords": "小米8",
                "specification": "6GB+64GB",
                "colour": 1,
                "thumbsUp": 17,
                "thumbsDown": 9,
                "isShow": 1
            },
            {
                "id": 2,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-02-26 11:27:02",
                "modified": "2019-02-26 11:27:02",
                "mainProductId": 1,
                "keyWords": "小米8",
                "specification": "8GB+128GB",
                "colour": 1,
                "thumbsUp": 8,
                "thumbsDown": 2,
                "isShow": 1
            },
            {
                "id": 3,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-02-20 11:05:22",
                "modified": "2019-02-20 11:05:25",
                "mainProductId": 1,
                "keyWords": "小米8",
                "specification": "6GB+64GB",
                "colour": 2,
                "thumbsUp": 1,
                "thumbsDown": 1,
                "isShow": 1
            },
            {
                "id": 4,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-02-20 11:05:18",
                "modified": "2019-02-20 11:05:14",
                "mainProductId": 1,
                "keyWords": "小米8",
                "specification": "8GB+128GB",
                "colour": 3,
                "thumbsUp": 1,
                "thumbsDown": 1,
                "isShow": 1
            },
            {
                "id": 5,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "mainProductId": 1,
                "keyWords": "小米8",
                "specification": "8GB+222GB",
                "colour": 3,
                "thumbsUp": 1,
                "thumbsDown": 1,
                "isShow": 1
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
                "isShow": 1
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
                "isShow": 1
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
                "isShow": 1
            }
        ]
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
        "id": 17,
        "mainProductId": 1,
        "subFeature": "{\"拆字\"\":\"黄松木\"}",
        "keyWords": "小米1,插板1",
        "specification": "经典",
        "colour": 1,
        "isShow": 1,
        "thumbsUp":10,
        "thumbsDown":20,
        "shopUrl": "购买链接",
        "pictures": [
            {
                "id": 11,
                "pictureurl": "//1static.mifanxing.com/wx/image/29/15/990601.jpg",
                "title": "TestPicTURE2",
                "groupId": 1,
                "orderNo": 0
            },
            {
                "id": 12,
                "pictureurl": "//static.mifanxing.com/article/image/253/86/5700886.jpg",
                "title": "TestPicTURE2",
                "groupId": 1,
                "orderNo": 1
            },
            {
                "id": 13,
                "pictureurl": "//static.mifanxing.com/article/image/253/86/570088116.jpg",
                "title": "TestPicTURE2",
                "groupId": 36,
                "orderNo": 0
            },
            {
                "id": 14,
                "pictureurl": "//static.mifanxing.com/article/image/253/86/570081186.jpg",
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
    + id  子产品的信息
    
+ Request (application/json)
       
        {
        "data": {
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
        "pictures": [
            {
                "id": 11,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-03-04 14:16:25",
                "modified": "2019-03-04 14:16:25",
                "pictureurl": "//1static.mifanxing.com/wx/image/29/15/990601.jpg",
                "title": "TestPicTURE2",
                "md5": "0",
                "groupId": 1,
                "orderNo": 0
            },
            {
                "id": 12,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-03-04 14:16:27",
                "modified": "2019-03-04 14:16:27",
                "pictureurl": "//static.mifanxing.com/article/image/253/86/5700886.jpg",
                "title": "TestPicTURE2",
                "md5": "147524386900817203547092139257261658029",
                "groupId": 1,
                "orderNo": 1
            }
        ],
        "imageRotation": true,
        "rotations": [
            {
                "id": 13,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-03-04 14:16:29",
                "modified": "2019-03-04 14:16:29",
                "pictureurl": "//static.mifanxing.com/article/image/253/86/570088116.jpg",
                "title": "TestPicTURE2",
                "md5": "0",
                "groupId": 36,
                "orderNo": 0
            },
            {
                "id": 14,
                "enabled": 1,
                "creator": 0,
                "modifier": 0,
                "created": "2019-03-04 14:16:29",
                "modified": "2019-03-04 14:16:29",
                "pictureurl": "//static.mifanxing.com/article/image/253/86/570081186.jpg",
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
            "colourPicture": "http://img.alicdn.com/imgextra/i4/804206007/TB2vBDgxxlmpuFjSZPfXXc9iXXa_!!804206007.jpg_40x40q90.jpg"
        }
        }
        }

+ Request 400  （查询为空）

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
