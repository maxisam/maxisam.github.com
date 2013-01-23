---
layout: post
title: "$observe vs $watch"
date: 2013-01-20 02:09
comments: true
categories: AngularJS AngularJS_Directive $watch $observe Attribute
---

####Objective####
1. Example of showing the difference between [observe][0] and [watch][0]
2. Example of showing [$eval][1]


<iframe style="margin: 20px 0; width: 100%; height: 250px" src="http://embed.plnkr.co/jxGl8aLKy1snCMlRbRxC" frameborder="0" allowfullscreen="allowfullscreen"></iframe>

{% codeblock Markup  lang:html https://github.com/maxisam/AngularJSExample/blob/master/ng008/index.html Github %}

<input type="text" ng-model="xinput" />
<div my-dir textinput='xinput' valinput='{{xinput}}'></div>

{% endcodeblock %}

{% codeblock AngularJS  lang:javascript https://github.com/maxisam/AngularJSExample/blob/master/ng008/app.js Github %}

var app = angular.module('ngApp', [])
    .directive('myDir', function () {
        "use strict";
        return {
            scope: true,
            template: '<div>observe-textinput: {{observe1}}</div><div>observe-valinput: {{observe2}}</div><div>eval: {{evalVal}}</div><div>eval2: {{evalVal2}}</div><div>watch: {{watchVal}}</div>',
            link: function (scope, iElement, iAttrs) {
                iAttrs.$observe('textinput', function (value) {
                    scope.observe1 = value;
                });
                iAttrs.$observe('valinput', function (value) {
                    scope.observe2 = value;
                });
                scope.$watch(iAttrs.textinput, function (newVal, oldVal, scope) {
                    scope.evalVal = scope.$eval(iAttrs.textinput);
                    scope.evalVal2 = scope.$eval('xinput');
                    scope.watchVal = newVal;
                }, false);
            }
        };
    });

app.controller('MainCtrl', ['$scope', function ($scope) {
    'use strict';
    $scope.xinput = 'test';
}]);

{% endcodeblock %}




[0]:http://docs.angularjs.org/guide/directive
[1]:http://docs.angularjs.org/api/ng.$rootScope.Scope#$eval