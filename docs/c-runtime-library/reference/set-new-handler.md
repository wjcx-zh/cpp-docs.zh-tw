---
title: _set_new_handler | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _set_new_handler
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
dev_langs:
- C++
helpviewer_keywords:
- _set_new_handler function
- set_new_handler function
- error handling
- transferring control to error handler
ms.assetid: 1d1781b6-5cf8-486a-b430-f365e0bb023f
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 11ffd955f18a58c8b3d767697b7f7146f2b8db5a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="setnewhandler"></a>_set_new_handler

將控制項傳送至您的錯誤處理機制，如果**新**運算子無法配置記憶體。

## <a name="syntax"></a>語法

```cpp
_PNH _set_new_handler( _PNH pNewHandler );
```

### <a name="parameters"></a>參數

*pNewHandler*<br/>
應用程式所提供記憶體處理函式的指標。 引數 0 會移除新的處理常式。

## <a name="return-value"></a>傳回值

讓指標回到先前的例外狀況處理函式註冊 **_set_new_handler**，如此一來，可以將其還原先前的函數。 如果尚未設定任何先前的函數，傳回的值可用來還原預設行為。這個值可以是**NULL**。

## <a name="remarks"></a>備註

C + + **_set_new_handler**函式會指定如果中取得控制例外狀況處理函式**新**運算子無法配置記憶體。 如果**新**失敗，執行階段系統會自動呼叫做為引數傳遞的例外狀況處理函式 **_set_new_handler**。 **_PNH**、 h 中定義、 傳回類型的函式的指標**int**接受型別引數和**size_t**。 使用**size_t**來指定要配置的空間數量。

沒有預設處理常式。

**_set_new_handler**基本上回收配置。 每次函式傳回非零值時，執行階段系統都會重試配置，如果函式傳回 0 則失敗。

項目 **_set_new_handler**函式在程式中的註冊執行階段系統引數清單中指定的例外狀況處理函式：

```cpp
// set_new_handler1.cpp
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

您可以將儲存最後傳遞至函式位址 **_set_new_handler**函式，並稍後再重新啟用它：

```cpp
   _PNH old_handler = _set_new_handler( my_handler );
   // Code that requires my_handler
   // . . .
   _set_new_handler( old_handler )
   // Code that requires old_handler
   // . . .
```

C++ [_set_new_mode](set-new-mode.md) 函式會設定 [malloc](malloc.md) 的新處理常式模式。 新的處理常式模式指出是否在失敗時， **malloc**是新的處理常式呼叫所設定的 **_set_new_handler**。 根據預設， **malloc**不會呼叫新的處理常式在無法配置記憶體。 您可以覆寫此預設行為，讓，當**malloc**無法配置記憶體， **malloc**呼叫新的處理常式在相同的方式來**新**運算子會當它失敗基於相同原因。 若要覆寫預設值，請及早在程式中呼叫：

```cpp
_set_new_mode(1);
```

，或使用 Newmode.obj 連結。

如果使用者定義`operator new`提供新的處理常式函式不會自動呼叫失敗。

如需詳細資訊，請參閱《C++ 語言參考》中的 [new](../../cpp/new-operator-cpp.md) 和 [delete](../../cpp/delete-operator-cpp.md)。

沒有單一 **_set_new_handler**處理常式所有以動態方式連結的 Dll 或可執行檔; 即使您呼叫 **_set_new_handler**可能由另一個取代您的處理常式，或您要取代另一個 DLL 或可執行檔所設定的處理常式。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_set_new_handler**|\<new.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

在此範例中，配置失敗時，控制權會轉移到 MyNewHandler。 傳遞至 MyNewHandler 的引數是所要求的位元組數目。 從 MyNewHandler 傳回的值是指出是否應該重試配置的旗標︰非零值表示應該重試配置，零值則表示配置失敗。

```cpp
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

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[free](free.md)<br/>
[realloc](realloc.md)<br/>
