---
title: 編譯器錯誤 C2386
ms.date: 11/04/2016
f1_keywords:
- C2386
helpviewer_keywords:
- C2386
ms.assetid: aaaa1284-34a0-4da2-8547-9fcbb559dae0
ms.openlocfilehash: a75ccd9824106f2b954cd090a0e00ab11786d243
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667648"
---
# <a name="compiler-error-c2386"></a>編譯器錯誤 C2386

'symbol': 目前範圍中已經有使用這個名稱的符號

您嘗試建立命名空間別名，但所選名稱已存在。

下列範例會產生 C2386：

```
// C2386.cpp
namespace A {
   int k;
}

int i;
namespace i = A;   // C2386, i already exists
```