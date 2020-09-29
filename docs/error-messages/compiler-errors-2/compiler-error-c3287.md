---
title: 編譯器錯誤 C3287
description: 描述 Microsoft c + + 編譯器錯誤 C3287。
ms.date: 09/25/2020
f1_keywords:
- C3287
helpviewer_keywords:
- C3287
ms.assetid: c1fa73d2-2c82-4136-a7da-0e75e3b420ad
ms.openlocfilehash: 4067355ef1bc1992d0f8519656bcd1063179aef4
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2020
ms.locfileid: "91414316"
---
# <a name="compiler-error-c3287"></a>編譯器錯誤 C3287

> 類型 '*type*' (GetEnumerator) 的傳回型別必須有適合的公用 MoveNext 成員函式和公用 Current 屬性

## <a name="remarks"></a>備註

使用者定義的集合類別必須包含 `MoveNext` 和 `Current`的定義。

如需詳細資訊，請參閱 [中的](../../dotnet/for-each-in.md)。

## <a name="example"></a>範例

下列範例會產生 C3287。

```cpp
// C3287.cpp
// compile with: /clr
using namespace System;

ref struct R {
   bool MoveNext() {
      return true;
   }
   property Object^ Current {
      Object^ get() {
         Object ^ o = gcnew Object;
         return o;
      }
   }
};

ref struct R2 {
   R ^GetEnumerator() {
      R^ r = gcnew R;
      return r;
   }
};

ref struct T {};

ref struct T2 {
   T ^GetEnumerator() {
      T^ t = gcnew T;
      return t;
   }
};

int main() {
   for each (int i in gcnew T2) {}   // C3287
   for each (int i in gcnew R2) {}   // OK
}
```
