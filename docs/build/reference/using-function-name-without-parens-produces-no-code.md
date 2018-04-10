---
title: 使用無 （） 會不產生任何程式碼的函式名稱 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- functions [C++], without parentheses
ms.assetid: edf4a177-a160-44aa-8436-e077b5b27809
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c03706be0b9853cbbdebe79b58e410f7237692ee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="using-function-name-without--produces-no-code"></a>使用不帶 () 的函式名稱不會產生程式碼
在您的程式中宣告的函式名稱使用時沒有括號，編譯器不會產生程式碼。 無論函式接受參數，因為編譯器會計算函式的位址。不過，函式呼叫運算子 」 （）"不存在，因為沒有進行呼叫。 這個結果會是如下所示：  
  
```  
// compile with /Wall to generate a warning  
int a;  
a;      // no code generated here either  
```  
  
 在 Visual c + + 中，即使使用警告層級 4 不會產生診斷輸出。 不會發出警告。會不產生任何程式碼。  
  
 下列範例程式碼編譯 （警告），並連結正確無誤，但會產生任何程式碼中的參考`funcn( )`。 為了要正確運作，加入函式呼叫運算子 」 （）"。  
  
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
 [最佳化程式碼](../../build/reference/optimizing-your-code.md)