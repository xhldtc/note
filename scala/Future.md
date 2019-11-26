##方法使用

###onComplete
future执行完之后调用回调方法，无论成功或者抛异常，都会调用

###foreach
future执行成功之后调用回调方法，没结束或者抛异常则回调方法不会被调用，执行完之后future里的值会被丢弃

###transform
接收两个函数，成功后变换，或者抛异常后做变换，异常必须仍变换为异常

###transform
接收Try到Try的映射，做变换

###transformWith
接收Try到Future的映射，做变换

