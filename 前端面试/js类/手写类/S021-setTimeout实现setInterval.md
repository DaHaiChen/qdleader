# 手写-setTimeout 模拟实现 setInterval
```

function mySetInterval(fn, time = 1000) {
  let timer = null,
    isClear = false;
  function interval() {
    if (isClear) {
      isClear = false;
      clearTimeout(timer);
      return;
    }
    fn();
    timer = setTimeout(interval, time);
  }
  timer = setTimeout(interval, time);
  return () => {
    isClear = true;
  };
}

```



### 2、用setInterval实现setTimeout


function mySetInterval(fn, delay) {
    const timer = setInterval(() => {
        fn()
        clearInterval(timer)
    }, delay)
}
// 测试
mySetInterval(() => console.log(888), 1000)

