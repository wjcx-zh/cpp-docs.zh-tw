---
title: "請勿-while 陳述式 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: do_cpp
dev_langs: C++
helpviewer_keywords:
- do keyword [C++], do-while
- do-while keyword [C++]
- do keyword [C++]
- while keyword [C++], do-while
ms.assetid: e01e6f7c-7da1-4591-87f9-c26ff848e7b0
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b9ef52e04bd855824e709c66693cb989a18b1283
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="do-while-statement-c"></a>do-while 陳述式 (C++)
執行*陳述式*重複直到指定的終止條件 (*運算式*) 會評估為零。  
  
## <a name="syntax"></a>語法  
  
```  
do  
   statement  
while ( expression ) ;  
```  
  
## <a name="remarks"></a>備註  
 終止條件的測試是在每次執行迴圈之後進行；因此，`do-while` 迴圈會執行一次或多次取決於終止運算式的值。 `do-while`陳述式也可以終止時[中斷](../cpp/break-statement-cpp.md)， [goto](../cpp/goto-statement-cpp.md)，或[傳回](../cpp/return-statement-cpp.md)陳述式主體內執行陳述式。  
  
 *expression* 必須有算術或指標類型。 執行程序如下所示：  
  
1.  會執行陳述式主體。  
  
2.  接下來會評估 *expression*。 如果 *expression* 為 false，`do-while` 陳述式會終止，而並將控制項傳遞至程式中的下一個陳述式。 如果 *expression* 為 true (非零)，則會從步驟 1 開始重複處理序。  
  
## <a name="example"></a>範例  
 以下範例示範 `do-while` 陳述式：  
  
```  
// do_while_statement.cpp  
#include <stdio.h>  
int main()  
{  
    int i = 0;  
    do  
    {  
        printf_s("\n%d",i++);  
    } while (i < 3);  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [反覆運算陳述式](../cpp/iteration-statements-cpp.md)   
 [關鍵字](../cpp/keywords-cpp.md)   
 [while 陳述式 (C++)](../cpp/while-statement-cpp.md)   
 [for 陳述式 (C++)](../cpp/for-statement-cpp.md)   
 [以範圍為基礎的 for 陳述式 (C++)](../cpp/range-based-for-statement-cpp.md)