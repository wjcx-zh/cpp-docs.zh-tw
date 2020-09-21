---
title: 編譯器錯誤 C2804
ms.date: 11/04/2016
f1_keywords:
- C2804
helpviewer_keywords:
- C2804
ms.assetid: b066e563-cca4-450c-8ba7-3b0d7a89f3ea
ms.openlocfilehash: bdd1b4155d30dd2513d87ac217ca20ca7baabd8a
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743161"
---
# <a name="compiler-error-c2804"></a>編譯器錯誤 C2804

二元運算子 'operator operator' 的參數太多

多載的二元運算子成員函式會使用多個參數宣告。 二元運算子成員函式的第一個運算元參數 (其類型是運算子的封閉式類型) 為隱含。

## <a name="examples"></a>範例

下列範例會產生 C2804，並示範如何修正此問題。

```cpp
// C2804.cpp
// compile by using: cl /c /W4 C2804.cpp
class X {
public:
   X& operator+= (const X &left, const X &right);   // C2804
   X& operator+= (const X &right);   // OK - left operand implicitly *this
};

int main() {
   X x, y;
   x += y;   // equivalent to x.operator+=(y)
}
```

下列範例會產生 C2804，並示範如何修正此問題。

```cpp
// C2804_2.cpp
// compile with: /clr /c
ref struct Y {
   Y^ operator +(Y^ hY, int i);   // C2804
   static Y^ operator +(Y^ hY, int i);   // OK
   Y^ operator +(int i);   // OK
};
```
