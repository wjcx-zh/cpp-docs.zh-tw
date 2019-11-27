---
title: 編譯器警告 (層級 4) C4239
ms.date: 11/04/2016
f1_keywords:
- C4239
helpviewer_keywords:
- C4239
ms.assetid: a23dc16a-649e-4870-9a24-275de1584fcd
ms.openlocfilehash: fcb66fca7e5b8708171849f885518c15b8355ac4
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541739"
---
# <a name="compiler-warning-level-4-c4239"></a>編譯器警告 (層級 4) C4239

使用非標準的擴充： ' token '：從 ' type ' 轉換成 ' type '

C++標準不允許這種類型轉換，但在這裡允許它做為擴充功能。 這個警告後面一律至少有一行說明，描述違反的語言規則。

## <a name="example"></a>範例

下列範例會產生 C4239。

```cpp
// C4239.cpp
// compile with: /W4 /c
struct C {
   C() {}
};

void func(void) {
   C & rC = C();   // C4239
   const C & rC2 = C();   // OK
   rC2;
}
```

## <a name="example"></a>範例

不允許從整數類資料類型轉換為列舉類型。

下列範例會產生 C4239。

```cpp
// C4239b.cpp
// compile with: /W4 /c
enum E { value };
struct S {
   E e : 2;
} s = { 5 };   // C4239
// try the following line instead
// } s = { (E)5 };
```