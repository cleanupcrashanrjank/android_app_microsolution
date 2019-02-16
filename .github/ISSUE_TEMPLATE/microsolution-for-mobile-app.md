---
name: MicroSolution for Mobile App
about: 帮助解决手机各类专项问题的微方案
title: '["stack_regex":"ObjectOutputStream","problem_type":"io_small_buffer"]'
labels: Janky and ANR（卡顿）
assignees: cleanupcrashanrjank

---

## description（解决方案描述）
通过xxxx, 减少或增加或优化xxxx，以提升xxxx，减少xxxxxx
eg: 通过配合BufferedOutputStream使用，减少用户态到内核态的切换次数，提升I/O读写效率

## verify（验证结果）
提供性能验证对比的数据，eg: 
| compare   |      ObjectOutputStream      |  ObjectOutputStream+ByteArrayOutputStream |
|----------|:-------------:|------:|
| I/O times（I/O次数） |  499 | 1 |
| I/O cost time（耗时） |    162.8   |   87.3 |

## code（代码）
优化后的代码
```java
ByteArrayOutputStream bos = null;
ObjectOutputStream oos = null;
FileOutputStream fos = null;
try{
    bos = new ByteArrayOutputStream(4096);
    oos = new ObjectOutputStream(bos);
    oos.writeObject();
    oos.flush();

    fos = new FileOutputStream(file);
    bos.writeTo(fos);
    bos.flush();
}
catch(Exception ex) {
    ex.printStack()
}
finally {
    if (oos != null) {
        oos.close();
    }
    if (bos != null) { 
        bos.close();
    }
    if (fos != null) {
        fos.close();
    }
}
```

### Optimized Library or Sample Project Links  (优化过的代码库或者样例项目的超链接）
- [xx代码库](http://write.blog.csdn.net/postlist)
- [xx代码库](http://write.blog.csdn.net/postlist)
