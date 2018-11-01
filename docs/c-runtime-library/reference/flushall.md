---
title: _flushall
ms.date: 11/04/2016
apiname:
- _flushall
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _flushall
helpviewer_keywords:
- flushall function
- flushing streams
- streams, flushing
- _flushall function
ms.assetid: 2cd73562-6d00-4ca2-b13c-80d0ae7870b5
ms.openlocfilehash: de8caf30568816f41441f5d9487293c346d2bff1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466223"
---
# <a name="flushall"></a>_flushall

清除所有資料流；清除所有緩衝區。

## <a name="syntax"></a>語法

```C
int _flushall( void );
```

## <a name="return-value"></a>傳回值

**_flushall**傳回開啟的資料流 （輸入和輸出） 的數目。 不會傳回錯誤。

## <a name="remarks"></a>備註

根據預設， **_flushall**函式會寫入適當的檔案與開啟輸出資料流相關聯的所有緩衝區的內容。 會清除與開啟之輸入資料流相關聯的所有緩衝區中的目前內容 (這些緩衝區通常是由作業系統所維護，以判斷將資料自動寫入至磁碟的最佳時機︰緩衝區已滿時、關閉資料流時，或程式正常結束而未關閉資料流時)。

如果呼叫 **_flushall**，新的資料從輸入檔讀取到緩衝區。 所有資料流保持開啟狀態之後呼叫 **_flushall**。

執行階段程式庫的認可到磁碟功能可讓您確保將重大資料直接寫入至磁碟，而不是作業系統緩衝區。 不需要重新撰寫現有程式，即可連結程式的物件檔案與 Commode.obj 來啟用這項功能。在產生的可執行檔中，呼叫 **_flushall**寫入磁碟中的所有緩衝區的內容。 只有 **_flushall**並[fflush](fflush.md)會受到 Commode.obj 影響。

如需控制認可到磁碟功能的資訊，請參閱[資料流 I/O](../../c-runtime-library/stream-i-o.md)、[fopen](fopen-wfopen.md) 和 [_fdopen](fdopen-wfdopen.md)。

## <a name="requirements"></a>需求

|功能|必要的標頭|
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
