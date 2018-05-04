---
title: 繼續陳述式 （c + +） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- continue_cpp
dev_langs:
- C++
helpviewer_keywords:
- continue keyword [C++]
ms.assetid: 3c94ee57-f732-4c1d-8537-d0ce5382bfd4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b153c9f5dfae93f1a5cb83dc2b9bcfc09e77af07
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="continue-statement-c"></a>continue 陳述式 (C++)
強制將控制項傳輸至最小的封入的控制運算式[不要](../cpp/do-while-statement-cpp.md)，[如](../cpp/for-statement-cpp.md)，或[時](../cpp/while-statement-cpp.md)迴圈。  
  
## <a name="syntax"></a>語法  
  
```  
continue;  
```  
  
## <a name="remarks"></a>備註  
 目前反覆項目中其餘的任何陳述式都不會執行。 迴圈中下一個反覆項目的判斷方式如下：  
  
-   在 `do` 或 `while` 迴圈中，下一個反覆項目是藉由重新計算 `do` 或 `while` 陳述式的控制運算式的值開始。  
  
-   在 `for` 迴圈中 (使用語法 `for`(`init-expr`; `cond-expr`; `loop-expr`)) 會執行 `loop-expr` 子句。 然後會重新求出 `cond-expr` 子句的值，而根據結果，迴圈會結束或另一個反覆項目會發生。  
  
 下列範例將示範如何使用 `continue` 陳述式略過程式碼區段及開始迴圈的下一個反覆項目。  
  
## <a name="example"></a>範例  
  
```  
// continue_statement.cpp  
#include <stdio.h>  
int main()  
{  
    int i = 0;  
    do  
    {  
        i++;  
        printf_s("before the continue\n");  
        continue;  
        printf("after the continue, should never print\n");  
     } while (i < 3);  
  
     printf_s("after the do loop\n");  
}  
```  
  
```Output  
before the continue  
before the continue  
before the continue  
after the do loop  
```  
  
## <a name="see-also"></a>另請參閱  
 [跳躍陳述式](../cpp/jump-statements-cpp.md)   
 [關鍵字](../cpp/keywords-cpp.md)