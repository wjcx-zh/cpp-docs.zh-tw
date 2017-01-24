---
title: "_resetstkoflw | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_resetstkoflw"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "resetstkoflw"
  - "_resetstkoflw"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_resetstkoflw 函式"
  - "resetstkoflw 函式"
  - "堆疊溢位"
  - "堆疊, 復原"
ms.assetid: 319529cd-4306-4d22-810b-2063f3ad9e14
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _resetstkoflw
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從堆疊溢位中復原。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
  
int _resetstkoflw ( void );  
  
```  
  
## 傳回值  
 如果函式成功則非零，失敗則為零。  
  
## 備註  
 `_resetstkoflw` 函式可從堆疊溢位的情況中復原，讓程式得以繼續執行，不會因嚴重的例外狀況錯誤而失敗。  如果未呼叫 `_resetstkoflw` 函式，則在上述的例外狀況之後不會產生保護分頁。  下次發生堆疊溢位時，完全不會有例外狀況，且會在沒有產生警告的情況下結束此處理序。  
  
 如果在應用程式中的執行緒會產生 **EXCEPTION\_STACK\_OVERFLOW** 例外狀況時，執行緒是使自己的堆疊處於損毀狀態。  與其他例外狀況比較，例如 **EXCEPTION\_ACCESS\_VIOLATION** 或 **EXCEPTION\_INT\_DIVIDE\_BY\_ZERO**則是堆疊無損壞的情況。  當程式第一次載入時，堆疊設為一個小的隨機值。  堆疊再來會依執行緒需求調整為想要的大小。  方法為代換頁面為目前堆疊最末端的 PAGE\_GUARD 存取。  如需詳細資訊，請參閱[建立保護頁面](http://msdn.microsoft.com/library/windows/desktop/aa366549)。  
  
 當程式碼造成堆疊指標指向這個頁面的位址時，例外狀況會出現並且系統會做下列三件事情:  
  
-   移除保護網頁的 PAGE\_GUARD 保護，讓執行緒可以寫入和讀取記憶體資料。  
  
-   配置一個新保護網頁，此頁面接在最後一個頁面之後。  
  
-   重新執行引發例外狀況的指示。  
  
 如此一來，系統可以為執行緒自動加大堆疊的大小。  處理序中的每個執行緒有堆疊大小的上限。  堆疊大小在編譯時期由 [\/STACK \(堆疊配置\)](../../build/reference/stack-stack-allocations.md)，或是在 .def 檔中的 [STACKSIZE](../../build/reference/stacksize.md) 陳述式的專案設定。  
  
 當超過這個最大堆疊大小時，系統會做下列三件事情:  
  
-   如前所述，移除保護網頁的 PAGE\_GUARD 保護。  
  
-   嘗試在最後一個網頁後配置一個新的保護網頁。  然而，因最大堆疊大小已超過所以會失敗。  
  
-   引發一個例外狀況，以便執行緒可以在例外狀況區塊處理它。  
  
 請注意此時堆疊不會產生保護分頁。  下次程式隨時增加到堆疊的末端，最末端會產生一個保護分頁，寫入在此堆疊後面的程式會造成存取違規。  
  
 每當在復原堆疊溢位的例外狀況完成後，會呼叫 `_resetstkoflw` 還原保護頁面。  這個函式可從 `__except` 區塊內部主體呼叫或是 **\_\_except** 區塊的外部呼叫。  不過在使用時，仍然有一些限制存在。  `_resetstkoflw`不應該從以下地方呼叫:  
  
-   篩選條件運算式。  
  
-   一個 filter 函式。  
  
-   從篩選函式呼叫的函式。  
  
-   **catch** 區塊。  
  
-   `__finally` 區塊。  
  
 在這幾個地方，堆疊還不會回溯。  
  
 堆疊溢位例外狀況會以結構化例外狀況產生，因此 `_resetstkoflw` 不適用於一般 **catch** 區塊，因為它不會攔截堆疊溢位例外狀況。  不過，如果 [\_set\_se\_translator](../../c-runtime-library/reference/set-se-translator.md) 用來實作傳回 C\+\+ 例外狀況的結構化的例外狀況轉譯器 \(第二個範例中\)，C\+\+ 例外狀況的堆疊溢位例外狀況產生可由 C \+\+ catch 區塊處理。  
  
 在 C \+\+ catch 區塊呼叫 **\_resetstkoflw**  從結構化例外狀況轉譯函式所擲回的例外狀況是不安全的。  在這種情況下，堆疊空間不會釋放，且堆疊指標不會重設到 catch 區塊之外，即使在 Catch 區塊之前解構函式由可終結物件被呼叫。  此函式不應該被呼叫，直到堆疊空間被釋放且堆疊指標重設。  因此，應該在離開 catch 區塊之後再呼叫它。  盡可能不要在 catch 區塊中使用堆疊空間，因為在 catch 區塊本身就會嘗試復原先前不可復原的堆疊溢位 \(Stack Overflow\) ，且在 catch 區塊的溢位觸發本身同一個 catch 區塊處理的例外狀況可能造成程式停止回應。  
  
 **\_resetstkoflw** 在正確的位置下仍可能會失敗，例如在 **\_\_except**  區塊內。  如果，在回溯堆疊後，在不寫入堆疊的最後一頁的情況下，仍然是以不足夠的堆疊空間執行 **\_resetstkoflw** ， **\_resetstkoflw** 會因為保護網頁失敗，並傳回 0，。  因此，這個函式的正確使用方式應該包括檢查傳回值而非假設此堆疊是保證不會出錯的。  
  
 結構化例外處理 \(Exception Handling\) 將不會攔截 `STATUS_STACK_OVERFLOW` 例外狀況，在編譯應用程式與 `/clr` 或 `/clr:pure` \(請參閱 [\/clr \(Common Language Runtime 編譯\)](../../build/reference/clr-common-language-runtime-compilation.md)\)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_resetstkoflw`|\<malloc.h\>|  
  
 如需詳細的相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
 **程式庫:** [CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
 下列範例為 `_resetstkoflw` 函式的推薦使用方法。  
  
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
  
## 範例輸出  
 沒有程式引數:  
  
```  
loop #1  
```  
  
 程式停止回應，而不執行下一步的反覆項目。  
  
 含有程式引數:  
  
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
  
### 描述  
 下列範例為 `_resetstkoflw` 在有結構化的例外狀況被轉換成 C\+\+ 的程式推薦用法。  
  
### 程式碼  
  
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
  
## 範例輸出  
  
```  
0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24  
Stack overflow!  
Recovered from stack overflow and allocated 100,000 bytes using _alloca.  
```  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [\_alloca](../../c-runtime-library/reference/alloca.md)