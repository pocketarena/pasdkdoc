# Common API

## new EmojigaGamesPASDK

> new EmojigaGamesPASDK( options )

```javascript
var options = {
    gameId : 'xxxxx',
    recaptcha : {
        siteKey : 'xxxxxxxx',
        verifyUrl : 'http://.....'
    }
}
var sdk = new EmojiGamesPASDK(options)
```

`new EmojigaGamesPASDK( options )`

Create a PA SDK instance.

### Arguments

Argument | Type | Default | Description
--------- | ------- | ------- | -----------
options | object | API call is success

### `options` argument
Type | Key | Key | Default | Description
----- | -- | --- | ------- | -----------
String | gameId |   | - | Game ID
Object | recaptcha |    | - | ReCaptcha info
String |          | siteKey | - | ReCaptcha site key
String |          | verifyUrl | - | Site URL to verify reCaptcha


## ISREADY

> ISREADY( onComplete, onError )

```javascript
pasdk.ISREADY(function() {
    //onComplete arg
    
}, function(err){
    //error arg
    console.log('error object', err)
})
```

`ISREADY(onComplete, onError)`

SDK is ready to use. All functions of PA SDK should be called after this API is triggered.

### `onComplete` argument
Type | Description
----- | ------- 
Function | Triggered when call is success.

### `onError` argument
Type | Description
----- | ------- 
Function | Triggered when error occured.

