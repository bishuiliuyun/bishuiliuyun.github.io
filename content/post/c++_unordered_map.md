---
title: "C++ unordered_map使用示例"
date: 2020-03-01T14:28:38+08:00
draft: true
---

# unordered_map

这是一个简单的测试例子，仅仅用于测试博客的样式
```cpp
#include <string.h>
#include <iostream>
#include <unordered_map>
#define INT 128
#define MAX 256

struct Test {
    Test() : a(0), b(1), c(2) { }
    int a;
    int b;
    int c;
};

int main() {
    std::unordered_map<int, Test*> map;
    for (int i = 0; i < 16; ++i) {
        Test *ptr = new Test();
        map.insert(std::pair<int, Test*>(i, ptr));
    }

    std::unordered_map<int, Test*>::iterator it;
    it = map.find(1);
    char buf[12] = {0};
    if (it != map.end()) {
        memcpy(it->second, buf, sizeof(buf));
        std::cout << "bad memcpy" << std::endl;
    }

    for (it = map.begin(); it != map.end(); ++it) {
        std::cout << "iterator: " << it->first << std::endl;
    }

    for (int i = 0; i < 16; ++i) {
        it = map.find(i);
        if (it != map.end()) {
            std::cout << "find " << i << std::endl;
        }
    }

    map.insert(std::pair<int, Test*>(1, NULL));
    return 0;
}
```
