# taskQueue
使用过多setTimeout，会产生性能问题。taskQueue,将多个任务，整合在一个队列中，使用一个定时器去执行指定数量的任务。

```js
const taskqueue = new TaskCountQueue();

taskqueue.setFirstTime(true);
// good
for (let index = 0; index < 100000; index++) {
     // 只使用一个定时器去执行任务
     taskqueue.pushAndRun(() => {
          console.log(index);
     });
}

// bad 糟糕的demo
for (let index = 0; index < 100000; index++) {
     // 使用了 很多个定时器去执行任务，对性能影响较大
     setTimeout(() => {
          console.log(index);
     })
}
```
