---
title: 編譯器警告 (層級 3) C4414
ms.date: 11/04/2016
f1_keywords:
- C4414
helpviewer_keywords:
- C4414
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
ms.openlocfilehash: 0a9ceb332888e306b8cb3bcbe1832f773d02d63d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401939"
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