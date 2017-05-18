---
title: _resetstkoflw | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _resetstkoflw
apilocation:
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
apitype: DLLExport
f1_keywords:
- resetstkoflw
- _resetstkoflw
dev_langs:
- C++
helpviewer_keywords:
- resetstkoflw function
- stack overflow
- stack, recovering
- _resetstkoflw function
ms.assetid: 319529cd-4306-4d22-810b-2063f3ad9e14
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 16d166f205f026977673e39bd539b377496bdc0c
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="resetstkoflw"></a>_resetstkoflw
從堆疊溢位復原。  
  
> [!IMPORTANT]
>  這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>語法  
  
```  
  
int _resetstkoflw ( void );  
  
```  
  
## <a name="return-value"></a>傳回值  
 如果函式成功則為非零值，失敗則為 0。  
  
## <a name="remarks"></a>備註  
 `_resetstkoflw` 函式從堆疊溢位狀況復原，讓程式繼續執行而不是因嚴重的例外狀況錯誤而失敗。 如果未呼叫 `_resetstkoflw` 函式，在前一個例外狀況之後便沒有防護頁面。 下次發生堆疊溢位時，完全沒有任何例外狀況，且處理序會終止而不發出警告。  
  
 如果應用程式中的執行緒造成 **EXCEPTION_STACK_OVERFLOW** 例外狀況，執行緒的堆疊便已處於損毀狀態。 這與其他例外狀況，例如 **EXCEPTION_ACCESS_VIOLATION** 或 **EXCEPTION_INT_DIVIDE_BY_ZERO** 相反，它們的堆疊並未損毀。 程式第一次載入時，堆疊會設定為很小的值。 然後堆疊會視需要成長，以符合執行緒的需要。 這樣的實作方法是在目前堆疊結尾處放置具有 PAGE_GUARD 存取的頁面。 如需詳細資訊，請參閱 [Creating Guard Pages](http://msdn.microsoft.com/library/windows/desktop/aa366549) (建立防護頁面)。  
  
 當程式碼造成堆疊指標指向這個頁面上的位址時，會發生例外狀況，且系統會執行下列三件事︰  
  
-   移除防護頁面上的 PAGE_GUARD 保護，使執行緒可以讀取和寫入記憶體中的資料。  
  
-   配置新的防護頁面，位於前一個防護頁面的下方一個頁面。  
  
-   重新執行引發例外狀況的指令。  
  
 如此一來，系統可以自動增加執行緒的堆疊大小。 處理序中的每個執行緒都有最大堆疊大小。 堆疊大小在編譯時期由 [/STACK (堆疊配置)](../../build/reference/stack-stack-allocations.md) 所設定，或是由專案 .def 檔案中的 [STACKSIZE](../../build/reference/stacksize.md) 陳述式設定。  
  
 當超過這個最大堆疊大小時，系統會執行下列三件事︰  
  
-   移除防護頁面上的 PAGE_GUARD 保護，如先前所述。  
  
-   嘗試在前一個防護頁面下方配置新的防護頁面。 不過，這會失敗，因為已經超過最大堆疊大小。  
  
-   引發例外狀況，使執行緒可以在例外狀況區塊中處理它。  
  
 請注意，此時，堆疊不再有防護頁面。 下次程式堆疊一直成長到最後時，在該處應該有防護頁面，程式會寫入超過堆疊的結尾，並造成存取違規。  
  
 每當發生堆疊溢位例外狀況之後完成復原時，請呼叫 `_resetstkoflw` 還原防護頁面。 此函式可以從 `__except` 區塊主體內呼叫，或是在 **__except** 區塊之外呼叫。 不過，它的使用時機有一些限制。 `_resetstkoflw` 永遠不可從下列位置呼叫︰  
  
-   篩選條件運算式。  
  
-   篩選函式。  
  
-   從篩選函式呼叫的函式。  
  
-   **catch** 區塊。  
  
-   `__finally` 區塊。  
  
 在這些點，堆疊尚無法充分回溯。  
  
 堆疊溢位例外狀況會產生為結構化例外狀況，而不是 C++ 例外狀況，因此 `_resetstkoflw` 並不適用於一般 **catch** 區塊，因為它不會攔截堆疊溢位例外狀況。 不過，如果 [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md) 用來實作結構化例外狀況轉譯器，擲回 C++ 例外狀況 (如第二個範例中)，堆疊溢位例外狀況會造成 C++ 例外狀況，而可以由 C++ catch 區塊處理。  
  
 在從結構化例外狀況翻譯器函式所擲回例外狀況達到的 C++ catch 區塊中呼叫 **_resetstkoflw** 並不安全。 在此情況下，不會釋放堆疊空間，而且一直達到 catch 區塊之外以前都不會重設堆疊指標，即使已經在 catch 區塊之前呼叫任何可破壞物件的解構函式。 在堆疊空間釋放且堆疊指標重設之前，不應該呼叫此函式。 因此，它只應該在結束 catch 區塊之後呼叫。 在 catch 區塊中應該盡可能減少使用堆疊空間，因為如果堆疊溢位發生在 catch 區塊中，而 catch 區塊本身正在嘗試從先前堆疊溢位復原時，這樣的堆疊溢位是無法復原的，並且可能造成程式停止回應，因為 catch 區塊中的溢位會觸發例外狀況，該例外狀況又是由相同的 catch 區塊處理。  
  
 在有些情況下 **_resetstkoflw** 可能會失敗，即使是使用於正確的位置，例如在 **__except** 區塊內。 如果即使是在回溯堆疊之後，仍沒有足夠的堆疊空間可執行 **_resetstkoflw** 而不寫入至堆疊的最後一頁，那麼 **_resetstkoflw** 便無法將堆疊的最後一頁重設為防護頁面，並且會傳回 0，表示失敗。 因此，安全地使用此函式應該要包含檢查傳回值，而不是假設堆疊的使用是安全的。  
  
 結構化例外狀況處理不會抓取`STATUS_STACK_OVERFLOW`應用程式編譯時的例外狀況`/clr`(請參閱[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md))。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_resetstkoflw`|\<malloc.h>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
 **程式庫︰**所有版本的 [CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="example"></a>範例  
 下列範例顯示 `_resetstkoflw` 函式的建議用法。  
  
```  
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
  
## <a name="sample-output"></a>範例輸出  
 不含程式引數：  
  
```  
loop #1  
```  
  
 程式停止回應，而不執行進一步的反覆項目。  
  
 含程式引數：  
  
```  
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
 下列範例將示範 `_resetstkoflw` 在程式中的建議用法，在該程式中，結構化例外狀況會轉換成 C++ 例外狀況。  
  
### <a name="code"></a>程式碼  
  
```  
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
  
## <a name="sample-output"></a>範例輸出  
  
```  
0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24  
Stack overflow!  
Recovered from stack overflow and allocated 100,000 bytes using _alloca.  
```  
  
## <a name="see-also"></a>另請參閱  
 [_alloca](../../c-runtime-library/reference/alloca.md)
