---
title: 編譯器錯誤 C3919
ms.date: 11/04/2016
f1_keywords:
- C3919
helpviewer_keywords:
- C3919
ms.assetid: 5f8eddda-d751-478b-930d-e18f7191ddfb
ms.openlocfilehash: 05ac2fc9258a078f352b6012e64e86fe4b70c3f0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59777181"
---
# <a name="compiler-error-c3919"></a>編譯器錯誤 C3919

'event_method': 函式必須有類型 'type'

事件存取子方法宣告不正確。

如需有關事件的詳細資訊，請參閱[事件](../../extensions/event-cpp-component-extensions.md)。

下列範例會產生 C3919:

```
// C3919.cpp
// compile with: /clr /c
using namespace System;
delegate void D(String^);
ref class R {
   event D^ e {
      int add(int);   // C3919
      int remove(int);   // C3919

      void add(D^);   // OK
      void remove(D^);   // OK
   }
};
```