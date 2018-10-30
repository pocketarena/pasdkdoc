# Game API

## GAME.START

> GAME.START( onComplete, onError )

```javascript
pasdk.GAME.START(function(){
    //onComplete
    console.log('success')
}, function (err) {
    //onError
    console.log('err', err)
})
```

`GAME.START( onComplete, onError )`

Call when a game start. This API must be called for every single play.

### `onComplete` argument
Type | Description
----- | ------- 
Function | Triggered when call is success.

### `onError` argument
Type | Description
----- | ------- 
Function | Triggered when error occured.

See [Errors](#errors) menu


## GAME.REPORTSCORE

> GAME.REPORTSCORE( score, type, code, onComplete, onError )

```javascript
var score = 22,
    type = 0,    //single play
    code = 1;   //win
    
pasdk.GAME.REPORTSCORE(score, type, code, function(rewardpoc){
    //onComplete
    console.log('rewardpoc', rewardpoc) //rewardpoc null | 14
}, function(err){
    //onError
    console.log('err', err)
})
```

`GAME.REPORTSCORE(score, type, code, onComplete, onError)`

Call when a game has finished to record the score to leaderboard

### `score` argument
Type | Description
----- | ------- 
Number | Score to send

### `type` argument
Type | Value | Description
----- | ------- | ------- 
Number | `0` | Single play
     | `1` | Multi play

### `code` argument
Type | Value | Description
----- | ------- | ------- 
Number | `0` | Single
     | `1` | Win
     | `2` | Lose
     | `3` | Draw

### `onComplete` argument
Type | Description
----- | ------- 
Function | Triggered when call is success.

`onComplete` returns belows.

Type | Argument | Description
----- | ------- | ------- 
Number / Null | rewardPOC | Amount of POC as a reward. If this argument’s value is not `null`, either you can use [`UI.REWARD`](#ui-reward) API or build your own UI using [`GETREWARDPOC`](#getrewardpoc)   

### `onError` argument
Type | Description
----- | ------- 
Function | Triggered when error occured.

See [Errors](#errors) menu


## GAME.SETSAVEDATA

> GAME.SETSAVEDATA( data1, data2, data3, data4, data5, onComplete, onError )

```javascript
var data1 = '980;',
    data2 = '295;263;||263;262;',
    data3 = '',
    data4 = '4000',
    data5 = '3;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;'

pasdk.GAME.SETSAVEDATA(data1, data2, data3, data4, data5, function(){
    //onComplete
    console.log('success')
}, function(err){
    //onError
    console.log('err', err)
})
```

`GAME.SETSAVEDATA( data1, data2, data3, data4, data5, onComplete, onError )`

Set user game data

<aside class="notice">
Each `data(n)` can store up to 13,000 characters, if the character takes 1 byte of space.
</aside>

### `data1` ~ `data5` arguments
Type | Argument | Description
----- | ------- | ------- 
String / Null | data1 | Any data. Send `null` if there is nothing to save.
String / Null | data2 | Any data. Send `null` if there is nothing to save.
String / Null | data3 | Any data. Send `null` if there is nothing to save.
String / Null | data4 | Any data. Send `null` if there is nothing to save.
String / Null | data5 | Any data. Send `null` if there is nothing to save.

### `onComplete` argument
Type | Description
----- | ------- 
Function | Triggered when call is success.

### `onError` argument
Type | Description
----- | ------- 
Function | Triggered when error occured.

See [Errors](#errors) menu


## GAME.GETSAVEDATA

> GAME.GETSAVEDATA( onComplete, onError )

```javascript
pasdk.GAME.GETSAVEDATA(function(data1, data2, data3, data4, data5){
    //onComplete
    console.log('data', data1, data2, data3, data4, data5)  //data '980;' '' '295;263;||263;262;' '4000' '3;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;0;'
}, function(err){
    //onError
    console.log('err', err)
})
```

`GAME.GETSAVEDATA(onComplete, onError)`

Get user game data

### `onComplete` argument
Type | Description
----- | ------- 
Function | Triggered when call is success.

`onComplete` returns belows.

Type | Argument | Description
----- | ------- | ------- 
String | data1 | Any data. When it's empty, Empty string(`''`) will be returned.
String | data2 | Any data. When it's empty, Empty string(`''`) will be returned.
String | data3 | Any data. When it's empty, Empty string(`''`) will be returned.
String | data4 | Any data. When it's empty, Empty string(`''`) will be returned.
String | data5 | Any data. When it's empty, Empty string(`''`) will be returned.


### `onError` argument
Type | Description
----- | ------- 
Function | Triggered when error occured.

See [Errors](#errors) menu


## GAME.LEADERBOARD

> GAME.LEADERBOARD( refresh, onComplete, onError )

```javascript
var refresh = true;

pasdk.GAME.LEADERBOARD(refresh, function(leaderboard){
    //onComplete
    console.log('leaderboard', leaderboard)     //see below 'leaderboard' object
}, function(err){
    //onError
    console.log('err', err) 
});
```
> Value of `leaderboard`

```json
{  
   "eventtile":"",
   "startdate":1533254400,
   "enddate":1564790400,
   "myscore":"3",
   "myranking":"12",
   "leadertype":"0",
   "totalcount":21,
   "leader":{  
      "rowcount":21,
      "leaderdata":[  
         //see below 'entry' object
      ]
   }
}
```

> `entry` object

```json
[{  
    "ranking":"12",
    "isme":"1",
    "locale":"EN",
    "picture":"NrPtCkznLubJ.jpg",
    "nickname":"Spike Kang12",
    "gamescore":"3"
 }, {  
    "ranking":"14",
    "isme":"0",
    "locale":"VN",
    "picture":"",
    "nickname":"simon",
    "gamescore":"1"
}]
```

`GAME.LEADERBOARD(refresh, onComplete, onError)`

Get leaderboard data. Ordered by rank ascending

### `refresh` argument
Type | Description
----- | ------- 
Boolean | `true`, get leaderboard data from server.
        | `false`, get leaderboard data from SDK local data.

### `onComplete` argument
Type | Description
----- | ------- 
Function | Triggered when call is success.

`onComplete` returns belows.

#### `leaderboard` argument
Type | Key | Key | Description
----- | ------- | --- | ------- 
 String | myranking | | User's rank
 Object | leader | | Leaderboard data
 Number |       | rowcount  | Total number of entries
 Array |       | leaderdata  | Leaderboard list data. See `entry` object below
 String | type | | Leaderboard type. `0` : Win, `1` : Score
 Number | totalcount | | Total number of entries
                      
#### `entry` object
Type | Key | Description
--------- | ------- | -----------
String | ranking | Entry user's ranking
String | nickname | Entry user's nickname
String | gamescore | Entry user's gamescore
String | isme | `0` : Not user, `1` : User
String | locale | Entry user's locale
String | picture | Entry user's profile image. `''` for user who doesn't have profile image


### `onError` argument
Type | Description
----- | ------- 
Function | Triggered when error occured.

See [Errors](#errors) menu


