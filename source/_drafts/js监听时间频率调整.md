---
title: js监听时间频率调整
tags: 
category: 功能实现
---

场景：监听搜索框内容改变后发出搜索提示内容的请求，导致搜索过于频繁
目标：每次搜索框内容改变后.2s内没有变化，则发出搜索提示内容的请求（如果.2s内有变化，暂不请求，监听变化后的.2s内有无改变）

```
    /**
     * 搜索相关企业
     * 函数逻辑：搜索.2s后的文本，并设置flag减少请求次数
     * @param e
     */
    _searchHint: function (e) {
        if (!IS_HINT_SEARCHING) {
            IS_HINT_SEARCHING = true;
            setTimeout(function () {
                var searchHintList = document.querySelector("#search-hint-list");
                $.get(API + "/organizations", {name_like: e.target.value, _range: "1,5"}, function (result) {
                    searchHintList.innerHTML = '';
                    if (result.count > 0) {
                        for (var i = 0; i < result.organizations.length; i++) {
                            var li = document.createElement("li");
                            li.innerHTML = result.organizations[i].name.replace(e.target.value, "<em>" + e.target.value + "</em>");
                            li.classList.add("sb-hint-item");
                            li.addEventListener('click', view._searchOrganization);
                            searchHintList.appendChild(li);
                        }
                        searchHintList.classList.remove("hide");
                    } else {
                        searchHintList.classList.add("hide");
                    }
                    IS_HINT_SEARCHING = false;
                });
            }, 200);
            return;
        }
    },
```