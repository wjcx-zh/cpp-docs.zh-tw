---
title: 編譯器錯誤 C3287
ms.date: 11/04/2016
f1_keywords:
- C3287
helpviewer_keywords:
- C3287
ms.assetid: c1fa73d2-2c82-4136-a7da-0e75e3b420ad
ms.openlocfilehash: ab0b93aa1a74ea79515e24ef2b1e289cf0227dac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222673"
---
# <a name="compiler-error-c3287"></a>編譯器錯誤 C3287

類型 'type' (GetEnumerator 的傳回類型) 必須有適合的公用 MoveNext 成員函式和公用 Current 屬性

使用者定義的集合類別必須包含 `MoveNext` 和 `Current`的定義。

請參閱[如何：反覆運算 Over a User-Defined 集合與每個](../../dotnet/how-to-iterate-over-a-user-defined-collection-with-for-each.md)如需詳細資訊。

## <a name="example"></a>範例

下列範例會產生 C3287。

```
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