---
layout: post
title: "Observe two variables in one $watch"
date: 2013-01-16 00:04
comments: true
categories: AngularJS AngularJS_Directive $Watch
---

####Objective####
1. Example of [$watch][0]

<iframe style="margin: 20px 0; width: 100%; height: 300px" src="http://embed.plnkr.co/o3cnXm" frameborder="0" allowfullscreen="allowfullscreen"></iframe>

{% codeblock Markup  lang:html https://github.com/maxisam/AngularJSExample/blob/master/ng006/index.html Github %}
<div>X: <input type='text' ng-model='x'/></div>
<div>Y: <input type='text' ng-model='y'/></div>
<div data-xng-watcher x='{{x}}' y='{{y}}'></div>
{% endcodeblock %}

{% codeblock AngularJS  lang:javascript https://github.com/maxisam/AngularJSExample/blob/master/ng006/app.js Github %} 
var app = angular.module('ngApp', [])
    .directive('xngWatcher', function () {
        "use strict";
        return {
            template: '<span>X:{{x}}, Y:{{y}}</span>',
            link: function (scope, elm, iAttrs) {
                scope.$watch(function () {
                    return {x: iAttrs.x, y: iAttrs.y};
                }, function (newVal, oldVal, scope) {
                    console.log('change !');
                    scope.x = newVal.x;
                    scope.y = newVal.y;
                }, true);
            }
        };
    });
{% endcodeblock %}
[0]:http://docs.angularjs.org/api/ng.$rootScope.Scope#$watch