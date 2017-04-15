# 单体模式

```
 let DOMs = (function() {
       let dom1 = $('.dom1')
       let dom2 = $('.dom2')

       let innerX = 20

       function getX() {
         return innerX
       }

       return {
         dom1,
         dom2,
         getX
       }
     })()
```

一个简单的单例模式实例， 将用法相近或联系紧密的各个对象写在同一个对象里， 需要使用的时候用点运算符进行使用， 若有像`innerX`这样的需要保护的变量， 可以如上仅提供查看而不提供修改的接口

- 单体是一个划分命名空间并将一批相关方法或属性组织在一起的对象，若其可以实例化，那么它只可以被实例化一次

----------------------------------------------------------------------

- 划分命名空间

```
  let namespace1 = {
    func1() {

    },
    func2() {

    }
  }

  let namespace2 = {
    func1() {

    },
    func2() {

    }
  }

```
namespace1 和 namespace2中都有func1 和 func2, 但他们不会互相影响

- 单体模式中的私有变量

```
 let obj = {
   name: 'tst',
   func() {
     obj._init()
     ...
   },
   _init()
   ...
 }
```
通常，私有变量可以用`_`标示， 也可以用闭包实现完全私有。
而私有变量不应该被发布给外界做接口， 程序员开发时也应该避免调用单例内部的私有方法和属性， 防止日后单例内部这些私有成员变化引起的程序崩溃。

- 用闭包实现单例的私有成员

```
let obj = (function () {
      let _init = function _init () {

      }
      ...
      return {
        ...
      }
    })()

```
这样， _init方法在外部是无法访问的

- *惰性加载单体

当单体内的成员数量过多时，若在脚本开始执行的时候就加载， 可能会对性能造成一定影响， 对于这样占时较长的单体， 通常可以等到使用的时候在加载， 就是常说的'惰性加载'(lazy-loading)

```
    let obj = (function () {
      let interfaceObj
      function _init () {
        // 真正的单体内容写在这...


        return {

        }
      }
      return {
        getInterface() {
          if (!interfaceObj)
            interfaceObj = _init()

          return interfaceObj
        }
      }
    })()

```

![单体模式的优势](../../images/dt1.png)
