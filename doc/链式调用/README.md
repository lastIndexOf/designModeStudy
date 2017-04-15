# 链式调用

- 让在取值函数中使用链式调用

```
(function () {
  function _$() {}

  _$.prototype = {
    callName(cb) {
      const self = this

      if (cb) {
        cb && cb.call(self, self.name)
        return self
      }
      else
        return self.name
    }
  }

  return window.$ = new _$()
})()

```
- 利用回调函数处理返回值， 保持链式调用风格
