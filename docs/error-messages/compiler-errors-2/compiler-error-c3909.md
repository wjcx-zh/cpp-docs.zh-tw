---
title: 編譯器錯誤 C3909
ms.date: 11/04/2016
f1_keywords:
- C3909
helpviewer_keywords:
- C3909
ms.assetid: 0a443132-e53f-42dc-a58b-f086da3e7bfd
ms.openlocfilehash: 69613a1058bd5178ea4c03931664dd00bad7a101
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74748992"
---
# <a name="compiler-error-c3909"></a>編譯器錯誤 C3909

aWinRT 或 managed 事件宣告必須發生在 WinRT 或 managed 類型中

在原生類型中宣告 Windows 執行階段事件或 managed 事件。 若要修正這個錯誤，請在 Windows 執行階段類型或 managed 類型中宣告事件。

如需詳細資訊，請參閱[事件](../../extensions/event-cpp-component-extensions.md)。

下列範例會產生 C3909，並顯示如何修正此問題：

```cpp
// C3909.cpp
// compile with: /clr /c
delegate void H();
class X {
   event H^ E;   // C3909 - use ref class X instead
};

ref class Y {
   static event H^ E {
      void add(H^) {}
      void remove( H^ h ) {}
      void raise( ) {}
   }
};
```
