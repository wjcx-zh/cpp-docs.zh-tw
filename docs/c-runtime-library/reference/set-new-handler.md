---
title: "_set_new_handler | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_set_new_handler"
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
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_set_new_handler"
  - "set_new_handler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_set_new_handler 函式"
  - "錯誤處理"
  - "set_new_handler 函式"
  - "將控制權轉移到錯誤處理常式"
ms.assetid: 1d1781b6-5cf8-486a-b430-f365e0bb023f
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# _set_new_handler
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果 `new` 運算子無法配置記憶體，將控制權轉移給錯誤處理機制。  
  
## 語法  
  
```  
_PNH _set_new_handler(  
   _PNH pNewHandler   
);  
```  
  
#### 參數  
 `pNewHandler`  
 由應用程式所提供的記憶體處理函式的指標。  引數 0 會將新的處理常式移除。  
  
## 傳回值  
 傳回前一個由 `_set_new_handler` 註冊的轉譯器函式指標，如此前一個函式即可之後被還原。  如果先前函式未設定，則傳回值可用來還原預設行為；此值可能為 `NULL`。  
  
## 備註  
 如果 `new` 運算子無法配置記憶體，C\+\+ `_set_new_handler` 函式指定取得控制項的例外狀況處理函式。  如果 `new` 失敗，這個執行階段系統會自動呼叫當做引數傳遞至 `_set_new_handler`的例外狀況處理函式。  `_PNH`定義在 New.h，是傳回 `int` 型別並接受一個型別 `size_t` 為引述的函式之指標。  使用 `size_t` 指定欲配置的空間大小。  
  
 沒有預設處理常式。  
  
 `_set_new_handler` 基本上是記憶體回收配置方案。  如果您的函式傳回 0，則執行階段系統重新配置每次您的函式傳回非零的值及失敗時。  
  
 程式中 `_set_new_handler` 函式的發生會註冊引數清單中指定的例外狀況處理常式與執行階段系統。  
  
```  
#include <new.h>  
int handle_program_memory_depletion( size_t )  
{  
   // Your code  
}  
int main( void )  
{  
   _set_new_handler( handle_program_memory_depletion );  
   int *pi = new int[BIG_NUMBER];  
}  
```  
  
 您可以保留最後會傳遞至 `_set_new_handler` 函式的函式位址並之後再還原它：  
  
```  
_PNH old_handler = _set_new_handler( my_handler );  
   // Code that requires my_handler  
   _set_new_handler( old_handler )  
   // Code that requires old_handler  
```  
  
 C\+\+ [\_set\_new\_mode](../../c-runtime-library/reference/set-new-mode.md) 函式會設定 [](../../c-runtime-library/reference/malloc.md "malloc") 的新處理常式模式。  失敗時，新的處理常式模式表示 `malloc` 是否要呼叫由 `_set_new_handler` 設定的新處理常式。  根據預設， `malloc` 不會在無法配置記憶體時呼叫新的處理常式。  您可以覆寫這個預設行為，因此，當 `malloc` 無法配置記憶體時，`malloc` 會以 `new` 運算子因相同原因失敗時所執行的相同方式，呼叫新處理常式。  若要覆寫預設值，請呼叫：  
  
```  
_set_new_mode(1)  
```  
  
 及早在您的程式中呼叫，或與 Newmode.obj 連結。  
  
 如果提供使用者定義的 `operator new`，新處理常式函式不會自動呼叫失敗。  
  
 如需詳細資訊，請參閱 *C\+\+ 語言參考* 中的 [建立](../../cpp/new-operator-cpp.md) 和 [刪除](../../cpp/delete-operator-cpp.md)。  
  
 所有動態連接的 DLL 或可執行檔具有單一 `_set_new_handler` 處理常式；即使您呼叫 `_set_new_handler` 您的處理常式可能由另一個取代或由另一個 DLL 或可執行檔集取代的處理常式。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_set_new_handler`|\<new.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
 在此範例中，配置失敗時，控制權會轉移到 MyNewHandler。  傳遞至 MyNewHandler 的引數是所要求的位元組數目。  從 MyNewHandler 傳回的值是應該重試配置的旗標：非零值表示應該重試配置，而零值則表示配置失敗。  
  
```  
// crt_set_new_handler.cpp  
// compile with: /c  
#include <stdio.h>  
#include <new.h>  
#define BIG_NUMBER 0x1fffffff  
  
int coalesced = 0;  
  
int CoalesceHeap()  
{  
   coalesced = 1;  // Flag RecurseAlloc to stop   
   // do some work to free memory  
   return 0;  
}  
// Define a function to be called if new fails to allocate memory.  
int MyNewHandler( size_t size )  
{  
   printf("Allocation failed. Coalescing heap.\n");  
  
   // Call a function to recover some heap space.  
   return CoalesceHeap();  
}  
  
int RecurseAlloc() {  
   int *pi = new int[BIG_NUMBER];  
   if (!coalesced)  
      RecurseAlloc();  
   return 0;  
}  
  
int main()  
{  
   // Set the failure handler for new to be MyNewHandler.  
   _set_new_handler( MyNewHandler );  
   RecurseAlloc();  
}  
```  
  
  **Allocation failed.  Coalescing heap.**  
**This application has requested the Runtime to terminate it in an unusual way.**  
**Please contact the application's support team for more information.**    
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)