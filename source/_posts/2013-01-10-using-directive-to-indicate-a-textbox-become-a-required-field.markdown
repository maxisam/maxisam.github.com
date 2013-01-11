---
layout: post
title: "Using directive to indicate a textbox become a required field"
date: 2013-01-10 00:54
comments: true
categories: AngularJS AngularJS_Directive
---
####Objective####
1. Example of ng-required
2. Example of using instance [attributes][0] in link function in directive
3. Example of having key:element mapping attribute

<iframe style="margin: 20px 0; width: 100%; height: 300px" src="http://embed.plnkr.co/83wZy086dHDl1r9EDAcS" frameborder="0" allowfullscreen="allowfullscreen"></iframe>

{% codeblock Markup lang:html https://github.com/maxisam/AngularJSExample/blob/master/ng003/index.html Github %}
<form ng-submit="submit()" name="form">
    <input type="checkbox" ng-model="partner" checked/>
    Are you bringing along a partner?<br/>
    Partner name:
    <input type="text" ng-model="partnerName" xng-placeholder="{ 'required': partner }" ng-required="partner"/> <br/>
    <input type="submit" value="save" ng-disabled="form.$invalid" class="btn"/>
</form>
{% endcodeblock %}


{% codeblock AngularJS lang:javascript https://github.com/maxisam/AngularJSExample/blob/master/ng003/app.js Github %}
app.directive('xngPlaceholder', function () {
    'use strict';
    return {
        restrict: 'A',
        link: function (scope, element, attrs) {
            scope.$watch(attrs.ngPlaceholder, function (newVal) {
                element.removeAttr('placeholder');
                var att = '';
                angular.forEach(newVal, function (elm, key) {
                    att += elm ? (key + ' ') : '';
                });
                element.attr('placeholder', att);
            }, true);
        }
    };
});
{% endcodeblock %}



[0]:http://docs.angularjs.org/api/ng.$compile.directive.Attributes