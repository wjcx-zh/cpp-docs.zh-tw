---
title: 編譯器錯誤 C2695 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2695
dev_langs:
- C++
helpviewer_keywords:
- C2695
ms.assetid: 3f6f2091-c38b-40ea-ab6c-f1846f5702d7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a618c02fcf3a8927d8090b1ad51ed16d9ac28542
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056049"
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