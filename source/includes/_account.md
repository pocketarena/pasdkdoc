# Account API

## PLAYER.GETINFO

> PLAYER.GETINFO()

```javascript
pasdk.PLAYER.GETINFO()    //see below
```

> `player` object : for player signed in

```json
{
    "country":"Switzerland",
    "countryCode":"CH",
    "email":"me@emojigames.io",
    "idType":"email",
    "image":"https://pacoin.pocketarena.com/upload/player/image/NrPtCkznLubJ.jpg",
    "isVerified":true,
    "level":5,
    "nickname":"Spike Kang",
    "rewardExp":{
        "POC":18,
        "exp":87
    }
}
```

> `player` object : for player who is not signed in

```json
{
    "rewardExp" : 87,
    "countryCode" : "CH",
    "country" : "Switzerland",
    "isAnonymous": true
}
```

`PLAYER.GETINFO()`

Get player’s information such as email, name, and so on. `isAnonymous` is returned only for player who is not signed in.


### Return value
 Type | Description
 ------- | -----------
 <span class="d-type object">Object</span> | if player is not signed in. `isAnonymous` is returned for non-signed player only.

### `player` object : for player signed in
Type | Key | Key | Description
--------- | ------- | ------- | -----------
<span class="d-type string">String</span> | country | | Player country
<span class="d-type string">String</span> | countryCode | | Player country code
<span class="d-type string">String</span> | email | | Player email
<span class="d-type string">String</span> | idType | | Determine if it's SNS account or email account<br> `email` or `sns`
<span class="d-type string">String</span> | image | | Player profile image
<span class="d-type bool">Boolean</span> | isVerified | | `true` if player finished phone/email verification
<span class="d-type number">Number</span> | level | | Player level
<span class="d-type string">String</span> | nickname | | Player nickname
<span class="d-type object">Object</span> | rewardExp | | Player's POC and level exp info
<span class="d-type number">Number</span> | | POC | Player's POC amount
<span class="d-type number">Number</span> | | exp | Player's level exp in percent

### `player` object : for player who is not signed in
Type | Key | Description
--------- | ------- | -----------
<span class="d-type number">Number</span> | rewardExp | Player's level exp info
<span class="d-type bool">Boolean</span> | isAnonymous | `true` always, since this key is for non-signed player
<span class="d-type string">String</span> | country | Ex) Player's country. ex) `Switzerland`.
<span class="d-type string">String</span> | countryCode | Ex) Player's country code. ex) `CH`.

### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

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
 <span class="d-type string">String</span> / Null | `null` if player is not signed in.
 
### `countryCode` argument
Type | Description
------- | -----------
<span class="d-type string">String</span>* | Required. Player's country code

### `currentPassword` argument
Type | Description
------- | -----------
<span class="d-type string">String</span> | Player's current password. At least 8, and up to 50 characters

### `newPassword` argument
Type | Description
------- | -----------
<span class="d-type string">String</span> | New password that player set to change. At least 8, and up to 50 characters

### `onComplete` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when call is success.

### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

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
<span class="d-type func">Function</span> | Triggered when call is success.



### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

