---
layout: post
title: "Checkbox w/ auto focus textbox"
date: 2013-01-10 23:35
comments: true
categories: AngularJS AngularJS_Directive
---
####Objective####
1. Show the different between Controller and Directive
2. Example of using instance [attributes][0] with watch in link function in directive

<iframe style="margin:20px 0; width: 100%; height: 300px" src="http://embed.plnkr.co/84NRZHlGeL3LqS4XgTGY" frameborder="0" allowfullscreen="allowfullscreen"></iframe>

{% codeblock Markup lang:html https://github.com/maxisam/AngularJSExample/blob/master/ng004/index.html Github %}
<div class='row'>
    <span class='span4'>
      controller version
    </span>
    <span class='span8'>
      <input type="checkbox" id='checkbox' ng-model="isChecked">
      <input type="text" id="name">
    </span>
</div>
<div class='row'>
    <span class='span4'>
      directive version
    </span>
    <span class='span8'>
      <input type="checkbox" ng-model="isChecked2">
      <input type="text" xng-focus='isChecked2'>
    </span>
</div>
{% endcodeblock %}

{% codeblock AngularJS lang:javascript https://github.com/maxisam/AngularJSExample/blob/master/ng004/app.js Github %} 
var app = angular.module('ngApp', [])
    .directive('xngFocus', function () {
        "use strict";
        return function (scope, element, iattrs) {
            scope.$watch(iattrs.xngFocus,
                function (newValue) {
                    newValue && element.focus();
                }, true);
        };
    });
app.controller('MainCtrl', ['$scope', function ($scope) {
    'use strict';
    $scope.$watch('isChecked', function (newV) {
        newV && $('#name').focus();
    }, true);
}]);
{% endcodeblock %}
