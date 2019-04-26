---
title: tmpfile
ms.date: 11/04/2016
apiname:
- tmpfile
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
- tmpfile
helpviewer_keywords:
- temporary files
- tmpfile function
- temporary files, creating
ms.assetid: c4a4dc24-70da-438d-ae4e-98352d88e375
ms.openlocfilehash: 98afcb7a3e04a96a1b08bc1b975634153e550839
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155559"
---
# <a name="tmpfile"></a>tmpfile

建立暫存檔。 此函式已被取代，因為有更安全的版本可用。請參閱 [tmpfile_s](tmpfile-s.md)。

## <a name="syntax"></a>語法

```C
FILE *tmpfile( void );
```

## <a name="return-value"></a>傳回值

如果成功， **tmpfile**傳回資料流指標。 否則，它會傳回**NULL**指標。

## <a name="remarks"></a>備註

**Tmpfile**函式會建立暫存檔，並傳回該資料流的指標。 暫存檔案建立於根目錄。 若要在非根目錄的目錄建立暫存檔案，請使用 [tmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md) 或 [tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md) 搭配 [fopen](fopen-wfopen.md)。

無法開啟檔案，如果**tmpfile**會傳回**NULL**指標。 關閉檔案時，一般來說，或當，在程式終止時，會自動刪除這個暫存檔 **_rmtmp**呼叫時，假設目前的工作目錄不會變更。 在中開啟暫存檔**w + b** （二進位讀取/寫入） 模式。

如果您嘗試超過 TMP_MAX，就會發生失敗 （請參閱 STDIO。使用 H） 呼叫**tmpfile**。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**tmpfile**|\<stdio.h>|

如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

> [!NOTE]
> 這個範例需要系統管理權限才能在 Windows Vista 上執行。

```C
// crt_tmpfile.c
// compile with: /W3
// This program uses tmpfile to create a
// temporary file, then deletes this file with _rmtmp.
#include <stdio.h>

int main( void )
{
   FILE *stream;
   int  i;

   // Create temporary files.
   for( i = 1; i <= 3; i++ )
   {
      if( (stream = tmpfile()) == NULL ) // C4996
      // Note: tmpfile is deprecated; consider using tmpfile_s instead
         perror( "Could not open new temporary file\n" );
      else
         printf( "Temporary file %d was created\n", i );
   }

   // Remove temporary files.
   printf( "%d temporary files deleted\n", _rmtmp() );
}
```

```Output
Temporary file 1 was created
Temporary file 2 was created
Temporary file 3 was created
3 temporary files deleted
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_rmtmp](rmtmp.md)<br/>
[_tempnam、_wtempnam、tmpnam、_wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
