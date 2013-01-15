---
layout: post
title: "Using directive to work with highlight.js"
date: 2013-01-15 00:59
comments: true
categories: AngularJS AngularJS_Directive
---

1. Example of ussing directive to work with [highlight.js][0], or any other jQuery plugin.
2. Example of [ng-transclude][1].
3. Example of [$interpolate][2]. (It is different from [$compile][3])

<iframe style="margin:20px 0; width: 100%; height: 300px" src="http://embed.plnkr.co/3rtp1v" frameborder="0" allowfullscreen="allowfullscreen"></iframe>

{% codeblock Markup lang:html https://github.com/maxisam/AngularJSExample/blob/master/ng005/index.html Github %} 
<snippet>&lt;!--[if IE]&gt;&lt;script src="{{cdnPath}}{{version}}/js/gaig-ui-ie.js"&gt;&lt;/script&gt;&lt;![endif]--&gt;
    &lt;link rel="stylesheet" href="{{cdnPath}}{{version}}/css/gaig-bootstrap.css" /&gt;
    &lt;script src="{{cdnPath}}{{version}}/js/gaig-ui.js"&gt;&lt;/script&gt;</snippet>
{% endcodeblock %}

{% codeblock AngularJS lang:javascript https://github.com/maxisam/AngularJSExample/blob/master/ng005/app.js Github %} 
var app = angular.module('ngApp', [])
    .directive('snippet', ['$timeout', '$interpolate', function ($timeout, $interpolate) {
        "use strict";
        return {
            restrict: 'E',
            template: '<pre><code ng-transclude></code></pre>',
            replace: true,
            transclude: true,
            link: function (scope, elm) {
                var tmp = $interpolate(elm.find('code').text())(scope);
                elm.find('code').html(hljs.highlightAuto(tmp).value);
            }
        };
    }]);

app.controller('MainCtrl', ['$scope', function ($scope) {
    'use strict';
    $scope.cdnPath = "//path/to/cdn/";
    $scope.version = "1.0";
}]);
{% endcodeblock %}


[0]:http://softwaremaniacs.org/soft/highlight/en/
[1]:http://docs.angularjs.org/api/ng.directive:ngTransclude
[2]:http://docs.angularjs.org/api/ng.$interpolate
[3]:http://docs.angularjs.org/api/ng.$compile
