## Boolean

<!-- toc -->

### 持有引用

当把基础数据类型作为参数调用某方法，修改并不会修改原引用的值，如果希望修改原引用，则需要封装成对象之后传递给方法。

    // import org.apache.commons.lang3.mutable
    MutableBoolean sth = new MutableBoolean(true);
    sth.setValue(false);
    sth.setTrue();

### OrAndXor

`MutableBoolean`封装有点美中不足的是，没有提供`or`/`and`等方法，这些小工具在某些场景下还是很实用的，目前可以使用下面的工具方法替代，但还是不如集成到`MutableBoolean`简洁，某些语言中就直接集成到了bool型里：

    // import org.apache.commons.lang3.BooleanUtils
    BooleanUtils.or(b1, b2);
    BooleanUtils.xor(b1, b2);
    BooleanUtils.and(b1, b2);

### toString

如果希望布尔型变量能够输出成true/false之外的字符串，可以：

    // import org.apache.commons.lang3.BooleanUtils
    BooleanUtils.toStringTrueFalse(b);          // = true / false
    BooleanUtils.toStringOnOff(b);              // = on / off
    BooleanUtils.toStringYesNo(b);              // = yes / no
    BooleanUtils.toString(b, "right", "wrong"); // = right / wrong
