---
layout: post
title: "Scope and Isolated scope in directive"
date: 2013-01-18 11:31
comments: true
categories: AngularJS AngularJS_Directive Scope Attribute
---

####Objective####
1. Example of showing the relationship between scope and [isolated scope][1]
2. Example of using instance [attributes][0] in link function in directive and interacting with parent scope

####Notice####
1. There are 3 scopes in this example.

<iframe style="margin: 20px 0; width: 100%; height: 300px" src="http://embed.plnkr.co/uQSLHhv6uz2mCdmtPWSg" frameborder="0" allowfullscreen="allowfullscreen"></iframe>

{% codeblock Markup lang:html https://github.com/maxisam/AngularJSExample/blob/master/ng007/index.html Github %}

<div data-my-component attribute-foo="{{foo}}" binding-foo="foo"
     isolated-expression-foo="updateFoo(newFoo)" non-iso-attribute="foo">
    <h4>Attribute <span class="badge badge-important">@</span></h4>

    <div>
        <strong>get:</strong> {{isolatedAttributeFoo}}
    </div>
    <div class="row">
        <span class="span3"><strong>set:</strong> <input type="text" ng-model="isolatedAttributeFoo"></span>
        <span class="span6 text-success">  <i> This does not update the parent scope.</i>  </span>
    </div>

    <h4>Binding <span class="badge badge-important">=</span></h4>

    <div>
        <strong>get:</strong> {{isolatedBindingFoo}}
    </div>
    <div class="row">
        <span class="span3"><strong>set:</strong> <input type="text" ng-model="isolatedBindingFoo"></span>
        <span class="span6 text-success"> <i> This does update the parent scope.</i> </span>
    </div>

    <h4>Expression <span class="badge badge-important">&</span></h4>

    <div class="row">
       <span class="span3 input-append">
           <input type="text" class="input-medium" ng-model="isolatedFoo">
           <button class="btn" ng-click="isolatedExpressionFoo({newFoo:isolatedFoo})">Submit</button>
       </span>
        <span class="span6 text-success"> <i> And this calls a function on the parent scope.</i> </span>
    </div>

    <h4>Non Isolated Attribute</h4>

    <div class="row">
       <span class="span3"> <strong>get:</strong> {{$parent.nonIsoAttribute}}</span>
        <span class="span6 text-success"> <i> This reflects parent scope</i> </span>
    </div>
</div>
{% endcodeblock %}
{% codeblock AngularJS  lang:javascript https://github.com/maxisam/AngularJSExample/blob/master/ng007/app.js Github %} 
var app = angular.module('ngApp', [])
    .directive('myComponent', function () {
        "use strict";
        return {
            scope: {
                isolatedAttributeFoo: '@attributeFoo',
                isolatedBindingFoo: '=bindingFoo',
                isolatedExpressionFoo: '&'
            },
            link: function (scope, iElement, iAttrs) {
                scope.$parent.$watch(iAttrs.nonIsoAttribute, function (newVal, oldVal, scope) {
                    scope.nonIsoAttribute = newVal;
                }, false);
            }
        };
    });

app.controller('MainCtrl', ['$scope', function ($scope) {
    'use strict';
    $scope.foo = 'Hello!';
    $scope.updateFoo = function (newFoo) {
        $scope.foo = newFoo;
    };
}]);
{% endcodeblock %}

[0]:http://docs.angularjs.org/api/ng.$compile.directive.Attributes
[1]:http://docs.angularjs.org/guide/directive
