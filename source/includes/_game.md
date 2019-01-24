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
<span class="d-type func">Function</span> | Triggered when call is success.

### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

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

Call when a game has finished to record the score to leaderboard. User’s sign in status can change after API call.

### `score` argument
Type | Description
----- | ------- 
<span class="d-type number">Number</span> | Score to send

### `type` argument
Type | Value | Description
----- | ------- | ------- 
<span class="d-type number">Number</span> | `0` | Single play
     | `1` | Multi play

### `code` argument
Type | Value | Description
----- | ------- | ------- 
<span class="d-type number">Number</span> | `0` | Single
     | `1` | Win
     | `2` | Lose
     | `3` | Draw

### `onComplete` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when call is success.

`onComplete` returns belows.

Type | Argument | Description
----- | ------- | ------- 
<span class="d-type number">Number</span> / Null | rewardPOC | Amount of POC as a reward. If this argument’s value is not `null`, either you can use [`UI.REWARD`](#ui-reward) API or build your own UI using [`GETREWARDPOC`](#getrewardpoc)   

### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

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
<span class="d-type string">String</span> / Null | data1 | Any data. Send `null` if there is nothing to save.
<span class="d-type string">String</span> / Null | data2 | Any data. Send `null` if there is nothing to save.
<span class="d-type string">String</span> / Null | data3 | Any data. Send `null` if there is nothing to save.
<span class="d-type string">String</span> / Null | data4 | Any data. Send `null` if there is nothing to save.
<span class="d-type string">String</span> / Null | data5 | Any data. Send `null` if there is nothing to save.

### `onComplete` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when call is success.

### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

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
<span class="d-type func">Function</span> | Triggered when call is success.

`onComplete` returns belows.

Type | Argument | Description
----- | ------- | ------- 
<span class="d-type string">String</span> | data1 | Any data. When it's empty, Empty string(`''`) will be returned.
<span class="d-type string">String</span> | data2 | Any data. When it's empty, Empty string(`''`) will be returned.
<span class="d-type string">String</span> | data3 | Any data. When it's empty, Empty string(`''`) will be returned.
<span class="d-type string">String</span> | data4 | Any data. When it's empty, Empty string(`''`) will be returned.
<span class="d-type string">String</span> | data5 | Any data. When it's empty, Empty string(`''`) will be returned.


### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

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
> Value of `leaderboard` for <b>normal</b> mode

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
> Value of `leaderboard` for <b>eSports</b> mode

```json
{  
   "eventtile":"",
   "startdate":1533254400,
   "enddate":1564790400,
   "gameid":"yVvIYCpw",
   "gameesportsno":"25",
   "gametitle":"Cricket Championship for MicroMax",
   "durationno": 2,
   "remaintime": 234550,
   "bgimage": "https:\/\/..com\/upload\/game\/pic\/1.png",
   "stageno": "20",
   "myleaderno": 24,
   "groupno": 1,
   "leadercount": 2,
   "leader":{
      "leaderdata":[  
         //see below 'entry' object
      ]
   },
   "rewards": [{
           "reward_en": {
               "title_1": "Final 10 users : $60   50 POC",
               "title_2": "TOP 3 of each Group :50 POC ",
               "description": "Final 10 users will be selected …...."
           },
           "reward_de": {
               "title_1": "Final 10 users : $60   50 POC",
               "title_2": "TOP 3 of each Group :50 POC ",
               "description": "Final 10 users will be selected …...."
   
           },
           "reward_zh": {
               "title_1": "Final 10 users : $60   50 POC",
               "title_2": "TOP 3 of each Group :50 POC ",
               "description": "Final 10 users will be selected …...."
   
           },
           "reward_ko": {
               "title_1": "Final 10 users : $60   50 POC",
               "title_2": "TOP 3 of each Group :50 POC ",
               "description": "Final 10 users will be selected …...."
           }
       }]
}
```

> `entry` object. Values are the same in both mode.

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
<span class="d-type bool">Boolean</span> | `true`, get leaderboard data from server.
        | `false`, get leaderboard data from SDK local data.

### `onComplete` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when call is success.

`onComplete` returns belows. There are two ways the value returned.<br> Normal mode and eSports mode

#### `leaderboard` argument

1. normal mode

Type | Key | Key | Description
----- | ------- | --- | ------- 
 <span class="d-type string">String</span> | myranking | | User's rank
 <span class="d-type object">Object</span> | leader | | Leaderboard data
 <span class="d-type number">Number</span> |       | rowcount  | Total number of entries
 <span class="d-type array">Array</span> |       | leaderdata  | Leaderboard list data. See `entry` object below
 <span class="d-type string">String</span> | type | | Leaderboard type. `0` : Win, `1` : Score
 <span class="d-type number">Number</span> | totalcount | | Total number of entries
 
2. eSports mode

Type | Key | Key | Description
----- | ------- | --- | ------- 
 <span class="d-type string">String</span> | eventtitle | | Its value will be returned if event exists. Otherwise, empty string("") 
 <span class="d-type string">String</span> | gameid | | Game id of current game
 <span class="d-type string">String</span> | gameesportsno | | Game id of current game
 <span class="d-type string">String</span> | gametitle | | Title of current eSports game
 <span class="d-type number">Number</span> | durationno | | 
 <span class="d-type number">Number</span> | remaintime | | Remaining time of this duration. in seconds.
 <span class="d-type string">String</span> | bgimage | | Background image to decorate current game's status. Developers can use their own image. 
 <span class="d-type string">String</span> | stageno | | Stage number for this duration.
 <span class="d-type number">Number</span> | myleaderno | | Number of my leaderboard.
 <span class="d-type number">Number</span> | groupno | | Group number of my leaderboard.
 <span class="d-type number">Number</span> | leadercount | | Total number of leaderboard entries.
 <span class="d-type object">Object</span> | leader | | This one has below properties. 
 <span class="d-type number">Number</span> |       | rowcount  | Total number of leaderboard entries.
 <span class="d-type array">Array</span> |       | leaderdata  | Leaderboard list data. See `entry` object below
 <span class="d-type array">Array</span> | rewards | | list of `reward` object. See below `reward` object.
 
#### `reward` object
 
 Type | Key | Key | Description
 ----- | ------- | --- | ------- 
 <span class="d-type object">Object</span> | reward_(language code, ex) `en`) | | This one has below properties. 
 <span class="d-type string">String</span> | | title_1 | Title
 <span class="d-type string">String</span> | | title_2 | Title 
 <span class="d-type string">String</span> | | description | Description 
 

#### `entry` object

Both normal and eSports mode are the same. 

Type | Key | Description
--------- | ------- | -----------
<span class="d-type string">String</span> | ranking | Entry user's ranking
<span class="d-type string">String</span> | nickname | Entry user's nickname
<span class="d-type string">String</span> | gamescore | Entry user's gamescore
<span class="d-type string">String</span> | isme | `0` : Not user, `1` : User
<span class="d-type string">String</span> | locale | Entry user's locale
<span class="d-type string">String</span> | picture | Entry user's profile image. `''` for user who doesn't have profile image


### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

See [Errors](#errors) menu


