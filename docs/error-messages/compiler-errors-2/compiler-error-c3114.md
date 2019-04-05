---
title: 編譯器錯誤 C3114
ms.date: 11/04/2016
f1_keywords:
- C3114
helpviewer_keywords:
- C3114
ms.assetid: b5d2df4f-87d0-4292-9981-25c6a6013c05
ms.openlocfilehash: c5a4feae5c8805a27c020b532fd58e0562e46b6b
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "58773771"
---
# <a name="compiler-error-c3114"></a>編譯器錯誤 C3114

'argument': 不是有效的具名屬性引數

為了讓屬性類別資料成員是有效的具名引數，它不能標示`static`， `const`，或`literal`。 如果屬性，屬性不得為`static`和必須有 get 和 set 存取子。

如需詳細資訊，請參閱 <<c0> [ 屬性](../../extensions/property-cpp-component-extensions.md)並[User-Defined Attributes](../../extensions/user-defined-attributes-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3114。

```
// C3114.cpp
// compile with: /clr /c
public ref class A : System::Attribute {
public:
   static property int StaticProp {
      int get();
   }

   property int Prop2 {
      int get();
      void set(int i);
   }
};

[A(StaticProp=123)]   // C3114
public ref class R {};

[A(Prop2=123)]   // OK
public ref class S {};
```