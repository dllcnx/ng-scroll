# @dllcn/ng-scroll
ng的瀑布流滚动条监听指令.
## Features
- 检测元素或窗口上的滚动并发出事件，计算用户是否到达该元素的顶部/底部。
## Install
- With NPM
```sh
npm install @dllcn/ng-scroll --save
```


```typescript
// app.module.ts
import { ScrollEventModule } from '@dllcn/ng-scroll';

@NgModule({
  imports: [
    ...,
    ScrollEventModule,
    ...,
  ]
})
export class AppModule { }
```

在模板中，您可以向任何元素添加'detect scroll'属性和`（onscroll）`事件。

您还可以添加`[BottomOffset]`或`[TopOffset]`以在到达底部或顶部检测时进行更改，值默认为100px，该值应为像素数。
```typescript
// app.awesome.component.ts

...
import { ScrollEvent } from '@dllcn/ng-scroll';
...

@Component({
   ...
   template: `...
        <div detect-scroll (onScroll)="handleScroll($event)" [bottomOffset]="200" [topOffset]="200" >
            <div>Bla bla bla</div>
            <div>Bla bla bla</div>
            <div>Bla bla bla</div>
            <div>Bla bla bla</div>
            <div>Bla bla bla</div>
            <div>Bla bla bla</div>
            <div>Bla bla bla</div>
            <div>Bla bla bla</div>
            <div>Bla bla bla</div>
        <div>
   ...`,
})
export class AwesomeComponent {
  public handleScroll(event: ScrollEvent) {
    console.log('scroll occurred', event.originalEvent);
    if (event.isReachingBottom) {
      console.log(`the user is reaching the bottom`);
    }
    if (event.isReachingTop) {
      console.log(`the user is reaching the top`);
    }
    if (event.isWindowEvent) {
      console.log(`This event is fired on Window not on an element.`);
    }

  }
}
```
