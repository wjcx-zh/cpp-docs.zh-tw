---
title: 編譯器警告 (層級 4) C4239
ms.date: 11/04/2016
f1_keywords:
- C4239
helpviewer_keywords:
- C4239
ms.assetid: a23dc16a-649e-4870-9a24-275de1584fcd
ms.openlocfilehash: 25b97cfb50847a0929f3d3a97b822209e6a11900
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2020
ms.locfileid: "90686674"
---
# <a name="compiler-warning-level-4-c4239"></a>編譯器警告 (層級 4) C4239

使用非標準的擴充： ' token '：從 ' type ' 轉換成 ' type '

C + + 標準不允許此類型轉換，但在此允許為延伸模組。 這個警告後面一律會接著至少一行說明，描述違反的語言規則。

## <a name="examples"></a>範例

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
