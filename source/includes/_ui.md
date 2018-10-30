# UI API

Display UI such as leaderboard, sign in/up so on on screen

## UI.SIGNUP

> UI.SIGNUP( onComplete, onError )

```javascript
pasdk.UI.SIGNUP(function(player, poc){
    //onComplete
    console.log('success', player, poc)     //success {...} 87568
}, function (err) {
    //onError
    //ex) User clicked 'X'(close) button
    console.log('err', err)
})
```

`UI.SIGNUP( onComplete, onError )`

Display sign up modal

### `onComplete` argument
Type | Description
----- | ------- 
Function | Triggered when call is success.

`onComplete` returns belows.

Type | Argument | Description
----- | ------- | ------- 
Object | player | Player info. See [PLAYER.GETINFO](#player-getinfo)
Number / Null | poc | `null` if user has not done phone verification. Otherwise POC balance.


### `onError` argument
Type | Description
----- | ------- 
Function | Triggered when error occured.

See [Errors](#errors) menu



## UI.SIGNIN

> UI.SIGNIN( onComplete, onError )

```javascript
pasdk.UI.SIGNIN(function(player, poc){
    //onComplete
    console.log('success', player, poc)     //success {...} 87568
}, function (err) {
    //onError
    //ex) User clicked 'X'(close) button
    console.log('err', err)
})
```

`UI.SIGNIN( onComplete, onError )`

Display sign in modal

### `onComplete` argument
Type | Description
----- | ------- 
Function | Triggered when call is success.

`onComplete` returns belows.

Type | Argument | Description
----- | ------- | ------- 
Object | player | Player info. See [PLAYER.GETINFO](#player-getinfo)
Number / Null | poc | `null` if user has not done phone verification. Otherwise POC balance.


### `onError` argument
Type | Description
----- | ------- 
Function | Triggered when error occured.

See [Errors](#errors) menu



## UI.MYPROFILE

> UI.MYPROFILE( onSignOut, onError )

```javascript
pasdk.UI.MYPROFILE(function(){
    //onSignout
    console.log('success')
}, function (err) {
    //onError
    //ex) User clicked 'X'(close) button
    console.log('err', err)
})
```

`UI.MYPROFILE( onSignOut, onError )`

Display my profile modal

### `onSignOut` argument
Type | Description
----- | ------- 
Function | Triggered when user clicks `sign out` button.


### `onError` argument
Type | Description
----- | ------- 
Function | Triggered when error occured.

See [Errors](#errors) menu




## UI.EDITPROFILE

> UI.EDITPROFILE( onComplete, onError )

```javascript
pasdk.UI.EDITPROFILE(function(){
    //onComplete
    console.log('success')
}, function (err) {
    //onError
    //ex) User clicked 'X'(close) button
    console.log('err', err)
})
```

`UI.EDITPROFILE( onComplete, onError )`

Display my profile edit form modal

### `onComplete` argument
Type | Description
----- | ------- 
Function | Triggered when call is success.


### `onError` argument
Type | Description
----- | ------- 
Function | Triggered when error occured.

See [Errors](#errors) menu




## UI.MESSAGEBOX

> UI.MESSAGEBOX( onError )

```javascript
pasdk.UI.MESSAGEBOX(function (err) {
    //onError
    //ex) User clicked 'X'(close) button
    console.log('err', err)
})
```

`UI.MESSAGEBOX( onError )`

Display my message box modal

### `onError` argument
Type | Description
----- | ------- 
Function | Triggered when error occured.

See [Errors](#errors) menu




## UI.REWARD

> UI.REWARD( POCamount, onComplete, onError )

```javascript
var pocAmount = 18;

pasdk.UI.REWARD( pocAmount, function(){
    //onComplete
    console.log('success')
}, function (err) {
    //onError
    //ex) User clicked 'X'(close) button
    console.log('err', err)
})
```

`UI.REWARD( POCamount, onComplete, onError )`

Display POC reward modal. This API is for `onComplete` argument of [`GAME.REPORTSCORE`](#game-reportscore)

### `POCamount` argument
Type | Description
----- | ------- 
Number | POC amount to receive. This value is from `onComplete` argument of [`GAME.REPORTSCORE`](#game-reportscore)

### `onComplete` argument
Type | Description
----- | ------- 
Function | Triggered when call is success.

`onComplete` returns belows.

Type | Argument | Description
----- | ------- | ------- 
Number | POCamount | Reward POC after reCaptcha verification


### `onError` argument
Type | Description
----- | ------- 
Function | Triggered when error occured.

See [Errors](#errors) menu




## UI.LEADERBOARD

> UI.LEADERBOARD( onError )

```javascript
pasdk.UI.LEADERBOARD(function (err) {
    //onError
    //ex) User clicked 'X'(close) button
    console.log('err', err)
})
```

`UI.LEADERBOARD( onError )`

Display leaderboard modal

### `onError` argument
Type | Description
----- | ------- 
Function | Triggered when error occured.

See [Errors](#errors) menu




## UI.PATOKENSHOP

> UI.PATOKENSHOP( onClose, onError )

```javascript
pasdk.UI.PATOKENSHOP( function(POC, purchasedItem){
    //onClose
    //User clicked 'X'(close) button after purchase
    console.log('success', POC, purchasedItem)      //success 19 3
}, function (err) {
    //onError
    //ex) User clicked 'X'(close) button without purchase
    console.log('err', err)
})
```

`UI.PATOKENSHOP(onClose, onError)`

Display token shop modal. When purchase is made, SDK will calculate and return POC balance and the total amount of item to `onClose` argument.

### `onClose` argument
Type | Description
----- | ------- 
Function | Triggered when user click ‘x’(close) button **after purchasing item(s)**.

`onClose` returns belows.

Type | Argument | Description
----- | ------- | ------- 
String | POC | POC balance after purchase
Number | purchsedItem | Amount of items purchased in the modal


### `onError` argument
Type | Description
----- | ------- 
Function | Triggered when error occured.

See [Errors](#errors) menu




## UI.MESSAGE

> UI.MESSAGE( message, onComplete, onError )

```javascript
var message = {title : 'Hi there', 
        message: 'Welcome to Pocket Arena!<br>Want to join?',
        buttons: [
            { text : "Sure" },
            { text : "No, thanks" }     //up to two buttons
             ]};

pasdk.UI.MESSAGE( message, function(idx){
    //onComplete
    if ( idx == 0 ) {
        console.log('\'Sure\' button clicked ')
    }else if ( idx == 1 ) {
        console.log('\'No, thanks\' button clicked ')
    }
    
}, function (err) {
    //onError
    //ex) User clicked 'X'(close) button 
    console.log('err', err)
})
```

`UI.MESSAGE( message, onComplete, onError )`

Display a dialog that contains messages.

### `message` argument
Type | Description
----- | ------- 
object | Setting for message dialog

Type | Key | Description
----- | ------- | ------- 
String | title | Modal title
String | message | Modal message
Array | buttons | Text for buttons. Up to two buttons. Contains `button` object

#### `button` object
Type | Key | Description
----- | ------- | ------- 
String | text | Button text


### `onComplete` argument
Type | Description
----- | ------- 
Function | Triggered when user click `OK` button.


### `onError` argument
Type | Description
----- | ------- 
Function | Triggered when error occured.

See [Errors](#errors) menu




## UI.CLOSE

> UI.CLOSE()

```javascript
pasdk.UI.CLOSE()
```

`UI.CLOSE()`

Close modal that is open currently

