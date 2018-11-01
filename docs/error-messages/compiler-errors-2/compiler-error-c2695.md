---
title: 編譯器錯誤 C2695
ms.date: 11/04/2016
f1_keywords:
- C2695
helpviewer_keywords:
- C2695
ms.assetid: 3f6f2091-c38b-40ea-ab6c-f1846f5702d7
ms.openlocfilehash: 08f74bf635324ed9a05c13ecf532862d58e4f0b1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50429415"
---
# <a name="compiler-error-c2695"></a>編譯器錯誤 C2695

'function1': 覆寫虛擬函式不同於 'function2'，只是藉由呼叫慣例

在衍生類別中的函式的簽章無法覆寫基底類別中的函式，並變更的呼叫慣例。

下列範例會產生 C2695:

```
// C2695.cpp
class C {
   virtual void __fastcall func();
};

class D : public C {
   virtual void __clrcall func();   // C2695
};
```