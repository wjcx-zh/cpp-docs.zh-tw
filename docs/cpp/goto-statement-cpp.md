---
title: "goto 陳述式 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: goto_cpp
dev_langs: C++
helpviewer_keywords: goto keyword [C++]
ms.assetid: 724c5deb-2de1-42d8-8ef1-23589d9bf5ed
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a002071bdb4e271df525b138647b0544cfe9f3c0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="goto-statement-c"></a>goto 陳述式 (C++)
`goto` 陳述式無條件地將控制項傳送至所指定識別項標記的陳述式。  
  
## <a name="syntax"></a>語法  
  
```  
goto identifier;  
```  
  
## <a name="remarks"></a>備註  
 `identifier` 所指定之標記的陳述式必須位於目前的函式。 所有 `identifier` 名稱是內部命名空間的成員，因此不會干擾其他識別項。  
  
 陳述式標籤只對 `goto` 陳述式有意義，否則會忽略陳述式標籤。 標籤不能重新宣告。  
  
 理想的程式設計風格是盡可能先使用 `break`、`continue` 和 `return` 陳述式，而不是 `goto` 陳述式。 不過，因為 `break` 陳述式只從一層迴圈結束，您可能必須使用 `goto` 陳述式來結束深度巢狀迴圈。  
  
 如需標籤和`goto`陳述式，請參閱[標記陳述式](../cpp/labeled-statements.md)和[使用標籤與 goto 陳述式](http://msdn.microsoft.com/en-us/6cd7c31a-9822-4241-8566-f79f51be48fe)。  
  
## <a name="example"></a>範例  
 在這個範例中，當 `i` 等於 3 時，`goto` 陳述式會將控制項傳送至標記 `stop` 的點。  
  
```  
// goto_statement.cpp  
#include <stdio.h>  
int main()  
{  
    int i, j;  
  
    for ( i = 0; i < 10; i++ )  
    {  
        printf_s( "Outer loop executing. i = %d\n", i );  
        for ( j = 0; j < 2; j++ )  
        {  
            printf_s( " Inner loop executing. j = %d\n", j );  
            if ( i == 3 )  
                goto stop;  
        }  
    }  
  
    // This message does not print:   
    printf_s( "Loop exited. i = %d\n", i );  
  
    stop:   
    printf_s( "Jumped to stop. i = %d\n", i );  
}  
```  
  
```Output  
Outer loop executing. i = 0  
 Inner loop executing. j = 0  
 Inner loop executing. j = 1  
Outer loop executing. i = 1  
 Inner loop executing. j = 0  
 Inner loop executing. j = 1  
Outer loop executing. i = 2  
 Inner loop executing. j = 0  
 Inner loop executing. j = 1  
Outer loop executing. i = 3  
 Inner loop executing. j = 0  
Jumped to stop. i = 3  
```  
  
## <a name="see-also"></a>請參閱  
 [跳躍陳述式](../cpp/jump-statements-cpp.md)   
 [關鍵字](../cpp/keywords-cpp.md)