# Runtime 类的 gc() 和 runFinalization() 方法

---

## gc()
gc()是垃圾回收器，它在回收废弃对象时，会调用将要回收对象的 finalize() 方法

-

## runFinalization()
runFinalization() 方法，只是运行 finalize() 方法