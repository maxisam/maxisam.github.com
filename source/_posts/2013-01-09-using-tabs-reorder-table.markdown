---
layout: post
title: "Using tabs reorder table"
date: 2013-01-09 22:49
comments: true
categories: AngularJS AngularJS_Filter
---

####Objective:####
1. Example for using filter to set order by certain column with tab UI.
2. Exampe for using ng-class to switch twitter bootstrap tabs.

<iframe style="margin:20px 0; width: 100%; height: 300px" src="http://embed.plnkr.co/fMrhagVKl2nehzTOHriF" frameborder="0" allowfullscreen="allowfullscreen"></iframe>

{% codeblock Mark up for Twitter bootstrap tab lang:html https://github.com/maxisam/AngularJSExample/blob/master/ng002/Index.html Github %}
<body ng-controller="MainCtrl">
<ul class="nav nav-pills">
    <li ng-class="{'active': order=='name'}">
        <a href="#" ng-click="setOrder('name')">name</a>
    </li>
    <li  ng-class="{'active': order=='phone'}">
        <a href="#" ng-click="setOrder('phone')">phone</a>
    </li>
</ul>
<ul>
    <li data-ng-repeat="friend in friends|orderBy:order">
        <span class="name">{{friend.name}}</span>
        <span class="phone">{{friend.phone}}</span>
    </li>
</ul>
{% endcodeblock %}

{% codeblock AngularJS controller lang:javascript https://github.com/maxisam/AngularJSExample/blob/master/ng002/app.js Github%}
app.controller('MainCtrl', ['$scope', function ($scope) {
    'use strict';
    $scope.order = 'name';
    $scope.friends = [
        {name: 'John', phone: '555-1276'},
        {name: 'Mary', phone: '800-BIG-MARY'},
        {name: 'Mike', phone: '555-4321'},
        {name: 'Adam', phone: '555-5678'},
        {name: 'Julie', phone: '555-8765'}
    ];
    $scope.setOrder = function (order) {
        $scope.order = order;
    };
}]);
{% endcodeblock %}


