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

- 
