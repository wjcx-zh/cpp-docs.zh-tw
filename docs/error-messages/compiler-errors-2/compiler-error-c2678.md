---
title: 編譯器錯誤 C2678
ms.date: 11/04/2016
f1_keywords:
- C2678
helpviewer_keywords:
- C2678
ms.assetid: 1f0a4e26-b429-44f5-9f94-cb66441220c8
ms.openlocfilehash: c8f5b06e6c2f9966d714f4a360525617dbff400f
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90743174"
---
# <a name="compiler-error-c2678"></a>編譯器錯誤 C2678

二元 'operator'：未定義使用左方運算元類型 'type' 的運算子 (或是沒有可接受的轉換)

若要使用運算子，您必須針對指定類型進行多載，或針對已定義運算子的類型定義轉換。

當左方運算元是 const 限定，而運算子定義成採用非 const 引數時，可能會發生 C2678。

## <a name="examples"></a>範例

下列範例會產生 C2678，並示範如何修正此問題：

```cpp
// C2678a.cpp
// Compile by using: cl /EHsc /W4 C2678a.cpp
struct Combo {
   int number;
   char letter;
};

inline Combo& operator+=(Combo& lhs, int rhs) {
   lhs.number += rhs;
   return lhs;
}

int main() {
   Combo const combo1{ 42, 'X' };
   Combo combo2{ 13, 'Z' };

   combo1 += 6; // C2678
   combo2 += 9; // OK - operator+= matches non-const Combo
}
```

如果您沒有先 pin 原生成員，就在其上呼叫成員函式，也可能會發生 C2678。

下列範例會產生 C2678，並示範如何修正此問題。

```cpp
// C2678.cpp
// compile with: /clr /c
struct S { int _a; };

ref class C {
public:
   void M( S param ) {
      test = param;   // C2678

      // OK
      pin_ptr<S> ptest = &test;
      *ptest = param;
   }
   S test;
};
```