See [Errors](#errors) menu

## GETLEADERBOARDTYPE

> GETLEADERBOARDTYPE()

```javascript
var res = pasdk.GETLEADERBOARDTYPE()

console.log('res', res)     // 'res win'
```

`GETLEADERBOARDTYPE()`

Get leaderboard type.

### Return value
 Type | Value | Description
 ------- | ------- | -----------
 String | `win` | Rank is based on number of win
  | `score` | Rank is based on stage clear score or stage number.  


## SIGNIN

> SIGNIN( type, params, onComplete, onError )

> `email` type

```javascript
pasdk.SIGNIN('email', {email : 'mbiz.spike@emojigames.io', password : '12341234'}, 
    function(player, poc){
    //onComplete
    //console.log('player', player)     //see PLAYER.GETINFO
    console.log('poc', poc)             //'poc null' | 'poc 28342'
}, function(err){
    //onError
    console.log('err', err)
})
```

> `sns` type

```javascript
pasdk.SIGNIN('sns', {snsName : 'facebook'}, 
    function(player, poc){
    //onComplete
    //console.log('player', player)     //see PLAYER.GETINFO
    console.log('poc', poc)             //'poc null' | 'poc 28342'
}, function(err){
    //onError
    console.log('err', err)
})
```

`SIGNIN( type, params, onComplete, onError )`

User sign in

### `type` argument
 Sign in type
 
 Type | Value | Description
 ------- | ------- | -----------
 String | `email` | for email sign in
        | `sns` | for SNS account sign in (Google, Facebook)
  
### `params` argument
Parameters to send to server. Key varies depending on the `type` argument.

#### For `email` type
Key | Type | Description
--------- | ------- | -----------
email | String | email address
password | String | password. up to 8 characters

#### For `sns` type
Key | Type | Value | Description
--------- | ------- | ------- | ----
snsName | String | `facebook` | 
         |       | `google` | 

### `onComplete` argument
Type | Description
----- | ------- 
Function | Triggered when call is success.

Argument | Type | Description
--------- | ------- | -----------
player | object | Player data. See [PLAYER.GETINFO](#player-getinfo)
poc | number/null | POC balance, `null` if user didn’t do phone verification


### `onError` argument
Type | Description
----- | ------- 
Function | Triggered when error occured.

See [Errors](#errors) menu



## SIGNUP

> SIGNUP( type, params, onComplete, onError )

> `email` type

```javascript
pasdk.SIGNUP('email', {email : 'mbiz.spike@emojigames.io', password : '12341234'}, 
    function(player, poc){
    //onComplete
    //console.log('player', player)     //see PLAYER.GETINFO
    console.log('poc', poc)             //'poc null' | 'poc 28342'
}, function(err){
    //onError
    console.log('err', err)
})
```

> `sns` type

```javascript
pasdk.SIGNUP('sns', {snsName : 'facebook'}, 
    function(player, poc){
    //onComplete
    //console.log('player', player)     //see PLAYER.GETINFO
    console.log('poc', poc)             //'poc null' | 'poc 28342'
}, function(err){
    //onError
    console.log('err', err)
})
```

`SIGNUP(type, params, onComplete, onError)`

User sign up.

### `type` argument
 Sign up type
 
 Type | Value | Description
 ------- | ------- | -----------
 String | `email` | for email sign in
        | `sns` | for SNS account sign in (Google, Facebook)
  
### `params` argument
Parameters to send to server. Key varies depending on the `type` argument.

#### For `email` type
Key | Type | Description
--------- | ------- | -----------
email | String | email address
password | String | password. up to 8 characters

#### For `sns` type
Key | Type | Value | Description
--------- | ------- | ------- | ----
snsName | String | `facebook` | 
         |       | `google` | 
         
### `onComplete` argument
Type | Description
----- | ------- 
Function | Triggered when call is success.

Argument | Type | Description
--------- | ------- | -----------
player | object | Player data. See [PLAYER.GETINFO](#player-getinfo)
poc | number/null | POC balance, `null` if user didn’t do phone verification

### `onError` argument
Type | Description
----- | ------- 
Function | Triggered when error occured.

See [Errors](#errors) menu



## RESETPASSWORD

> RESETPASSWORD( email, onComplete, onError )

```javascript
pasdk.RESETPASSWORD ( 'mbiz.spike@emojigames.io', 
    function(){
    //onComplete
}, function(err){
    //onError
    console.log('err', err)
})
```

`RESETPASSWORD( email, onComplete, onError )`

Send an email to reset password.

### `email` argument
Type | Description
----- | ------- 
String | User's email address 

### `onComplete` argument
Type | Description
----- | ------- 
Function | Triggered when call is success.

### `onError` argument
Type | Description
----- | ------- 
Function | Triggered when error occured.

See [Errors](#errors) menu



## POCPURCHASE

> POCPURCHASE( gameShopNo, onComplete, onError )

```javascript
pasdk.POCPURCHASE(2, 
    function(){
    //onComplete
}, function(err){
    //onError
    console.log(err) 
});
```

`POCPURCHASE( gameShopNo, onComplete, onError )`

Request exchange POC for items or game currency such as Ruby. The item can be various depending on game.

### `gameShopNo` argument
Type | Description
----- | ------- 
Number | The `shopNo` value received from [GETSHOPINFO](#getshopinfo) 

### `onComplete` argument
Type | Description
----- | ------- 
Function | Triggered when call is success.

### `onError` argument
Type | Description
----- | ------- 
Function | Triggered when error occured.

See [Errors](#errors) menu



## GETSHOPINFO

> GETSHOPINFO( onComplete, onError )

```javascript
pasdk.GETSHOPINFO(function(returncode, poc, gameshop){
    //onComplete
    console.log('success', returncode, poc, gameshop);   //success 200, 4, see below about gameshop array
}, function(err){ 
    //onError
    console.log(err) 
});
```

> `gameshop` object list

```json
[{
    "shopno":"2",
    "title":"item 1",
    "itemimage":"https://ipascf.pocketarena.com/pa/ruby01.png",
    "itemamount":"1000",
    "pocamount":"10"
},{
    "shopno":"3",
    "title":"item 2",
    "itemimage":"https://ipascf.pocketarena.com/pa/ruby02.png",
    "itemamount":"5500",
    "pocamount":"50"
}]
```

`GETSHOPINFO( onComplete, onError )`

Get info that exchanges POC for items or game currency such as Ruby. The item can be various depending on game.

### `onComplete` argument
Type | Description
----- | ------- 
Function | Triggered when call is success.

`onComplete` returns belows.

Type | Argument | Description
----- | ------- | ------- 
Number | returncode | 
Number | poc | User's POC balance
Array | gameshop | `gameshop` list. See below

#### `gameshop` object
Type | Key | Description
--------- | ------- | -----------
String | shopno | Shop unique id
String | title | Shop name
String | itemimage | Shop iamge
String | itemamount | Amount to buy
String | pocamount | Required POC to buy 

### `onError` argument
Type | Description
----- | ------- 
Function | Triggered when error occured.

See [Errors](#errors) menu



## GETREWARDEXP

> GETREWARDEXP( onComplete, onError )

```javascript
pasdk.GETREWARDEXP(function(exp, poc){

    //onComplete
    console.log(exp, poc) //87 18
    
    }, function(err){

    //onEror
    console.log('err', err) 
});
```

`GETREWARDEXP(onComplete, onError)`

Get user’s POC reward exp and amount to get when the exp reaches 100.

### `onComplete` argument
Type | Description
----- | ------- 
Function | Triggered when call is success.

`onComplete` returns belows.

Type | Argument | Description
----- | ------- | ------- 
Number | exp | User's level experiece. in percent
Number | poc | POC that user will gain when current exp reaches next level. (ex : x18). /n Returns `null`, If user has not done phone verification.

Type | Description
----- | ------- 
Function | Triggered when error occured.


### `onError` argument
Type | Description
----- | ------- 
Function | Triggered when error occured.

See [Errors](#errors) menu



## GETREWARDPOC

> GETREWARDPOC( params, onComplete, onError )

```javascript
pasdk.GETREWARDPOC({token: 'xxxxxx'}, 
    function(poc){
        //onComplete
        console.log(poc)    //17
    }, function(err){
        //onError
        console.log('err', err) 
    });
```

`GETREWARDPOC(params, onComplete, onError)`

Get POC reward after a game when the POC exp reaches 100. 
Please note that this API must be called when [`GAME.REPORTSCORE`](#game-reportscore) returns `rewardPoc`. 
Also, Google reCaptcha verification is required. For that, you need a server API to verify the token. 
SDK will use reCaptcha info given at constructor API to verify server side. 
Developers need to implement how to get verified token, unless using UI.REWARD. 
For more information about reCaptcha please refer to [its official documentation] 
(https://developers.google.com/recaptcha/intro).
Instead of this API, you can use [`UI.REWARD`](#ui-reward), it will take care of this process.


### `params` argument
Type | Description
----- | ------- 
Object | Object for parameters to send to server verifying Google reCaptcha a verified token. `token` key is required. Also, additional parameters can be added. It depends on the server API’s need.

Type | Key | Description
----- | ------- | ------- 
String | token | Google reCaptcha verified token


### `onComplete` argument
Type | Description
----- | ------- 
Function | Triggered when call is success.

`onComplete` returns belows.

Type | Argument | Description
----- | ------- | ------- 
Number | poc | POC balance user is going to get when exp reaches 100

### `onError` argument
Type | Description
----- | ------- 
Function | Triggered when error occured.

See [Errors](#errors) menu



## OPENLINK

> OPENLINK( pageName )

> `wallet`

```javascript
//redirect to PA Wallet website
pasdk.OPENLINK('wallet')

```

> `emojigames`

```javascript
//redirect to Emojigames website
pasdk.OPENLINK('emojigames')

```

`OPENLINK(pageName)`

Open PA Wallet or EmojiGames website page.

### `pageName` argument
Type | Value | Description
----- | ------ | ------- 
String | `wallet` | Redirect to PA Wallet website in new tab.
     | `emojigames` | Redirect to EmojiGames website in new tab.


