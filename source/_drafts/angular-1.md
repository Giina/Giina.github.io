---
title: angular-1
date: 2016-01-13 17:20:00
tags:
---

### ·1

```javascript
window.bind('click',function(e){
	if(e.target.parentNode != $element[0]){
		console.log(e);
		$scope.isOpen=false;
		$scope.$apply();
	}
});
```

### ·2

```javascript
<dd ng-show="data2" class="dropdown" ng-click="isOpen=!isOpen;select(-1)" ng-class="{'active':list_index===-1}" style="position: relative">
	<span ng-bind="list_more_index"></span>
    <ul ng-class="{'open':isOpen}" class="dropdown-list">
        <li ng-repeat="item in data2" class="dropdown-list-item" ng-click="$parent.list_more_index=item;" ng-bind="item"></li>
    </ul>
</dd>
//wrong reason
function createEventHandler(element, events) {
  var eventHandler = function(event, type) {
    // jQuery specific api
    event.isDefaultPrevented = function() {
      return event.defaultPrevented;
    };
……
}

//
$scope.$apply()
```