---
title: 請勿-do-while 陳述式 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- do_cpp
dev_langs:
- C++
helpviewer_keywords:
- do keyword [C++], do-while
- do-while keyword [C++]
- do keyword [C++]
- while keyword [C++], do-while
ms.assetid: e01e6f7c-7da1-4591-87f9-c26ff848e7b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d2de180d58c31f4bd6c8b15eb69076b99f8b57b0
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942943"
---
# <a name="do-while-statement-c"></a>do-while 陳述式 (C++)
執行*陳述式*重複直到指定的終止條件 (*運算式*) 評估為零。  
  
## <a name="syntax"></a>語法  
  
```  
do  
   statement  
while ( expression ) ;  
```  
  
## <a name="remarks"></a>備註  
 終止條件的測試會在迴圈中; 每次執行之後因此，**請勿-雖然**迴圈會執行一次以上，取決於終止運算式的值。 **請勿-雖然**陳述式也可能會終止時[中斷](../cpp/break-statement-cpp.md)， [goto](../cpp/goto-statement-cpp.md)，或[傳回](../cpp/return-statement-cpp.md)陳述式主體中執行陳述式。  
  
 *expression* 必須有算術或指標類型。 執行程序如下所示：  
  
1.  會執行陳述式主體。  
  
2.  接下來會評估 *expression*。 如果*運算式*為 false，**請勿-雖然**陳述式會終止，而控制權會傳遞至程式中的下一個陳述式。 如果 *expression* 為 true (非零)，則會從步驟 1 開始重複處理序。  
  
## <a name="example"></a>範例  
 下列範例會示範**請勿-雖然**陳述式：  
  
```cpp 
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