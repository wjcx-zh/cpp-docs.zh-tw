---
title: 撰寫例外狀況篩選條件
ms.date: 11/04/2016
helpviewer_keywords:
- exception handling [C++], filters
ms.assetid: 47fc832b-a707-4422-b60a-aaefe14189e5
ms.openlocfilehash: 05d3aa79d1293001e80a77b3171b7a4607cd81c7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369490"
---
# <a name="writing-an-exception-filter"></a>撰寫例外狀況篩選條件

您可以藉由跳至例外狀況處理常式的層級或繼續執行的方式處理例外狀況。 您可以使用*篩選器*來清理問題,然後返回 -1,在不清除堆疊的情況下恢復正常流,而不是使用異常處理程式代碼來處理異常並中斷。

> [!NOTE]
> 某些例外狀況無法繼續執行。 如果*篩選器*對於此類異常計算為 -1,則系統將引發新的異常。 當您呼叫[「提升異常](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raiseexception)」時,您可以確定異常是否將繼續。

例如,以下代碼在*篩選器*表示式中使用函數呼叫:此函數處理問題,然後返回 -1 以復原正常的控制流:

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

最好在*篩選器*運算式中使用函數調用,每當*篩選器*需要執行任何複雜操作時。 評估運算式會讓函式執行，在這個案例中是 `Eval_Exception`。

請注意使用[GetExceptionCode](/windows/win32/Debug/getexceptioncode)來確定異常。 您必須在 filter 本身內呼叫這個函式。 `Eval_Exception`無法呼叫`GetExceptionCode`,但它必須將異常代碼傳遞給它。

除非例外狀況是整數或浮點溢位，否則這個處理常式會將控制項傳遞至另一個處理常式。 如果是，處理常式會呼叫函式 (`ResetVars` 只是範例，不是應用程式開發介面函式) 重設部分全域變數。 *語句-塊-2*(在此示例中為空)永遠無法執行,`Eval_Exception`因為 永遠不會返回EXCEPTION_EXECUTE_HANDLER (1)。

使用函式呼叫是處理複雜的篩選條件運算式時理想的通用技術。 另外兩項實用的 C 語言功能為：

- 條件運算子

- 逗號運算子

條件運算子通常很有用，因為它可以用來檢查特定傳回碼，然後傳回兩個不同值的其中一個。 例如,只有在異常STATUS_INTEGER_OVERFLOW時,以下代碼中的篩選器才會識別異常:

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ? 1 : 0 ) {
```

這個案例中條件運算子的目的主要在於避免混淆，因為下列程式碼會產生相同的結果：

```cpp
__except( GetExceptionCode() == STATUS_INTEGER_OVERFLOW ) {
```

條件運算子在您可能希望篩選器計算到 -1、EXCEPTION_CONTINUE_EXECUTION的情況下更有用。

逗號運算子可讓您在單一運算式內執行多項獨立的運算。 這個效果大致上與執行多個陳述式，然後傳回最後一個運算式的值相同。 例如，下列程式碼會將例外狀況代碼儲存在變數中，然後進行測試：

```cpp
__except( nCode = GetExceptionCode(), nCode == STATUS_INTEGER_OVERFLOW )
```

## <a name="see-also"></a>另請參閱

[編寫錯誤程式](../cpp/writing-an-exception-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
