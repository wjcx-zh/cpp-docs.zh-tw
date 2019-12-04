---
title: 編譯器錯誤 C3114
ms.date: 11/04/2016
f1_keywords:
- C3114
helpviewer_keywords:
- C3114
ms.assetid: b5d2df4f-87d0-4292-9981-25c6a6013c05
ms.openlocfilehash: 6f548c72a0e95c533ed711fe9f2583a7abd6c500
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760757"
---
# <a name="compiler-error-c3114"></a>編譯器錯誤 C3114

' argument '：不是有效的命名屬性引數

為了讓屬性類別資料成員成為有效的具名引數，它不得標記 `static`、`const`或 `literal`。 如果屬性，則屬性不得為 `static`，而且必須具有 get 和 set 存取子。

如需詳細資訊，請參閱[屬性](../../extensions/property-cpp-component-extensions.md)和[使用者定義屬性](../../extensions/user-defined-attributes-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3114。

```cpp
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
