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

- 字符的ASCII码

                str="0";
                code = str.charCodeAt(0); //48
- [字串样版匹配](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Guide/Regular_Expressions)
  
        let str = 'hello world!';
        let result = /^hello/.test(str);
        console.log(result); 
        // true
- 判断字符串是否为非数字: 
        function milliseconds(x) {
                if (isNaN(x)) {
                        return 'Not a Number!';
                }
                return x * 1000;
        }

        console.log(milliseconds('100F'));
        // expected output: "Not a Number!"

        console.log(milliseconds('0.0314E+2'));
        // expected output: 3140
**注意：[isNaN](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/isNaN)
**
1. Boolean的true会判断为数字1，false会判断为数字0
2. null '' "" 这些空值会判断为数字0
3. Date类型的值会判断为数字

Number
- n次方计算

        Math.pow(base, exponent) 
        **参数**
        base: 底的值
        exponent: 表达式的指数值
- 非整数的 Number 类型无法用 ==（=== 也不行） 来比较
        
        console.log( Math.abs(0.1 + 0.2 - 0.3) <= Number.EPSILON);
- 指数(power)
  
                0.0314e2 //3.14
                .0618e1  //0.618
                .1e2     //10
                3.e-2    //0.03
- 小数(decimal)

                4.       //4.0
                .5       //0.5
                
[Boolean](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Boolean)
- 非
  
                let x = !(expression);
- 或
  
                let x = expression1 || expression2;
- 且
  
                let x = expression1 && expression2;

[null](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/null)
- 是否为null

                const m = 'sky'.match(/[aeiou]/gi);
                if (m === null) {
                        console.log(0); //0
                }
  
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


