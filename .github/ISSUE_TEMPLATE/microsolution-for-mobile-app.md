---
name: MicroSolution for Mobile App
about: 帮助解决手机各类专项问题的微方案
title: "[key_feature]"
labels: Janky and ANR（卡顿）
assignees: cleanupcrashanrjank

---

## feature（特征）: 
["stack_regex":"ObjectOutputStream","problem_type":"io_small_buffer"]

## description（解决方案描述）
配合BufferedOutputStream使用

## verify（验证结果）
| compare   |      ObjectOutputStream      |  ObjectOutputStream+ByteArrayOutputStream |
|----------|:-------------:|------:|
| I/O times（I/O次数） |  499 | 1 |
| I/O cost time（耗时） |    162.8   |   87.3 |

## code（代码）
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
