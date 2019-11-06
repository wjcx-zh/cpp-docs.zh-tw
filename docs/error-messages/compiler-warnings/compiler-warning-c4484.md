---
title: 編譯器警告 C4484
ms.date: 11/04/2016
f1_keywords:
- C4484
helpviewer_keywords:
- C4484
ms.assetid: 3d30e5b3-2297-45b7-a37a-1360056fdd0e
ms.openlocfilehash: 4d3f72ddf7675ea7ad73022dc55a60fdc74d4390
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2019
ms.locfileid: "73623622"
---
# <a name="compiler-warning-c4484"></a>編譯器警告 C4484

' override_function '：符合基底 ref 類別方法 ' base_class_function '，但未標記為 ' virtual '、' new ' 或 ' override ';假設為 ' new ' （而非 ' virtual '）

以 **/clr**進行編譯時，編譯器不會隱含覆寫基類函式，這表示函數會在 vtable 中取得新的位置。 若要解決此問題，請明確指定函數是否為覆寫。

如需詳細資訊，請參閱:

- [/clr (通用語言執行平台編譯)](../../build/reference/clr-common-language-runtime-compilation.md)

- [override](../../extensions/override-cpp-component-extensions.md)

- [new (vtable 中的新位置)](../../extensions/new-new-slot-in-vtable-cpp-component-extensions.md)

C4484 一律會發出為錯誤。 請使用[warning](../../preprocessor/warning.md) pragma 來隱藏 C4484。

## <a name="example"></a>範例

下列範例會產生 C4484。

```cpp
// C4484.cpp
// compile with: /clr
ref struct A {
   virtual void Test() {}
};

ref struct B : A {
   void Test() {}   // C4484
};

// OK
ref struct C {
   virtual void Test() {}
   virtual void Test2() {}
};

ref struct D : C {
   virtual void Test() new {}
   virtual void Test2() override {}
};
```