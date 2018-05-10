---
title: return 陳述式 (C) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- ( ) parentheses in return statements
ms.assetid: 18cd82cf-f899-4b28-83ad-4eff353ddcb4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 08407f26e3c3d9064fded1620538262b0c91e2ba
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="return-statement-c"></a>return 陳述式 (C)
`return` 陳述式可終止函式的執行，並且將控制權還給呼叫函式。 執行作業會在進行呼叫的函式中緊接著呼叫之後繼續進行。 `return` 陳述式也可將值傳回至呼叫函式。 如需詳細資訊，請參閱[傳回型別](../c-language/return-type.md)。  
  
## <a name="syntax"></a>語法  
 *jump-statement*：  
 **return**  *expression* opt **;**  
  
 *expression* 的值 (如果有) 會傳回至呼叫函式。 如果省略 *expression*，則函式的傳回值會是未定義。 此運算式 (如果有) 會先評估，再轉換為函式所傳回的類型。 如果函式是使用傳回型別 `void` 宣告，則包含運算式的 `return` 陳述式會產生警告，而且不會評估運算式。  
  
 如果函式定義中未出現 `return` 陳述式，則會在執行所呼叫函式的最後一個陳述式之後，自動將控制權還給呼叫函式。 在此情況下，所呼叫函式的傳回值會是未定義。 如果不需要傳回值，請宣告函式具有 `void` 傳回型別；否則預設的傳回型別會是 `int`。  
  
 許多程式設計人員使用括號括住 `return` 陳述式的 *expression* 引數。 不過，C 不需要括號。  
  
 這個範例將示範 `return` 陳述式：  
  
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
  
 在此範例中，`main` 函式會呼叫兩個函式︰`sq` 和 `draw`。 `sq` 函式會將 `x * x` 的值傳回至 `main`，再將傳回值指派給 `y`。 `sq` 中括住傳回運算式的括號會當做運算式的一部分評估，return 陳述式則不需要括號。 由於傳回運算式在轉換為傳回型別之前已經過評估，因此 `sq` 會強制將運算式類型轉換為傳回型別，以避免發生可能導致未預期結果的整數溢位。 `draw` 函式會宣告為 `void` 函式。 它會列印其參數的值，然後空的 return 陳述式會結束函式而不會傳回值。 嘗試指派 `draw` 的傳回值會導致發出診斷訊息。 `main` 函式會接著將 `x` 的值傳回至作業系統。  
  
 此範例的輸出如下所示：  
  
```Output  
i = 2147483647, ll = 4611686014132420609  
```  
  
## <a name="see-also"></a>請參閱  
 [陳述式](../c-language/statements-c.md)