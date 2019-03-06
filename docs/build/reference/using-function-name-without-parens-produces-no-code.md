---
title: 使用不帶 () 的函式名稱不會產生程式碼
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C++], without parentheses
ms.assetid: edf4a177-a160-44aa-8436-e077b5b27809
ms.openlocfilehash: 50053244787d1ceafe4e60083e7e7353e337dbbe
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2019
ms.locfileid: "57424895"
---
# <a name="using-function-name-without--produces-no-code"></a>使用不帶 () 的函式名稱不會產生程式碼

使用您的程式中宣告的函式名稱時，沒有括號，編譯器不會產生程式碼。 這是不論會函式接受參數，因為編譯器會計算函式的位址;不過，函式呼叫運算子 」 （）"不存在，因為沒有進行呼叫。 此結果會如下所示：

```
// compile with /Wall to generate a warning
int a;
a;      // no code generated here either
```

Visual c + +，甚至使用警告層級 4 不會產生診斷輸出。 不會發出警告。會不產生任何程式碼。

下列範例程式碼編譯 （警告），並連結正確無誤，但會產生任何程式碼參考`funcn( )`。 此選項可正常運作，加入函式呼叫運算子 」 （）"。

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

## <a name="see-also"></a>另請參閱

[最佳化程式碼](../../build/reference/optimizing-your-code.md)
