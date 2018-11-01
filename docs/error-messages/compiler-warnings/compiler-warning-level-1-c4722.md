---
title: 編譯器警告 (層級 1) C4722
ms.date: 11/04/2016
f1_keywords:
- C4722
helpviewer_keywords:
- C4722
ms.assetid: d8660710-f67b-4f59-a5fd-59259475529e
ms.openlocfilehash: 320061c2daf2be042afe45828af637638399beaf
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50469468"
---
# <a name="compiler-warning-level-1-c4722"></a>編譯器警告 (層級 1) C4722

'function' : 解構函式從未返回，可能有記憶體遺漏

控制流程會在解構函式終止。 執行緒或整個程式會終止，且可能不會釋放已配置的資源。  此外，如果例外狀況的處理期間將呼叫解構函式以進行堆疊回溯，則未定義可執行檔的行為。

若要解決，請移除導致解構函式不返回的函式呼叫。

## <a name="example"></a>範例

下列範例會產生 C4722：

```
// C4722.cpp
// compile with: /O1 /W1 /c
#include <stdlib.h>
class C {
public:
   C();
   ~C() { exit(1); };   // C4722
};

extern void func (C*);

void Test(){
   C x;
   func(&x);
   // control will not leave Test because destructor will exit
}
```