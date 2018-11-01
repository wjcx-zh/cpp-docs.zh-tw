---
title: 編譯器警告 (層級 1) C4353
ms.date: 11/04/2016
f1_keywords:
- C4353
helpviewer_keywords:
- C4353
ms.assetid: 6e79f186-ed82-4c95-9923-0ad5bb9c4db1
ms.openlocfilehash: 305c1156ae8dc664edba17287786db50bfabbd18
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483689"
---
# <a name="compiler-warning-level-1-c4353"></a>編譯器警告 (層級 1) C4353

使用非標準擴充： 常數 0 當做函式運算式。 改為使用內建函式的 '__noop' 函式

您無法使用常數零 (0) 做為函式運算式。 如需詳細資訊，請參閱 < [__noop](../../intrinsics/noop.md)。

下列範例會產生 C4353:

```
// C4353.cpp
// compile with: /W1
void MyPrintf(void){};
#define X 0
#if X
   #define DBPRINT MyPrint
#else
   #define DBPRINT 0   // C4353 expected
#endif
int main(){
DBPRINT();
}
```