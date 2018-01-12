---
title: _set_new_handler | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _set_new_handler
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _set_new_handler
- set_new_handler
dev_langs: C++
helpviewer_keywords:
- _set_new_handler function
- set_new_handler function
- error handling
- transferring control to error handler
ms.assetid: 1d1781b6-5cf8-486a-b430-f365e0bb023f
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 581942f828bb666606b8f176ae3e2bb3454cbf98
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="setnewhandler"></a>_set_new_handler
若 `new` 運算子無法配置記憶體，則將控制項傳送至您的錯誤處理機制。  
  
## <a name="syntax"></a>語法  
  
```  
_PNH _set_new_handler(  
   _PNH pNewHandler   
);  
```  
  
#### <a name="parameters"></a>參數  
 `pNewHandler`  
 應用程式所提供記憶體處理函式的指標。 引數 0 會移除新的處理常式。  
  
## <a name="return-value"></a>傳回值  
 傳回 `_set_new_handler` 所註冊之先前例外狀況處理函式的指標，因此，稍後可以還原先前函式。 如果尚未設定先前函式，傳回值可以用於還原預設行為；這個值可以是 `NULL`。  
  
## <a name="remarks"></a>備註  
 如果 `new` 運算子無法配置記憶體，則 C++ `_set_new_handler` 函式會指定取得控制權的例外狀況處理函式。 如果 `new` 失敗，執行階段系統會自動呼叫傳遞為 `_set_new_handler` 之引數的例外狀況處理函式。 New.h 中所定義的 `_PNH` 是函式的指標，而函式傳回類型 `int` 並接受類型 `size_t` 的引數。 使用 `size_t` 來指定要配置的空間量。  
  
 沒有預設處理常式。  
  
 `_set_new_handler` 基本上是記憶體回收配置。 每次函式傳回非零值時，執行階段系統都會重試配置，如果函式傳回 0 則失敗。  
  
 程式中出現的 `_set_new_handler` 函式會向執行階段系統註冊引數清單中所指定的例外狀況處理函式：  
  
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
  
 您可以儲存最後傳遞至 `_set_new_handler` 函式的函式位址，並稍後進行恢復：  
  
```  
_PNH old_handler = _set_new_handler( my_handler );  
   // Code that requires my_handler  
   _set_new_handler( old_handler )  
   // Code that requires old_handler  
```  
  
 C++ [_set_new_mode](../../c-runtime-library/reference/set-new-mode.md) 函式會設定 [malloc](../../c-runtime-library/reference/malloc.md) 的新處理常式模式。 新的處理常式模式表示失敗時，`malloc` 是否呼叫 `_set_new_handler` 所設定的新處理常式。 根據預設，`malloc` 不會在無法配置記憶體時呼叫新的處理常式。 您可以覆寫這個預設行為，因此，在 `malloc` 無法配置記憶體時，`malloc` 會呼叫新的處理常式，其方法與 `new` 運算子因相同原因而失敗時所執行的方法相同。 若要覆寫預設值，請及早在程式中呼叫：  
  
```  
_set_new_mode(1)  
```  
  
 ，或使用 Newmode.obj 連結。  
  
 如果使用者定義`operator new`提供新的處理常式函式不會自動呼叫失敗。  
  
 如需詳細資訊，請參閱《C++ 語言參考》中的 [new](../../cpp/new-operator-cpp.md) 和 [delete](../../cpp/delete-operator-cpp.md)。  
  
 所有動態連結的 DLL 或可執行檔都有一個單一 `_set_new_handler` 處理常式；即使您呼叫 `_set_new_handler`，還是會將您的處理常式取代為其他處理常式，或是取代其他 DLL 或可執行檔所設定的處理常式。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|`_set_new_handler`|\<new.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>範例  
 在此範例中，配置失敗時，控制權會轉移到 MyNewHandler。 傳遞至 MyNewHandler 的引數是所要求的位元組數目。 從 MyNewHandler 傳回的值是指出是否應該重試配置的旗標︰非零值表示應該重試配置，零值則表示配置失敗。  
  
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
  
```Output  
Allocation failed. Coalescing heap.  
  
This application has requested the Runtime to terminate it in an unusual way.  
Please contact the application's support team for more information.  
```  
  
## <a name="see-also"></a>請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)   
 [calloc](../../c-runtime-library/reference/calloc.md)   
 [free](../../c-runtime-library/reference/free.md)   
 [realloc](../../c-runtime-library/reference/realloc.md)