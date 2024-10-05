### Account without Mismatch (fixed)
#### Data is the sheet
Customer Email Address (New): Sangior@optonline.net
CUID: 507407775
Redirect Email Address: sangior@outlook.com
CUID: 3723714451
#### Data in DB for CUID 507407775
##### CCDS:
```
{
	"id": 507407775,
	"email": "Sangior@optonline.net",
	"shard": 1,
	"firstName": "Kathleen",
	"identitySubjectId": "84298000",
}
```
##### AuthIdentity:
```
{
	"id": 84298000,
	"lock_type": "None",
	"login": "Sangior@optonline.net",
	"email_address": "Sangior@optonline.net",
}
```
#### Data in DB for CUID customer
##### CCDS:
```
{
	"id": 3723714451,
	"email": "sangior@outlook.com",
	"shard": 1,
	"firstName": null,
	"identitySubjectId": null,
}
```
### Account with Mismatch
#### Data in the sheet
Customer Email Address (New): [mark@oceansgroup.ca](mailto:mark@oceansgroup.ca)
CUID: 5283548402
Redirect Email Address: markamantel@gmail.com
CUID: 6105875357
#### Data in DB for CUID 5283548402
##### CCDS:
```
{
	"id": 5283548402,
	"email": "mark@oceansgroup.ca",
	"shard": 7,
	"firstName": "Mark",
	"creationDate": "2019-12-25 13:51:24.727",
	"updatedDate": "2024-09-27 13:10:59.35",
	"identitySubjectId": "133690145",
}
```
##### AuthIdentity:
```
{
	"id": 133690145,
	"lock_type": "None",
	"login": "markamantel@gmail.com",
	"email_address": "markamantel@gmail.com",
}
```
#### Data in DB for CUID 6105875357
##### CCDS:
```
{
	"id": 6105875357,
	"email": "markamantel@gmail.com",
	"shard": 7,
	"firstName": "Mark",
	"creationDate": "2024-07-10 00:40:39.403",
	"updatedDate": "2024-09-13 14:14:04.947",
	"identitySubjectId": "282392068",
}
```
##### AuthIdentity:
```
{
	"id": 282392068,
	"lock_type": "None",
	"login": "mark@oceansgroup.ca",
	"email_address": "mark@oceansgroup.ca",
}
```
