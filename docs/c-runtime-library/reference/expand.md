---
title: _expand
ms.date: 4/2/2020
api_name:
- _expand
- _o__expand
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
- _bexpand
- fexpand
- expand
- nexpand
- _fexpand
- _nexpand
- bexpand
- _expand
helpviewer_keywords:
- memory blocks, changing size
- _expand function
- expand function
ms.assetid: 4ac55410-39c8-45c7-bccd-3f1042ae2ed3
ms.openlocfilehash: 7f2a789bc5f475411808bc00a4280b7573b67cf2
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347536"
---
# <a name="_expand"></a>_expand

變更記憶體區塊的大小。

## <a name="syntax"></a>語法

```C
void *_expand(
   void *memblock,
   size_t size
);
```

### <a name="parameters"></a>參數

*memblock*<br/>
先前配置之記憶體區塊的指標。

*大小*<br/>
新的大小 (以位元組計)。

## <a name="return-value"></a>傳回值

**_expand**返回指向重新分配的記憶體塊的空指標。 **_expand,** 不像**真正的塊**,不能移動一個方塊來改變其大小。 因此,如果有足夠的記憶體可用於展開塊而不移動它,則**要_expand**的*memblock*參數與返回值相同。

**_expand**在操作過程中檢測到錯誤時傳回**NULL。** 例如,如果 **_expand**用於收縮記憶體,它可能會偵測小塊堆或無效區塊的損壞,並傳**回 NULL**。

如果沒有足夠的記憶體可用於在不移動區將區擴展到給定大小,則函數將傳回**NULL**。 **_expand**永遠不會返回擴展為小於請求的大小的塊。 如果發生故障 **,errno**指示故障的性質。 有關**errno**的詳細資訊,請參閱[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

儲存空間的傳回值指標，是能夠適當地對齊任何物件類型之儲存區的保證。 要檢查專案的新大小,請使用 **_msize**。 要取得指向**void**以外的類型的指標,請使用返回值上強制轉換的類型。

## <a name="remarks"></a>備註

**_expand**函數通過嘗試展開或收縮塊而不移動其在堆中的位置來更改以前分配的記憶體塊的大小。 *memblock*參數指向塊的開頭。 *大小*參數提供塊的新大小(以位元組為單位)。 區塊內容在不超過新的和舊的大小範圍內不會變更。 *memblock*不應是已釋放的塊。

> [!NOTE]
> 在 64 位平臺上,如果新大小小於當前大小 **,_expand**可能不會收縮塊;特別是,如果塊的大小小於 16K,因此在低碎片堆中分配 **,_expand**保留塊不變並返回*memblock*。

當應用程式連結到 C 執行時庫的除錯版本時 **,_expand**解析為[_expand_dbg](expand-dbg.md)。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。

這個函式會驗證它的參數。 如果*memblock*是空指標,則此函數將調用無效的參數處理程式,如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行 **,errno**將設定為**EINVAL,** 並且函數傳回**NULL**。 如果*大小*大於 **_HEAP_MAXREQ** **,errno**設定為**ENOMEM,** 函數傳回**NULL**。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|必要的標頭|
|--------------|---------------------|
|**_expand**|\<malloc.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_expand.c

#include <stdio.h>
#include <malloc.h>
#include <stdlib.h>

int main( void )
{
   char *bufchar;
   printf( "Allocate a 512 element buffer\n" );
   if( (bufchar = (char *)calloc( 512, sizeof( char ) )) == NULL )
      exit( 1 );
   printf( "Allocated %d bytes at %Fp\n",
         _msize( bufchar ), (void *)bufchar );
   if( (bufchar = (char *)_expand( bufchar, 1024 )) == NULL )
      printf( "Can't expand" );
   else
      printf( "Expanded block to %d bytes at %Fp\n",
            _msize( bufchar ), (void *)bufchar );
   // Free memory
   free( bufchar );
   exit( 0 );
}
```

```Output
Allocate a 512 element buffer
Allocated 512 bytes at 002C12BC
Expanded block to 1024 bytes at 002C12BC
```

## <a name="see-also"></a>另請參閱

[記憶體配置](../../c-runtime-library/memory-allocation.md)<br/>
[calloc](calloc.md)<br/>
[自由](free.md)<br/>
[malloc](malloc.md)<br/>
[_msize](msize.md)<br/>
[realloc](realloc.md)<br/>
