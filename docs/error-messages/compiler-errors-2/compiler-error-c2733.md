---
title: 編譯器錯誤 C2733
ms.date: 11/04/2016
f1_keywords:
- C2733
helpviewer_keywords:
- C2733
ms.assetid: 67f83561-c633-407c-a2ee-f9fd16e165bf
ms.openlocfilehash: 26819f1928223b5fa96d275290105f32787057f5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518842"
---
# <a name="compiler-error-c2733"></a>編譯器錯誤 C2733

第二個 C 連結的多載函式 'function' 不允許

使用 C 連結宣告多個多載函式。 使用 C 連結時，只有一種指定的函式可以是外部。 多載函式具有相同的未裝飾的名稱，因為它們無法搭配 C 程式。

下列範例會產生 C2733:

```
// C2733.cpp
extern "C" {
   void F1(int);
}

extern "C" {
   void F1();   // C2733
   // try the following line instead
   // void F2();
}
```