# UI API

Display UI on screen such as leaderboard, sign in/up and tokenshop. Please note that … <br>
1. animation duration of modal open and closing is 400ms. This may close a modal that is called during the animation phase. <br>
2. User’s sign in status can be changed after UI API call. For example, non signed in user can sign in/up when the modal is open, because some contents are required sign in/up and the UI will prompt the user to sign in/up modal.<br>

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
<span class="d-type func">Function</span> | Triggered when call is success.

`onComplete` returns belows.

Type | Argument | Description
----- | ------- | ------- 
<span class="d-type object">Object</span> | player | Player info. See [PLAYER.GETINFO](#player-getinfo)
<span class="d-type number">Number</span> / Null | poc | `null` if user has not done phone verification. Otherwise POC balance.


### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

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
<span class="d-type func">Function</span> | Triggered when call is success.

`onComplete` returns belows.

Type | Argument | Description
----- | ------- | ------- 
<span class="d-type object">Object</span> | player | Player info. See [PLAYER.GETINFO](#player-getinfo)
<span class="d-type number">Number</span> / Null | poc | `null` if user has not done phone verification. Otherwise POC balance.


### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

See [Errors](#errors) menu


## UI.MYPROFILE

> UI.MYPROFILE( onComplete, onError )

```javascript
pasdk.UI.MYPROFILE(function(isSignedIn){
    //onSignout
    console.log('success')
}, function (err) {
    //onError
    //ex) User clicked 'X'(close) button
    console.log('err', err)
})
```

`UI.MYPROFILE( onComplete, onError )`

Display my profile modal. Please note that user can sign out and change profile info while using this UI. 

### `onComplete` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when user clicks `sign out` button, and edit profile and closes it.<br>It returns below argument.

#### `isSignedIn` argument
Type | Description
----- | ------- 
<span class="d-type bool">Boolean</span> | `true` if user kept the session. Otherwise, `false` 

### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

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
<span class="d-type func">Function</span> | Triggered when call is success.


### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

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
<span class="d-type func">Function</span> | Triggered when error occurs.

See [Errors](#errors) menu




## UI.REWARD

> UI.REWARD( POCamount, onComplete, onError )

```javascript
var pocAmount = 18;

pasdk.UI.REWARD( POCamount, function(POCamount, POCbalance, itemAmount){
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
<span class="d-type number">Number</span> | POC amount to receive. This value is from `onComplete` argument of [`GAME.REPORTSCORE`](#game-reportscore)

### `onComplete` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when call is success.

`onComplete` returns belows.

Type | Argument | Description
----- | ------- | ------- 
<span class="d-type number">Number</span> | POCamount | Rewarded POC
<span class="d-type number">Number</span> / Null | POCbalance | Number is returned, when user purchased something from POC Shop. Otherwise, null. The balance doesn’t include POCamount.
<span class="d-type number">Number</span> / Null | itemAmount | Number is returned, when user purchased something from POC Shop. Otherwise, null. Item that user purchased by POC.


### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

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
<span class="d-type func">Function</span> | Triggered when error occurs.

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
<span class="d-type func">Function</span> | Triggered when user click ‘x’(close) button **after purchasing item(s)**.

`onClose` returns belows.

Type | Argument | Description
----- | ------- | ------- 
<span class="d-type string">String</span> | POC | POC balance after purchase
<span class="d-type number">Number</span> | purchsedItem | Amount of items purchased in the modal


### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

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
<span class="d-type string">String</span> | title | Modal title
<span class="d-type string">String</span> | message | Modal message
<span class="d-type array">Array</span> | buttons | Text for buttons. Up to two buttons. Contains `button` object

#### `button` object
Type | Key | Description
----- | ------- | ------- 
<span class="d-type string">String</span> | text | Button text


### `onComplete` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when user click `OK` button.


### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

See [Errors](#errors) menu




## UI.CLOSE

> UI.CLOSE()

```javascript
pasdk.UI.CLOSE()
```

`UI.CLOSE()`

Close modal that is open currently

