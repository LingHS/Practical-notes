# 函数防抖
  >假设电梯一次只能载一人的话，10 个人要上楼的话电梯就得走 10 次，是一种浪费资源的行为；而实际生活正显然不是这样的，当电梯里有人准备上楼的时候如果外面又有人按电梯的话，电梯会再次打开直到满载位置，从电梯的角度来说，这时一种节约资源的行为（相对于一次只能载一个人）。  
  
  函数防抖同电梯得运行机制一样：__当最后一次操作结束后，再运行指定函数__  



**场景：fn是一个异步函数，希望经防抖处理后得到fn的返回值**

  ``` js
  /**
 * 函数防抖
 * @param {function} fn 传入的函数
 * @param {Number} delay 延迟毫秒数 
 */

export function debounce(fn, delay = 200) {
  // 定时器，用来 setTimeout
  let timer;
  // 返回一个函数，这个函数会在一个时间区间结束后的 delay 毫秒时执行 fn 函数
  const debounced = function (...args) {
    // 每次这个返回的函数被调用，就清除定时器，以保证不执行 fn
    clearTimeout(timer);
    // 当返回的函数被最后一次调用后（也就是s用户停止了某个连续的操作），
    // 再过 delay 毫秒就执行 fn
    return new Promise(resolve => {
      timer = setTimeout(() => {
        resolve(fn.apply(this,args));
      }, delay);
    });
  }
  return debounced;
}
//调用方法
let newFn = debounce(fn);
  newFn([x, y, z]).then(res => {
    //res为返回值
    //do something
  })
  ```