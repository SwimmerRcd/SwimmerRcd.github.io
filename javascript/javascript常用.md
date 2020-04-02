# 基础知识
## 数据类型及其对象原型提供的方法
[String](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String)<br/>
- 返回字符串中某个位置上的字符
  
        return 'cat'.charAt(1) // returns "a"
        return 'cat'[1] // returns "a"
- 返回字符串长度

        const str = 'Life, the universe and everything. Answer:';
        console.log(str + ' ' + str.length);
        // expected output: "Life, the universe and everything. Answer: 42"
- 字符串拼接
  
        let longString = "This is a very long string which needs " +
                 "to wrap across multiple lines because " +
                 "otherwise my code is unreadable."
- 长字符串断行
        let longString = "This is a very long string which needs \
to wrap across multiple lines because \
otherwise my code is unreadable."

[Array](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array)
- 添加元素到数组末尾：push()
  
        let fruits = ['Apple', 'Banana']
        let newLength = fruits.push('Orange')
        // ["Apple", "Banana", "Orange"]
- 移除数组末尾元素：pop()
  
        let last = fruits.pop() // remove Orange (from the end)
        // ["Apple", "Banana"]
- 移除数组开头元素：shift()

        let first = fruits.shift() // remove Apple from the front
        // ["Banana"]
- 添加元素在数组开头：unshift()
  
        let newLength = fruits.unshift('Strawberry') // add to the front
        // ["Strawberry", "Banana"]
- 返回数组长度：length
  
        const fruits = []
        fruits.push('banana', 'apple', 'peach')
        console.log(fruits.length) // 3
- 遍历元素：forEach()
  
        let fruits = ['Apple', 'Banana']
        fruits.forEach(function(item, index, array) {
            console.log(item, index)
        })
        // Apple 0
        // Banana 1
---
## 流程控制语句
for循环
- 退出当前循环或switch： break
  
        for(let i=1;i<=10;i++) { 
            if(i==8) { 
                break; 
            } 
            document.write(i); 
        } 
- 跳至循环的下一次：continue
  
        for(var i=1;i<=10;i++) { 
            if(i==8) { 
                continue; 
            } 
            document.write(i); 
        } 
- 退出当前函数：return
  
        for(var i=1;i<=10;i++) { 
            if(i==8) { 
                return; 
            } 
        document.write(i); 
        } 


