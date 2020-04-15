---
title: tmpfile_s
ms.date: 4/2/2020
api_name:
- tmpfile_s
- _o_tmpfile_s
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- tmpfile_s
helpviewer_keywords:
- temporary files
- tmpfile_s function
- temporary files, creating
ms.assetid: 50879c69-215e-425a-a2a3-8b5467121eae
ms.openlocfilehash: 8f9dd58abdf1d3225341e40661c14ae3a5013257
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81362467"
---
# <a name="tmpfile_s"></a>tmpfile_s

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

|*pFilePtr*|**返回值**|** ** *pFilePtr*的內容  |
|----------------|----------------------|---------------------------------|
|**空**|**埃因瓦爾**|未變更|

如果發生上述參數驗證錯誤，會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許執行繼續 **,errno**設定為**EINVAL,** 傳回值為**EINVAL**。

## <a name="remarks"></a>備註

**tmpfile_s**函數創建一個暫存檔,並在*pFilePtr*參數中放置指向該流的指標。 暫存檔案建立於根目錄。 若要在非根目錄的目錄建立暫存檔案，請使用 [tmpnam_s](tmpnam-s-wtmpnam-s.md) 或 [tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md) 搭配 [fopen](fopen-wfopen.md)。

如果無法開啟該檔 **,tmpfile_s**將**NULL**寫入*pFilePtr*參數。 當檔案關閉、程式正常終止時或調用 **_rmtmp**時,假設當前工作目錄未更改,此暫存檔將自動刪除。 暫存檔以**w+b(** 二進制讀取/寫入)模式打開。

如果嘗試超過**TMP_MAX_S,** 可能會發生故障(請參閱 STDIO)。H) 呼叫**tmpfile_s**。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**tmpfile_s**|\<stdio.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

> [!NOTE]
> 此示例可能需要管理許可權才能在 Windows 上運行。

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
