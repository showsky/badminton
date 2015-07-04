Badminton API Document
===

Last update time: 2015/07/05 #1

* Api base URL: **http://3tr.mooo.com/api**
* Image base URL: **http://3tr.mooo.com/image**
* ***All use of string type***
* Base pattern

	```json
{
   "status": success / fail,
   "errno": error No,
   "errmsg": error Message
}

	```

## Place

* **/place**

	| name | require | default | explanation |
	|------|------|-----|----|
	|lat|Y|-|latitude|
	|long|Y|-|longitude|
	|disance|N|3000|unit: meter
	
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

	| name | require | default | explanation |
	|------|------|-----|----|
	|id|Y|-|must numeric|
	
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

	| name | require | default | explanation |
	|------|------|-----|----|

* **/place/add**

	| name | require | default | explanation |
	|------|------|-----|----|

* **/place/edit**

	| name | require | explanation |
	|------|------|-----|

## User

## Ticket

## Error No

|No|Message|
|----|----|
|201|Not place id|
|202|Illegal parameter|
|203|Lack parameter|
|204|Data null|
|999|Not implement method|