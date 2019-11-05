## Int

<!-- toc -->

### 持有引用

当把基础数据类型作为参数调用某方法，修改并不会修改原引用的值，如果希望修改原引用，则需要封装成对象之后传递给方法。

    // import org.apache.commons.lang3.mutable.MutableInt
    MutableInt i = new MutableInt();
    i.setValue(1);