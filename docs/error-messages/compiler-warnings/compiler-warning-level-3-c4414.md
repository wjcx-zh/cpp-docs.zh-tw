---
title: 編譯器警告 （層級 3） C4414 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4414
dev_langs:
- C++
helpviewer_keywords:
- C4414
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd0868fea89cd868178956c0aba171ce6525bd75
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043205"
---
# <a name="compiler-warning-level-3-c4414"></a>編譯器警告 (層級 3) C4414

'function': 函式的 short 跳躍指令被轉換為 near

簡短的跳躍點產生精簡指令，指示從分支到限制範圍內的位址。 指示包含簡短的位移，其代表的跳躍的目標位址，而函式定義之間的距離。 連結期間函式可能會移動，或因連結時間最佳化，讓函式移出範圍可從簡短的位移。 編譯器必須產生特殊記錄，而這需要不久或目前的 jmp 指示跳躍。 編譯器會進行轉換。

例如，下列程式碼會產生 C4414:

```
// C4414.cpp
// compile with: /W3 /c
// processor: x86
int DoParityEven();
int DoParityOdd();
unsigned char global;
int __declspec(naked) DoParityEither()
{
   __asm
   {
      test global,0
      jpe SHORT DoParityEven  // C4414
      jmp SHORT DoParityOdd   // C4414
   }
}
```