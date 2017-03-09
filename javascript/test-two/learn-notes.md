###JS中的二维数组
######1.二维数组的本质：数组中的元素又是数组
######2.二维数组的初始化
```
var arr = [[1,2],[a,b]];
  alert(arr[1][0]); //a 第2列第1行所在的元素
```
或<br>
```
var arr = new array(new array(1,2),new array("a","b"));
alert(arr[1][0]);
```
###JavaScript中数组排序方法
######1.sort()方法使用
sort方法并不像我们想的那么容易使用，不是单纯的arr.sort()就行了，需要我们定义里面的回调函数！因为sort()方法默认情况下按照升序排列数组项，sort()方法会调用toString()转型方法，然后比较得到的字符串，即使我们比较的是数字，他也会把数字转为字符串以后再排序。<br><br>对一维数组进行排序<br><br>
```
var arr1 = [0, 1, 3, 10, 16, 5, 9, 0, 3];
console.log(arr1.sort()) //很明显，这样不是我们要的结果，[ 0, 0, 1, 10, 16, 3, 3, 5, 9 ]

//传入自定义回调函数之后
function ascend(a,b){
    return a-b;
}
//降序排列
function descend(a,b){
    return b-a;
}
console.log(arr1.sort(ascend));     //[ 0, 0, 1, 10, 16, 3, 3, 5, 9 ]
console.log(arr1.sort(descend));    //[ 16, 10, 9, 5, 3, 3, 1, 0, 0 ]
```
对二维数组进行排序<br><br>

```
var arr1 = [[4,5,7],[11,3,6,100,77],[12,9,12,10],[3,1,2,99,22]];
function ascend(x,y){
    return x[3] - y[3];  //按照数组的第4个值升序排列
}
function descend(x,y){
    return y[0] - x[0];  //按照数组的第1个值降序排列
}
console.log(arr1.sort(ascend));
console.log(arr1.sort(descend));
```
######2.reverse()方法
reverse方法会反转数组项的顺序，请看如下示例：<br><br>
```
var arr1 = [0, 1, 3, 10, 16, 5, 9, 0, 3];
console.log(arr1.reverse());//[ 3, 0, 9, 5, 16, 10, 3, 1, 0 ]
```
