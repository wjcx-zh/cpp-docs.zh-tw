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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 8878bb046a122b545f969dd067c37eeb97126387
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920248"
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

*size*<br/>
新的大小 (以位元組計)。

## <a name="return-value"></a>傳回值

**_expand**會傳回重新配置記憶體區塊的 void 指標。 不同于**realloc**， **_expand**無法移動區塊來變更其大小。 因此，如果有足夠的記憶體可用來展開區塊，而不移動它，則 **_expand**的*memblock*參數會與傳回值相同。

**_expand**在其作業期間偵測到錯誤時，會傳回**Null** 。 例如，如果 **_expand**用來壓縮記憶體區塊，它可能會偵測到社區塊堆積中的損毀或不正確區塊指標，並傳回**Null**。

如果沒有足夠的記憶體可將區塊展開為指定大小，而不移動它，則函數會傳回**Null**。 **_expand**絕不會傳回擴充到小於所要求之大小的區塊。 如果發生失敗， **errno**會指出失敗的本質。 如需**errno**的詳細資訊，請參閱[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

儲存空間的傳回值指標，是能夠適當地對齊任何物件類型之儲存區的保證。 若要檢查項目的新大小，請使用 **_msize**。 若要取得**void**以外類型的指標，請在傳回值上使用類型轉換。

## <a name="remarks"></a>備註

**_Expand**函式會藉由嘗試展開或收縮區塊，而不在堆積中移動其位置，來變更先前配置的記憶體區塊大小。 *Memblock*參數會指向區塊的開頭。 *Size*參數會提供新的區塊大小（以位元組為單位）。 區塊內容在不超過新的和舊的大小範圍內不會變更。 *memblock*不應該是已釋放的區塊。

> [!NOTE]
> 在64位平臺上，如果新的大小小於目前的大小， **_expand**可能不會對區塊進行合約。特別是，如果區塊的大小小於16K，因而配置於低分散堆積中， **_expand**會將區塊保持不變，並傳回*memblock*。

當應用程式與 C 執行時間程式庫的 debug 版本連結時， **_expand**會解析成[_expand_dbg](expand-dbg.md)。 如需如何在偵錯程序期間管理堆積的詳細資訊，請參閱 [CRT 偵錯堆積](/visualstudio/debugger/crt-debug-heap-details)。

這個函式會驗證它的參數。 如果*memblock*為 null 指標，則此函式會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， **errno**會設為**EINVAL** ，而函數會傳回**Null**。 如果*size*大於 **_HEAP_MAXREQ**， **errno**會設為**ENOMEM** ，而函式會傳回**Null**。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

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
[受](free.md)<br/>
[malloc](malloc.md)<br/>
[_msize](msize.md)<br/>
[realloc](realloc.md)<br/>
