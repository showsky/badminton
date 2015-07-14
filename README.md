Badminton API Document
===

* Api base URL: **http://[domain name]/api**
* Image base URL: **http://[domain name]/images**
* ***All response JSON format use of string type***
* Base rsponse JSON pattern

	```
{
		"status": [success or fail],
		"errno": [error No],
		"errmsg": [error Message],
		"data": [data]
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
	|order|N|-|distance ASC|
	
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
         "image_filename": "lkfjwljfljlfj.jpg",
         "image_timestamp": "11283812691",
         "disance": "1861"
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
         "image_filename": "lkfjwljfljlfj.jpg",
         "image_timestamp": "11283812691",
         "disance": "1861"
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
         "image_filename": "lkfjwljfljlfj.jpg",
         "image_timestamp": "11283812691",
         "disance": "1861"
      }
   ]
}
	
	```

* **/place/fetch/[id]**
	* GET
	* sing_date range within a month

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
	|team_name|Y|-|-|
	|team_comment|N|-|-|
	|country|Y|-|-|
	|city|Y|-|-|
	|location|Y|-|-|
	|address|Y|-|-|
	|price_boy|Y|-|-|
	|price_girl|Y|-|-|
	|start_date|Y|-|1985-02-22|
	|end_data|Y|-|1985-02-22|
	|week|Y|-|-|
	|start_time|Y|-|22:00:00|
	|end_time|Y|-|19:00:00|
	|degress|Y|-|-|
	|people|Y|-|-|
	|contact_name|Y|-|-|
	|contact_email|Y|-|-|
	|contact_phone|Y|-|-|
	|device_space|Y|-|-|
	|device_floor|Y|0|-|
	|device\_ball\_brand|Y|0|-|
	|device\_ball\_price|Y|0|-|
	|device_light|Y|0|-|
	|device_ac|Y|0|-|
	|device_water|Y|0|-|
	|device_bathroom|Y|0|-|
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
	|name|Y|-|-|
	|email|Y|-|-|

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
	* sory by update_time DESC and status DESC

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
	         "contact_name": "hsin",
	         "contact_email": "hsin7377",
	         "contact_phone": "0989818737"
	      },
	      {
	         "id": "8",
	         "people": "1",
	         "date": "2015-07-13",
	         "status": "1",
	         "name": "jasonni",
	         "email": "jasonni1231@gmail.com",
	         "update_time": "2015-07-11 17:17:08",
	         "contact_name": "hsin",
	         "contact_email": "hsin7377",
	         "contact_phone": "0989818737"
	      },
	      {
	         "id": "5",
	         "people": "1",
	         "date": "2015-07-13",
	         "status": "1",
	         "name": "Ting",
	         "email": "showsky@gmail.com",
	         "update_time": "2015-07-11 01:05:00",
	         "contact_name": "hsin",
	         "contact_email": "hsin7377",
	         "contact_phone": "0989818737"
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
	      "place_id": "1",
	      "people": "3",
	      "date": "2015-07-13",
	      "name": "Ting",
	      "email": "Ted@gmail.com",
	      "update_time": "2015-07-12 21:25:51",
	      "sign_people": "3",
	      "total_people": "13"
	   }
	}
	```
* **/ticket/confirm?code=[code]
	* POST
	* the code only bind only once
	
	| name | require | default | explanation |
	|------|------|-----|----|
	|code|Y|-|-|-|
	|ticket_id|-|-|-|
	|status|-|-|1: Yest 2: No|
	
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

* Place Error 2xx

	|No|Message|
	|----|----|
	|201|Not exist place id|
	|202|Illegal parameter|
	|203|Insert place fail|

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
	
* Ticket Error 5xx

	|No|Message|
	|----|----|
	|501|Not exist date|
	|502|People exceeds limit|
	|503|Insert ticket fail|
	|504|Illegal code|
	|505|Illegal parameter|
	|506|Fail ticket has closed|

* Other Error 9xx

	|No|Message|
	|----|----|
	|999|Not implement method|

## Author

<p>name: Ting Cheng</p>