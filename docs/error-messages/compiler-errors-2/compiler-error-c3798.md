---
title: 編譯器錯誤 C3798
ms.date: 11/04/2016
f1_keywords:
- C3798
helpviewer_keywords:
- C3798
ms.assetid: b2f8b1d8-8812-49b8-a346-28e48f02ba5c
ms.openlocfilehash: cc21f0bdcc8e2171dd0c87fc31396e6caab9e6fc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755313"
---
# <a name="compiler-error-c3798"></a>編譯器錯誤 C3798

' 規範 '：屬性宣告不能有覆寫規範（應該放在屬性 get/set 方法上）

屬性宣告不正確。 如需詳細資訊，請參閱

- [屬性](../../extensions/property-cpp-component-extensions.md)

- [abstract](../../extensions/abstract-cpp-component-extensions.md)

- [sealed](../../extensions/sealed-cpp-component-extensions.md)

## <a name="example"></a>範例

下列範例會產生 C3798

```cpp
// C3798.cpp
// compile with: /clr /c
ref struct A {
   property int Prop_1 abstract;   // C3798
   property int Prop_2 sealed;   // C3798

   // OK
   property int Prop_3 {
      virtual int get() abstract;
      virtual void set(int i) abstract;
   }

   property int Prop_4 {
      virtual int get() sealed;
      virtual void set(int i) sealed;
   }
};
```
