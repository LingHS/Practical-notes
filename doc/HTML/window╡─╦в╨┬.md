# window对象的刷新问题
  
> 在一个vue项目中的mounted中添加了window.addEventListener('xxx',()=>{}),再刷新页面的时候，发现事件被二次监听。  

结论：window对象不会因为页面刷新而刷新，所以原有的监听事件还在。
  
---
__另外__：发现`window.name`是window的原有属性，可基于它实现`跨域`