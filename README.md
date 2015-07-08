Badminton API Document
===

* Api base URL: **http://[domain name]/api**
* Image base URL: **http://[domain name]/image**
* ***All use of string type***
* Base pattern

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

	| name | require | default | explanation |
	|------|------|-----|----|
	|token|N|-|-|
	|lat|Y|-|latitude|
	|long|Y|-|longitude|
	|disance|N|3000|unit: meter|
	
	* Request

	```
	GET /place?lat=-1212.123123&long=123.5675675
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
         "update_time": "0000-00-00 00:00:00",
         "latitude": "0.0",
         "longitude": "0.0",
         "disance": "1861"
      },
      {
         "id": "2",
         "team_name": "采翼羽球隊",
         "city": "台北",
         "location": "興雅國小",
         "address": "台北市基隆路一段83巷",
         "update_time": "0000-00-00 00:00:00",
         "latitude": "0.0",
         "longitude": "0.0",
         "disance": "2960"
      },
      {
         "id": "3",
         "team_name": "超勝羽球隊-大安",
         "city": "台北",
         "location": "銘傳國小四樓羽球場",
         "address": "台北市大安區羅斯福路四段21號",
         "update_time": "0000-00-00 00:00:00",
         "latitude": "0.0",
         "longitude": "0.0",
         "disance": "1614"
      }
   ]
}
	
	```

* **/place/info/[id]**
	* GET

	| name | require | default | explanation |
	|------|------|-----|----|
	|token|N|-|-|
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
      "start_date": "0007-01-15",
      "end_date": "0007-01-16",
      "week": "1",
      "start_time": "19:00:00",
      "end_time": "21:30:00",
      "degree": "1,3",
      "people": "13",
      "contact_name": "hsin",
      "contact_email": "hsin7377",
      "contact_phone": "0989818737",
      "device_space": "1",
      "device_floor": "1",
      "device_ball_brand": "10",
      "device_ball_price": "2",
      "device_light": "0",
      "device_ac": "0",
      "device_water": "0",
      "device_bathroom": "0",
      "update_time": "0000-00-00 00:00:00",
      "latitude": "0.0",
      "longitude": "0.0",
      "disance": "1399",
      "image": [
         "/demo1.jpg?1436032389",
         "/demo2.jpg?1436032389",
         "/demo3.jpg?1436032389"
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
	* image max limit 3, and must JPG type
	* file upload key name must image1, image2, image3
	
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
	|long|Y|-|-|
	
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

* **/image/delete/[filename]**
	* GET

	| name | require | default | explanation |
	|------|------|-----|----|
	|filename|Y|-|-|
	
	* Request

	```
	GET /image/delete/qwkldfjoqwjflqwjlf.jpg
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
	* Response token string length = 40

	| name | require | default | explanation |
	|------|------|-----|----|
	|code|Y|-|-|
	|platform|Y|-|1:Android 2:iOS|
	|token|Y|-|-|

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
			"token": "opqjdfoqpwjfwjkfnqw892y3rwejkrhwk",
		}
	}
	```
	
* **/user/check?token=[token]**
	* GET
	
	| name | require | default | explanation |
	|------|------|-----|----|
	
	* Request

	```
	GET /user/check?token=opqjdfoqpwjfwjkfnqw892y3rwejkrhwk
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
			"token": "opqjdfoqpwjfwjkfnqw892y3rwejkrhwk"
		}
	}
	```

## Ticket

* **/ticket/sign?token=[token]**
	* POST

	| name | require | default | explanation |
	|------|------|-----|----|
	|place_id|Y|-|
	|date|Y|-|-|
	|count|Y|-|-|
	|name|Y|-|-|
	|token|Y|-|-|

	* Request
	
	```
	POST /ticket/sign?token=opqjdfoqpwjfwjkfnqw892y3rwejkrhwk
	```

	* Response

	```
	{
		"status": "success",
		"errno": "",
		"errmsg": "",
		"data": {
			"place_id: "1",
			"name": "Ted",
			"count": "1",
			"datetime": "2015-02-22"
		}
	}
	```
	
* **/ticket/history?token=[token]**
	* GET

	| name | require | default | explanation |
	|------|------|-----|----|
	
	* Request

	```
	GET /ticket/history?token=opqjdfoqpwjfwjkfnqw892y3rwejkrhwk
	```
	
	* Response
	
	```
	{
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
	|402|Illegal code|
	|403|Insert user fail|
	|404|Not exist phone number|
	|405|Illegal parameter|
	|406|Illegal phone number|
	|407|Illegal token|
	
* Ticket Error 5xx

	|No|Message|
	|----|----|

* Other Error 9xx

	|No|Message|
	|----|----|
	|999|Not implement method|

## Author

<p>name: Ting Cheng</p>