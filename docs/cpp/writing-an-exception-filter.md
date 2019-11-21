---
title: 撰寫例外狀況篩選條件
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling [C++], filters
ms.assetid: 47fc832b-a707-4422-b60a-aaefe14189e5
ms.openlocfilehash: aaf0dc77207399d7c6be86127d7decf03895ced5
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245992"
---
# <a name="writing-an-exception-filter"></a>撰寫例外狀況篩選條件

您可以藉由跳至例外狀況處理常式的層級或繼續執行的方式處理例外狀況。 Instead of using the exception handler code to handle the exception and falling through, you can use *filter* to clean up the problem and then, by returning -1, resume normal flow without clearing the stack.

> [!NOTE]
>  某些例外狀況無法繼續執行。 If *filter* evaluates to -1 for such an exception, the system raises a new exception. When you call [RaiseException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raiseexception), you determine whether the exception will continue.

For example, the following code uses a function call in the *filter* expression: this function handles the problem and then returns -1 to resume normal flow of control:

```cpp
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

It is a good idea to use a function call in the *filter* expression whenever *filter* needs to do anything complex. 評估運算式會讓函式執行，在這個案例中是 `Eval_Exception`。

Note the use of [GetExceptionCode](/windows/win32/Debug/getexceptioncode) to determine the exception. 您必須在 filter 本身內呼叫這個函式。 `Eval_Exception` cannot call `GetExceptionCode`, but it must have the exception code passed to it.

除非例外狀況是整數或浮點溢位，否則這個處理常式會將控制項傳遞至另一個處理常式。 如果是，處理常式會呼叫函式 (`ResetVars` 只是範例，不是應用程式開發介面函式) 重設部分全域變數。 *Statement-block-2*, which in this example is empty, can never be executed because `Eval_Exception` never returns EXCEPTION_EXECUTE_HANDLER (1).

使用函式呼叫是處理複雜的篩選條件運算式時理想的通用技術。 另外兩項實用的 C 語言功能為：

- 條件運算子

- 逗號運算子

條件運算子通常很有用，因為它可以用來檢查特定傳回碼，然後傳回兩個不同值的其中一個。 For example, the filter in the following code recognizes the exception only if the exception is STATUS_INTEGER_OVERFLOW:

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ? 1 : 0 ) {
```

這個案例中條件運算子的目的主要在於避免混淆，因為下列程式碼會產生相同的結果：

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ) {
```

The conditional operator is more useful in situations where you might want the filter to evaluate to -1, EXCEPTION_CONTINUE_EXECUTION.

逗號運算子可讓您在單一運算式內執行多項獨立的運算。 這個效果大致上與執行多個陳述式，然後傳回最後一個運算式的值相同。 例如，下列程式碼會將例外狀況代碼儲存在變數中，然後進行測試：

```cpp
__except( nCode = GetExceptionCode(), nCode == STATUS_INTEGER_OVERFLOW )
```

## <a name="see-also"></a>請參閱

[Writing an exception handler](../cpp/writing-an-exception-handler.md)<br/>
[結構化例外狀況處理 (C/C++)](../cpp/structured-exception-handling-c-cpp.md)