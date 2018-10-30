# Account API

## PLAYER.GETINFO

> PLAYER.GETINFO()

```javascript
pasdk.PLAYER.GETINFO()    //see below
```

> `player` parameter

```json
{
    "country":"Canada",
    "countryCode":"CA",
    "email":"mbiz.spike@emojigames.io",
    "idType":"email",
    "image":"https://pacoin.pocketarena.com/upload/user/image/NrPtCkznLubJ.jpg",
    "isVerified":true,
    "level":5,
    "nickname":"Spike Kang12",
    "rewardExp":{
        "POC":18,
        "exp":87
    }
}
```

`PLAYER.GETINFO()`

Get player’s information such as email, name, and so on.

### Return value
 Type | Description
 ------- | -----------
 `player` Object / Null | `null` if player is not signed in.

### `player` object
Type | Key | Key | Description
--------- | ------- | ------- | -----------
String | country | | Player country
String | countryCode | | Player country code
String | email | | Player email
String | idType | | Determine if it's SNS account or email account
String | image | | Player profile image
Boolean | isVerified | | `true` if user finished phone verification
Number | level | | Player level
String | nickname | | Player nickname
Object | rewardExp | | Player's POC and level exp info
Number | | POC | Player's POC amount
Number | | exp | Player's level exp in percent

### `onError` argument
Type | Description
----- | ------- 
Function | Triggered when error occured.

