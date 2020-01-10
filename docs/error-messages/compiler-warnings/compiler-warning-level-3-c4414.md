---
title: 編譯器警告（層級3） C4414
ms.date: 11/04/2016
f1_keywords:
- C4414
helpviewer_keywords:
- C4414
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
ms.openlocfilehash: 43570cd43ca6e9d4f892dc577f615e9fa980e561
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051574"
---
# <a name="compiler-warning-level-3-c4414"></a>編譯器警告（層級3） C4414

' function '：將函式轉換為 near 的短跳躍

「短跳躍」會產生精簡的指令，其會從指令中分支到有限範圍內的位址。 指令包含一個短位移，代表跳躍與目標位址（函式定義）之間的距離。 在連結期間，函式可能會移動，或受限於連結時間優化，使函式從短位移可存取的範圍中移出。 編譯器必須為跳躍產生特殊的記錄，這需要 jmp 指令接近或距離。 編譯器進行轉換。

例如，下列程式碼會產生 C4414：

```cpp
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