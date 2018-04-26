---
title: fflush | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- fflush
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
- fflush
dev_langs:
- C++
helpviewer_keywords:
- streams, flushing
- flushing
- fflush function
ms.assetid: 8bbc753f-dc74-4e77-b563-74da2835e92b
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9a92affa1483c8dba9be0718acc00d4574eb44bb
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="fflush"></a>fflush

排清資料流。

## <a name="syntax"></a>語法

```C
int fflush(
   FILE *stream
);
```

### <a name="parameters"></a>參數

*資料流*<br/>
**FILE** 結構的指標。

## <a name="return-value"></a>傳回值

**fflush**傳回 0，如果已成功清除緩衝區。 如果指定的資料流沒有任何緩衝區或僅開啟為唯讀，也會傳回值 0。 傳回值為**EOF**表示發生錯誤。

> [!NOTE]
> 如果**fflush**傳回**EOF**，資料可能已遺失，因為發生寫入失敗。 設定時的重大錯誤處理常式，方式是先關閉緩衝處理與**setvbuf**函式或使用低層級 I/O 常式例如 **_open**， **_close**，和 **_write**而不是資料流 I/O 函式。

## <a name="remarks"></a>備註

**Fflush**函式會排清資料流*資料流*。 如果資料流已在寫入模式中開啟，或已在更新模式中開啟而最後的作業是寫入，則資料流緩衝區的內容會寫入基礎檔案或裝置，而緩衝區會被捨棄。 如果在讀取模式中，開啟資料流或資料流已無緩衝區，呼叫**fflush**沒有作用，而且會保留任何緩衝區。 呼叫**fflush**取消任何先前呼叫的效果**ungetc**資料流。 資料流在呼叫之後仍保持開啟。

如果*資料流*是**NULL**，行為等同於呼叫**fflush**上每個開啟的資料流。 所有在寫入模式中開啟的資料流，以及所有在更新模式中開啟且最後作業是寫入的資料流，都會排清。 呼叫對其他資料流不起作用。

緩衝區通常是由作業系統維護，這會決定資料自動寫入磁碟的最佳時機︰當緩衝區已滿、當資料流已關閉，或當程式正常結束但不關閉資料流。 執行階段程式庫的認可到磁碟功能可讓您確保將重大資料直接寫入至磁碟，而不是作業系統緩衝區。 不需要重新撰寫現有程式，即可連結程式的物件檔案與 COMMODE.OBJ 來啟用這項功能。 在產生的可執行檔中，呼叫 **_flushall**寫入磁碟中的所有緩衝區的內容。 只有 **_flushall**和**fflush** COMMODE.OBJ 受影響。

如需控制認可到磁碟功能的資訊，請參閱[資料流 I/O](../../c-runtime-library/stream-i-o.md)、[fopen](fopen-wfopen.md) 和 [_fdopen](fdopen-wfdopen.md)。

此函示鎖定呼叫執行緒，所以是安全執行緒。 如需非鎖定版本，請參閱 **_fflush_nolock**。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**fflush**|\<stdio.h>|

如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_fflush.c
#include <stdio.h>
#include <conio.h>

int main( void )
{
   int integer;
   char string[81];

   // Read each word as a string.
   printf( "Enter a sentence of four words with scanf: " );
   for( integer = 0; integer < 4; integer++ )
   {
      scanf_s( "%s", string, sizeof(string) );
      printf( "%s\n", string );
   }

   // You must flush the input buffer before using gets.
   // fflush on input stream is an extension to the C standard
   fflush( stdin );
   printf( "Enter the same sentence with gets: " );
   gets_s( string, sizeof(string) );
   printf( "%s\n", string );
}
```

```Output

      This is a test
This is a test

```

```Output

      This is a test
This is a testEnter a sentence of four words with scanf: This is a test
This
is
a
test
Enter the same sentence with gets: This is a test
This is a test
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fclose、_fcloseall](fclose-fcloseall.md)<br/>
[_flushall](flushall.md)<br/>
[setvbuf](setvbuf.md)<br/>
