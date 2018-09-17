---
title: 使用函式名稱，（） 會不產生任何程式碼無 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], without parentheses
ms.assetid: edf4a177-a160-44aa-8436-e077b5b27809
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13ca43386c9ef46f526538781a91fd1a81ade537
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710576"
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