---
title: 編譯器錯誤 C2597
ms.date: 11/04/2016
f1_keywords:
- C2597
helpviewer_keywords:
- C2597
ms.assetid: 2e48127d-e3ff-4a40-8156-2863e45b1a38
ms.openlocfilehash: 680268948f8642b02768bd4b3092666982e14eb7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759304"
---
# <a name="compiler-error-c2597"></a>編譯器錯誤 C2597

參考非靜態成員 'identifier' 是不合法的

可能的原因:

1. 非靜態成員是在靜態成員函式中指定。 若要存取非靜態成員，您必須傳入或建立類別的本機執行個體，並使用成員存取運算子 (`.` 或 `->`)。

1. 指定的識別項不是類別、結構或等位的成員。 請檢查識別項拼寫。

1. 成員存取運算子是指非成員函式。

1. 下列範例會產生 C2597，並示範如何修正此問題：

```cpp
// C2597.cpp
// compile with: /c
struct s1 {
   static void func();
   static void func2(s1&);
   int i;
};

void s1::func() {
   i = 1;    // C2597 - static function can't access non-static data member
}

// OK - fix by passing an instance of s1
void s1::func2(s1& a) {
   a.i = 1;
}
```
