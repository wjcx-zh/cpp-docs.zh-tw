---
title: "return 陳述式 (C) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "return 陳述式中的 ( ) 括號"
ms.assetid: 18cd82cf-f899-4b28-83ad-4eff353ddcb4
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# return 陳述式 (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`return` 陳述式用於結束函式的執行，並且將控制權還給呼叫函式。  在呼叫的函式中呼叫的點繼續執行。  `return` 陳述式也可以傳回值給呼叫的函式。  如需詳細資訊，請參閱 [Return Type](../c-language/return-type.md) 。  
  
## 語法  
 *跳躍陳述式*:  
 **回傳**  *運算式*  opt **;**  
  
 如果*運算式*出現的話，運算式的值會傳回至呼叫函式。  若省略*運算式*，函式的傳回值為 undefined。  如果有運算式的話，將評估且再轉換成函式傳回的型別。  如果函式宣告具有傳回型別 `void`，包含運算式產生的 `return` 陳述式警告和運算式不會被評估。  
  
 如果 `return` 陳述式不會出現在函式定義中，控制項會自動回到呼叫的函式，在呼叫函式的最後一個陳述式執行之後。  在這種情況下，呼叫函式的傳回值為 undefined。  如果不需要傳回值，請宣告函式有 `void` 傳回型別；否則，預設傳回型別為 `int`。  
  
 許多程式設計人員使用括號關住 `return` 陳述式的 *運算式* 引數。  不過， C 不需要括號。  
  
 以下範例說明 `return` 陳述式：  
  
```  
#include <limits.h>  
#include <stdio.h>  
  
void draw( int i, long long ll );  
long long sq( int s );  
  
int main()  
{  
    long long y;  
    int x = INT_MAX;  
  
    y = sq( x );  
    draw( x, y );  
    return x;  
}  
  
long long sq( int s )  
{  
    // Note that parentheses around the return expression   
    // are allowed but not required here.  
    return( s * (long long)s );  
}  
  
void draw( int i, long long ll )  
{  
    printf( "i = %d, ll = %lld\n", i, ll );  
    return;  
}  
  
```  
  
 在此範例中， `main` 函式會呼叫兩個功能: `sq` 和 `draw`。  `sq` 函式傳回 `x * x` 的值為 `main`，傳回值則指派給 `y`。  在 `sq` 中傳回運算式周圍的括號評估為運算式的一部分，且不需要 return 陳述式。  因為轉換為傳回型別之前，會傳回評估運算式， `sq` 強制運算式類型為傳回型別以避免一個可能的整數溢位的轉換，可能會產生未預期的結果。  `draw` 函式宣告為 `void` 函式。  它會列印其參數的值且空的傳回陳述式會結束函式，並且不會傳回值。  嘗試指派 `draw` 的傳回值會造成一個診斷資訊發行。  `main` 函式會傳回 `x` 的值給作業系統。  
  
 此範例的輸出如下所示：  
  
  **i \= 2147483647， ll \= 4611686014132420609**   
## 請參閱  
 [陳述式](../c-language/statements-c.md)