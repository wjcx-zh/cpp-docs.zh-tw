---
title: 編譯器錯誤 C3290
ms.date: 11/04/2016
f1_keywords:
- C3290
helpviewer_keywords:
- C3290
ms.assetid: 0baf684b-1143-4953-ac99-a2fa267d8017
ms.openlocfilehash: f2a346354d8da7d78c5517b01b4438bfb8af50ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222703"
---
# <a name="compiler-error-c3290"></a>編譯器錯誤 C3290

'type : trivial 屬性不能有參考類型

屬性宣告不正確。 當您宣告 trivial 屬性時，編譯器會建立屬性將更新的變數，而且類別中不可以有追蹤參考變數。

請參閱[屬性](../../extensions/property-cpp-component-extensions.md)並[追蹤參考運算子](../../extensions/tracking-reference-operator-cpp-component-extensions.md)如需詳細資訊。

## <a name="example"></a>範例

下列範例會產生 C3290。

```
// C3290.cpp
// compile with: /clr /c
ref struct R {};

ref struct X {
   R^ mr;

   property R % y;   // C3290
   property R ^ x;   // OK

   // OK
   property R% prop {
      R% get() {
         return *mr;
      }

      void set(R%) {}
   }
};

int main() {
   X x;
   R% xp = x.prop;
}
```