See [Errors](#errors) menu


## PLAYER.SETINFO

> PLAYER.SETINFO( nickname, countryCode, currentPassword, newPassword, onComplete, onError )

```javascript
pasdk.PLAYER.SETINFO('Brandon Jeong', 'KR', '12341234', '12341234', 
    function(){
    //onComplete
    console.log('success');
}, function (err) {
    //onError
    console.log('err', err);
});
```

`PLAYER.SETINFO(nickname, countryCode, currentPassword, newPassword, onComplete, onError)`

Set player’s information such as email, name, birthday, and gender.

### `nickname` argument
 Type | Description
 ------- | -----------
 String / Null | `null` if player is not signed in.
 
### `countryCode` argument
Type | Description
------- | -----------
String* | Required. User's country code

### `currentPassword` argument
Type | Description
------- | -----------
String | User's current password. At least 8, and up to 50 characters

### `newPassword` argument
Type | Description
------- | -----------
String | New password that user set to change. At least 8, and up to 50 characters

### `onComplete` argument
Type | Description
----- | ------- 
Function | Triggered when call is success.

### `onError` argument
Type | Description
----- | ------- 
Function | Triggered when error occured.

See [Errors](#errors) menu



## PLAYER.GETACTIVITY

> PLAYER.GETACTIVITY( onComplete, onError )

```javascript
pasdk.PLAYER.GETACTIVITY(function(activity){
    //onComplete
    console.log('res', activity)     //see below 'activity' object
}, function(err) {
    //onError
    console.log(err)
});
```

> `activity` object

```json
{
    "draw":7,
    "highscore":36,
    "lastAccess":"2018-10-17T02:50:08-07:00",
    "lose":8,
    "win":39
}
```

`PLAYER.GETACTIVITY(onComplete, onError)`

Get player’s PA activity statistic such as number of wins, lose, and last access time.

### `onComplete` argument
Type | Description
----- | ------- 
Function | Triggered when call is success.



### `onError` argument
Type | Description
----- | ------- 
Function | Triggered when error occured.

See [Errors](#errors) menu



## PLAYER.GETMYPOC

> PLAYER.GETMYPOC( onComplete, onError )

```javascript
pasdk.PLAYER.GETMYPOC(function(poc){
    //onComplete
    console.log('res', poc) //4
}, function(err) {
    //onError
    console.log(err)
});
```

`PLAYER.GETMYPOC(onComplete, onError)`

Get current POC balance

### `onComplete` argument
Type | Description
----- | ------- 
Function | Triggered when call is success.

`onComplete` returns belows.

Type | Argument | Description
--------- | ------- | -----------
Number / null | poc | POC balance user currently has. Returns `null`, if user has not done phone verification.

### `onError` argument
Type | Description
----- | ------- 
Function | Triggered when error occured.

See [Errors](#errors) menu



## PLAYER.GETMESSAGE

> PLAYER.GETMESSAGE( limit, page, onComplete, onError )`

```javascript
pasdk.PLAYER.GETMESSAGE(null, null, function(limit, pagebalance, hasNext){
    //onComplete
    console.log('success', limit, pagebalance, hasNext);
}, function (err) {
    //onError
    console.log('err', err);
});
```

> `notification` object

```json
{
  "notificationno":"1",
  "title":"Notice Title",
  "description":"Notice Description",
  "notificationtype":"1",
  "pocamount":null,
  "registdate":1523976927
}
```

`PLAYER.GETMESSAGE( limit, page, onComplete, onError )`

Get messages for user

### `limit` argument
Type | Description
--------- | -----------
Number / null | Amount of messages in a page. default 10

### `page` argument
Type | Description
--------- | -----------
Number / null | Page number to laod. default 1


### `onComplete` argument
Type | Description
----- | ------- 
Function | Triggered when call is success.

`onComplete` returns belows.

Type | Argument | Description
----- | ------- | ------- 
Number | currentPage | Current page number
Array | list | List of notifications. See `notification` object below.
Boolean | hasNext | `true` there are more pages. `false` there is no more pages.

### `notification` object
Type | Key | Description
--------- | ------- | -----------
String | notificationno | Notification number. Unique.
String | title | Title
String | description | Description
String | notificationtype | Notification type. `1` : system notice, `2` : title
String\Null | pocamount | POC amount
Timestamp | registdate | Registered date


### `onError` argument
Type | Description
----- | ------- 
Function | Triggered when error occured.

See [Errors](#errors) menu



## PLAYER.GETITEM

> PLAYER.GETITEM( onComplete, onError )

```javascript
pasdk.PLAYER.GETITEM(function(list){
    //onComplete
    console.log('success', list);       //see below
}, function (err) {
    //onError
    console.log('err', err);
});
```

> `item` object

```json
{
  "useritemno":"928",
  "title":"Iron Ball",
  "subtitle":"Destroy all kind of bircks",
  "itemimage":"https://ipascf.pocketarena.com/pa/iron-ball.png",
  "price":"100",
  "itemtype":"2",
  "itemstatus":"1",
  "itemlevel":"1",
  "itemexp":"0",
  "marketyn":"1",
  "productid":"bfLGiKLxJdwjwQ"
}
```

`PLAYER.GETITEM(onComplete, onError)`

Get user’s item list

### `onComplete` argument
Type | Description
----- | ------- 
Function | Triggered when call is success.

`onComplete` returns belows.

Type | Argument | Description
----- | ------- | ------- 
Array | list | List of `item` object. See below

### `item` object
Type | Key | Description
--------- | ------- | -----------
String | itemshopno | Item shop number
String | title | Item title
String | subtitle | Item subtitle
String | itemimage | Item image url
String | price | Item price
String | itemtype | `1` : All mode (single and multi play)
        |          | `2` : Single play
        |          | `3` : Multi play
String | itemstatus | `1` : Not yet on market  
        |          | `2` : On market  
String | itemlevel | Item level
String | itemexp | Item experience

### `onError` argument
Type | Description
----- | ------- 
Function | Triggered when error occured.

See [Errors](#errors) menu



## PLAYER.UPDATEITEM

> PLAYER.UPDATEITEM( items, onComplete, onError )

```javascript
//'items' array should contains all 'item' objects from ITEM.GETGAMEITEM
var items = [{
             useritemno:"928",
             title:"Iron Ball",
             subtitle:"Destroy all kind of bircks",
             itemimage:"https://ipascf.pocketarena.com/pa/iron-ball.png",
             price:"100",
             itemtype:"2",
             itemstatus:"1",
             itemlevel:"1",
             itemexp:"0",
             marketyn:"1",
             productid:"bfLGiKLxJdwjwQ"
           }]
           
pasdk.PLAYER.UPDATEITEM( items, function(){
    //onComplete
    console.log('success');
}, function (err) {
    console.log('err', err);
});
```

`PLAYER.UPDATEITEM( items, onComplete, onError )`

Update user’s item list

### `items` argument
Type | Description
----- | ------- 
Array | Array of containing item object.It should include not only items to update, but also the other items those user have. Item object is from [ITEM.GETGAMEITEM](#item-getgameitem)

### `onComplete` argument
Type | Description
----- | ------- 
Function | Triggered when call is success.

### `onError` argument
Type | Description
----- | ------- 
Function | Triggered when error occured.

See [Errors](#errors) menu



## PLAYER.SIGNOUT

`PLAYER.SIGNOUT()`

