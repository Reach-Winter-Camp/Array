# 元组 Tuple 和数组 Array

## Tuples

```js
[ ]
[1, 2 + 3, 4 * 5]
```

元组(tuple)，写作`[ EXPR_0, ..., EXPR_n]`，是一个表达式，计算结果为 `n` 个值的元组，其中 `EXPR_0` 到 `EXPR_n` 是表达式。

`...expr` 可能出现在元组表达式中，在这种情况下，扩展表达式必须计算为一个被拼接到位的元组或数组。

## Arrays

```javascript
const x = arr(UInt, [1, 2, 3]);
```

相同的特定数值类型的元组(tuple)称为数组(array)。

## 元素参考

```js
arr[3]
```

一个写作`REF_EXPR[IDX_EXPR]`的引用，其中 `REF_EXPR` 是一个计算结果为数组、元组或结构的表达式，`IDX_EXPR` 是一个计算结果为小于数组大小的自然数的表达式，它选择数组给定索引处的元素。指数从零开始。

如果 `REF_EXPR` 是一个元组，那么 `IDX_EXPR` 必须是一个编译时常量，因为元组不支持动态访问，每个元素可能是不同的类型。

如果 `REF_EXPR` 是一个映射并且 `IDX_EXPR` 计算为一个地址，则此引用计算为 `Maybe(TYPE)` 类型的值，其中 `TYPE` 是映射的类型。

## 数组 & 元组的长度

### `Tuple.length, Array.length 和 .length`

```js
Tuple.length(tup);
tup.length;
Array.length(arr);
arr.length;
```

`Tuple.length`返回给定元组的长度。

`Array.length`返回给定数组的长度。

两者都可以缩写为 `expr.length` 其中 `expr` 为元组或数组。

## 数组 & 元组的更新

### `Tuple.set, Array.set 和 .set`

```js
Tuple.set(tup, idx, val);
tup.set(idx, val);
Array.set(arr, idx, val);
arr.set(idx, val);
```

`Tuple.set`返回一个与 `tup` 相同的新元组，除了索引 `idx` 处的值被替换为 `val`。 idx 必须是编译时常量，因为元组不支持动态访问，每个元素可能是不同的类型。

`Array.set`返回一个与 `arr` 相同的新数组，除了索引 `idx` 处被替换为 `val`。

两者都可以缩写为 `expr.set(idx, val)` 其中 `expr` 为元组或数组。

## 数组元素类型

### `Array.elemType` 和 `.elemType`

```js
Array.elemType(arr)
arr.elemType
```

`Array.elemType`返回数组包含的元素的类型

## 可折叠操作

以下方法可用于任何可折叠容器，例如：`Array`和`Map`。

### `Foldable.forEach` && `.forEach`

```js
c.forEach(f)
Foldable.forEach(c, f)
Array.forEach(c, f)
Map.forEach(c, f)
```

`Foldable.forEach(c, f)` 在容器 `c` 的元素上迭代函数 `f`，丢弃结果。这可以缩写为 `c.forEach(f)`。

### `Foldable.all` && `.all`

```js
Foldable.all(c, f)
Array.all(c, f)
Map.all(c, f)
c.all(f)
```

`Foldable.all(c, f)` 确定容器 `c` 的每个元素是否满足谓词 `f`。

### `Foldable.any && .any`

```js
Foldable.any(c, f)
Array.any(c, f)
Map.any(c, f)
c.any(f)
```

`Foldable.any(c, f)`确定容器的至少一个元素 `c` 是否满足断言 `f`.

### `Foldable.or && .or`

``` js
Foldable.or(c)
Array.or(c)
Map.or(c)
c.or()
```

`Foldable.or(c)` 返回布尔容器的析取.

### `Foldable.and && .and`

```js
Foldable.and(c)
Array.and(c)
Map.and(c)
c.and()
```

`Foldable.and(c)` 返回布尔容器的结合.

### `Foldable.includes && .includes`

```js
Foldable.includes(c, x)
Array.includes(c, x)
Map.includes(c, x)
c.includes(x)
```

`Foldable.includes(c, x)` 判断容器 `c` 是否包含元素 `x`. 

### `Foldable.count && .count`


```js
Foldable.count(c, f)
Array.count(c, f)
Map.count(c, f)
c.count(f)
```

`Foldable.count(c, f)` 返回容器 `c` 中满足断言 `f` 的元素数量.

### `Foldable.size && .size`


```js
Foldable.size(c)
Array.size(c)
Map.size(c)
c.size()
```

`Foldable.size(c)` 返回容器 `c` 中元素的数量.

### `Foldable.min && .min`


```js
Foldable.min(c)
Array.min(c)
Map.min(c)
c.min()
```

`Foldable.min(c)` 返回正整数容器中最小元素的值

### `Foldable.max && .max`


```js
Foldable.max(c)
Array.max(c)
Map.max(c)
c.max()
```

`Foldable.max(c)` 返回正整数容器中最大元素的值

### `Foldable.sum && .sum`


```js
Foldable.sum(c)
Array.sum(c)
Map.sum(c)
c.sum()
```

`Foldable.sum(c)` 返回正整数容器中所有元素的和.

### `Foldable.product && .product`


```js
Foldable.product(c)
Array.product(c)
Map.product(c)
c.product()
```

`Foldable.product(c)` 返回正整数容器中的产品

### `Foldable.average && .average`


```js
Foldable.average(c)
Array.average(c)
Map.average(c)
c.average()
```

`Foldable.average(c)` 返回一个正整数容器中的所有元素的平均值

## Array 组操作

