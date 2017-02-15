###数组
>数组,英文为Array 

数组是一组按顺序排列的集合，集合的每个值称为元素。不同于Java等编程语言,JavaScript的数组可以包括任意数据类型。例如：
```
[1, 3.14, 'Hello', null, true];
```
上述数组包含5个元素。数组用[]表示，元素之间用,分隔。

另一种创建数组的方法是通过Array()函数实现：
```
new Array(1, 2, 3); // 创建了数组[1, 2, 3]
```
然而，出于代码的可读性考虑，强烈建议直接使用[]。
数组的元素可以通过索引来访问。请注意，索引的起始值为0：
```
var arr = [1,3.14, 'Hello', null, true];
arr[0]; // 返回索引为0的元素，即1
arr[4]; // 返回索引为4的元素，即true
arr[5]; // 索引超出了范围，返回undefined
```

要取得Array的长度，直接访问length属性：
```
var arr = [1,3.14, 'Hello', null, true];
console.log(arr.length); //输出5
```

**请注意，直接给Array的length赋一个新的值会导致Array大小的变化**：

```
var arr = [1, 2, 3];
arr.length; // 3
arr.length = 6; //长度变成6
arr; // arr变为[1, 2, 3, undefined, undefined, undefined]
arr.length = 2;
arr; // arr变为[1, 2]
```

`Array`可以通过索引把对应的元素修改为新的值，因此，对Array的索引进行赋值会直接修改这个Array：
```
var arr = ['A', 'B', 'C'];
arr[1] = 520;
arr; // arr现在变为['A', 520, 'C']
```
**如果通过索引赋值时，索引超过了范围，同样会引起Array大小的变化：**
```
var arr = [1, 2, 3];
arr[5] = 'x';
arr; // arr变为[1, 2, 3, undefined, undefined, 'x']
```

大多数其他编程语言不允许直接改变数组的大小，越界访问索引会报错。然而，JavaScript的Array却不会有任何错误。

**在编写代码时，不建议直接修改Array的大小，访问索引时要确保索引不会越界。**

####indexOf()
与字符串类似，数组也可以通过indexOf()来搜索一个指定的元素的位置：
```
var arr = [10, 20, '30', 'xyz'];
arr.indexOf(10); // 元素10的索引为0
arr.indexOf(20); // 元素20的索引为1
arr.indexOf(30); // 元素30没有找到，返回-1
arr.indexOf('30'); // 元素'30'的索引为2
```
注意了，数字30和字符串'30'是不同的元素。

####slice()
slice()就是对应字符串的substring()方法，它截取数组的部分元素，然后返回一个新的数组：
```
var arr = ['A', 'B', 'C', 'D', 'E', 'F', 'G'];

// 从索引0开始，到索引3结束，但不包括索引3: ['A', 'B', 'C']
arr.slice(0, 3); 

// 从索引3开始到结束: ['D', 'E', 'F', 'G']
arr.slice(3);
```
注意到`slice()`的起止参数包括开始索引，不包括结束索引。

如果不给slice()传递任何参数，它就会从头到尾截取所有元素。利用这一点，我们可以很容易地复制一个数组：
```
var arr = ['A', 'B', 'C', 'D', 'E', 'F', 'G'];
var aCopy = arr.slice();
aCopy; // ['A', 'B', 'C', 'D', 'E', 'F', 'G']
```
####push()和pop()
`push()`向数组的末尾添加若干元素，`pop()`则把数组的最后一个元素删除掉：
```
var arr = [1, 2];
arr.push('A', 'B'); // 返回Array新的长度: 4
arr; // [1, 2, 'A', 'B']
arr.pop(); // pop()返回'B'
arr; // [1, 2, 'A']
arr.pop(); arr.pop(); arr.pop(); // 连续pop 3次
arr; // []
arr.pop(); // 空数组继续pop不会报错，而是返回undefined
arr; // []
```

#### unshift()和shift()

如果要往数组的头部添加若干元素，使用`unshift()`方法，`shift()`方法则把Array的第一个元素删掉：

```
var arr = [1, 2];
arr.unshift('A', 'B'); // 返回Array新的长度: 4
arr; // ['A', 'B', 1, 2]
arr.shift(); // 'A'
arr; // ['B', 1, 2]
arr.shift(); arr.shift(); arr.shift(); // 连续shift 3次
arr; // []
arr.shift(); // 空数组继续shift不会报错，而是返回undefined
arr; // []
```

####sort()
`sort()`可以对当前数组进行排序，它会直接修改当前数组的元素位置，直接调用时，按照默认顺序排序：
```
var arr = ['B', 'C', 'A'];
arr.sort();
arr; // ['A', 'B', 'C']
```
如果想按照自己指定的方式排序,需要借助函数，后面介绍函数的时候再给大家补充。

####reverse()
reverse()把整个Array的元素给掉个个，也就是反转：
```
var arr = ['one', 'two', 'three'];
arr.reverse(); 
arr; // ['three', 'two', 'one']
```