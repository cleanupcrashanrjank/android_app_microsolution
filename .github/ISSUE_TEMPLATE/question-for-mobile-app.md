---
name: Question for Mobile App
about: 手机App各类专项问题
title: Note：复制剪贴板中的【生成标题】作为标题，【生成Labels】作为Labels
labels: ''
assignees: cleanupcrashanrjank

---

## 生成标题
【Buffer too small】call java.io.FileOutputStream on x device

## 影响范围
- 项目：手Q、音乐等X个项目
- 人数：1千万
- 时间：3个月

## 生成Labels
Disk（磁盘）

## stack feature（堆栈特征）
隐藏应用堆栈剩余的stack
eg：
```
java.lang.Thread.getStackTrace(Thread.java:1565)
    |-java.io.FileOutputStream.open(Native Method)
        |-java.io.FileOutputStream.(FileOutputStream.java:221)
            |-java.io.FileWriter.(FileWriter.java:107)
                [隐藏应用堆栈]
```
## Environment（环境特征）
- Device：CUN-AL00 （80%）
- System：5.1 （80%）
