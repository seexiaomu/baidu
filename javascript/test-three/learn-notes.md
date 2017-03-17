## js二维数组定义和初始化的三种方法总结
##### 方法一：直接定义并且初始化，这种遇到数量少的情况可以用
```
var _TheArray = [["0-1","0-2"],["1-1","1-2"],["2-1","2-2"]]
```
##### 方法二：未知长度的二维数组
```
var tArray = new Array();  //先声明一维
for(var k=0;k<i;k++){    //一维长度为i,i为变量，可以根据实际情况改变
 
tArray[k]=new Array();  //声明二维，每一个一维数组里面的一个元素都是一个数组；
 
for(var j=0;j<p;j++){   //一维数组里面每个元素数组可以包含的数量p，p也是一个变量；
 
tArray[k][j]="";    //这里将变量初始化，我这边统一初始化为空，后面在用所需的值覆盖里面的值
 }
}
```
## 将两个一维数组合并成一个二维数组
```
var array1 = ["one","two","three"];
var array2 = ["1","2","3"];
var arr=[];
array1.forEach((currentValue,index)=>arr.push([currentValue,array2[index]]));
```
传统一点：
```
var array1 = ["one","two","three"];
var array2 = ["1","2","3"];
var arrayAll=[];
for(let i=0;i<array1.length;i++){

arrayAll.push([array1[i],array2[i]])

}
```
## JS数组的push与concat区别
##### push() 方法可向数组的末尾添加一个或多个元素，并返回新的长度。
```
var a = [1,2,3,4];
a.push(5);  //a 现在是1,2,3,4,5
```
##### concat() 方法用于连接两个或多个数组。该方法不会改变现有的数组，而仅仅会返回被连接数组的一个副本。
```
var a = [1,2,3,4];
var b = [5,6];
var c = a.concat(b); // a,b 数组都不变，c变成了1,2,3,4,5,6
```
