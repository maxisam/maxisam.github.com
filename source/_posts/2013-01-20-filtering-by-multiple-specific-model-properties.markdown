---
layout: post
title: "Filtering by Multiple Specific Model Properties"
date: 2013-01-20 14:12
comments: true
categories: AngularJS filter
---
####Objective####
1. Example of showing to filter by Multiple Specific Model Properties by using [filter function][0]
2. Example of [currency filter][1]

<iframe style="width: 100%; height: 320px" src="http://embed.plnkr.co/scuPYt" frameborder="0" allowfullscreen="allowfullscreen"></iframe>

{% codeblock Markup  lang:html https://github.com/maxisam/AngularJSExample/blob/master/ng009/index.html Github %} 
<div class="row">
    <input class="span4 pull-right" type="text" placeholder="Search for smartphone in model and brand" ng-model="query">
</div>
<div class="row">
    <table id="results" class="table table-striped table-bordered table-hover">
        <thead>
        <tr>
            <th>Brand</th>
            <th>Model</th>
            <th>Price</th>
        </tr>
        </thead>
        <tbody>
        <tr ng-repeat="smartphone in smartphones | filter: search ">
            <td id="brand">{{smartphone.brand}}</td>
            <td id="model">{{smartphone.model}}</td>
            <td id="price">{{smartphone.price | currency}}</td>
        </tr>
        </tbody>
    </table>
</div>
{% endcodeblock %}
{% codeblock AngularJS  lang:javascript https://github.com/maxisam/AngularJSExample/blob/master/ng009/app.js Github %} 
var app = angular.module('ngApp', []);

app.controller('MainCtrl', ['$scope', function ($scope) {
    'use strict';
    $scope.smartphones = [
        {brand: 'Apple', model: 'iPhone 4S', price: '999'},
        {brand: 'Samsung', model: 'SIII', price: '888' },
        {brand: 'LG', model: 'Optimus', price: '777'},
        {brand: 'htc', model: 'Desire', price: '666'},
        {brand: 'Nokia', model: 'N9', price: '555'}
    ];
    $scope.search = function (row) {
        return !!((row.brand.indexOf($scope.query || '') !== -1 || row.model.indexOf($scope.query || '') !== -1));
    };
}]);
{% endcodeblock %}
[0]:http://docs.angularjs.org/api/ng.filter:filter
[1]:http://docs.angularjs.org/api/ng.filter:currency