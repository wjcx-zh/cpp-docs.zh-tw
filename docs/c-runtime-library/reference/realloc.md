---
title: realloc
description: 'Realloc ( # A1; 的 API 參考這會重新配置記憶體區塊。'
ms.date: 9/11/2020
api_name:
- realloc
- _o_realloc
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _brealloc
- _nrealloc
- realloc
- _frealloc
helpviewer_keywords:
- _brealloc function
- realloc function
- nrealloc function
- frealloc function
- _nrealloc function
- memory blocks, reallocating
- memory, reallocating
- _frealloc function
- reallocate memory blocks
ms.assetid: 2b2239de-810b-4b11-9438-32ab0a244185
ms.openlocfilehash: c68909b2f5d73959465d63af522ceeb00c8ce23e
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2020
ms.locfileid: "90075812"
---
# <a name="realloc"></a>realloc

重新配置記憶體區塊。

## <a name="syntax"></a>語法

```C
void *realloc(
   void *memblock,
   size_t size
);
```

### <a name="parameters"></a>參數

*`memblock`*\
先前配置之記憶體區塊的指標。

*`size`*\
新的大小 (以位元組計)。

## <a name="return-value"></a>傳回值

**`realloc`** 傳回重新配置之 **`void`** (的指標，可能會移動) 記憶體區塊。

如果沒有足夠的可用記憶體將區塊展開為指定大小，則原始區塊會保持不變，並 **`NULL`** 傳回。

如果 *`size`* 是零，則會釋放所指向的區塊 *`memblock`* ; 傳回值是 **`NULL`** ，而且 *`memblock`* 會保持指向已釋放的區塊。

傳回值指向針對任何物件類型的儲存適當對齊的儲存空間。 若要取得其他類型的指標 **`void`** ，請對傳回值使用類型轉換。

## <a name="remarks"></a>備註

> [!NOTE]
> **`realloc`** 尚未更新來執行 C17 行為，因為新的行為與 Windows 作業系統不相容。

函數會變更配置的 **`realloc`** 記憶體區塊大小。 *`memblock`* 引數會指向記憶體區塊的開頭。 如果 *`memblock`* 為 **`NULL`** ，則 **`realloc`** 的行為會與相同，並配置 **`malloc`** 新的 *`size`* 位元組區塊。 如果 *`memblock`* 不是 **`NULL`** ，則它應該是由先前的、或呼叫所傳回的指標 **`calloc`** **`malloc`** **`realloc`** 。

*`size`* 引數會提供區塊的新大小（以位元組為單位）。 區塊的內容維持為新舊大小的較短者，不過新區塊可能在不同的位置。 因為新的區塊可以在新的記憶體位置，所以不保證傳回的指標 **`realloc`** 是透過引數傳遞的指標 *`memblock`* 。 **`realloc`** 在緩衝區成長時，不會以新配置的記憶體為零。

**`realloc`****`errno`** **`ENOMEM`** 如果記憶體配置失敗，或所要求的記憶體數量超過，則設定為 **`_HEAP_MAXREQ`** 。 如需此錯誤碼和其他錯誤碼的資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

**`realloc`** 呼叫，以便 **`malloc`** 使用 c + + [_set_new_mode](set-new-mode.md) 函式來設定新的處理常式模式。 新的處理常式模式會指出失敗時是否 **`malloc`** 要呼叫 [_set_new_handler](set-new-handler.md)所設定的新處理常式常式。 根據預設，不 **`malloc`** 會在失敗時呼叫新的處理常式常式來配置記憶體。 您可以覆寫這個預設行為，如此一來，當 **`realloc`** 無法配置記憶體時，就會 **`malloc`** 呼叫新的處理常式常式，其方式與 **`new`** 運算子因相同原因而失敗時所執行的方式相同。 若要覆寫預設值，請及早在程式中呼叫

```C
_set_new_mode(1);
```

，或使用 NEWMODE.OBJ 連結 (請參閱[連結選項](../../c-runtime-library/link-options.md))。

當應用程式與 C 執行時間程式庫的 debug 版本連結時，會 **`realloc`** 解析成 [_realloc_dbg](realloc-dbg.md)。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。

**`realloc`** 標示為 `__declspec(noalias)` ，表示函式不 `__declspec(restrict)` 會修改全域變數，而且傳回的指標沒有別名。 如需詳細資訊，請參閱 [noalias](../../cpp/noalias.md) 和 [restrict](../../cpp/restrict.md)。

依預設，此函式的全域狀態範圍為應用程式。 若要變更此項，請參閱 [CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**`realloc`**|\<stdlib.h> 和 \<malloc.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_realloc.c
// This program allocates a block of memory for
// buffer and then uses _msize to display the size of that
// block. Next, it uses realloc to expand the amount of
// memory used by buffer and then calls _msize again to
// display the new amount of memory allocated to buffer.

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>

int main( void )
{
   long *buffer, *oldbuffer;
   size_t size;

   if( (buffer = (long *)malloc( 1000 * sizeof( long ) )) == NULL )
      exit( 1 );

   size = _msize( buffer );
   printf_s( "Size of block after malloc of 1000 longs: %u\n", size );

   // Reallocate and show new size:
   oldbuffer = buffer;     // save pointer in case realloc fails
   if( (buffer = realloc( buffer, size + (1000 * sizeof( long )) ))
        ==  NULL )
   {
      free( oldbuffer );  // free original block
      exit( 1 );
   }
   size = _msize( buffer );
   printf_s( "Size of block after realloc of 1000 more longs: %u\n",
            size );

   free( buffer );
   exit( 0 );
}
```

```Output
Size of block after malloc of 1000 longs: 4000
Size of block after realloc of 1000 more longs: 8000
```

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)\
[calloc](calloc.md)\
[自由](free.md)\
[malloc](malloc.md)
