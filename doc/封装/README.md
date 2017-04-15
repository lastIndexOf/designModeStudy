# 封装

- 先看个例子

![一个例子](../../images/fz1.png)

#### 封装是为了更好的解耦
```
  class Test {
    constructor(test) {
      this.test = test
      this._age = 12
    }

    setTest(val) {
      this.test = val + this._age
    }
  }

  const tst = new Test('test')
  tst.setTest('test2')
```
有这样一个类，里面有一个私有变量_age, 每一次调用setTest方法时都用到了这个内部的私有变量, 若是没有这个私有变量， 写法如下

```
  const tst = new Test('test')
  const _age = 12
  tst.setTest('test2' + _age)
```

这样对象就与当前环境产生了耦合

---------------------------------------
js 实现对象的私有变量(private)的方法

```
  class Person {
    constructor(name) {
      let name
      this.setName = function(val) {
        name = val
      }
      this.getName = function () {
        return name
      }

      this.setName(name)
    }
  }
```
