---
title: Angular Pipe
type: angular
order: 2
---

### angular 自定义管道
> Angular 内置了一些管道，比如 DatePipe、UpperCasePipe、LowerCasePipe、CurrencyPipe 和 PercentPipe。 它们全都可以直接用在任何模板中;但是在angular(angular2)中由于性能的原因官方没有提供有关[筛选和排序的管道](https://www.angular.cn/guide/pipes#appendix-no-filterpipe-or-orderbypipe)，于是当我们在使用<code>*ngFor</code>需要筛选数据时可以自定义筛选管道。

* in component
```js
filterargs = {title: 'hello'};
items = [{title: 'hello world'}, {title: 'hello kitty'}, {title: 'foo bar'}];
```

* in template
```html
<li *ngFor="let item of items | myfilter:filterargs">
```

* in pipe
```js
import { Pipe, PipeTransform } from '@angular/core';

@Pipe({
    name: 'myfilter',
    pure: false
})
export class MyFilterPipe implements PipeTransform {
    transform(items: any[], filter: Object): any {
        if (!items || !filter) {
            return items;
        }
        // filter items array, items which match and return true will be
        // kept, false will be filtered out
        return items.filter(item => item.title.indexOf(filter.title) !== -1);
    }
}
```
* in<code> app.module.ts</code>; you no longer need to register the pipes in your <code>@Component</code>

```js
import { MyFilterPipe } from './shared/pipes/my-filter.pipe';

@NgModule({
    imports: [
        ..
    ],C
    declarations: [
        MyFilterPipe,
    ],
    providers: [
        ..
    ],
    bootstrap: [AppComponent]
})
export class AppModule { }
```

参考链接： 

[https://stackoverflow.com/questions/34164413/how-to-apply-filters-to-ngfor](https://stackoverflow.com/questions/34164413/how-to-apply-filters-to-ngfor)