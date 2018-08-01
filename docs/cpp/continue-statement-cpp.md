---
title: continue 陳述式 （c + +） |Microsoft Docs
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
ms.openlocfilehash: d0ab1e052b3e6d843813c33e5444fc3c08796d00
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/01/2018
ms.locfileid: "39402087"
---
# <a name="continue-statement-c"></a>continue 陳述式 (C++)
強制將控制項傳輸至最小的封入的控制運算式[請勿](../cpp/do-while-statement-cpp.md)，[如](../cpp/for-statement-cpp.md)，或[雖然](../cpp/while-statement-cpp.md)迴圈。  
  
## <a name="syntax"></a>語法  
  
```  
continue;  
```  
  
## <a name="remarks"></a>備註  
 目前反覆項目中其餘的任何陳述式都不會執行。 迴圈中下一個反覆項目的判斷方式如下：  
  
-   中**請勿**或**雖然**藉由重新評估的控制運算式的迴圈下, 一個反覆項目開始**執行**或**時**陳述式。  
  
-   在  **for**迴圈 (使用語法`for`(`init-expr`;`cond-expr`;`loop-expr`))，則`loop-expr`子句執行。 然後會重新求出 `cond-expr` 子句的值，而根據結果，迴圈會結束或另一個反覆項目會發生。  
  
 下列範例示範如何**繼續**陳述式可用來略過的程式碼區段及開始迴圈的下一個反覆項目。  
  
## <a name="example"></a>範例  
  
```cpp 
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