---
title: PA SDK Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript

toc_footers:

includes:
  - common
  - account
  - game
  - item
  - ui
  - errors

search: true
---

# Introduction

Welcome to Pocket Arena SDK documentation. 

# How to use

> 1 Insert script in the head tag of your game.

```html
<head>
    <script src="jquery-2.1.1.min.js"></script> <!-- jquery required-->
    <script type="text/javascript" src="EmojiGamesPASDK.min.js"></script>
</head>
```

> 2 Create a new instance of SDK

```javascript
var pasdk = new EmojiGamesPASDK({
    gameId : 'xxxxxx'    //game id
});
```

> 3 After below `onComplete` function is triggered, you can just call any API.

```javascript
pasdk.ISREADY(function(){ 
        //onComplete
        console.log('sdk is ready. Now SDK API is available.') 
    }, function(err){ 
        //onError
        console.log(err, 'error occurred during initializing.') 
    });
```

1. Insert script in the head tag of your game.
2. Create a new instance of SDK
3. After `onComplete` function of `ISREADY` is triggered, you can just call any SDK API.


<aside class="notice">
Most of API will work ONLY after onComplete function of ISREADY() API is triggered.
</aside>
