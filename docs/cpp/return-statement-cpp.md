---
title: "return 陳述式 （c + +） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- return_cpp
dev_langs:
- C++
helpviewer_keywords:
- return keyword [C++], syntax
- return keyword [C++]
ms.assetid: a498903a-056a-4df0-a6cf-72f633a62210
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 7474bc55a5c9d2406465a6ee763c19c2e56e1159
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="return-statement-c"></a>return 陳述式 (C++)
終止函式執行並將控制項傳回至進行呼叫的函式 (或者，如果您是從 `main` 函式傳送控制項，則傳回至作業系統)。 執行作業會在進行呼叫的函式中緊接著呼叫之後繼續進行。  
  
## <a name="syntax"></a>語法  
  
```  
return [expression];  
```  
  
## <a name="remarks"></a>備註  
 `expression` 子句 (如果有的話) 會轉換成函式宣告中指定的類型，就像執行初始化一般。 從運算式的類型轉換成函式的 `return` 類型可能會建立暫存物件。 如需有關如何及何時建立暫存物件的詳細資訊，請參閱[暫存物件](../cpp/temporary-objects.md)。  
  
 `expression` 子句的值會傳回至進行呼叫的函式。 如果省略運算式，則函式的傳回值會是未定義。 建構函式和解構函式和函式的型別`void`，不能指定的運算式中`return`陳述式。 所有其他類型的函式都必須在 `return` 陳述式中指定運算式。  
  
 當控制流程離開封入函式定義的區塊時，結果會與執行沒有運算式之 `return` 陳述式的結果相同。 這對於宣告為傳回值的函式是無效的。  
  
 函式可以擁有任意數目的 `return` 陳述式。  
  
 下列範例將使用具有 `return` 陳述式的運算式取得兩個整數的最大者。  
  
## <a name="example"></a>範例  
  
```  
// return_statement2.cpp  
#include <stdio.h>  
  
int max ( int a, int b )  
{  
   return ( a > b ? a : b );  
}  
  
int main()  
{  
    int nOne = 5;  
    int nTwo = 7;  
  
    printf_s("\n%d is bigger\n", max( nOne, nTwo ));  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [跳躍陳述式](../cpp/jump-statements-cpp.md)   
 [關鍵字](../cpp/keywords-cpp.md)
