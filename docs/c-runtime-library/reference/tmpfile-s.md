---
title: tmpfile_s
ms.date: 11/04/2016
apiname:
- tmpfile_s
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
- tmpfile_s
helpviewer_keywords:
- temporary files
- tmpfile_s function
- temporary files, creating
ms.assetid: 50879c69-215e-425a-a2a3-8b5467121eae
ms.openlocfilehash: 341e1c8ed6dd20ec7e6a3d71999fb365e45e614a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155572"
---
# <a name="tmpfiles"></a>tmpfile_s

建立暫存檔。 它是 [tmpfile](tmpfile.md) 版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

## <a name="syntax"></a>語法

```C
errno_t tmpfile_s(
   FILE** pFilePtr
);
```

### <a name="parameters"></a>參數

*pFilePtr*<br/>
用來儲存所產生資料流指標位址的指標位址。

## <a name="return-value"></a>傳回值

如果成功，則傳回 0，如果失敗，則為錯誤碼。

### <a name="error-conditions"></a>錯誤狀況

|*pFilePtr*|**傳回值**|**內容***pFilePtr*|
|----------------|----------------------|---------------------------------|
|**NULL**|**EINVAL**|未變更|

如果發生上述參數驗證錯誤，會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續，請執行**errno**設為**EINVAL**傳回的值，而且**EINVAL**。

## <a name="remarks"></a>備註

**Tmpfile_s**函式會建立暫存檔，並將指標放在該資料流*pFilePtr*引數。 暫存檔案建立於根目錄。 若要在非根目錄的目錄建立暫存檔案，請使用 [tmpnam_s](tmpnam-s-wtmpnam-s.md) 或 [tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md) 搭配 [fopen](fopen-wfopen.md)。

無法開啟檔案，如果**tmpfile_s**寫入**NULL**來*pFilePtr*參數。 關閉檔案時，一般來說，或當，在程式終止時，會自動刪除這個暫存檔 **_rmtmp**呼叫時，假設目前的工作目錄不會變更。 在中開啟暫存檔**w + b** （二進位讀取/寫入） 模式。

如果您嘗試，就會發生失敗超過**TMP_MAX_S** （請參閱 STDIO。使用 H） 呼叫**tmpfile_s**。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**tmpfile_s**|\<stdio.h>|

如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

> [!NOTE]
> 此範例中，可能需要系統管理權限才能在 Windows 上執行。

```C
// crt_tmpfile_s.c
// This program uses tmpfile_s to create a
// temporary file, then deletes this file with _rmtmp.
//

#include <stdio.h>

int main( void )
{
   FILE *stream;
   char tempstring[] = "String to be written";
   int  i;
   errno_t err;

   // Create temporary files.
   for( i = 1; i <= 3; i++ )
   {
      err = tmpfile_s(&stream);
      if( err )
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
