# UI API

Display UI on screen such as leaderboard, login/sign up and tokenshop. Please note that … <br>
1. animation duration of modal open and closing is 400ms. This may close a modal that is called during the animation phase. <br>
2. User’s login status can be changed after UI API call. For example, user who is not logged in can login or signup when the modal is open, because some contents are required login/sign up and the UI will prompt the user to login/sign up modal.<br>
3. `.modal-overlay` is the wrapper element of the modal UI, and its `z-index` is 100.

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
<span class="d-type number">Number</span> / Null | poc | `null` if user has not done verification. Otherwise POC balance.


### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurrs.

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

Display login modal

### `onComplete` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when call is success.

`onComplete` returns belows.

Type | Argument | Description
----- | ------- | ------- 
<span class="d-type object">Object</span> | player | Player info. See [PLAYER.GETINFO](#player-getinfo)
<span class="d-type number">Number</span> / Null | poc | `null` if user has not done verification. Otherwise POC balance.


### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurrs.

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
<span class="d-type func">Function</span> | Triggered when error occurrs.

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
<span class="d-type func">Function</span> | Triggered when error occurrs.

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
<span class="d-type func">Function</span> | Triggered when error occurrs.

See [Errors](#errors) menu


## UI.LEADERBOARD

> UI.LEADERBOARD( onLogin, onError )

```javascript
pasdk.UI.LEADERBOARD(function(player, poc){
    // onLogin
    // same as `UI.SIGNIN` or `UI.SIGNUP`'s `onComplete` argument
    console.log('success', player, poc)     //success {...} 87568
}, function (err) {
    //onError
    //ex) User clicked 'X'(close) button
    console.log('err', err)
})
```

`UI.LEADERBOARD( onLogin, onError )`

Display leaderboard modal. Note that there are two types of leaderboards, normal and eSports. These leaderboards have different layout and slightly different functions. User can login or sign up from eSports leaderboard. 

### `onLogin` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when user sign up or login by clicking eSports leaderboard.

`onLogin` returns belows.

Type | Argument | Description
----- | ------- | ------- 
<span class="d-type object">Object</span> | player | Player info. See [PLAYER.GETINFO](#player-getinfo)
<span class="d-type number">Number</span> / Null | poc | `null` if user has not done verification. Otherwise POC balance.

### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurrs.

See [Errors](#errors) menu


## UI.TOGGLELEADERBOARD

> UI.TOGGLELEADERBOARD( show )

```javascript
// Force to show the leaderboard
pasdk.UI.TOGGLELEADERBOARD(true);

// Force to hide the leaderboard
pasdk.UI.TOGGLELEADERBOARD(false);   

// Show the leaderboard if the leaderboard is hidden
// Hide the leaderboard if the leaderboard is shown
pasdk.UI.TOGGLELEADERBOARD();
```

`UI.TOGGLELEADERBOARD( show )`

Show/hide eSports leaderboard. This API works for only eSports leaderboard. So please make sure if the leaderboard type is eSports leaderboard and `UI.LEADERBOARD` is displayed. Note that the data is not refreshed.<br>

### `show` argument
Type | Description
----- | ------- 
<span class="d-type bool">Boolean</span> | `true`, force to show the leaderboard<br>`false`, force to hide the leaderboard
<span class="d-type undefined">undefined</span> | Toggle the leaderboard


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
<span class="d-type func">Function</span> | Triggered when error occurrs.

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
<span class="d-type func">Function</span> | Triggered when error occurrs.

See [Errors](#errors) menu


## UI.SHARE

> UI.SHARE( onComplete, onError )

```javascript

pasdk.UI.SHARE( function(){
    //onComplete; nothing happens here
}, function (err) {
    //onError
    //User clicked 'X'(close) button 
    console.log('err', err)
})
```

`UI.SHARE( onComplete, onError )`

Display a SNS share dialog. Currently, below platforms are supported.

* Whats app
* FB Messenger
* Kakao Talk
* Line
* Pinterest
* Facebook
* Twitter
* VK
* Wechat
* QQ

SDK create share links using below info. So please make sure if these are set up to the `index.html` file.

* url : The game's url
* image : Using `meta[property='og:image']` value
* title : Using `title` tag's value.
* description : Using `meta[property='og:description']` value

### `onComplete` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | This is currently not used.


### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when the modal is closed.


## UI.ESPORTSINFO

> UI.ESPORTSINFO( onError )

```javascript
pasdk.UI.ESPORTSINFO( function(){
    // modal is closed
})
```

`UI.ESPORTSINFO()`

Display eSports information image.


## UI.CLOSE

> UI.CLOSE()

```javascript
pasdk.UI.CLOSE()
```

`UI.CLOSE()`

Close modal that is open currently


## UI.CLEAR

> UI.CLEAR()

```javascript
pasdk.UI.CLEAR()
```

`UI.CLEAR()`

Remove all elements that is created by SDK from DOM.