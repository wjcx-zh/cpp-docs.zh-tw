---
title: calloc
description: C 運行時庫函數 calloc 分配零初始化記憶體。
ms.date: 4/2/2020
api_name:
- calloc
- _o_calloc
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
- api-ms-win-crt-heap-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- calloc
helpviewer_keywords:
- memory allocation, arrays
- calloc function
ms.assetid: 17bb79a1-98cf-4096-90cb-1f9365cd6829
ms.openlocfilehash: fb4f7d6dc059023d34cb0b811edf5dfb48cb7a34
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333643"
---
# <a name="calloc"></a>calloc

配置記憶體中項目初始化為 0 的陣列。

## <a name="syntax"></a>語法

```C
void *calloc(
   size_t number,
   size_t size
);
```

### <a name="parameters"></a>參數

*數量*<br/>
項目數。

*大小*<br/>
每個項目的長度 (位元組)。

## <a name="return-value"></a>傳回值

**calloc**傳回指向已分配空間的指標。 傳回值所指向的儲存空間一定可以適當地對齊任何物件類型之儲存區的保證。 要取得指向**void**以外的類型的指標,請使用返回值上強制轉換的類型。

## <a name="remarks"></a>備註

**calloc**函數為*數位*元素陣組分配存儲空間,每個陣列的長度 大小 位*元*組。 每個項目都會初始化為 0。

**如果**記憶體分配失敗或請求的記憶體量超過_HEAP_MAXREQ,calloc將**errno**設置到 **_HEAP_MAXREQ****ENOMEM。** 如需此錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

在 Microsoft 實現中,如果*數位*或*大小*為零 **,calloc**將返回指向非零大小的已分配塊的指標。 嘗試通過返回的指標讀取或寫入會導致未定義的行為。

**calloc**使用[C++_set_new_mode](set-new-mode.md)函數來設定*新的處理程式模式*。 新的處理程式模式指示在發生故障時 **,calloc**是否調用[由 _set_new_handler](set-new-handler.md)設置的新處理程式例程。 默認情況下 **,calloc**不會在分配記憶體失敗時調用新的處理程式例程。 您可以重寫此預設行為,以便在**calloc**無法分配記憶體時,它調用新處理程式例程的方式**與新運算符由於**同樣原因失敗時相同。 若要覆寫預設值，請及早在程式中呼叫

```C
_set_new_mode(1);
```

在程式的早期,或與*NEWMODE 連結。OBJ(* 參見[連結選項](../../c-runtime-library/link-options.md))。

當應用程式連結到 C 執行時庫的除錯版本時 **,calloc**解析為[_calloc_dbg](calloc-dbg.md)。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。

**calloc**`__declspec(noalias)`被`__declspec(restrict)`標記 和 ,這意味著保證函數不修改全域變數,並且返回的指標不會別名。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**calloc**|\<stdlib.h> 和 \<malloc.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_calloc.c
// This program uses calloc to allocate space for
// 40 long integers. It initializes each element to zero.

#include <stdio.h>
#include <malloc.h>

int main( void )
{
   long *buffer;

   buffer = (long *)calloc( 40, sizeof( long ) );
   if( buffer != NULL )
      printf( "Allocated 40 long integers\n" );
   else
      printf( "Can't allocate memory\n" );
   free( buffer );
}
```

```Output
Allocated 40 long integers
```

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
[自由](free.md)<br/>
[malloc](malloc.md)<br/>
[realloc](realloc.md)<br/>
