# Common API

## new EmojigaGamesPASDK

> new EmojigaGamesPASDK( options )

```javascript
var options = {
    gameId : 'xxxxx',
    useLeaderboard : false
}
var sdk = new EmojiGamesPASDK(options)
```

`new EmojigaGamesPASDK( options )`

Create a PA SDK instance.

### Arguments

Argument | Type | Default | Description
--------- | ------- | ------- | -----------
options | <span class="d-type object">Object</span> | - | API call is success

### `options` argument
Type | Key | Default | Description
----- | -- | ------- | -----------
<span class="d-type string">String</span> | gameId <span class="req">*</span> | - | Game ID. You can get this id when you register your game.
<span class="d-type bool">Boolean</span> | useLeaderboard | false | This option works only for the game that leaderboard is set to use. You can set leaderboard when you register your game.<br> `true` Use leaderboard.<br> `false` Not use.

### Return
Type | Description
----- | -----------
<span class="d-type">EmojiGamesPASDK</span> | SDK instance 

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
<span class="d-type func">Function</span> | Triggered when call is success.

### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

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
 <span class="d-type string">String</span> | `win` | Rank is based on number of win
  | `score` | Rank is based on stage clear score or stage number.  


## SIGNIN

> SIGNIN( type, params, onComplete, onError )

> `email` type

