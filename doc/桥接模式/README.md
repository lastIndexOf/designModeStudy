# 桥接模式

```
dom1.addEventListener('click', function asFunc(e) {
  let id = this.id

  request.get('/api/v1')
    .send({ id })
    .end()
})
```
该事件中 回调函数asFunc中因为this.id而与当前环境产生了耦合， 要消除这种耦合继续要引入一层'桥梁'

```
dom1.addEventListener('click', function asFuncBrideg(e) {
  let id = this.id
  asFunc(id)
})

function asFunc(id) {
  request.get('/api/v1')
    .send({ id })
    .end()
}
```

这样, 利用asFuncBrideg这个'桥梁'就消除了asFunc函数与环境因为'this'而产生的耦合



- '桥梁'还可以把多个类联接起来

```
class A {
  constructor(a, b, c) {
    this.a = a
    this.b = b
    this.c = c
  }
}
class B {
  constructor(d) {
    this.d = d
  }
}

function bridge(a, b, c, d) {
  let a = new A(a, b, c)
  let b = new B(d)
}
```
