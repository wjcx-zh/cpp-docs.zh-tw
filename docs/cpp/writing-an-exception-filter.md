---
title: "撰寫例外狀況篩選條件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "例外狀況處理, 篩選條件"
ms.assetid: 47fc832b-a707-4422-b60a-aaefe14189e5
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 撰寫例外狀況篩選條件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您可以藉由跳至例外狀況處理常式的層級或繼續執行的方式處理例外狀況。  除了使用例外狀況處理常式程式碼處理例外狀況並繼續之外，您可以使用 *filter* 清除問題，然後藉由傳回 – 1 繼續正常流程，而不清除堆疊。  
  
> [!NOTE]
>  某些例外狀況無法繼續執行。  如果這類例外狀況的 *filter* 判斷值為 – 1，則系統會引發新的例外狀況。  呼叫 [RaiseException](http://msdn.microsoft.com/library/windows/desktop/ms680552) 時，您就可判斷例外狀況是否會繼續。  
  
 例如，下列程式碼在 *filter* 運算式中使用函式呼叫：這個函式會處理問題，然後傳回 – 1，繼續進行控制項的正常流程：  
  
```  
// exceptions_Writing_an_Exception_Filter.cpp  
#include <windows.h>  
int main() {  
   int Eval_Exception( int );  
  
   __try {}  
  
   __except ( Eval_Exception( GetExceptionCode( ))) {  
      ;  
   }  
  
}  
void ResetVars( int ) {}  
int Eval_Exception ( int n_except ) {  
   if ( n_except != STATUS_INTEGER_OVERFLOW &&   
      n_except != STATUS_FLOAT_OVERFLOW )   // Pass on most exceptions  
   return EXCEPTION_CONTINUE_SEARCH;  
  
   // Execute some code to clean up problem  
   ResetVars( 0 );   // initializes data to 0  
   return EXCEPTION_CONTINUE_EXECUTION;  
}  
```  
  
 理想的方式是，只要 *filter* 需要進行複雜的工作，就在 *filter* 中使用函式呼叫。  評估運算式會讓函式執行，在這個案例中是 `Eval_Exception`。  
  
 請注意判斷例外狀況的 [GetExceptionCode](http://msdn.microsoft.com/library/windows/desktop/ms679356) 用法。  您必須在 filter 本身內呼叫這個函式。  `Eval_Exception` 無法呼叫 **GetExceptionCode**，不過必須將例外狀況代碼傳遞給它。  
  
 除非例外狀況是整數或浮點溢位，否則這個處理常式會將控制項傳遞至另一個處理常式。  如果是，處理常式會呼叫函式 \(`ResetVars` 只是範例，不是應用程式開發介面函式\) 重設部分全域變數。  *Statement\-block\-2* 在這個範例中是空的，由於 `Eval_Exception` 絕不會傳回 EXCEPTION\_EXECUTE\_HANDLER \(1\)，因此它永遠不會執行。  
  
 使用函式呼叫是處理複雜的篩選條件運算式時理想的通用技術。  另外兩項實用的 C 語言功能為：  
  
-   條件運算子  
  
-   逗號運算子  
  
 條件運算子通常很有用，因為它可以用來檢查特定傳回碼，然後傳回兩個不同值的其中一個。  例如，下列程式碼中的篩選條件只有在例外狀況是 `STATUS_INTEGER_OVERFLOW` 時，才會辨識例外狀況：  
  
```  
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ? 1 : 0 ) {  
```  
  
 這個案例中條件運算子的目的主要在於避免混淆，因為下列程式碼會產生相同的結果：  
  
```  
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ) {  
```  
  
 條件運算子在您想要將篩選條件評估為 – 1 \(EXCEPTION\_CONTINUE\_EXECUTION\) 的情況下更有用。  
  
 逗號運算子可讓您在單一運算式內執行多項獨立的運算。  這個效果大致上與執行多個陳述式，然後傳回最後一個運算式的值相同。  例如，下列程式碼會將例外狀況代碼儲存在變數中，然後進行測試：  
  
```  
__except( nCode = GetExceptionCode(), nCode == STATUS_INTEGER_OVERFLOW )  
```  
  
## 請參閱  
 [撰寫例外狀況處理常式](../cpp/writing-an-exception-handler.md)   
 [結構化例外狀況處理](../cpp/structured-exception-handling-c-cpp.md)