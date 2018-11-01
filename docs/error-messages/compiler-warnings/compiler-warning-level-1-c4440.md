---
title: 編譯器警告 (層級 1) C4440
ms.date: 11/04/2016
f1_keywords:
- C4440
helpviewer_keywords:
- C4440
ms.assetid: 78b9642a-a93e-401e-9d92-372f6451bc5d
ms.openlocfilehash: ccd7c14cbd078d4740795d25ad772bdc78840a60
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660044"
---
# <a name="compiler-warning-level-1-c4440"></a>編譯器警告 (層級 1) C4440

呼叫慣例已忽略 'calling_convention2' 從 'calling_convention1' 重複定義

嘗試變更的呼叫慣例已忽略。

下列範例會產生 C4440:

```
// C4440.cpp
// compile with: /W1 /LD /clr
typedef void __clrcall F();
typedef F __cdecl *PFV;   // C4440
```