# 后台
+ 2019年2月20日
    + 子产品经销商初始化
    + 产品颜色初始化
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
