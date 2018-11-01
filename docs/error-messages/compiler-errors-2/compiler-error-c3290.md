---
title: 編譯器錯誤 C3290
ms.date: 11/04/2016
f1_keywords:
- C3290
helpviewer_keywords:
- C3290
ms.assetid: 0baf684b-1143-4953-ac99-a2fa267d8017
ms.openlocfilehash: d82d3272563f7a5af5de399a2f7fff621500e612
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490476"
---
# <a name="compiler-error-c3290"></a>編譯器錯誤 C3290

'type : trivial 屬性不能有參考類型

屬性宣告不正確。 當您宣告 trivial 屬性時，編譯器會建立屬性將更新的變數，而且類別中不可以有追蹤參考變數。

請參閱[屬性](../../windows/property-cpp-component-extensions.md)並[追蹤參考運算子](../../windows/tracking-reference-operator-cpp-component-extensions.md)如需詳細資訊。

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