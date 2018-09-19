---
title: 編譯器錯誤 C3909 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3909
dev_langs:
- C++
helpviewer_keywords:
- C3909
ms.assetid: 0a443132-e53f-42dc-a58b-f086da3e7bfd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7bb3526f537a2eceb006f6af9e9b0faba44bf9cf
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46058701"
---
# <a name="compiler-error-c3909"></a>編譯器錯誤 C3909

aWinRT 或 managed 的事件宣告必須存在於 WinRT 或 managed 的類型

在原生類型中宣告 Windows 執行階段事件或 managed 事件。 若要修正這個錯誤，請在 Windows 執行階段類型或 managed 類型中宣告事件。

如需詳細資訊，請參閱 <<c0> [ 事件](../../windows/event-cpp-component-extensions.md)。

下列範例會產生 C3909，並顯示如何修正此問題：

```
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