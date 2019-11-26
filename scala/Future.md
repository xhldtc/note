## 方法使用

### onComplete
future执行完之后调用回调方法，无论成功或者抛异常，都会调用

### foreach
future执行成功之后调用回调方法，没结束或者抛异常则回调方法不会被调用，执行完之后future里的值会被丢弃

### transform
接收两个函数，成功后变换，或者抛异常后做变换，异常必须仍变换为异常

### transform
接收Try到Try的映射，做变换

### transformWith
接收Try到Future的映射，做变换

### map
常规类型的映射变换

### flatMap
常规类型到future类型的变换

### flatten
将多层嵌套的future拍平成一个future

### filter
将过滤条件应用到future内的元素，如果true就返回原来的元素，false会抛异常

### withFilter
同filter方法

### collect
应用一个偏函数，如果匹配了偏函数的条件，就做变换，匹配不上就抛异常

### recover
偏函数，将匹配到的异常做常规元素转换，没匹配上或者是成功的future就原样返回

### recoverWith
与recover类似，只不过变换成future

### zip
将另一个future进行组合，返回一个包含二元组的future

### zipWith
二元组到一个结果的常规映射变换

### fallbackTo
如果this future是成功的，就原样返回，如果this失败但是that成功，就返回that的future，如果两个都失败就返回this抛出的异常

### mapTo
TODO

### andThen
应用一个偏函数，如果匹配上就执行。注意如果中间的andThen调用抛异常了，后面的andThen会使用原future的值做入参，所以这个方法会吞掉异常

