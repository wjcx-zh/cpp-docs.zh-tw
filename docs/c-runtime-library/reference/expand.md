---
title: _expand | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _expand
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
- api-ms-win-crt-heap-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _bexpand
- fexpand
- expand
- nexpand
- _fexpand
- _nexpand
- bexpand
- _expand
dev_langs:
- C++
helpviewer_keywords:
- memory blocks, changing size
- _expand function
- expand function
ms.assetid: 4ac55410-39c8-45c7-bccd-3f1042ae2ed3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f709df131ded856881dc171c2e1549d3d5d378e1
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="expand"></a>_expand

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

*size*<br/>
新的大小 (以位元組計)。

## <a name="return-value"></a>傳回值

**_expand**傳回重新配置的記憶體區塊的 void 指標。 **_expand**不同的是**realloc**，無法移動所要變更其大小的區塊。 因此，如果沒有足夠的記憶體將區塊展開不移動的方式， *memblock*參數 **_expand**傳回的值相同。

**_expand**傳回**NULL**當其作業期間偵測到錯誤。 例如，如果 **_expand**是用來壓縮的記憶體區塊，同時可能會偵測損毀小型區塊，堆積中的無效的區塊的指標，並傳回**NULL**。

如果沒有可用記憶體不足以不移動的方式，將區塊展開為指定大小，則此函數會傳回**NULL**。 **_expand**永遠不會傳回將區塊展開為大小小於所要求。 如果發生失敗， **errno**指出失敗的性質。 如需有關**errno**，請參閱[errno、 _doserrno、 _sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

儲存空間的傳回值指標，是能夠適當地對齊任何物件類型之儲存區的保證。 若要檢查新項目的大小，請使用 **_msize**。 若要取得指標的類型以外**void**，使用類型，對傳回值轉型。

## <a name="remarks"></a>備註

**_Expand**函式嘗試將展開或收縮區塊，而不移動堆積中的位置變更先前配置的記憶體區塊的大小。 *Memblock*參數指向區塊的開頭。 *大小*參數會提供新的區塊大小，以位元組為單位。 區塊內容在不超過新的和舊的大小範圍內不會變更。 *memblock*不應被釋出區塊。

> [!NOTE]
> 64 位元平台上， **_expand**可能並未在合約區塊是否新的大小小於目前的大小比; 特別是，如果區塊已小於 16k 的大小，因此在低分散堆積中配置 **_expand**會保留不變的區塊，並傳回*memblock*。

當應用程式的 C 執行階段程式庫的偵錯版本連結時 **_expand**解析成[_expand_dbg](expand-dbg.md)。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。

這個函式會驗證它的參數。 如果*memblock*為 null 指標，此函式叫用無效參數處理常式中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 若要繼續，允許執行**errno**設**EINVAL**並傳回函式**NULL**。 如果*大小*大於 **_HEAP_MAXREQ**， **errno**設**ENOMEM**並傳回函式**NULL**.

## <a name="requirements"></a>需求

|功能|必要的標頭|
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
[free](free.md)<br/>
[malloc](malloc.md)<br/>
[_msize](msize.md)<br/>
[realloc](realloc.md)<br/>
