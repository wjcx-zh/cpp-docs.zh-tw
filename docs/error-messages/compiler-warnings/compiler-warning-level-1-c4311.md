---
title: 編譯器警告 (層級 1) C4311
ms.date: 11/04/2016
f1_keywords:
- C4311
helpviewer_keywords:
- C4311
ms.assetid: ddc579d0-d051-47bc-915d-71ffb32323c9
ms.openlocfilehash: f60daa66daa42687522400284a19ec87eb13f67c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50513720"
---
# <a name="compiler-warning-level-1-c4311"></a>編譯器警告 (層級 1) C4311

'variable' : 指標從 'type' 到 'type' 截斷

此警告會偵測 64 位元指標截斷問題。 例如，如果程式碼是針對 64 位元架構而編譯的，若指派給 `int` (32 位元)，指標 (64 位元) 的值將會被截斷。 如需詳細資訊，請參閱 <<c0> [ 規則使用指標](/windows/desktop/WinProg64/rules-for-using-pointers)。

其他與警告 C4311 的常見原因的相關資訊，請參閱[常見編譯器錯誤](/windows/desktop/WinProg64/common-compiler-errors)。

下列程式碼範例會在針對 64 位元目標而編譯時產生 C4311，並接著示範如何修正此問題：

```
// C4311.cpp
// compile by using: cl /W1 C4311.cpp
int main() {
   void* p = &p;
   unsigned int i = (unsigned int) p;   // C4311 for 64-bit targets
   unsigned long long j = (unsigned long long) p;   // OK
}

```