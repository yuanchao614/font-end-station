---
title: Angular Router
type: angular
order: 3
---

### angular2 scroll top on router change

当我们在第一个路由滑动到底部当我们点击导航跳转到另一个路由时页面没有回到顶部而是保持上一个路由的滚动位置，基本的解决办法有两种。

#### 第一种解决方法是在组建的ngOnIinit()中进行调换路由后的重置

```js
import { Component, OnInit } from '@angular/core';
import { Router, NavigationEnd } from '@angular/router';

@Component({
    selector: 'my-app',
    template: '<ng-content></ng-content>',
})
export class MyAppComponent implements OnInit {
    constructor(private router: Router) { }

    ngOnInit() {
        this.router.events.subscribe((evt) => {
            if (!(evt instanceof NavigationEnd)) {
                return;
            }
            window.scrollTo(0, 0)
        });
    }
}
````

#### 第二种解决方法是在import中对路由进行注入的时候设置<code>scrollPositionRestoration</code>参数(angular6之后)。

```js
RouterModule.forRoot(routes, {scrollPositionRestoration: 'enabled'})
```