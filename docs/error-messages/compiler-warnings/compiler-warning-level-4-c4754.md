---
title: "編譯器警告 (層級 4) C4754 | Microsoft Docs"
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
  - "C4754"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4754"
ms.assetid: e0e4606a-754a-4f42-a274-21a34978d21d
caps.latest.revision: 6
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 4) C4754
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

比較中有算術運算的轉換規則，表示有一個分支無法執行到。  
  
 因為比較結果永遠相同， 所以發出 C4754 警告。  這表示一個條件的分支永遠不會執行，很可能因為關聯的整數運算式是無效的。  這個程式碼缺失最常發生於 64 位的錯誤整數溢位檢查。  
  
 整數轉換規則很複雜，而且有許多微妙的陷阱。  一個修正每個 C4754 警告的替代方式為，您可以更新程式碼使用 [SafeInt 程式庫](../../windows/safeint-library.md)。  
  
## 範例  
 這個範例產生 C4754：  
  
```cpp  
// C4754a.cpp  
// Compile with: /W4 /c  
#include "errno.h"  
  
int sum_overflow(unsigned long a, unsigned long b)   
{  
   unsigned long long x = a + b; // C4754  
  
   if (x > 0xFFFFFFFF)   
   {  
      // never executes!  
      return EOVERFLOW;  
   }  
   return 0;  
}  
```  
  
 於向上轉型成 64 位元的值和指派值給 64 位元變數 `x`之前，加法 `a + b` 可能造成了算術溢位。  這表示在 `x` 中檢查是多餘的，永遠不會攔截到溢位。  在這種情況下，編譯器就會發出這個警告:  
  
  **警告 C4754: 數學運算的轉換規則在 C4754a.cpp \(7\) 表示一項分支無法被執行。  請將 '\(a \+ ...\)' 轉換成 'ULONG64' \(或 8 位元組的類似類型\)。**  若要排除警告，您可以變更指派陳述式轉型運算元為 8 位元的值:  
  
```cpp  
// Casting one operand is sufficient to force all the operands in   
// the addition be upcast according to C/C++ conversion rules, but  
// casting both is clearer.  
unsigned long long x =   
   (unsigned long long)a + (unsigned long long)b;  
```  
  
## 範例  
 接下來的範例也會產生 C4754。  
  
```cpp  
// C4754b.cpp  
// Compile with: /W4 /c  
#include "errno.h"  
  
int wrap_overflow(unsigned long a)   
{  
   if (a + sizeof(unsigned long) < a) // C4754  
   {   
      // never executes!  
      return EOVERFLOW;  
   }  
   return 0;  
}  
```  
  
 `sizeof()` 運算子會傳回 `size_t`，大小為架構相關。  範例程式碼於 32 位元架構上運作，而 `size_t` 是 32 位元的型別。  不過，在 64 位元結構， `size_t` 是一個 64 位元的型別。  整數的轉換規則表示 `a` 是向上轉型至運算式 `a + b < a` 的 64 位元值，如同寫成 `(size_t)a + (size_t)b < (size_t)a`。  當 `a` 和 `b` 都是 32 位元整數時， 64 位元加法作業不會溢位，且限制式永不成立。  因此，程式碼不會偵測到 64 位元架構的整數溢位狀況。  這個範例會使編譯器發出這個警告:  
  
  **警告 C4754: 數學運算的轉換規則在 C4754b.cpp \(7\) 表示一項分支無法被執行。  cast '4' 到 'ULONG' \(或 4 個位元組的相似類型\)。**  請注意這個警告訊息明確列出常數值 4 而不是由分析警告發生違規的程式碼之時間的原始來源，當警告分析遇到違規的原始碼， `sizeof(unsigned long)` 已轉換為常數。  因此，您可能必須搜尋這個警告訊息的常數值在原始程式碼的運算式。  程式碼常在在 C4754 警告訊息中解析到的常數運算式，如 `sizeof(TYPE)` 和 `strlen(szConstantString)`。  
  
 在這種情況下，固定的程式碼會看起來像這樣:  
  
```cpp  
// Casting the result of sizeof() to unsigned long ensures  
// that all the addition operands are 32-bit, so any overflow   
// is detected by the check.  
if (a + (unsigned long)sizeof(unsigned long) < a)  
  
```  
  
 **注意事項** 在編譯器警告參考的行號是陳述式的最後一行。  在多行的複雜條件陳述式的警告訊息，程式碼缺失可能是在報告的幾行之前。  例如：  
  
```cpp  
unsigned long a;  
  
if (a + sizeof(unsigned long) < a || // incorrect check  
    condition1() ||   
    a == 0) {    // C4754 warning reported on this line  
         // never executes!  
         return INVALID_PARAMETER;  
}  
  
```