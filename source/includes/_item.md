# Item API

## ITEM.GETGAMEITEM

> ITEM.GETGAMEITEM( onComplete, onError )

```javascript
pasdk.ITEM.GETGAMEITEM(function(list){
    //onComplete
    console.log('list', list);   //see below
}, function (err) {
    //onError
    console.log('err', err);
});
```

> `item` object

```json
[{  
    "itemshopno":"1",
    "title":"Super Ball",
    "subtitle":"Destroy all kind of bircks",
    "itemimage":"https://ipascf.pocketarena.com/pa/superball.png",
    "price":"150",
    "itemtype":"2",
    "marketyn":"1",
    "productid":"OZUUEFKKjGHu"
}]
```

`ITEM.GETGAMEITEM( onComplete, onError )`

Get items that game offers to users

### `onComplete` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when call is success.

`onComplete` returns belows.

#### `list` argument
Type | Description
----- | ------- 
<span class="d-type array">Array</span> | List of `item` object

#### `item` object
Type | Argument | Description
----- | ------- | ------- 
<span class="d-type string">String</span> | itemshopno | Item shop number
<span class="d-type string">String</span> | title | Item title
<span class="d-type string">String</span> | subtitle | Item subtitle
<span class="d-type string">String</span> | itemimage | Item image url
<span class="d-type string">String</span> | price | Item price
<span class="d-type string">String</span> | itemtype | `1` : All mode
     |          | `2` : single play
     |          | `3` : multi play
<span class="d-type string">String</span> | marketyn | `1` : Using item in blockchain
     |          | `2` : Not using item in blockchain
<span class="d-type string">String</span> | productid | Product ID from EmojiGames itemshop. Empty string(`''`) when `marketyn` is `0`


### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

See [Errors](#errors) menu



## ITEM.CHECKDEFAULTITEMS

> ITEM.CHECKDEFAULTITEMS( onComplete, onError )

```javascript
pasdk.ITEM.CHECKDEFAULTITEMS(function(list){
    //onComplete
    console.log('list', list)       //see below
}, function(err){
    //onError
    console.log('err', err)
})
```

> `item` object

```json
[{  
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
}]
```

`ITEM.CHECKDEFAULTITEMS( onComplete, onError )`

Check if user is given default items. It not, it will be given.

### `onComplete` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when call is success.

`onComplete` returns belows.

Type | Argument | Description
----- | ------- | ------- 
<span class="d-type array">Array</span> | list | List of `item` object. Same from [`PLAYER.GETITEM`](#player-getitem)


### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

See [Errors](#errors) menu



## ITEM.PURCHASE

> ITEM.PURCHASE( items, onComplete, onError )

```javascript
//list of 'item' object
var items = [{
    itemshopno:"1",
    title:"Super Ball",
    subtitle:"Destroy all kind of bircks",
    itemimage:"https://ipascf.pocketarena.com/pa/superball.png",
    price:"150",
    itemtype:"2",
    marketyn:"1",
    productid:"OZUUEFKKjGHu"
}];

pasdk.ITEM.PURCHASE(items, function(){
	//onComplete
    console.log('success');
}, function (err) {
	//onError
    console.log('err', err);
});
```

`ITEM.PURCHASE( items, onComplete, onError )`

Call when user purchases an item from [ITEM.GETGAMEITEM](#item-getgameitem) API

### `items` argument
Type | Description
----- | ------- 
<span class="d-type array">Array</span> | List of `item` object to send to server. Same item from [ITEM.GETGAMEITEM](#item-getgameitem) API

### `onComplete` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when call is success.

### `onError` argument
Type | Description
----- | ------- 
<span class="d-type func">Function</span> | Triggered when error occurs.

See [Errors](#errors) menu

