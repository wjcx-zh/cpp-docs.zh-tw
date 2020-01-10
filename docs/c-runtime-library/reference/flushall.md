---
title: _flushall
ms.date: 11/04/2016
api_name:
- _flushall
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _flushall
helpviewer_keywords:
- flushall function
- flushing streams
- streams, flushing
- _flushall function
ms.assetid: 2cd73562-6d00-4ca2-b13c-80d0ae7870b5
ms.openlocfilehash: dce7412ccc19d4870494851d366c059ff01de16a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957144"
---
# <a name="_flushall"></a>_flushall

清除所有資料流；清除所有緩衝區。

## <a name="syntax"></a>語法

```C
int _flushall( void );
```

## <a name="return-value"></a>傳回值

**_flushall**會傳回開啟的資料流程數目（輸入和輸出）。 不會傳回錯誤。

## <a name="remarks"></a>備註

根據預設， **_flushall**函式會將與開啟的輸出資料流程相關聯之所有緩衝區的內容寫入適當的檔案。 會清除與開啟之輸入資料流相關聯的所有緩衝區中的目前內容 (這些緩衝區通常是由作業系統所維護，以判斷將資料自動寫入至磁碟的最佳時機︰緩衝區已滿時、關閉資料流時，或程式正常結束而未關閉資料流時)。

如果讀取會在呼叫 **_flushall**之後，則會從輸入檔案將新資料讀取到緩衝區。 所有資料流程在呼叫 **_flushall**之後都會保持開啟狀態。

執行階段程式庫的認可到磁碟功能可讓您確保將重大資料直接寫入至磁碟，而不是作業系統緩衝區。 不需要重新撰寫現有程式，即可連結程式的物件檔案與 Commode.obj 來啟用這項功能。在產生的可執行檔中，對 **_flushall**的呼叫會將所有緩衝區的內容寫入磁片。 只有 **_flushall**和[Fflush](fflush.md)會受到 commode.obj 的影響。

如需控制認可到磁碟功能的資訊，請參閱[資料流 I/O](../../c-runtime-library/stream-i-o.md)、[fopen](fopen-wfopen.md) 和 [_fdopen](fdopen-wfdopen.md)。

## <a name="requirements"></a>需求

|函數|必要的標頭|
|--------------|---------------------|
|**_flushall**|\<stdio.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_flushall.c
// This program uses _flushall
// to flush all open buffers.

#include <stdio.h>

int main( void )
{
   int numflushed;

   numflushed = _flushall();
   printf( "There were %d streams flushed\n", numflushed );
}
```

```Output
There were 3 streams flushed
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_commit](commit.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[fflush](fflush.md)<br/>
[setvbuf](setvbuf.md)<br/>
