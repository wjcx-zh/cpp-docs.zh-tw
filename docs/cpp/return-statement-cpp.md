---
title: return 陳述式 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- return_cpp
dev_langs:
- C++
helpviewer_keywords:
- return keyword [C++], syntax
- return keyword [C++]
ms.assetid: a498903a-056a-4df0-a6cf-72f633a62210
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aea9999adc7089499028850017a32245bba97db6
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942851"
---
# <a name="return-statement-c"></a>return 陳述式 (C++)
終止函式執行並將控制項傳回至進行呼叫的函式 (或者，如果您是從 `main` 函式傳送控制項，則傳回至作業系統)。 執行作業會在進行呼叫的函式中緊接著呼叫之後繼續進行。  
  
## <a name="syntax"></a>語法  
  
```  
return [expression];  
```  
  
## <a name="remarks"></a>備註  
 `expression` 子句 (如果有的話) 會轉換成函式宣告中指定的類型，就像執行初始化一般。 將運算式的類型轉換**傳回**函式類型可以建立暫存物件。 如需有關如何及何時建立暫存物件的詳細資訊，請參閱 <<c0> [ 暫存物件](../cpp/temporary-objects.md)。  
  
 `expression` 子句的值會傳回至進行呼叫的函式。 如果省略運算式，則函式的傳回值會是未定義。 建構函式和解構函式和類型的函式**void**，不能指定的運算式**傳回**陳述式。 所有其他類型的函式必須指定的運算式**傳回**陳述式。  
  
 當控制流程離開封入函式定義的區塊時，結果會相同，就像如果**傳回**執行未使用運算式的陳述式。 這對於宣告為傳回值的函式是無效的。  
  
 函式可以有任意數目的**傳回**陳述式。  
  
 下列範例會使用與運算式**傳回**陳述式，以取得最大的兩個整數。  
  
## <a name="example"></a>範例  
  
```cpp 
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