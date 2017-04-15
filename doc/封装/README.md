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

但这种实现private变量的方式导致没创建一个对象实例都会在内存中新创建一些内部的私有方法，无法很好的利用到原型链，而且也无法很好的派生子类， 被称作“继承破坏封装”，所以若不是一定要确保变量私有的场合，还是建议别采用这种对象创建方式

## 总的说来，封装以利于降低类之间的耦合，让程序员对类的内部数据和结构有高度的掌控，可以'随心的所欲'地修改内部细节而不用担心对外部产生影响
