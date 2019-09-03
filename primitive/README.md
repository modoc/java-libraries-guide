## 基础数据类型

个人比较希望有但目前没有找到的方法：

1. String to 基础类型

    例如：

        Boolean.valueOf(String.valueOf(o));
        Integer.valueOf(String.valueOf(o));

    如果可以使用下面的语句完成就更完美了：

        BooleanUtils.valueOf(obj);
        IntegerUtils.valueOf(obj);