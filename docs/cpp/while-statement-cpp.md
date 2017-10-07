---
title: "while 陳述式 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- while_cpp
dev_langs:
- C++
helpviewer_keywords:
- while keyword [C++]
- while keyword [C++], syntax
ms.assetid: 358dbe76-5e5e-4af5-b575-c2293c636899
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 694852e40699ac7b2663392cb8a4c02218a422a7
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="while-statement-c"></a>while 陳述式 (C++)
執行*陳述式*重複直到*運算式*判斷值為零。  
  
## <a name="syntax"></a>語法  
  
```  
  
      while ( expression )  
   statement  
```  
  
## <a name="remarks"></a>備註  
 測試*運算式*將之前每次執行迴圈; 因此，`while`迴圈會執行零次以上。 *運算式*必須是整數類型、 指標類型，或類別類型，可明確轉換為整數或指標類型。  
  
 A`while`迴圈可以也會終止時[中斷](../cpp/break-statement-cpp.md)， [goto](../cpp/goto-statement-cpp.md)，或[傳回](../cpp/return-statement-cpp.md)主體就會執行的陳述式中。 使用[繼續](../cpp/continue-statement-cpp.md)終止目前的反覆項目，但不結束`while`迴圈。 **繼續**將控制項傳遞至下一個反覆運算`while`迴圈。  
  
 下列程式碼使用 `while` 迴圈修剪字串中的結尾底線：  
  
```  
// while_statement.cpp  
  
#include <string.h>  
#include <stdio.h>  
char *trim( char *szSource )  
{  
    char *pszEOS = 0;  
  
    //  Set pointer to character before terminating NULL  
    pszEOS = szSource + strlen( szSource ) - 1;  
  
    //  iterate backwards until non '_' is found   
    while( (pszEOS >= szSource) && (*pszEOS == '_') )  
        *pszEOS-- = '\0';  
  
    return szSource;  
}  
int main()  
{  
    char szbuf[] = "12345_____";  
  
    printf_s("\nBefore trim: %s", szbuf);  
    printf_s("\nAfter trim: %s\n", trim(szbuf));  
}  
```  
  
 終止條件在迴圈頂端進行評估。 如果沒有結尾底線，此迴圈絕不會執行。  
  
## <a name="see-also"></a>另請參閱  
 [反覆運算陳述式](../cpp/iteration-statements-cpp.md)   
 [關鍵字](../cpp/keywords-cpp.md)   
 [do-while 陳述式 (C++)](../cpp/do-while-statement-cpp.md)   
 [for 陳述式 (C++)](../cpp/for-statement-cpp.md)   
 [以範圍為基礎的 for 陳述式 (C++)](../cpp/range-based-for-statement-cpp.md)
