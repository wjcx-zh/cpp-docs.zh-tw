---
title: 使用不帶 () 的函式名稱不會產生程式碼
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], without parentheses
ms.assetid: edf4a177-a160-44aa-8436-e077b5b27809
ms.openlocfilehash: 51be77dc8f4fe072ea6cc46dd51e38862649feda
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62314594"
---
# <a name="using-function-name-without--produces-no-code"></a>使用不帶 () 的函式名稱不會產生程式碼

使用在程式中宣告的函式名稱時，若沒有括弧，編譯器不會產生程式碼。 不論函式是否採用參數，都會發生這種情況，因為編譯器會計算函式位址。不過，因為函式呼叫運算子 "（）" 不存在，所以不會進行任何呼叫。 此結果如下所示：

```
// compile with /Wall to generate a warning
int a;
a;      // no code generated here either
```

在 Visual C++ 中，即使使用警告層級4也不會產生診斷輸出。 不發出警告;不會產生任何程式碼。

下列範例程式碼會在沒有錯誤的情況下編譯（含警告）並正確連結，但不`funcn( )`會在參考中產生任何程式碼。 若要讓此作業正常運作，請新增函式呼叫運算子 "（）"。

```
#include <stdio.h>
void funcn();

int main() {
   funcn;      /* missing function call operator;
                  call will fail.  Use funcn() */
   }

void funcn() {
   printf("\nHello World\n");
}
```

## <a name="see-also"></a>請參閱

[最佳化程式碼](optimizing-your-code.md)
