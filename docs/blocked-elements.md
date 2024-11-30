# 屏蔽的对象

易次元代码执行是通过将易次元自身的处理代码和用户代码拼接，然后使用 eval() 函数进行执行，出于安全考虑，在上下文中使用以下代码屏蔽了部分对象或函数。

?> 并不是所有被屏蔽的对象或函数都是自带对象或函数

```javascript
var cc = null // Cocos 2D 全局对象
var window = null
var globalThis = null
var WebSocket = null
var alert = null
var self = null
var parent = null
var top = null
var opener = null
var frames = null
var frameElement = null
var content = null
var _content = null
var document = null
var XMLHttpRequest = null
var fetch = null
var localStorage = null
var sessionStorage = null
var location = null
var setTimeout = null
var setInterval = null
var Function = null
var _report = null

var innerAc = null // 易次元 ac对象实际处理函数
var innerOc = null
```

但是根据现代浏览器的运行规则，`globalThis`通常指向`window`，利用一些不那么优雅的 polyfill 方案即可拿到被屏蔽的全局对象或函数，您可以将以下代码直接放置于易次元的全局函数第一条中，以在整个项目中正常使用被屏蔽的全局对象或函数。

!> 易次元在程序闭包外，疑似会对`window`中所有多出的属性执行`delete`操作来删除这些属性，请不要通过直接操作`window`对象的属性来向您的浏览器控制台传递数据或对象。

```javascript
var globalThis = (function () {
  var gbthis
  Object.prototype.__defineGetter__('__magic__', function () {
    return this
  })
  __magic__.globalThis = __magic__
  gbthis = __magic__.globalThis
  delete Object.prototype.__magic__
  return gbthis
})()

var __fakeGlobalThis = (() => {
  const __tryGetObject = (name) => {
    if (globalThis && globalThis[name]) {
      return globalThis[name]
    }
    if (eval) {
      return (0, eval)(`window["${name}"]`)
    }
    console.log('Failed.', name)
    return null
  }
  return new Proxy(
    {},
    {
      get: (target, prop, receiver) => {
        return __tryGetObject(prop)
      },
    }
  )
})()

var window = globalThis
var self = globalThis

var {
  WebSocket,
  XMLHttpRequest,
  alert,
  fetch,

  setTimeout,
  setInterval,
  Function,

  parent,
  top,
  opener,
  frames,

  content,
  document,

  localStorage,
  sessionStorage,
  location,

  cc,
} = __fakeGlobalThis
```
