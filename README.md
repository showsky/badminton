Badminton API Document
===

[![Join the chat at https://gitter.im/showsky/3tr](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/showsky/3tr?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

* Api base URL: **https://[domain name]/api**
* Image base URL: **https://[domain name]/images**
* ***All response JSON format use of string type***
* Support HTTP compression
* Base rsponse JSON pattern

	```
{
		"status": [success or fail],
		"errno": [error No],
		"errmsg": [error Message],
		"data": [data]
}

	```
* Use memcached image and ticket and user data 

Chart
===

## Bind Phone

![](https://github.com/showsky/3tr/blob/master/image/bind_phone.png?raw=true)

## Sign Place

![](https://github.com/showsky/3tr/blob/master/image/sign_place.png?raw=true)

## Server

* **/server/endpoint**
	* GET
	* Request
	
	```
	GET /server/endpoint
	```
	
	* Response
	
	```
	{
	    "status": "success",
	    "errno": "",
	    "errmsg": "",
	    "data": {
	        "api_domain": "xxxx",
	        "images_domain": "xxx",
	        "api_version": "v1.0.0"
	    }
	}
	```
	
## Report

* **/report/sign/**
	* GET
	
	| name | require | default | explanation |
	|------|------|-----|----|
	|place_id|Y|-|-|
	|date|Y|2016-04-04|-|
	|status|Y|-|1: 等待確定 2: 報名成功  3: 報名失敗|
	
	* Request

	```
	GET /report/sign?place_id=8&date=2016-04-07&status=1
	```
	
	* Response

	```
	{
	  "status": "success",
	  "errno": "",
	  "errmsg": "",
	  "data": [
	    {
	      "name": "測試員",
	      "email": "",
	      "phone": "886973350015",
	      "people": "2",
	      "date": "2016-04-07",
	      "time": "19:00:00",
	      "status": "1",
	      "update_time": "2016-03-31 16:48:50",
	      "create_time": "2016-03-31 16:46:41"
	    },
	    {
	      "name": "測試員",
	      "email": "",
	      "phone": "886973350015",
	      "people": "2",
	      "date": "2016-04-07",
	      "time": "19:00:00",
	      "status": "2",
	      "update_time": "2016-03-31 16:39:49",
	      "create_time": "2016-03-31 16:39:14"
	    },
	    {
	      "name": "測試員",
	      "email": "",
	      "phone": "886973350015",
	      "people": "3",
	      "date": "2016-04-07",
	      "time": "19:00:00",
	      "status": "3",
	      "update_time": "2016-03-31 16:32:57",
	      "create_time": "2016-03-31 16:32:16"
	    }
	  ]
	}
	```

## Place

* **/place**
	* GET
	* result data end_date before

	| name | require | default | explanation |
	|------|------|-----|----|
	|lat|Y|-|latitude|
	|lon|Y|-|longitude|
	|distance|N|3000|unit: meter|
	|order|N|-|distance, date|can OR use|
	|p|N|-|page|
	|c|N|-|count|
	
	* Request

	```
	GET /place?lat=-1212.123123&lon=123.5675675
	```
	
	* Response
	
	```
	{
   "status": "success",
   "errno": "",
   "errmsg": "",
   "data": [
      {
         "id": "1",
         "team_name": "欣動羽球社",
         "city": "台北",
         "location": "東門國小",
         "address": "台北市中正區仁愛路一段2之4號",
         "latitude": "0.0",
         "longitude": "0.0",
         "update_time": "0000-00-00 00:00:00",
         "start_time": "19:50:00",
         "end_time": "21:50:00",
         "image_filename": "lkfjwljfljlfj.jpg",
         "image_timestamp": "11283812691",
         "disance": "1861",
         "datetime": "2015-05-06 19:50:00",
         "date": "2015-05-06"
      },
      {
         "id": "2",
         "team_name": "采翼羽球隊",
         "city": "台北",
         "location": "興雅國小",
         "address": "台北市基隆路一段83巷",
         "latitude": "0.0",
         "longitude": "0.0",
         "update_time": "0000-00-00 00:00:00",
         "start_time": "19:50:00",
         "end_time": "21:50:00",
         "image_filename": "lkfjwljfljlfj.jpg",
         "image_timestamp": "11283812691",
         "disance": "1861",
         "datetime": "2015-05-06 19:50:00",
         "date": "2015-05-06"
      },
      {
         "id": "3",
         "team_name": "超勝羽球隊-大安",
         "city": "台北",
         "location": "銘傳國小四樓羽球場",
         "address": "台北市大安區羅斯福路四段21號",
         "latitude": "0.0",
         "longitude": "0.0",
         "update_time": "0000-00-00 00:00:00",
         "start_time": "19:50:00",
         "end_time": "21:50:00",
         "image_filename": "lkfjwljfljlfj.jpg",
         "image_timestamp": "11283812691",
         "disance": "1861",
         "datetime": "2015-05-06 19:50:00",
         "date": "2015-05-06"
      }
   ]
}
	
	```

* **/place/fetch/[id]**
	* GET
	* sign_date range within a month

	| name | require | default | explanation |
	|------|------|-----|----|
	|id|Y|-|must numeric|

	* Request

	```
	GET /place/info/1
	```
	
	* Response
	
	```
	{
	    "status": "success",
	    "errno": "",
	    "errmsg": "",
	    "data": {
	        "id": "1",
	        "team_name": "欣動羽球社",
	        "team_comment": "歡迎初級到中上,會有一面場開放給初學者打",
	        "country": "台灣",
	        "city": "台北",
	        "location": "東門國小",
	        "address": "台北市中正區仁愛路一段2之4號",
	        "price_boy": "200",
	        "price_girl": "200",
	        "start_date": "2015-01-01",
	        "end_date": "2015-12-31",
	        "week": "1",
	        "start_time": "19:00:00",
	        "end_time": "21:30:00",
	        "degree": "1,3",
	        "people": "13",
	        "device_space": "1",
	        "device_floor": "1",
	        "device_ball_brand": "10",
	        "device_ball_price": "2",
	        "device_light": "0",
	        "device_ac": "0",
	        "device_water": "0",
	        "device_bathroom": "0",
	        "lat": "0.000000",
	        "long": "0.000000",
	        "update_time": "2015-07-09 19:22:51",
	        "images": [
	            {
	                "filename": "cec6c4fdf0ebb6bddcb9387775571d9f.jpg",
	                "timestamp": "1436336651"
	            }
	        ],
	        "sign_date": [
	            {
	                "date": "2015-07-13",
	                "people": 0
	            },
	            {
	                "date": "2015-07-20",
	                "people": 0
	            },
	            {
	                "date": "2015-07-27",
	                "people": 0
	            },
	            {
	                "date": "2015-08-03",
	                "people": 0
	            }
	        ]
	    }
	}
	```
	
* **/place/search**
	* GET

	| name | require | default | explanation |
	|------|------|-----|----|

	* Request
	
	```
	```

	* Response

	```
	{
	}
	```

* **/place/add**
	* POST
	
	| name | require | default | explanation |
	|------|------|-----|----|
	|team_name|Y|-|團隊名稱|
	|team_comment|N|-|團隊說明|
	|country|Y|-|國家|
	|city|Y|-|城市|
	|location|Y|-|地標|
	|address|Y|-|地址|
	|price_boy|Y|-|男生價錢|
	|price_girl|Y|-|女生價錢|
	|start_date|Y|-|1985-02-22|
	|end_data|Y|-|1985-02-22|
	|week|Y|0|1 2 3 4 5 6 7|
	|start_time|Y|-|22:00:00|
	|end_time|Y|-|19:00:00|
	|degress|Y|-|1. 初級 2. 中下級 3. 中等 4. 中上 5. 高級|
	|people|Y|0|人數|
	|contact_name|Y|-|聯絡姓名|
	|contact_email|Y|-|聯絡信箱|
	|contact_phone|Y|-|聯絡電話|
	|device_space|Y|0|場地數|
	|device_floor|Y|0|1. 木板 2. PU 3. 其他|
	|device\_ball\_brand|Y|0|1.勝利 2.YY 3.超勝 4.MMOA 5.Bonny 6.久奈司 7.桑瑪氏   8.超力  9.其他|
	|device\_ball\_price|Y|0|1.300-350 2.350-400 3.400-450 4.450-500 5.500以上|
	|device_light|Y|0|1. 頂燈 2. 側燈|
	|device_ac|Y|0|1. 有 2. 無|
	|device_water|Y|0|1. 有 2. 無|
	|device_bathroom|Y|0|1. 有 2. 無|
	|lat|Y|-|-|
	|lon|Y|-|-|
	
	* Response
	
	```
{
		"status": "success",
		"errno": "",
		"errmsg": "",
		"data": {
			"place_id" => 12
		}
}
	```

* **/place/edit**
	* POST

	| name | require | default | explanation |
	|------|------|-----|----|
	
	* Request
	
	```
	```
	
	* Response

	```
	{
	}
	```
	
* **/place/delete/**
	* POST

	| name | require | default | explanation |
	|------|------|-----|----|

	* Request
	
	```
	```

	* Response

	```
	{
	}
	```

## Image

* **/image/fetch/[place id]**
	* GET

	| name | require | default | explanation |
	|------|------|-----|----|
	|place id|Y|-|-|
	
	* Request
	
	```
	GET /image/detch/1
	```
	
	* Response

	```
{
		"status": "success",
		"errno": "",
		"errmsg": "",
		"data" : [
    		{
      			"filename" : "cdd41435828345612aa43758797ebe83.jpg",
      			"timestamp" : "1436180721"
    		},
    		{
      			"filename" : "0c285cda7116b339d1093a73ef66e639.jpg",
      			"timestamp" : "1436180797"
    		},
    		{
      			"filename" : "ffc8c29ac64c5764da93ef0a6535fc34.jpg",
      			"timestamp" : "1436180797"
    		}
  		]
}
	```
	

* **/image/upload/[place id]**
	* POST
	* image max limit 3, and must JPG type
	* image size limit 300kb
	* file upload key name must image1, image2, image3

	| name | require | default | explanation |
	|------|------|-----|----|
	|place id|Y|-|-|
	
	* Request

	```
	POST /image/upload/12
	```

	* Response

	```
{
		"status": "success",
		"errno": "",
		"errmsg": "",
		"data": {
			"place_id" => 12
		}
}
	```

* **/image/delete**
	* POST

	| name | require | default | explanation |
	|------|------|-----|----|
	|filename|Y|-|-|
	
	* Request

	```
	POST /image/delete
	```

	* Response

	```
{
		"status": "success",
		"errno": "",
		"errmsg": "",
		"data": {
			"filename" => "qwkldfjoqwjflqwjlf.jpg"
		}
}
	```

## User
	
* **/user/send**
	* POST
	* phone number must 10 length and first char is 0
	* Inspect send sms ip daily max 50
	* inspect send sms phone daily max 10

	| name | require | default | explanation |
	|------|------|-----|----|
	|phone|Y|-|0123456789|

	* Request
	
	```
	POST /user/send
	```

	* Response

	```
	{
		"status": "success,
		"errno":"",
		"errmsg:"",
		"data": {
			"phone": "123456789",
		}
	}
	```


* **/user/bind**
	* POST
	* passcode string length = 40
	* the code only bind only once

	| name | require | default | explanation |
	|------|------|-----|----|
	|code|Y|-|-|
	|name|Y|-|user name|
	|email|N|-|-|
	|platform|Y|-|1:Android 2:iOS|
	|token|Y|-|GCM token|

	* Request
	
	```
	POST /user/bind
	```

	* Response

	```
	{
		"status": "success",
		"errno": "",
		"errmsg": "",
		"data": {
			"passcode": "opqjdfoqpwjfwjkfnqw892y3rwejkrhwk",
		}
	}
	```
	
* **/user/update?passcode=[passcode]**
	* POST

	| name | require | default | explanation |
	|------|------|-----|----|
	|platform|Y|-|1:Android 2:iOS|
	|token|Y|-|GCM token|
	
	* Request
	
	```
	POST /user/update?passcode=opqjdfoqpwjfwjkfnqw892y3rwejkrhwk
	```
	
	* Response

	```
	{
		"status": "success",
		"errno": "",
		"errmsg": "",
		"data": {
			"token": "qwqwqwqwqwqwqwqwqwqwqwqwqwqwqwqq"
		}
	}
	```
	
* **/user/check?passcode=[passcode]**
	* GET
	
	| name | require | default | explanation |
	|------|------|-----|----|
	
	* Request

	```
	GET /user/check?passcode=opqjdfoqpwjfwjkfnqw892y3rwejkrhwk
	```
	
	* Response
	
	```
	{
		"status": "success",
		"errno": "",
		"errmsg": "",
		"data": {
			"id": "1",
			"phone": "886123456789",
			"passcode": "opqjdfoqpwjfwjkfnqw892y3rwejkrhwk"
		}
	}
	```

## Ticket

* **/ticket/sign?passcode=[passcode]**
	* POST

	| name | require | default | explanation |
	|------|------|-----|----|
	|place_id|Y|-|
	|date|Y|-|-|
	|people|Y|-|-|

	* Request
	
	```
	POST /ticket/sign?passcode=opqjdfoqpwjfwjkfnqw892y3rwejkrhwk
	```

	* Response

	```
	{
		"status": "success",
		"errno": "",
		"errmsg": "",
		"data": {
			"ticket_id: "1",
			"location": "東門國小",
        	"address": "台北市中正區仁愛路一段2之4號",
			"contact_name": "hsin",
        	"contact_email": "hsin7377",
        	"contact_phone": "0989818737"
        	"date": "2015-02-22",
			"name": "Ted",
			"email" "ted@xxx.xxx.tw",
			"people": "1",
		}
	}
	```

* **/ticket/history?passcode=[passcode]**
	* GET
	* sory by date DESC

	| name | require | default | explanation |
	|------|------|-----|----|
	
	
	* Request

	```
	GET /ticket/history?passcode=opqjdfoqpwjfwjkfnqw892y3rwejkrhwk
	```
	
	* Response
	
	```
	{
	   "status": "success",
	   "errno": "",
	   "errmsg": "",
	   "data": [
	      {
	         "id": "9",
	         "people": "1",
	         "date": "2015-07-13",
	         "status": "1",		// 1: comfirm 2: success 3: fail
	         "name": "jasonni",
	         "email": "jasonni1231@gmail.com",
	         "update_time": "2015-07-11 17:24:15",
	         "create_time": "2015-07-11 17:24:15",
	         "image_filename": "cb60204347baa256dd11cc88362e9429.jpg",
	         "image_timestamp": "1436704056",
	         "place_id": "1",
	         "team_name": "欣動羽球社",
	         "location": "東門國小",
	         "start_time": "19:00:00",
	         "end_time": "21:30:00"
	      },
	      {
	         "id": "8",
	         "people": "1",
	         "date": "2015-07-13",
	         "status": "1",
	         "name": "jasonni",
	         "email": "jasonni1231@gmail.com",
	         "update_time": "2015-07-11 17:17:08",
	         "create_time": "2015-07-11 17:24:15",
	         "image_filename": "cb60204347baa256dd11cc88362e9429.jpg",
	         "image_timestamp": "1436704056",
	         "place_id": "3",
	         "team_name": "欣動羽球社",
	         "location": "東門國小",
	         "start_time": "19:00:00",
	         "end_time": "21:30:00"
	      },
	      {
	         "id": "5",
	         "people": "1",
	         "date": "2015-07-13",
	         "status": "1",
	         "name": "Ting",
	         "email": "showsky@gmail.com",
	         "update_time": "2015-07-11 01:05:00",
	         "create_time": "2015-07-11 17:24:15",
	         "image_filename": "cb60204347baa256dd11cc88362e9429.jpg",
	         "image_timestamp": "1436704056",
	         "place_id": "2",
	         "team_name": "欣動羽球社",
	         "location": "東門國小",
	         "start_time": "19:00:00",
	         "end_time": "21:30:00"
	      }
	   ]
	}
	```

* **/ticket/check?code=[code]
	* GET
	
	| name | require | default | explanation |
	|------|------|-----|----|
	|code|Y|-|-|
	
	* Request
	
	```
	GET /ticket/check?code=JOEkdw
	```
	
	* Response

	```
	{
	   "status": "success",
	   "errno": "",
	   "errmsg": "",
	   "data": {
	      "user_id": "2",
	      "ticket_id": "6",
	      "place_id": "1",
	      "people": "3",
	      "date": "2015-07-13",
	      "name": "Ting",
	      "email": "Ted@gmail.com",
	      "update_time": "2015-07-12 21:25:51",
	      "location": "東門國小",
	      "address": "台北市中正區仁愛路一段2之4號"
	      "sign_people": "3",
	      "team_name": "xxx",
	      "total_people": "13",
	      "contact_name": "Ted",
	      "start_time": "13:00:00",
	      "end_time": "15:00:00",
	      "image_filename": "wwsofjweiofjw.jpg",
	      "image_timestamp": "1947891234789236847"
	   }
	}
	```
* **/ticket/confirm?code=[code]
	* POST
	* the code only bind only once
	
	| name | require | default | explanation |
	|------|------|-----|----|
	|code|Y|-|-|-|
	|ticket_id|Y|-|-|
	|status|Y|-|1: Yest 2: No|
	
	* Request

	```
	POST /ticket/confirm?code=JOEkdw
	```
	
	* Response

	```
	{
		"status": "success",
		"errno": "",
		"errmsg": "",
		"data": {
			"ticket_id': "2"
		}
	}
	```


## Error No

* Basic Error 1xx

	|No|Message|
	|----|----|
	|101|Lack parameter|
	|102|Data empty|
	|103|Illegal account|

* Place Error 2xx

	|No|Message|
	|----|----|
	|201|Not exist place id|
	|202|Illegal parameter|
	|203|Insert place fail|
	|204|Illegal date|
	|205|Date expire|

* Image Error 3xx

	|No|Message|
	|----|----|
	|301|Upload image fail|
	|302|Image exceeds limit|
	|303|Not exist image filename|

* User Error 4xx

	|No|Message|
	|----|----|
	|401|Send SMS code fail|
	|402|Illegal passcode|
	|403|Insert user fail|
	|404|Not exist phone number|
	|405|Illegal parameter|
	|406|Illegal phone number|
	|407|Update token fail|
	|408|SMS send ip exceeds limit|
	|409|SMS send phone exceeds limit|
	|410|Illegal code|
	|411|Insert SMS fail|
	|412|Illegal email address|
	
* Ticket Error 5xx

	|No|Message|
	|----|----|
	|501|Not exist date|
	|502|People exceeds limit|
	|503|Insert ticket fail|
	|504|Illegal code|
	|505|Illegal parameter|
	|506|Fail ticket has closed|
	|507|time expire|

* Other Error 9xx

	|No|Message|
	|----|----|
	|999|Not implement method|

## Author

<p>name: Ting Cheng</p>