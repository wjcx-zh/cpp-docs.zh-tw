---
title: 編譯器錯誤 C2553 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2553
dev_langs:
- C++
helpviewer_keywords:
- C2553
ms.assetid: 64bc1e9a-627f-4ce9-b7bc-dc911bdb9180
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 38fb61b7281dd0371c546fd7b7bc960232cf2e00
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043985"
---
# <a name="compiler-error-c2553"></a>編譯器錯誤 C2553

'base_function': 覆寫虛擬函式傳回型別不同於 'override_function'

在衍生類別中的函式嘗試覆寫虛擬函式在基底類別中，但在衍生的類別函式沒有相同的傳回類型的基底類別函式。  覆寫函式簽章必須符合要覆寫的函式的簽章。

下列範例會產生 C2553:

```
// C2553.cpp
// compile with: /clr /c
ref struct C {
   virtual void f();
};

ref struct D : C {
   virtual int f() override ;   // C2553

   // try the following line instead
   // virtual void f() override;
};
```