## Map的创建

<!-- toc -->

### 用KV对创建

Map的创建本身很简单，new一个实例化对象就可以，但是如果想在创建的时候填充KV对，就会比较麻烦，尤其是在定义静态全局变量的时候，如果不用工具，需要（`Java8`及以下）：

    // Java9以后请直接用Map.of(...)
    private static Map<K, V> map = new HashMap<>();
    static {
        map.put(k1, v1);
    }

如果初始化的KV对在5对以下，使用`guava`中的：

    // import com.google.common.collect.ImmutableMap
    private static Map<K, V> map = ImmutableMap.of(k1, k1);

如果kv对在6对以上，使用：

    // import com.google.common.collect.ImmutableMap
    private static Map<K, V> map = ImmutableMap.<K, V>builder()
        .put(k1, v1)
        .put(k2, v2)
        // ... 
        .put(kn, vn)
        .build();

但是注意，这样创建的Map是不能修改的Map，如果想要修改，需要在完成套上`new XxxMap<>(...)`。

如果项目已经升级到`Java9`，这个事情就更简单，10对KV以下都可以直接使用：

    private static Map<K, V> map = Map.of(k1, k1);

