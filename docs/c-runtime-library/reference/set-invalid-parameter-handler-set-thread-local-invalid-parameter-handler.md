---
title: "_set_invalid_parameter_handler _set_thread_local_invalid_parameter_handler | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_set_invalid_parameter_handler"
  - "_set_thread_local_invalid_parameter_handler"
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
  - "set_invalid_parameter_handler"
  - "_set_invalid_parameter_handler"
  - "_set_thread_local_invalid_parameter_handler"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "無效的參數處理常式"
  - "set_invalid_parameter_handler 函式"
  - "_set_invalid_parameter_handler 函式"
  - "_set_thread_local_invalid_parameter_handler 函式"
ms.assetid: c0e67934-1a41-4016-ad8e-972828f3ac11
caps.latest.revision: 27
caps.handback.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _set_invalid_parameter_handler _set_thread_local_invalid_parameter_handler
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

設定 CRT 偵測到無效的引數時要呼叫的函式。  
  
## 語法  
  
```  
_invalid_parameter_handler _set_invalid_parameter_handler(  
   _invalid_parameter_handler pNew  
);  
_invalid_parameter_handler _set_thread_local_invalid_parameter_handler(  
   _invalid_parameter_handler pNew  
);  
```  
  
#### 參數  
 \[in\] `pNew`  
 新的無效參數處理常式函式指標。  
  
## 傳回值  
 無效的參數處理常式的呼叫之前指標。  
  
## 備註  
 許多 C 執行階段函式會檢查引數傳遞給它們的有效性。 如果傳遞了無效的引數，則可以設定的函式 `errno` 錯誤號碼或傳回錯誤碼。 在這種情況下，也稱為無效參數處理常式。 C 執行階段會提供結束程式，並顯示執行階段錯誤訊息的預設全域無效參數處理常式。 您可以使用 `_set_invalid_parameter_handler` 將自己的函式設定為全域的無效參數處理常式。 C 執行階段也支援執行緒區域無效參數處理常式。 如果執行緒區域參數處理常式在執行緒中使用設定的 `_set_thread_local_invalid_parameter_handler`, ，從執行緒中呼叫 C 執行階段函式使用該處理常式，而不是全域的處理常式。 只有一個函式可指定為全域無效的引數的處理常式，一次。 只有一個函式可指定為每個執行緒，此執行緒區域無效的引數處理常式，但不同的執行緒可以有不同的執行緒區域處理常式。 這可讓您變更的處理常式，用於您的程式碼的一部分，而不會影響其他執行緒的行為。  
  
 當執行階段呼叫不正確的參數的函式時，通常表示，發生無法復原的錯誤。 您提供無效參數處理常式函式應該儲存任何資料，它可以並中止。 它不應傳回主函式控制項，除非您確定是復原的錯誤。  
  
 無效的參數處理常式函式必須具有下列原型︰  
  
```c  
void _invalid_parameter(  
   const wchar_t * expression,  
   const wchar_t * function,   
   const wchar_t * file,   
   unsigned int line,  
   uintptr_t pReserved  
);  
```  
  
 `expression` 引數是寬字串表示的引數運算式引發錯誤。`function` 引數是收到無效的引數的 CRT 函式名稱。`file` 引數是 CRT 原始程式檔包含函式的名稱。`line` 引數是在該檔案中的行號。 保留最後一個引數。 所有參數都具有值 `NULL` 除非使用 CRT 程式庫的偵錯版本。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_set_invalid_parameter_handler`, `_set_thread_local_invalid_parameter_handler`|C: \< stdlib.h \><br /><br /> C \+ \+: \< d l i b \> 或 \< stdlib.h \>|  
  
 `_set_invalid_parameter_handler` 和 `_set_thread_local_invalid_parameter_handler` 函式是 Microsoft 專有的。 相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 在下列範例中，不正確的參數錯誤處理常式用來列印收到無效的參數和檔案和行 CRT 來源中的函式。 使用偵錯 CRT 程式庫時，不正確的參數錯誤也會引發判斷提示，會停用在此範例使用 [\_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md)。  
  
```c  
// crt_set_invalid_parameter_handler.c  
// compile with: /Zi /MTd  
#include <stdio.h>  
#include <stdlib.h>  
#include <crtdbg.h>  // For _CrtSetReportMode  
  
void myInvalidParameterHandler(const wchar_t* expression,  
   const wchar_t* function,   
   const wchar_t* file,   
   unsigned int line,   
   uintptr_t pReserved)  
{  
   wprintf(L"Invalid parameter detected in function %s."  
            L" File: %s Line: %d\n", function, file, line);  
   wprintf(L"Expression: %s\n", expression);  
   abort();  
}  
  
int main( )  
{  
   char* formatString;  
  
   _invalid_parameter_handler oldHandler, newHandler;  
   newHandler = myInvalidParameterHandler;  
   oldHandler = _set_invalid_parameter_handler(newHandler);  
  
   // Disable the message box for assertions.  
   _CrtSetReportMode(_CRT_ASSERT, 0);  
  
   // Call printf_s with invalid parameters.  
  
   formatString = NULL;  
   printf(formatString);  
}  
```  
  
```Output  
在函式 common_vfprintf 中偵測到無效的參數。 檔案︰ minkernel\crts\ucrt\src\appcrt\stdio\output.cpp 行︰ 32 運算式︰ 格式 ！ = nullptr  
```  
  
## 請參閱  
 [\_get\_invalid\_parameter\_handler \_get\_thread\_local\_invalid\_parameter\_handler](../../c-runtime-library/reference/get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)   
 [CRT 函式的安全性增強版本](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)   
 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)