## Iterable到Iterable

<!-- toc -->

### List[F]转化为List[T]

在`Apache Commons`包里面似乎不支持这种不同类型间转化的语义，而`Guava`中进行这种操作的语义叫做`transform`：

    // import com.google.common.collect.Lists
    List<String> list = Lists.newArrayList("abc", "edf", "afr");
    List<Character> characters = Lists.transform(list, s -> s.charAt(0));
    // characters = [a, e, a]

### List[E]过滤为List[E]

诡异的是，无论`commons-collections4`还是`guava`，都没有提供List的filter方法，当然也可以通过`guava`的`Collections2`间接实现：

    // import com.google.common.collect.Collections2
    List<String> list = Lists.newArrayList("abc", "edf", "afr");
    List<String> characters = new ArrayList<>(Collections2.filter(list, s -> s.startsWith("a")));
    // characters = [abc, afr]

### Set[F]转化为Set[T]

或许因为Set转化之后目标集合和原集合不一定一一对应，`Guava`没有为Set提供`transform`方法，但是可以通过`Collections2`间接实现：

    // import com.google.common.collect.Collections2
    Set<String> set = Sets.newHashSet("abc", "edf", "afr");
    Set<Character> characters = new HashSet<>(Collections2.transform(set, s -> s.charAt(0)));
    // characters = [a, e]

### Set[E]过滤为Set[E]

    // import com.google.common.collect.Sets
    Set<String> set = Sets.newHashSet("abc", "edf", "afr");
    Set<String> characters = Sets.filter(set, s -> s.startsWith("a"));
    // characters = [abc, afr]




