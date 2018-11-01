---
title: 編譯器警告 C4485
ms.date: 11/04/2016
f1_keywords:
- C4485
helpviewer_keywords:
- C4485
ms.assetid: a6f2b437-ca93-4dcd-b9cb-df415e10df86
ms.openlocfilehash: 7138f1a3cecaaf75fbab01fd1aee18529b7a3a84
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50652441"
---
# <a name="compiler-warning-c4485"></a>編譯器警告 C4485

'override_function': 符合基底 ref 類別方法 'base_class_function'，但不是標示為 'new' override';'new' （和 'virtual'） 會假設

存取子會覆寫，不論`virtual`關鍵字，基底類別存取子函式，但`override`或`new`規範不是覆寫的函式簽章的一部分。 新增`new`或`override`規範來解決這個警告。

請參閱[覆寫](../../windows/override-cpp-component-extensions.md)並[新 (新 vtable 中的位置）](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md)如需詳細資訊。

C4485 一律發出為錯誤。 使用[警告](../../preprocessor/warning.md)隱藏 C4485 pragma。

## <a name="example"></a>範例

下列範例會產生 C4485

```
// C4485.cpp
// compile with: /clr
delegate void Del();

ref struct A {
   virtual event Del ^E;
};

ref struct B : A {
   virtual event Del ^E;   // C4485
};

ref struct C : B {
   virtual event Del ^E {
      void raise() override {}
      void add(Del ^) override {}
      void remove(Del^) override {}
   }
};
```