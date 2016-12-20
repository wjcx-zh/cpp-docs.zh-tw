---
title: "編譯器警告 (層級 2) C4146 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4146"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4146"
ms.assetid: d6c31ab1-3120-40d5-8d80-32b5f7046e32
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 2) C4146
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

一元減號運算子套用 unsigned 型別，所得的結果也會是 unsigned 型別  
  
 不帶正負號型別只能保留非負數值，所以一元 \(Unary\) 減號 \(否定\) 套用至不帶正負號型別是沒有意義的動作。  運算元和結果兩者都是非負數的。  
  
 事實上，這種情形發生在程式設計人員試著表示最小整數值 \(\-2147483648\) 時。  這個值不能寫成 \-2147483648，因為運算式以兩階段處理：  
  
1.  計算出 2147483648 數字。  因為它比最大值 2147483647 還要大，所以 2147483648 的型別不是 [int](../../c-language/integer-types.md)，而是 `unsigned int`。  
  
2.  一元減號套用至此不帶正負號結果的值，碰巧它也是 2147483648。  
  
 不帶正負號型別的結果可能導致未預期的行為。  如果該結果會用來比較，那麼便可能使用不帶正負號的比較，例如，當另一個運算元是 `int` 時。  這點說明了為什麼下列的程式範例只會列印一行。  
  
 必須要有的第二行 `1 is greater than the most negative int` 並沒有列印出來，因為 `((unsigned int)1) > 2147483648`  是 False。  
  
 您可以使用 limits.h 的 INT\_MIN \(具有型別 **signed int**\)，避免產生 C4146。  
  
## 範例  
 下列範例會產生 C4146：  
  
```  
// C4146.cpp  
// compile with: /W2  
#include <stdio.h>  
  
void check(int i)   
{  
    if (i > -2147483648)   // C4146  
        printf_s("%d is greater than the most negative int\n", i);  
}  
  
int main()   
{  
    check(-100);  
    check(1);  
}  
```