See [Errors](#errors) menu



## PLAYER.GETMYPOC

> PLAYER.GETMYPOC( onComplete, onError )

```javascript
pasdk.PLAYER.GETMYPOC(function(balance){
    //onComplete
    console.log('res', balance) //4
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
<span class="d-type func">Function</span> | Triggered when call is success.

`onComplete` returns belows.

Type | Argument | Description
--------- | ------- | -----------
<span class="d-type number">Number</span> / null | balance | POC balance player currently has. Returns `null`, if player has not done phone verification.

### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

See [Errors](#errors) menu


## PLAYER.COUNTNEWMESSAGES

> PLAYER.COUNTNEWMESSAGES( onComplete, onError )

```javascript
pasdk.PLAYER.COUNTNEWMESSAGES(function(amount){
    //onComplete
    console.log('res', amount); //4
}, function(err) {
    //onError
    console.log(err);
});
```

`PLAYER.COUNTNEWMESSAGES(onComplete, onError)`

Check if user has new messages or not. It returns amount of new(unread) messages.

### `onComplete` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when call is success.

`onComplete` returns belows.

Type | Argument | Description
--------- | ------- | -----------
<span class="d-type number">Number</span> | amount | Total number of new/unread messages. 0, if none.

### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

See [Errors](#errors) menu


## PLAYER.GETMESSAGE

> PLAYER.GETMESSAGE( limit, page, onComplete, onError )`

```javascript
pasdk.PLAYER.GETMESSAGE(null, null, function(list, hasNext){
    //onComplete
    console.log('success', list, hasNext);  // success (see below for list), true
}, function (err) {
    //onError
    console.log('err', err);
});
```

> `notification` object

```json
{
  "notificationno":"1",
  "notificationtype":"1",
  "title":"Notice Title",
  "description":"Notice Description",
  "pocamount":null,
  "isread":false,
  "registdate":1523976927
}
```

> `messages` object

```json
{
  "messageboxno":"1",
  "messageboxtype":"1",
  "winnertype":"2",
  "title":"Message Title",
  "description":"Message Description",
  "isread":false,
  "registdate":1523976927
}
```

> `prizes` object

```json
{
  "prizeno":"1",
  "prizetype":"1",
  "title":"Prize Title",
  "description":"Prize Description",
  "isread":false,
  "registdate":1523976927,
  "expiredate":1523976927
}
```

`PLAYER.GETMESSAGE( limit, page, onComplete, onError )`

Get player's messages

### `limit` argument
Type | Description
--------- | -----------
<span class="d-type number">Number</span> / null | Amount of messages to display in a page. default 10

### `page` argument
Type | Description
--------- | -----------
<span class="d-type number">Number</span> / null | Page number to load. default 1


### `onComplete` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when call is success.

`onComplete` returns belows.

Type | Argument | Description
----- | ------- | ------- 
<span class="d-type object">Object</span> | list | List of messages. See `list` object below.
<span class="d-type bool">Boolean</span> | hasNext | `true` there are more pages. `false` there is no more pages.

### `list` object
Type | Key | Description
--------- | ------- | -----------
<span class="d-type array">Array</span> | notices | List of notice object
<span class="d-type array">Array</span> | messages | List of message object
<span class="d-type array">Array</span> | prizes | List of prize object


### `notification` object
Type | Key | Description
--------- | ------- | -----------
<span class="d-type string">String</span> | notificationno | Notification number. Unique.
<span class="d-type string">String</span> | notificationtype | Notification type. `1` : system notice, `2` : reward via eSports
<span class="d-type string">String</span> | title | Title
<span class="d-type string">String</span> | description | Description
<span class="d-type string">String</span>\Null | pocamount | POC amount
<span class="d-type Bool">Boolean</span> | isread | Status whether the message is read or not. `true` if it's read, otherwise `false`
Timestamp | registdate | Registered date

### `messages` object
Type | Key | Description
--------- | ------- | -----------
<span class="d-type string">String</span> | messageboxno | Message number. Unique.
<span class="d-type string">String</span> | messageboxtype | Message type. `1` : system notice, `2` : reward via eSports
<span class="d-type string">String</span> | winnertype | Winner type. `1` : Team winner, `2` : Final winner eSports<br>This is for eSports games.
<span class="d-type string">String</span> | title | Title
<span class="d-type string">String</span> | description | Description
<span class="d-type Bool">Boolean</span> | isread | Status whether the message is read or not. `true` if it's read, otherwise `false`
Timestamp | registdate | Registered date

### `prizes` object
Type | Key | Description
--------- | ------- | -----------
<span class="d-type string">String</span> | prizeno | Prize number. Unique.
<span class="d-type string">String</span> | prizetype | Prize type. `1` : system notice, `2` : reward via eSports
<span class="d-type string">String</span> | title | Title
<span class="d-type string">String</span> | description | Description
<span class="d-type Bool">Boolean</span> | isread | Status whether the message is read or not. `true` if it's read, otherwise `false`
Timestamp | registdate | Registered date
Timestamp | expiredate | Expire date


### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

See [Errors](#errors) menu


## PLAYER.UPDATEMESSAGE

> PLAYER.UPDATEMESSAGE( action, mode, messageNo, options, onComplete, onError )

```javascript
pasdk.PLAYER.UPDATEMESSAGE('read', 'msg', 1, {}, function(){
    //onComplete
    console.log('success');
}, function(err) {
    //onError
    console.log(err);
});
```

`PLAYER.UPDATEMESSAGE( action, mode, messageNo, options, onComplete, onError )`

Check if user has new messages or not. It returns amount of new(unread) messages.

### `action` argument
Type | Description
----- | ------- 
<span class="d-type string">String</span> | `read` to set a message as read. <br> `delete` to delete a message.

### `mode` argument
Type | Description
----- | ------- 
<span class="d-type string">String</span> | `noti` for notification <br>`msg` for message <br>`prize` for prize

### `messageNo` argument
Type | Description
----- | ------- 
<span class="d-type number">Number</span> | Notification, message, or prize unique number. 

### `options` argument
Type | Description
----- | ------- 
<span class="d-type object">Object</span> | Not used yet. 

### `onComplete` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when call is success.

### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

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

Get player’s item list

### `onComplete` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when call is success.

`onComplete` returns belows.

Type | Argument | Description
----- | ------- | ------- 
<span class="d-type array">Array</span> | list | List of `item` object. See below

### `item` object
Type | Key | Description
--------- | ------- | -----------
<span class="d-type string">String</span> | itemshopno | Item shop number
<span class="d-type string">String</span> | title | Item title
<span class="d-type string">String</span> | subtitle | Item subtitle
<span class="d-type string">String</span> | itemimage | Item image url
<span class="d-type string">String</span> | price | Item price
<span class="d-type string">String</span> | itemtype | `1` : All mode (single and multi play)
        |          | `2` : Single play
        |          | `3` : Multi play
<span class="d-type string">String</span> | itemstatus | `1` : Not yet on market  
        |          | `2` : On market  
<span class="d-type string">String</span> | itemlevel | Item level
<span class="d-type string">String</span> | itemexp | Item experience

### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

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

Update player’s item list

### `items` argument
Type | Description
----- | ------- 
<span class="d-type array">Array</span> | Array of containing item object.It should include not only items to update, but also the other items those player have. Item object is from [ITEM.GETGAMEITEM](#item-getgameitem)

### `onComplete` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when call is success.

### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

See [Errors](#errors) menu


## PLAYER.SENDVERIFICATIONEMAIL

> PLAYER.SENDVERIFICATIONEMAIL( onComplete, onError )

```javascript
pasdk.PLAYER.SENDVERIFICATIONEMAIL( function(){
    //onComplete
    console.log('success');
}, function (err) {
    console.log('err', err);
});
```

`PLAYER.SENDVERIFICATIONEMAIL( onComplete, onError )`

Send an email that contains verification link. This API is only for players who registered before Oct. 2018 and have not verified.


### `onComplete` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when call is success.

### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

See [Errors](#errors) menu


## PLAYER.SIGNOUT

> PLAYER.SIGNOUT( onComplete, onError )

```javascript
pasdk.PLAYER.SIGNOUT( function( onComplete, onError ){
    //onComplete
    console.log('success');
}, function (err) {
    console.log('err', err);
});
```

`PLAYER.SIGNOUT( onComplete, onError )`

Remove user’s session data

