---
title: _resetstkoflw
ms.date: 4/2/2020
api_name:
- _resetstkoflw
- _o__resetstkoflw
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- resetstkoflw
- _resetstkoflw
helpviewer_keywords:
- resetstkoflw function
- stack overflow
- stack, recovering
- _resetstkoflw function
ms.assetid: 319529cd-4306-4d22-810b-2063f3ad9e14
ms.openlocfilehash: dfe0de4f48173a0e79bcdcfb24bfdf7a21f47a04
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332810"
---
# <a name="_resetstkoflw"></a>_resetstkoflw

從堆疊溢位復原。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int _resetstkoflw( void );
```

## <a name="return-value"></a>傳回值

如果函式成功則為非零值，失敗則為 0。

## <a name="remarks"></a>備註

**_resetstkoflw**函數從堆疊溢出條件中恢復,允許程序繼續,而不是由於致命異常錯誤而失敗。 如果未調用 **_resetstkoflw**函數,則上一個異常之後沒有保護頁。 下次發生堆疊溢位時，完全沒有任何例外狀況，且處理序會終止而不發出警告。

如果應用程式中的執行緒造成 **EXCEPTION_STACK_OVERFLOW** 例外狀況，執行緒的堆疊便已處於損毀狀態。 這與其他例外狀況，例如 **EXCEPTION_ACCESS_VIOLATION** 或 **EXCEPTION_INT_DIVIDE_BY_ZERO** 相反，它們的堆疊並未損毀。 程式第一次載入時，堆疊會設定為很小的值。 然後堆疊會視需要成長，以符合執行緒的需要。 這樣的實作方法是在目前堆疊結尾處放置具有 PAGE_GUARD 存取的頁面。 如需詳細資訊，請參閱 [Creating Guard Pages](/windows/win32/Memory/creating-guard-pages) (建立防護頁面)。

當程式碼造成堆疊指標指向這個頁面上的位址時，會發生例外狀況，且系統會執行下列三件事︰

- 移除防護頁面上的 PAGE_GUARD 保護，使執行緒可以讀取和寫入記憶體中的資料。

- 配置新的防護頁面，位於前一個防護頁面的下方一個頁面。

- 重新執行引發例外狀況的指令。

如此一來，系統可以自動增加執行緒的堆疊大小。 處理序中的每個執行緒都有最大堆疊大小。 堆疊大小在編譯時期由 [/STACK (堆疊配置)](../../build/reference/stack-stack-allocations.md) 所設定，或是由專案 .def 檔案中的 [STACKSIZE](../../build/reference/stacksize.md) 陳述式設定。

當超過這個最大堆疊大小時，系統會執行下列三件事︰

- 移除防護頁面上的 PAGE_GUARD 保護，如先前所述。

- 嘗試在前一個防護頁面下方配置新的防護頁面。 不過，這會失敗，因為已經超過最大堆疊大小。

- 引發例外狀況，使執行緒可以在例外狀況區塊中處理它。

請注意，此時，堆疊不再有防護頁面。 下次程式堆疊一直成長到最後時，在該處應該有防護頁面，程式會寫入超過堆疊的結尾，並造成存取違規。

呼叫 **_resetstkoflw,** 在堆疊溢出異常後完成恢復時恢復保護頁。 此功能可以從 **__except**塊的主體內部或 **__except**塊外部調用。 不過，它的使用時機有一些限制。 **_resetstkoflw 絕不**應從:

- 篩選條件運算式。

- 篩選函式。

- 從篩選函式呼叫的函式。

- **catch** 區塊。

- **__finally**塊。

在這些點，堆疊尚無法充分回溯。

堆疊溢出異常作為結構化異常生成,而不是C++異常,因此 **_resetstkoflw**在普通**catch**塊中沒有用處,因為它不會捕獲堆疊溢出異常。 不過，如果 [_set_se_translator](set-se-translator.md) 用來實作結構化例外狀況轉譯器，擲回 C++ 例外狀況 (如第二個範例中)，堆疊溢位例外狀況會造成 C++ 例外狀況，而可以由 C++ catch 區塊處理。

在從結構化例外狀況翻譯器函式所擲回例外狀況達到的 C++ catch 區塊中呼叫 **_resetstkoflw** 並不安全。 在此情況下，不會釋放堆疊空間，而且一直達到 catch 區塊之外以前都不會重設堆疊指標，即使已經在 catch 區塊之前呼叫任何可破壞物件的解構函式。 在堆疊空間釋放且堆疊指標重設之前，不應該呼叫此函式。 因此，它只應該在結束 catch 區塊之後呼叫。 在 catch 區塊中應該盡可能減少使用堆疊空間，因為如果堆疊溢位發生在 catch 區塊中，而 catch 區塊本身正在嘗試從先前堆疊溢位復原時，這樣的堆疊溢位是無法復原的，並且可能造成程式停止回應，因為 catch 區塊中的溢位會觸發例外狀況，該例外狀況又是由相同的 catch 區塊處理。

在有些情況下 **_resetstkoflw** 可能會失敗，即使是使用於正確的位置，例如在 **__except** 區塊內。 如果即使是在回溯堆疊之後，仍沒有足夠的堆疊空間可執行 **_resetstkoflw** 而不寫入至堆疊的最後一頁，那麼 **_resetstkoflw** 便無法將堆疊的最後一頁重設為防護頁面，並且會傳回 0，表示失敗。 因此，安全地使用此函式應該要包含檢查傳回值，而不是假設堆疊的使用是安全的。

使用 **/clr**編譯應用程式時,結構化異常處理不會捕獲**STATUS_STACK_OVERFLOW**異常(請參閱[/clr(通用語言運行時編譯)。](../../build/reference/clr-common-language-runtime-compilation.md)

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_resetstkoflw**|\<malloc.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

**程式庫︰** 所有版本的 [CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

下面的示例顯示了 **_resetstkoflw**函數的建議用法。

```C
// crt_resetstkoflw.c
// Launch program with and without arguments to observe
// the difference made by calling _resetstkoflw.