```javascript
pasdk.SIGNIN('email', {email : 'me@emojigames.io', password : '#12345678'}, 
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

> `phone` type

```javascript
pasdk.SIGNIN('phone', {number : '1112223333', countryCode : '82', password: '#12345678'}, 
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

User sign in. You can either make your own UI or use [UI.SIGNIN](#ui-signin) API.

### `type` argument
 Sign in type
 
 Type | Value | Description
 ------- | ------- | -----------
 <span class="d-type string">String</span> | `email` | For email sign in
        | `sns` | For SNS account sign in (Google, Facebook)
        | `phone` | For phone number sign in
  
### `params` argument
Parameters to send to server. Key varies depending on the `type` argument.

#### For `email` type
Type | Key | Description
--------- | ------- | -----------
<span class="d-type string">String</span> | email | Email address
<span class="d-type string">String</span> | password | Password. Up to 8 characters

#### For `sns` type
Type | Key | Value | Description
--------- | ------- | ------- | ----
<span class="d-type string">String</span> | snsName | `facebook` | 
         |       | `google` | 


#### For `phone` type
Type | Key | Description
--------- | ------- | -----------
<span class="d-type string">String</span> | number | Phone number
<span class="d-type string">String</span> | countryCode | Phone number country code. <br>ex) `1` for US/Canada, `41` for Switzerland
<span class="d-type string">String</span> | password | Password. Up to 8 characters

### `onComplete` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when call is success. It returns below arguments.

Type | Argument | Description
--------- | ------- | -----------
<span class="d-type object">Object</span> | player | Player data. See [PLAYER.GETINFO](#player-getinfo)
<span class="d-type number">Number</span>/null | poc | POC balance


### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

See [Errors](#errors) menu



## SIGNUP

> SIGNUP( type, params, onComplete, onError )

> `email` type

```javascript
pasdk.SIGNUP('email', {email : 'me@emojigames.io', password : '12341234', nickname: 'My Nickname', vcode: '1234'}, 
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

> `phone` type

```javascript
pasdk.SIGNUP('phone', {number : '1112223333', countryCode : '82', password: '@1231234', nickname: 'My Nickname', vcode: '1234'}, 
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

User sign up. You can either make your own UI or use [UI.SIGNUP](#ui-signup) API.

### `type` argument
 Sign up type
 
 Type | Value | Description
 ------- | ------- | -----------
 <span class="d-type string">String</span> | `email` | For email sign in
        | `sns` | For SNS account sign in (Google, Facebook)
        | `phone` | For phone number sign in
  
### `params` argument
Parameters to send to server. Key varies depending on the `type` argument.

#### For `email` type
Type | Key | Description
--------- | ------- | -----------
<span class="d-type string">String</span> | email | Email address
<span class="d-type string">String</span> | password | Password. Up to 8 characters
<span class="d-type string">String</span> | nickname | Player's nickname
<span class="d-type string">String</span> | vcode | Verification code. The code can be received via [SENDVERIFICATIONCODE](#sendverificationcode) API. The API will send an email that contains the code.

#### For `sns` type
Type | Key | Value | Description
--------- | ------- | ------- | ----
<span class="d-type string">String</span> | snsName | `facebook` | 
         |       | `google` | 

#### For `phone` type
Type | Key | Description
--------- | ------- | -----------
<span class="d-type string">String</span> | number | Email address
<span class="d-type string">String</span> | countryCode | Phone number country code. ex) `1` for US/Canada, `41` for Switzerland
<span class="d-type string">String</span> | password | Password. Up to 8 characters
<span class="d-type string">String</span> | nickname | Player's nickname
<span class="d-type string">String</span> | vcode | Verification code.  The code can be received via [SENDVERIFICATIONCODE](#sendverificationcode) API. The API will send a sms that contains the code.

### `onComplete` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when call is success.

Type | Argument | Description
--------- | ------- | -----------
<span class="d-type object">Object</span> | player | Player data. See [PLAYER.GETINFO](#player-getinfo)
<span class="d-type number">Number</span> | poc | POC balance

### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

See [Errors](#errors) menu



## RESETPASSWORD

> RESETPASSWORD( email, onComplete, onError )

```javascript
pasdk.RESETPASSWORD ( 'me@emojigames.io', 
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
<span class="d-type string">String</span> | User's email address 

### `onComplete` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when call is success.

### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

See [Errors](#errors) menu



## SENDVERIFICATIONCODE

> SENDVERIFICATIONCODE( method, id, phoneCountryCode, onComplete, onError )

> `email` method

```javascript
pasdk.SENDVERIFICATIONCODE ( 'email', 'me@emojigames.io', null, 
    function(){
    //onComplete
}, function(err){
    //onError
    console.log('err', err)
})
```

> `sms` method

```javascript
pasdk.SENDVERIFICATIONCODE ( 'sms', '123456789', '41', 
    function(){
    //onComplete
}, function(err){
    //onError
    console.log('err', err)
})
```


`SENDVERIFICATIONCODE( method, id, phoneCountryCode, onComplete, onError )`

Send an email or sms to verify a new account.

### `method` argument
Type | Description
----- | ------- 
<span class="d-type string">String</span> | Type to register an account. `email` or `sms`

### `id` argument
Type | Description
----- | ------- 
<span class="d-type string">String</span> | User ID to verify

#### For `email` method

| Description
|-----------
|Email address

#### For `sms` method
|Description
|-----------
|Phone number 

### `phoneCountryCode` argument
Type | Description
----- | ------- 
<span class="d-type string">String</span> | ex : `41` for switzerland, `1` for US/Canada

#### For `email` method

| Description
|-----------
| null or undefined

#### For `sms` method
|Description
|-----------
| phone country code

### `onComplete` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when call is success.

### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

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
<span class="d-type number">Number</span> | The `shopNo` value received from [GETSHOPINFO](#getshopinfo) 

### `onComplete` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when call is success.

### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

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
<span class="d-type func">Function</span> | Triggered when call is success.

`onComplete` returns belows.

Type | Argument | Description
----- | ------- | ------- 
<span class="d-type number">Number</span> | returncode | 200 : User verified.<br> 401 : User needs to verify the account
<span class="d-type number">Number</span> | poc | User's POC balance
<span class="d-type array">Array</span> | gameshop | `gameshop` list. See below

#### `gameshop` object
Type | Key | Description
--------- | ------- | -----------
<span class="d-type string">String</span> | shopno | Shop unique id
<span class="d-type string">String</span> | title | Shop name
<span class="d-type string">String</span> | itemimage | Shop iamge
<span class="d-type string">String</span> | itemamount | Amount to buy
<span class="d-type string">String</span> | pocamount | Required POC to buy 

### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

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
<span class="d-type func">Function</span> | Triggered when call is success.

`onComplete` returns belows.

Type | Argument | Description
----- | ------- | ------- 
<span class="d-type number">Number</span> | exp | User's level experiece. in percent
<span class="d-type number">Number</span> | poc | Amount of POC that user will gain when current exp reaches next level. (ex : x18). /n Returns `null`, If user has not done phone verification.


### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

See [Errors](#errors) menu



## GETREWARDPOC

> GETREWARDPOC( params, onComplete, onError )

```javascript
// When 'GAME.REPORTSCORE' is called...  
pasdk.GAME.REPORTSCORE(10, 0, 1, function(rewardpoc){
    
    //if 'rewardpoc' is returned
    if (rewardpoc) {
        
        //give POC as a reward to the user
        pasdk.GETREWARDPOC(null, function(poc){
                //onComplete
                console.log(poc)    //17
            }, function(err){
                //onError
                console.log('err', err) 
            });
        
    }else {
        
        // do something necessary ...
        
    }
    
}, function(err) {
    //onError
    console.log('err', err) 
})
```

`GETREWARDPOC(params, onComplete, onError)`

Get POC reward after a game when the POC exp reaches 100. 
Please note that this API must be called when [`GAME.REPORTSCORE`](#game-reportscore) returns `rewardPoc`.  
Instead, you can use [`UI.REWARD`](#ui-reward), it will take care of this process.


### `params` argument
Type | Description
----- | ------- 
<span class="d-type object">Object</span> / Null | Optional settings

Type | Key | Default | Description
----- | ------- | ------ | ------- 
<span class="d-type string">String</span> | mode | `reward` | `reward` or `check`


### `onComplete` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when call is success.

`onComplete` returns belows.

Type | Argument | Description
----- | ------- | ------- 
<span class="d-type number">Number</span> | poc | POC balance user is going to get when exp reaches 100

### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

See [Errors](#errors) menu



## OPENLINK

> OPENLINK( siteName, pageName )

> `wallet`

```javascript
//redirect to PA Wallet website
pasdk.OPENLINK('wallet')

```

> `emojigames`

```javascript
//redirect to Emojigames website
pasdk.OPENLINK('emojigames');

//redirect to Emojigames website's eSports result history page
pasdk.OPENLINK('emojigames', 'esportsHistory');

//redirect to Emojigames website's eSports leaderboard page
pasdk.OPENLINK('emojigames', 'esportsLeaderboard');

```

`OPENLINK(siteName, pageName)`

Open PA Wallet or EmojiGames website page.

### `siteName` argument
Type | Value | Description
----- | ------ | ------- 
<span class="d-type string">String</span> | `wallet` | Redirect to PA Wallet website in new tab.
     | `emojigames` | Redirect to EmojiGames website in new tab.
     

### `pageName` argument for `emojigames`
Type | Value | Description
----- | ------ | ------- 
<span class="d-type string">String</span> | `esportsHistory` | Redirect to eSports result history page of Emoji Games website in new tab.
                                        | `esportsLeaderboard` | Redirect to eSports leaderboard page of Emoji Games website in new tab.

