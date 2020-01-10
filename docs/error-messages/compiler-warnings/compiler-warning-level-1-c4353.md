---
title: 編譯器警告（層級1） C4353
ms.date: 11/04/2016
f1_keywords:
- C4353
helpviewer_keywords:
- C4353
ms.assetid: 6e79f186-ed82-4c95-9923-0ad5bb9c4db1
ms.openlocfilehash: f04bc78e1ff6183208f888d9072bfe90b3aca083
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966552"
---
# <a name="compiler-warning-level-1-c4353"></a>編譯器警告（層級1） C4353

使用非標準的擴充：常數0當做函數運算式。 請改用 ' __noop ' 函式內建函式

您不能使用常數零（0）做為函數運算式。 如需詳細資訊，請參閱[__noop](../../intrinsics/noop.md)。

下列範例會產生 C4353：

```cpp
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