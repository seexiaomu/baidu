##JS事件：target和currentTarget区别
> target在事件流的目标阶段；currentTarget在事件流的捕获，目标及冒泡阶段。只有当事件流处在目标阶段的时候，两个的指向才是一样的， 而当处于捕获和冒泡阶段的时候，target指向被单击的对象而currentTarget指向当前事件活动的对象（一般为父级）。

##js节点操作
####1.生成节点
> document.createElement(eName);  //创建一个节点

> document.createAttribute(attrName); //对某个节点创建属性

> document.createTextNode(text);  //创建文本节点

####2.添加节点
> document.insertBefore(newNode,referenceChild);  //在某个节点前插入节点<br>

> parentNode.appendChild(newNode);//给某个节点添加子节点

####3.复制节点
> cloneNode(true | false);

> 复制某个节点

> 参数：是否复制原节点的所有属性

####4.删除节点
> parentNode.removeChild(node)

> 删除某个节点的子节点

> node是要删除的节点

> ######注意：IE会忽略节点间生成的空白文本节点(例如，换行符号)，而Mozilla不会这样做。在删除指定节点的时候不会出错，但是如果要删除最后一个子结点或者是第一个子结点的时候，就会出现问题。这时候，就需要用一个函数来判断首个子结点的节点类型。
元素节点的节点类型是 1，因此如果首个子节点不是一个元素节点，它就会移至下一个节点，然后继续检查此节点是否为元素节点。整个过程会一直持续到首个元素子节点被找到为止。通过这个方法，我们就可以在 Internet Explorer 和 Mozilla 得到正确的方法。

####5.修改文本节点
> appendData(data);//
将data加到文本节点后面

> deleteData(start,length);//
将从start处删除length个字符

> insertData(start,data)//
在start处插入字符,start的开始值是0;

> replaceData(start,length,data)//
在start处用data替换length个字符

> splitData(offset)//
在offset处分割文本节点

> substringData(start,length)//
从start处提取length个字符

####6.属性操作
> getAttribute(name)//
通过属性名称获取某个节点属性的值

> setAttribute(name,value);//
修改某个节点属性的值

> removeAttribute(name)//
删除某个属性

####7.查找节点
> parentObj.firstChild
> 如果节点为已知节点的第一个子节点就可以使用这个方法。此方法可以递归进行使用
> parentObj.firstChild.firstChild.....

> parentObj.lastChild
> 获得一个节点的最后一个节点，与firstChild一样也可以进行递归使用
> parentObj.lastChild.lastChild.....

> parentObj.childNodes
> 获得节点的所有子节点，然后通过循环和索引找到目标节点

####8.获取相邻的节点
> neborNode.previousSibling :获取已知节点的相邻的上一个节点
> nerbourNode.nextSlbling: 获取已知节点的下一个节点

####9.获取父节点
> childNode.parentNode:得到已知节点的父节点

####10.替换节点 方法replace(new,old)

##js事件监听器用法实例详解

######1、当同一个对象使用.onclick的写法触发多个方法的时候，后一个方法会把前一个方法覆盖掉，也就是说，在对象的onclick事件发生时，只会执行最后绑定的方法。而用事件监听则不会有覆盖的现象，每个绑定的事件都会被执行。如下：

```
window.onload = function(){ 
 var btn = document.getElementById("yuanEvent"); 
 btn.onclick = function(){ 
  alert("第一个事件"); 
 } 
 btn.onclick = function(){ 
  alert("第二个事件"); 
 } 
 btn.onclick = function(){ 
  alert("第三个事件"); 
 } 
}
```
######最后只输出：第三个事件，因为后一个方法都把前一个方法覆盖掉了。

######原生态的事件绑定函数addEventListener：

```
var eventOne = function(){ 
 alert("第一个监听事件"); 
} 
function eventTwo(){ 
 alert("第二个监听事件"); 
} 
window.onload = function(){ 
 var btn = document.getElementById("yuanEvent"); 
 //addEventListener：绑定函数 
 btn.addEventListener("click",eventOne); 
 btn.addEventListener("click",eventTwo); 
}
```

######2、采用事件监听给对象绑定方法后，可以解除相应的绑定，写法如下：

```
var eventOne = function(){ 
 alert("第一个监听事件"); 
} 
function eventTwo(){ 
 alert("第二个监听事件"); 
} 
window.onload = function(){ 
 var btn = document.getElementById("yuanEvent"); 
 btn.addEventListener("click",eventOne); 
 btn.addEventListener("click",eventTwo); 
 btn.removeEventListener("click",eventOne); 
}
```

######输出：第二个监听事件

######3、解除绑定事件的时候一定要用函数的句柄，把整个函数写上是无法解除绑定的。
######错误写法：
```
btn.addEventListener("click",function(){ 
 alert(11); 
}); 
btn.removeEventListener("click",function(){ 
 alert(11); 
});
```
######正确写法：
```
btn.addEventListener("click",eventTwo); 
btn.removeEventListener("click",eventOne); 
```
