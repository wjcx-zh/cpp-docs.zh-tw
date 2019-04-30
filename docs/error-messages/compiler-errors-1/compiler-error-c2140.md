---
title: 編譯器錯誤 C2140
ms.date: 11/04/2016
f1_keywords:
- C2140
helpviewer_keywords:
- C2140
ms.assetid: d44a0500-002c-4632-9e5e-c71c3a473ec4
ms.openlocfilehash: 35b6e38290acddb41bdf53d9663a058259300ee8
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345685"
---
# <a name="compiler-error-c2140"></a>編譯器錯誤 C2140

'type': 相依於泛型類型參數的類型不允許做為編譯器內建類型特性 '特性' 引數

無效的類型規範已傳遞給類型特性。

如需詳細資訊，請參閱 <<c0> [ 類型特性的編譯器支援](../../extensions/compiler-support-for-type-traits-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C2140。

```
// C2140.cpp
// compile with: /clr /c
template <class T>

struct is_polymorphic {
   static const bool value = __is_polymorphic(T);
};

class x {};

generic <class T>
ref class C {
   void f() {
      System::Console::WriteLine(__is_polymorphic(T));   // C2140
      System::Console::WriteLine(is_polymorphic<T>::value);   // C2140

      System::Console::WriteLine(__is_polymorphic(x));   // OK
      System::Console::WriteLine(is_polymorphic<x>::value);   // OK
   }
};
```