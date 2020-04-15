---
title: _set_new_handler
ms.date: 4/2/2020
api_name:
- _set_new_handler
- _o__set_new_handler
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_new_handler
- set_new_handler
helpviewer_keywords:
- _set_new_handler function
- set_new_handler function
- error handling
- transferring control to error handler
ms.assetid: 1d1781b6-5cf8-486a-b430-f365e0bb023f
ms.openlocfilehash: c3f1b9bd8bf2a4404e2239858e4c3c59b755bacd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332368"
---
# <a name="_set_new_handler"></a>_set_new_handler

若 **new** 運算子無法配置記憶體，則將控制項傳送至您的錯誤處理機制。

## <a name="syntax"></a>語法

```cpp
_PNH _set_new_handler( _PNH pNewHandler );
```

### <a name="parameters"></a>參數

*p 紐漢德勒*<br/>
應用程式所提供記憶體處理函式的指標。 引數 0 會移除新的處理常式。

## <a name="return-value"></a>傳回值

返回指向 **_set_new_handler**註冊的前一個異常處理函數的指標,以便以後可以還原以前的函數。 如果未設置以前的函數,則返回值可用於還原默認行為;如果未設置以前的函數,則返回值可用於還原默認行為。這個值可以是**NULL**。

## <a name="remarks"></a>備註

C++_set_new_handler **_set_new_handler**函數指定一個異常處理函數,如果**新**運算元無法分配記憶體,該函數將獲得控制權。 如果**new**發生故障,執行時系統會自動調用作為參數傳遞給 **_set_new_handler**的異常處理函數。 **_PNH**在 New.h 中定義,是傳回類型**int**並採用類型**size_t**的參數的函數的指標。 使用**size_t**指定要分配的空間量。

沒有預設處理常式。

**_set_new_handler**本質上是一個垃圾回收方案。 每次函式傳回非零值時，執行階段系統都會重試配置，如果函式傳回 0 則失敗。

程式中 **_set_new_handler**函數的發生會將參數清單中指定的例外處理函數與執行時系統註冊:

```cpp
// set_new_handler1.cpp
By default, this function's global state is scoped to the application. To change this, see [Global state in the CRT](../global-state.md).

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

您可以儲存上次傳遞到 **_set_new_handler**函數的函數位址,並在以後恢復它:

```cpp
   _PNH old_handler = _set_new_handler( my_handler );
   // Code that requires my_handler
   // . . .
   _set_new_handler( old_handler )
   // Code that requires old_handler
   // . . .
```

C++ [_set_new_mode](set-new-mode.md) 函式會設定 [malloc](malloc.md) 的新處理常式模式。 新的處理程式模式指示在發生故障時 **,malloc**是否將調用**由 _set_new_handler**設置的新處理程式例程。 默認情況下 **,malloc**不會在分配記憶體失敗時調用新的處理程式例程。 您可以重寫此預設行為,以便在**malloc**無法分配記憶體時 **,malloc**呼叫新處理程式例程的方式**與新運算符出於**相同原因失敗時相同的方式呼叫新處理程式例程。 若要覆寫預設值，請及早在程式中呼叫：

```cpp
_set_new_mode(1);
```

，或使用 Newmode.obj 連結。

如果提供了使用者定義的`operator new`函數,則新處理程式函數不會在失敗時自動調用。

如需詳細資訊，請參閱《C++ 語言參考》** 中的 [new](../../cpp/new-operator-cpp.md) 和 [delete](../../cpp/delete-operator-cpp.md)。

對於所有動態連結的 DLL 或可執行檔,只有一個 **_set_new_handler**處理程式;即使您調用 **_set_new_handler**您的處理程式可能被另一個替換,或者您要取代由另一個 DLL 或可執行檔設定的處理程式。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_set_new_handler**|\<new.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

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
[自由](free.md)<br/>
[realloc](realloc.md)<br/>