#include <malloc.h>
#include <stdio.h>
#include <windows.h>

void recursive(int recurse)
{
   _alloca(2000);
   if (recurse)
      recursive(recurse);
}

// Filter for the stack overflow exception.
// This function traps the stack overflow exception, but passes
// all other exceptions through.
int stack_overflow_exception_filter(int exception_code)
{
   if (exception_code == EXCEPTION_STACK_OVERFLOW)
   {
       // Do not call _resetstkoflw here, because
       // at this point, the stack is not yet unwound.
       // Instead, signal that the handler (the __except block)
       // is to be executed.
       return EXCEPTION_EXECUTE_HANDLER;
   }
   else
       return EXCEPTION_CONTINUE_SEARCH;
}

int main(int ac)
{
   int i = 0;
   int recurse = 1, result = 0;

   for (i = 0 ; i < 10 ; i++)
   {
      printf("loop #%d\n", i + 1);
      __try
      {
         recursive(recurse);

      }

      __except(stack_overflow_exception_filter(GetExceptionCode()))
      {
         // Here, it is safe to reset the stack.

         if (ac >= 2)
         {
            puts("resetting stack overflow");
            result = _resetstkoflw();
         }
      }

      // Terminate if _resetstkoflw failed (returned 0)
      if (!result)
         return 3;
   }

   return 0;
}
```

沒有程式參數的取樣輸出:

```Output
loop #1
```

程式停止回應，而不執行進一步的反覆項目。

含程式引數：

```Output
loop #1
resetting stack overflow
loop #2
resetting stack overflow
loop #3
resetting stack overflow
loop #4
resetting stack overflow
loop #5
resetting stack overflow
loop #6
resetting stack overflow
loop #7
resetting stack overflow
loop #8
resetting stack overflow
loop #9
resetting stack overflow
loop #10
resetting stack overflow
```

### <a name="description"></a>描述

下面的示例演示了在將結構化異常轉換為C++異常的程序中建議使用 **_resetstkoflw。**

### <a name="code"></a>程式碼

```cpp
// crt_resetstkoflw2.cpp
// compile with: /EHa
// _set_se_translator requires the use of /EHa
#include <malloc.h>
#include <stdio.h>
#include <windows.h>
#include <eh.h>

class Exception { };

class StackOverflowException : Exception { };

// Because the overflow is deliberate, disable the warning that
// this function will cause a stack overflow.
#pragma warning (disable: 4717)
void CauseStackOverflow (int i)
{
    // Overflow the stack by allocating a large stack-based array
    // in a recursive function.
    int a[10000];
    printf("%d ", i);
    CauseStackOverflow (i + 1);
}

void __cdecl SEHTranslator (unsigned int code, _EXCEPTION_POINTERS*)
{
    // For stack overflow exceptions, throw our own C++
    // exception object.
    // For all other exceptions, throw a generic exception object.
    // Use minimal stack space in this function.
    // Do not call _resetstkoflw in this function.

    if (code == EXCEPTION_STACK_OVERFLOW)
        throw StackOverflowException ( );
    else
        throw Exception( );
}

int main ( )
{
    bool stack_reset = false;
    bool result = false;

    // Set up a function to handle all structured exceptions,
    // including stack overflow exceptions.
    _set_se_translator (SEHTranslator);

    try
    {
        CauseStackOverflow (0);
    }
    catch (StackOverflowException except)
    {
        // Use minimal stack space here.
        // Do not call _resetstkoflw here.
        printf("\nStack overflow!\n");
        stack_reset = true;
    }
    catch (Exception except)
    {
        // Do not call _resetstkoflw here.
        printf("\nUnknown Exception!\n");
    }
    if (stack_reset)
    {
        result = _resetstkoflw();
        // If stack reset failed, terminate the application.
        if (result == 0)
            exit(1);
    }

    void* pv = _alloca(100000);
    printf("Recovered from stack overflow and allocated 100,000 bytes"
           " using _alloca.");

    return 0;
}
```

```Output
0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24
Stack overflow!
Recovered from stack overflow and allocated 100,000 bytes using _alloca.
```

## <a name="see-also"></a>另請參閱

[_alloca](alloca.md)<br/>
