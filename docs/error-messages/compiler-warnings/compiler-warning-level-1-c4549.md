---
title: 編譯器警告 (層級 1) C4549
ms.date: 11/04/2016
f1_keywords:
- C4549
helpviewer_keywords:
- C4549
ms.assetid: 81a07676-625b-4f58-9b0c-3ee22830b04a
ms.openlocfilehash: 5732b2f963be52512d5d80f2552af4a80acb3372
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657232"
---
# <a name="compiler-warning-level-1-c4549"></a>編譯器警告 (層級 1) C4549

'operator': 逗號之前不會影響; 運算子您是否想 'operator'？

編譯器偵測到格式不正確的逗點運算式。

此警告預設為關閉。 如需詳細資訊，請參閱 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。

下列範例會產生 C4549:

```
// C4549.cpp
// compile with: /W1
#pragma warning (default : 4549)

int main() {
   int i = 0, k = 0;

   if ( i == 0, k )   // C4549
   // try the following line instead
   // if ( i == 0 )
      i++;
}
```