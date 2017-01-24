---
title: "return 陳述式 (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "return"
  - "return_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "return 關鍵字 [C++]"
  - "return 關鍵字 [C++], 語法"
ms.assetid: a498903a-056a-4df0-a6cf-72f633a62210
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# return 陳述式 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

終止函式執行並將控制項傳回至進行呼叫的函式 \(或者，如果您是從 `main` 函式傳送控制項，則傳回至作業系統\)。  執行作業會在進行呼叫的函式中緊接著呼叫之後繼續進行。  
  
## 語法  
  
```  
return [expression];  
```  
  
## 備註  
 `expression` 子句 \(如果有的話\) 會轉換成函式宣告中指定的類型，就像執行初始化一般。  從運算式的類型轉換成函式的 `return` 類型可能會建立暫存物件。  如需如何及何時建立暫存的詳細資訊，請參閱[暫存物件](../cpp/temporary-objects.md)。  
  
 `expression` 子句的值會傳回至進行呼叫的函式。  如果省略運算式，則函式的傳回值會是未定義。  建構函式和解構函式以及 `void` `` 類型的函式都無法在 `return` 陳述式中指定運算式。  所有其他類型的函式都必須在 `return` 陳述式中指定運算式。  
  
 當控制流程離開封入函式定義的區塊時，結果會與執行沒有運算式之 `return` 陳述式的結果相同。  這對於宣告為傳回值的函式是無效的。  
  
 函式可以擁有任意數目的 `return` 陳述式。  
  
 下列範例將使用具有 `return` 陳述式的運算式取得兩個整數的最大者。  
  
## 範例  
  
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
  
## 請參閱  
 [跳躍陳述式](../cpp/jump-statements-cpp.md)   
 [C\+\+ 關鍵字](../cpp/keywords-cpp.md)