Array 是一个可折叠容器. 除了可折叠方法之外，以下方法也可以用于Array. 

### `Array.iota`

```js
Array.iota(5)
```

`Array.iota(len)`  返回长度为 `len` 的数组，其中每个元素与其索引相同。例如，`Array.iota(4)` 返回 `[0,1,2,3]` .给定的 `len` 必须在编译时计算为整数.

### `Array.replicate`

```js
Array_replicate(5, "five")
Array_replicate(5, "five")
```

`Array.replicate(len, val)` 返回长度为 `len` 的数组，其中每个元素都是 `val`。例如，`array.replicate(4，“four”)` 返回 `[“four”、“four”、“four”、“four”]` .给定的 `len` 必须在编译时计算为整数.

### `Array.concat && .concat`


```js
Array.concat(x, y)
x.concat(y)
```

`Array.concat(x, y) ` 拼接两个数组 `x` 和 `y`，这可以缩写为 `x.concat(y)`.

### `Array.empty`

```js
Array_empty
Array.empty
```

`Array.empty` 是一个没有任何元素的数组 它是 `Array.concat` 的一个特征元素,也能够被写成 `Array_empty`

### `Array.zip && .zip`


```js
Array.zip(x, y)
x.zip(y)
```

`Array.zip(x, y)` 返回一个与 `x` 和 `y` 大小相同的新数组（必须大小相同），其元素是 `x` 和 `y` 元素的元组。可以缩写为 `x.zip(y)`.

### `Array.map && .map`


```js
Array.map(arr, f)
arr.map(f)
```

`Array.map(arr, f) ` 返回一个新数组，`arr_mapped`，大小与 `arr` 相同，其中 `arr_mapped[i]=f(arr[i])`表示所有 `i`。例如，`array.iota(4).map(x=>x+1)`返回 `[1,2,3,4]`。这可以缩写为 `arr.map(f)`。
此函数被推广到相同大小的任意数量的数组，这些数组在 `f` 参数之前提供。例如，`Array.iota(4).map(Array.iota(4)，add)` 返回 `[0,2,4,6]`.

### `Array.mapWithIndex && .mapWithIndex`


```js
Array.mapWithIndex(arr, f)
arr.mapWithIndex(f)
```

`Array.mapWithIndex(arr, f) ` 类似于 `Array.map`，但它为 `f` 提供了一个额外的参数，该参数是数组中当前元素的索引。映射时，该函数不能推广到任意数量的数组；它只接受一个数组。 

### `Array.forEachWithIndex && .forEachWithIndex`


```js
Array.forEachWithIndex(arr, f)
arr.forEachWithIndex(f)
```

`Array.forEachWithIndex(arr, f) ` 类似于 `Array.forEach`，但它为 `f` 提供了一个附加参数，它是数组中当前元素的索引。对于每一个数组，这个函数不能推广到任意数量的数组；它只接受一个数组。

### `Array.reduce && .reduce`


```js
Array.reduce(arr, z, f)
arr.reduce(z, f)
```

`Array.reduce(arr, z, f)` 返回函数 `f` 在给定数组上的左折叠，初始值为 `z`。. 例如, `Array.iota(4).reduce(0, add) ` 返回 `((0 + 1) + 2) + 3 = 6` .这可以缩写为 `arr.reduce(z, f)`. 
此函数被推广到任意数量的相同大小的数组，这些数组在 `z` 参数之前提供。例如, `Array.iota(4).reduce(Array.iota(4), 0, (x, y, z) => (z + x + y))`  返回 `((((0 + 0 + 0) + 1 + 1) + 2 + 2) + 3 + 3)`.

### `Array.reduceWithIndex && .reduceWithIndex`


```js
Array.reduceWithIndex(arr, z, f)
arr.reduceWithIndex(z, f)
```

`Array.reduceWithIndex(arr, z, f) ` 类似于 `Array.reduce` ，但它为 `f` 提供了一个额外的参数，即 `arr`中当前元素的索引。不像 `Array.reduce` 这个函数不能推广到任意数量的数组；它只接受一个数组。

### `Array.indexOf && .indexOf`


```js
Array.indexOf(arr, x)
arr.indexOf(x)
```

`Array.indexOf(arr, x) `返回给定数组中第一个等于 `x` 的元素的索引。返回值的类型为 `Maybe(UInt)`。如果数组中不存在该值，则不会返回任何值。

### `Array.findIndex && .findIndex`


```js
Array.findIndex(arr, f)
arr.findIndex(f)
```

`Array.findIndex(arr, f)` 返回给定数组中满足谓词 `f` 的第一个元素的索引。返回值的类型为 `Maybe(UInt)`。如果数组中没有满足谓词的值，则不返回任何值。

### `Array.find && .find`


```js
Array.find(arr, f)
arr.find(f)
```
`Array.find(arr, f) ` 返回数组中满足谓词 `f` 的第一个元素 `arr`。返回值的类型为 `Maybe` 。如果数组中没有满足谓词的值，则不返回任何值。 

### `Array.withIndex && .withIndex`


```js
Array.withIndex(arr)
arr.withIndex()
```

`Array.withIndex(arr)` 返回一个数组，其中 `arr` 的每个元素都与其索引配对.例如, `array(Bool, [false, true]).withIndex()` 返回 `array(Tuple(Bool, UInt), [[false, 0], [true, 1]])`. 

### `Array.slice && .slice`


```js
Array.slice(arr, start, length)
arr.slice(start, length)
```
`Array.slice(arr, start, length)` 返回 `arr` 的一部分，从 `start` 索引到 `start + length`。


