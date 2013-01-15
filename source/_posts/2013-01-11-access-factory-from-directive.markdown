---
layout: post
title: "Access factory from directive"
date: 2013-01-11 23:21
comments: true
categories: AngularJS AngularJS_Directive AngularJS_Factory
---
####Objective####
1. Example of showing directive accesses service (factory).
2. Example of ng-src

<iframe style="margin:20px 0; width: 100%; height: 300px" src="http://embed.plnkr.co/qGAvEtXmkJ3opTRvZUMQ" frameborder="0" allowfullscreen="allowfullscreen"></iframe>

{% codeblock Markup  lang:html https://github.com/maxisam/AngularJSExample/blob/master/ng001/index.html Github %}
Avatar url : <input type="text" ng-model="url" placeholder='input url'/>

<div> result:
    <img my-avatar/>
</div>
{% endcodeblock %}
{% codeblock AngularJS  lang:javascript https://github.com/maxisam/AngularJSExample/blob/master/ng001/app.js Github %}
var app = angular.module('myApp', [])
    .factory('CurrentUserService', function () {
        "use strict";
        var user = {
            avatarUrl: ''
        }, srv = {};
        srv.getCurrentUser = function () {
            return user;
        };

        return srv;
    }).directive('myAvatar', function () {
        "use strict";
        return {
            restrict: 'A',
            replace: true,
            template: '<img class="avatar" ng-src="{{url}}" alt="{{url}}" title="{{url}}"> ',
            controller: function ($scope, CurrentUserService) {
                $scope.url = CurrentUserService.getCurrentUser().avatarUrl;
            }
        };
    });
    app.controller('MainCtrl', ['$scope', 'CurrentUserService', function ($scope, CurrentUserService) {
        "use strict";
        CurrentUserService.getCurrentUser().avatarUrl = $scope.url;
    }]);
{% endcodeblock %}
