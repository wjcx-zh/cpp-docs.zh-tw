---
title: 編譯器錯誤 C2161
ms.date: 11/04/2016
f1_keywords:
- C2161
helpviewer_keywords:
- C2161
ms.assetid: d6798821-13bb-4e60-924f-85f7bf955387
ms.openlocfilehash: 366e848d566dbcbf9414565de604aa722f758456
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519427"
---
# <a name="compiler-error-c2161"></a>編譯器錯誤 C2161

'##' 不可以出現在巨集定義結尾

以語彙基元帶入的運算子 (#) 結尾的巨集定義。

下列範例會產生 C2161：

```
// C2161.cpp
// compile with: /c
#define mac(a,b) a   // OK
#define mac(a,b) a##   // C2161
```