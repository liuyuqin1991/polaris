# 防抖函数

> 当事件触发时，相应的函数并不会立即执行，而是会等待一定的时间再执行

防抖函数的执行过程具有以下特点：

1. 当事件密集触发时，函数的执行会被频繁的推迟；
2. 只有等待了一段时间也没有事件触发，才会真正的执行响应函数；

实现步骤：

1. 防抖函数的返回值是一个函数
2. 定义变量，保存上一次的定时
3. 如果时间内在次触发，要取消上一次的定时，重新开始定时
4. 开始延时执行
5. 执行外部转入的真正要执行的函数

```
// debounce.js
function debounce(fn, delay) {

  let timer = null  // 步骤2

  const _debounce = function() {
    if (timer) clearTimeout(timer)  // 步骤3

    timer = setTimeout(() => {  // 步骤4
      fn()  // 步骤5
      timer = null
    }, delay)
  }

  return _debounce  // 步骤1
}
```

# 节流函数

> 当多个事件在规定时间内多次触发，回调函数最终只会执行一次

节流函数的执行过程具有以下特点：

1. 如果这个事件会被频繁触发，那么节流函数会按照一定的频率来执行函数；
2. 不管在这个中间有多少次触发这个事件，执行函数的频繁总是固定的；

实现步骤：

1. 节流函数的返回值是一个函数
2. 记录上一次的开始时间
3. 获取当前事件触发时的时间
4. 计算出还剩余多长时间需要去触发函数
5. 真正触发函数，保留上次触发的时间，并保存时间

```
// throttle.js
function throttle(fn, interval) {
  let lastTime = 0  // 步骤2

  const _throttle = function() {
    const nowTime = Date.now()  // 步骤3
    // 步骤4 计算出还剩余多长时间需要去触发函数
    const remainTime = interval - (nowTime - lastTime)

    if (remainTime <= 0) {
      // 步骤5
      fn()
      lastTime = nowTime
    }
  }

  return _throttle  // 步骤1
}
```
