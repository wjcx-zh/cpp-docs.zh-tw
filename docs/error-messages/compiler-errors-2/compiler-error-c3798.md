---
title: 編譯器錯誤 C3798
ms.date: 11/04/2016
f1_keywords:
- C3798
helpviewer_keywords:
- C3798
ms.assetid: b2f8b1d8-8812-49b8-a346-28e48f02ba5c
ms.openlocfilehash: 52900a662211609e1e7adeb7cb493cf2d72ab846
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548261"
---
# <a name="compiler-error-c3798"></a>編譯器錯誤 C3798

'specifier': 屬性宣告不能有覆寫規範 （應該置於屬性 get/set 方法）

屬性宣告不正確。 如需詳細資訊，請參閱

- [屬性](../../windows/property-cpp-component-extensions.md)

- [abstract](../../windows/abstract-cpp-component-extensions.md)

- [sealed](../../windows/sealed-cpp-component-extensions.md)

## <a name="example"></a>範例

下列範例會產生 C3798

```
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