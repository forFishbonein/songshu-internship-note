### **vue数组双向绑定问题及$set用法**

在vue开发中，我们有时会遇到数据更新视图不更新问题，**对象的地址没有改变，vue就监测不到数据变化**。这个时候，双向绑定就失效了。

**以下这几种情况,Vue都会检测不到数据的变化**

1.当你利用索引直接设置一个数组项时，例如：vm.items[indexOfItem] = newValue （vm 就是 this，即 vue 对象）

2.当你直接修改数组的长度时，例如：vm.items.length = newLength

3.当你进行对象属性的添加或删除时，由于 JavaScript 的限制，Vue不能检测对象属性的添加或删除，例如：obj[a] = “123”;

**正常情况下数组是完全可以响应式的：**

> **数组实现响应式的七个方法**

为什么这些方法可以？因为Vue对这几个数组的方法进行了劫持（即通过修改原生的数组方法来实现），也就是 vue 默认用这几个函数修改数组是可以检测变化的。

- push() 可向数组的末尾添加一个或多个元素，并返回新的长度
- pop() 从数组的尾部删除一个元素，返回删除的元素
- unshift() 向数组的前面添加元素，返回值：数组的新长度
- shift() 从数组头部删除一个元素，返回删除的元素
- splice()截取数组的一部分，或者增删改查都可以

删除：两个参数，splice(index,num) 删除的第一项的位置以及要删除的项数

添加：三个参数，插入起始位置、删除的项数（为0）、插入的项，向指定位置插入任意数量的项。arr.splice(1,0,"or","ue")

替换：先删除再添加，三个参数：起始位置、删除的项数、要添加的项数。添加的与删除的数量不一定要一致。arr.splice(1,2,"or","ue")

- sort() 对数组元素进行排序，默认根据字符串Unicode码进行排序，对数字进行排序时参数要传递一个比较函数。

```
sortNumber(a,b){
	return a-b
}；
```

- reverse() 该方法用于颠倒数组中元素的顺序

上面的方法把原数组更改掉，可以选用这些方法来实现响应式。

flter()、concat() 和 slice()。它们不会变更原始数组，而总是返回一个新数组。使用这些方法会造成数据双向绑定失效。

- filter() 创建一个新的数组，新数组中的元素是通过检查指定数组中符合条件的所有元素。
- concat() 用于连接两个或多个数组。该方法不会改变现有的数组.
- slice() 可从已有的数组中返回选定的元素,选择从给定的 start 参数开始的元素，并在给定的 end 参数处结束，但不包括。该方法并不会修改数组，而是返回一个子数组.

**$set的用法**

this.$set(原数组, 索引值, 需要赋的值)

> vue中$set解决数据响应式失效：即vue中`$set`的使用场景

当你利用索引直接设置一个项时（通过下标修改数组），例如：vm.items[indexOfItem] = newValue;

当你给对象新增一个属性时，例如：obj[a] = “123”;

解决：用$set方法

```js
this.$set(Object, key, value)
//this.$set(this.list[i],"flag",true)
```

当你修改数组的长度时，例如：vm.items.length = newLength

解决：vm.items.splice(newLength)