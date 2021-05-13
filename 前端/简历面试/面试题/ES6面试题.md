- 填充字符串（编程）（字节2020实习面试题）

- 管道函数（编程）（字节2020实习面试题）

- 箭头函数和普通函数的区别 （字节2020实习面试题+京东2020校招面试题）

- 事件循环方面的执行顺序出了一个题（字节2020实习）

- 有关`promise`回调的,实现封装`fn`方法，成功时推向`fullied`，失败推向`rejected` (字节2020校招)
    ```javascript
    function  promisefy(fn){}
    function fn(callback){
      //两种情况，成功或失败
      callback(null,(res)=>{//成功})
      callback(err=>{//失败},(res)=>{//成功})
    }
    p = promisefy(fn)
    ```

- 编程题：保证`tasks`列表必须顺序调用，不允许使用`async`和`await`(字节2020校招)

  ```javascript
  let p1 = p0.then(succ, fail)
  tasks = [task1, task2, ...taskN];
  function seq(tasks) {
  }
  ```

  ```javascript
  /*参考答案*/
  function seq(tasks){
      var start = 0
      var pro = Promise.resolve()
      while(start<tasks.length){
          pro = pro.then(tasks[start])
          start ++
      }
  }
  ```
  
- 编程题(字节2020年校招)
  ```javascript
  有一个函数，接收3个参数：
  • asyncAdd 没有返回值
  • callback 没有返回值
  function asyncAdd(a, b, callback) {
  }
  asyncAdd(1, 2, function (err, result) {
  if (err) throw err;
  console.log(result); // 3;
  });
  -- 题目
  有一个数列：[1, 2, 3, 4, ..., N];
  基于 asyncAdd 完成数列的求和运算。
  例如：
  function sum(list) {
  // TODO
  }
  sum([1, 2, 3, 4]).then(v => console.log(v)); // 10
  ```

  编程题：输入一个无重复的字符串，找出其全排列。（字节2020校招）

  ```javascript
  'abc' -> ['abc', 'cba, 'cab', ...]
  result = []
  result = result.concat(permutation('bc').map(r => 'a' + r))
  permutation('ac').map(r => 'b' + r)
  permutation('ab').map(r => 'c' + r)
  function permutation(str) {}
  ```

  ```javascript
  /** 参考答案：*/
  function permutation(str) {
      if(str.length == 0) return []
       var result = []
      for(var i=0;i<str.length;i++){
          var pre = str[i]
          var nex = ""
          for(var j=0;j<str.length;j++){
              if(i!=j)
                nex += str[j]
          }  
          result = result.concat(permutation(nex).map(r=>pre + r))
      }
      return result
  }
  ```

- 编程题(字节2020年校招)
    ```javascript
    有一个函数，接收3个参数：
    • asyncAdd 没有返回值
    • callback 没有返回值
    function asyncAdd(a, b, callback) {
    }
    asyncAdd(1, 2, function (err, result) {
    if (err) throw err;
    console.log(result); // 3;
    });
    
    -- 题目
    有一个数列：[1, 2, 3, 4, ..., N];
    基于 asyncAdd 完成数列的求和运算。
    例如：
    function sum(list) {
    // TODO
    }
    sum([1, 2, 3, 4]).then(v => console.log(v)); // 10
    ```

