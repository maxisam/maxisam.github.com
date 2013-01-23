---
layout: post
title: "Run Foodme in windows"
date: 2013-01-23 10:12
comments: true
categories: AngularJS AngularJS_LearningResource
---

Lately I finially have some time to check the awesome example, [FoodMe][0], created by AngularJS team.

First of all, I am not a node.js user. So when I try to run foodme, it took me some time.

And this [doc][1] doesn't really help on this. They probably never image someone doesn't know this. lol

This tutorial is for people like me, a node.js newbie,

Doesn't know what to do with this kinda message:

{% codeblock %}
module.js:340
    throw err;
          ^
Error: Cannot find module 'express'
    at Function.Module._resolveFilename (module.js:338:15)
    at Function.Module._load (module.js:280:25)
    at Module.require (module.js:362:17)
    at require (module.js:378:17)
    at Object.<anonymous> (H:\Work\MyProject\foodme\server\index.js:1:77)
    at Module._compile (module.js:449:26)
    at Object.Module._extensions..js (module.js:467:10)
    at Module.load (module.js:356:32)
    at Function.Module._load (module.js:312:12)
    at Module.require (module.js:362:17)
{% endcodeblock %}


To run Foodme on Windows, you need to do the following step.

1. Install [node.js][2]

--The following steps are running in command line.--

2. Input `npm install -g express`

This step will install [express][3]

3. Input `npm install -g open`

This step will install [open][4]

4. Go to  Your Path\foodme\server\

5. Input `npm link express`

6. Input `npm link open`

7. Input `node start.js`

If you see the following message, you are good to go !

{% codeblock %}
GET / 200 4ms - 1.58kb
GET /css/app.css 200 6ms - 2.02kb
GET /js/app.js 200 6ms - 650
GET /lib/angular/angular-resource.js 200 8ms - 15.93kb
GET /js/controllers/CustomerController.js 200 8ms - 401
GET /css/bootstrap-united.css 200 13ms - 126.41kb
GET /js/controllers/NavbarController.js 200 8ms - 207
GET /js/controllers/RestaurantsController.js 200 8ms - 295
GET /js/services/customer.js 200 7ms - 476
GET /js/services/localStorage.js 200 6ms - 72
GET /js/services/Restaurant.js 200 5ms - 134
GET /lib/angular/angular.js 200 19ms - 479.29kb
GET /css/Ubuntu.font 200 1ms - 148
GET /views/restaurants.html 200 8ms - 3.11kb
GET /favicon.ico 200 2ms - 1.12kb
GET /robots.txt 404 1ms
GET /api/restaurant 200 3ms - 14.71kb
GET /robots.txt 404 1ms
GET /views/customer.html 200 4ms - 1.18kb
GET /img/restaurants/tofuparadise.jpg 200 6ms - 15.89kb
GET /img/restaurants/robatayaki.jpg 200 8ms - 12.82kb
GET /img/restaurants/khartoum.jpg 200 8ms - 17.16kb
GET /img/restaurants/bateaurouge.jpg 200 11ms - 15.08kb
GET /img/restaurants/sallys.jpg 200 9ms - 17.59kb
GET /img/restaurants/saucy.jpg 200 9ms - 14.33kb
GET /img/restaurants/speisewagen.jpg 200 7ms - 15.26kb
GET /img/restaurants/czechpoint.jpg 200 9ms - 10.95kb
GET /img/restaurants/beijing.jpg 200 7ms - 17.54kb
GET /img/restaurants/satay.jpg 200 9ms - 14.89kb
GET /img/restaurants/cancun.jpg 200 10ms - 15.07kb
GET /img/restaurants/curryup.jpg 200 8ms - 18.66kb
GET /img/restaurants/carthage.jpg 200 9ms - 10.24kb
GET /img/restaurants/burgerama.jpg 200 9ms - 11.76kb
GET /img/restaurants/littleprague.jpg 200 5ms - 13.13kb
GET /img/restaurants/dragon.jpg 200 5ms - 16.72kb
GET /img/restaurants/kohlhaus.jpg 200 7ms - 13.66kb
GET /img/restaurants/babythai.jpg 200 6ms - 17.35kb
GET /img/restaurants/wholetamale.jpg 200 8ms - 14.32kb
GET /img/restaurants/taqueria.jpg 200 6ms - 11.74kb
GET /img/restaurants/pedros.jpg 200 7ms - 12.42kb
GET /img/restaurants/bhangra.jpg 200 10ms - 14.03kb
GET /img/restaurants/superwonton.jpg 200 8ms - 16.15kb
GET /img/restaurants/sakura.jpg 200 7ms - 11.27kb
GET /img/restaurants/naansequitur.jpg 200 8ms - 16.77kb
GET /img/restaurants/shandong.jpg 200 8ms - 14.4kb
GET /img/restaurants/currygalore.jpg 200 7ms - 10.26kb
GET /img/restaurants/esthers.jpg 200 55ms - 11.85kb
GET /img/restaurants/beans.jpg 200 9ms - 15.7kb
GET /img/restaurants/north.jpg 200 11ms - 11.78kb
GET /img/restaurants/jeeves.jpg 200 9ms - 11.19kb
GET /img/restaurants/zardoz.jpg 200 10ms - 16.09kb
GET /img/restaurants/angular.jpg 200 7ms - 13.72kb
GET /img/restaurants/littlepigs.jpg 200 43ms - 12.64kb
GET /img/restaurants/flavia.jpg 200 11ms - 14.19kb
GET /img/restaurants/luigis.jpg 200 10ms - 16.36kb
GET /img/restaurants/thick.jpg 200 8ms - 14.13kb
GET /img/restaurants/wheninrome.jpg 200 8ms - 20.15kb
GET /img/restaurants/pizza76.jpg 200 5ms - 20.44kb
GET /favicon.ico 304 1ms
GET /img/customer_bkg.jpg 200 2ms - 32.42kb
GET /robots.txt 404 1ms
GET /robots.txt 404 1ms
{% endcodeblock %}

[0]:https://github.com/IgorMinar/foodme
[1]:https://docs.google.com/document/pub?id=1Fzq60IBaSf5mnsLWhig5nhZ9cJT85sresp0NqNIwh1I
[2]:http://nodejs.org/
[3]:https://npmjs.org/package/express
[4]:https://npmjs.org/package/open