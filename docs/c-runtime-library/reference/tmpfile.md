---
title: tmpfile
ms.date: 11/04/2016
api_name:
- tmpfile
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
- tmpfile
helpviewer_keywords:
- temporary files
- tmpfile function
- temporary files, creating
ms.assetid: c4a4dc24-70da-438d-ae4e-98352d88e375
ms.openlocfilehash: f58c23050fe89f84f283c3784a7c0cee72637bf2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957547"
---
# <a name="tmpfile"></a>tmpfile

建立暫存檔。 此函式已被取代，因為有更安全的版本可用。請參閱 [tmpfile_s](tmpfile-s.md)。

## <a name="syntax"></a>語法

```C
FILE *tmpfile( void );
```

## <a name="return-value"></a>傳回值

如果成功， **tmpfile**會傳回資料流程指標。 否則，它會傳回**Null**指標。

## <a name="remarks"></a>備註

**Tmpfile**函式會建立暫存檔案，並傳回該資料流程的指標。 暫存檔案建立於根目錄。 若要在非根目錄的目錄建立暫存檔案，請使用 [tmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md) 或 [tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md) 搭配 [fopen](fopen-wfopen.md)。

如果無法開啟檔案， **tmpfile**會傳回**Null**指標。 當檔案關閉、程式正常終止時，或呼叫 **_rmtmp**時（假設目前的工作目錄不會變更），就會自動刪除此暫存檔案。 暫存檔案會以**w + b** （二進位讀取/寫入）模式開啟。

如果您嘗試超過 TMP_MAX，可能會發生失敗（請參閱 STDIO.H）。H）使用**tmpfile**呼叫。

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
