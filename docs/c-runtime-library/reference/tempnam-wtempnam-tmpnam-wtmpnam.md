---
title: _tempnam、_wtempnam、tmpnam、_wtmpnam | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _wtempnam
- _wtmpnam
- tmpnam
- _tempnam
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
- wtempnam
- _wtmpnam
- wtmpnam
- tmpnam
- _wtempnam
- _tempnam
dev_langs:
- C++
helpviewer_keywords:
- wtempnam function
- file names [C++], creating temporary
- _tempnam function
- ttmpnam function
- tmpnam function
- tempnam function
- wtmpnam function
- temporary files, creating
- file names [C++], temporary
- _ttmpnam function
- _wtmpnam function
- _wtempnam function
ms.assetid: 3ce75f0f-5e30-42a6-9791-8d7cbfe70fca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce1b0a495c2556b39a18937635d9109eaaeb2433
ms.sourcegitcommit: fb9448eb96c6351a77df04af16ec5c0fb9457d9e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2018
ms.locfileid: "44691415"
---
# <a name="tempnam-wtempnam-tmpnam-wtmpnam"></a>_tempnam、_wtempnam、tmpnam、_wtmpnam

產生可用來建立暫存檔的名稱。 您現在已有這些函式當中某些更安全的版本可以使用，請參閱 [tmpnam_s、_wtmpnam_s](tmpnam-s-wtmpnam-s.md)。

## <a name="syntax"></a>語法

```C
char *_tempnam(
   const char *dir,
   const char *prefix
);
wchar_t *_wtempnam(
   const wchar_t *dir,
   const wchar_t *prefix
);
char *tmpnam(
   char *str
);
wchar_t *_wtmpnam(
   wchar_t *str
);
```

### <a name="parameters"></a>參數

*prefix*<br/>
將會附加至所傳回的名稱的字串 **_tempnam**。

*dir*<br/>
若沒有 TMP 環境變數，或是 TMP 不是有效的目錄時，檔案名稱中所使用的路徑。

*str*<br/>
將保留所產生名稱，並且將與函式所傳回之名稱相同的指標。 這便於儲存產生的名稱。

## <a name="return-value"></a>傳回值

所有這些函式都會傳回產生的名稱的指標或**NULL**失敗時。 如果您嘗試，就會發生失敗超過**TMP_MAX** （請參閱 STDIO。使用 H） 呼叫**tmpnam**或如果您使用 **_tempnam** ，而且沒有無效的目錄名稱指定為 TMP 環境變數中，然後在*dir*參數。

> [!NOTE]
> 所傳回的指標**tmpnam**並 **_wtmpnam**指向內部靜態緩衝區。 不應呼叫 [free](free.md) 來解除配置這些指標。 **免費**需要呼叫所配置的指標 **_tempnam**並 **_wtempnam**。

## <a name="remarks"></a>備註

這些函式均會傳回目前不存在的檔案名稱。 **tmpnam**會傳回在所傳回的指定 Windows 暫存目錄中是唯一的名稱[GetTempPathW](/windows/desktop/api/fileapi/nf-fileapi-gettemppathw)。 **\_tempnam**指定以外的目錄中產生的唯一名稱。 請注意，當檔案名稱前面附加反斜線且沒有路徑資訊時，例如 \fname21，這表示名稱對於目前工作目錄有效。

針對**tmpnam**，您可以儲存在此產生的檔案名稱*str*。 如果*str*是**NULL**，然後**tmpnam**將結果保留在內部靜態緩衝區。 因此任何後續呼叫會終結這個值。 所產生的名稱**tmpnam**包含的程式所產生的檔案名稱，以及在第一次呼叫之後**tmpnam**，副檔名為循序數字基底的 32 (.1.1-.vvu，當**TMP_MAX** STDIO 中。H 是 32,767）。

**_tempnam**會產生下列規則所選擇的目錄的唯一檔案名稱：

- 若已定義 TMP 環境變數，而且設定為有效的目錄名稱，則會針對 TMP 所指定的目錄產生唯一的檔案名稱。

- 如果未定義 TMP 環境變數，或如果它設定為不存在，目錄名稱 **_tempnam**會使用*dir*參數做為路徑，它會產生唯一的名稱。

- 如果未定義 TMP 環境變數或如果它設定為不存在，目錄的名稱，如果*dir*是**NULL**設定為不存在，目錄名稱或 **_tempnam**目前的工作目錄將用來產生唯一的名稱。 目前，如果 TMP 和*dir*指定之目錄的不存在，名稱 **_tempnam**函式呼叫將會失敗。

所傳回的名稱 **_tempnam**將會串連*前置詞*和序號，它們相結合，以建立唯一的檔名指定的目錄。 **_tempnam**會產生沒有副檔名的檔案名稱。 **_tempnam**會使用[malloc](malloc.md)配置空間，檔案名稱; 此程式會負責時不再需要時釋放此空間。

**_tempnam**並**tmpnam**處理多位元組字元字串引數適當地辨識多位元組字元序列，根據的 OEM 字碼頁從作業系統取得的自動。 **_wtempnam**是寬字元版本的 **_tempnam**; 引數和傳回值 **_wtempnam**是寬字元字串。 **_wtempnam**並 **_tempnam**運作方式完全相同，不同之處在於 **_wtempnam**不會處理多位元組字元字串。 **_wtmpnam**是寬字元版本的**tmpnam**; 的引數和傳回值 **_wtmpnam**是寬字元字串。 **_wtmpnam**並**tmpnam**運作方式完全相同，不同之處在於 **_wtmpnam**不會處理多位元組字元字串。

如果 **_DEBUG**並 **_CRTDBG_MAP_ALLOC**定義， **_tempnam**並 **_wtempnam**會取代藉由呼叫[_tempnam_dbg 和 _wtempnam_dbg](tempnam-dbg-wtempnam-dbg.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttmpnam**|**tmpnam**|**tmpnam**|**_wtmpnam**|
|**_ttempnam**|**_tempnam**|**_tempnam**|**_wtempnam**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_tempnam**|\<stdio.h>|
|**_wtempnam**， **_wtmpnam**|\<stdio.h> 或 \<wchar.h>|
|**tmpnam**|\<stdio.h>|

如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_tempnam.c
// compile with: /W3
// This program uses tmpnam to create a unique filename in the
// temporary directory, and _tempname to create a unique filename
// in C:\\tmp.

#include <stdio.h>
#include <stdlib.h>

int main(void)
{
   char * name1 = NULL;
   char * name2 = NULL;
   char * name3 = NULL;

   // Create a temporary filename for the current working directory:
   if ((name1 = tmpnam(NULL)) != NULL) { // C4996
   // Note: tmpnam is deprecated; consider using tmpnam_s instead
      printf("%s is safe to use as a temporary file.\n", name1);
   } else {
      printf("Cannot create a unique filename\n");
   }

   // Create a temporary filename in temporary directory with the
   // prefix "stq". The actual destination directory may vary
   // depending on the state of the TMP environment variable and
   // the global variable P_tmpdir.

   if ((name2 = _tempnam("c:\\tmp", "stq")) != NULL) {
      printf("%s is safe to use as a temporary file.\n", name2);
   } else {
      printf("Cannot create a unique filename\n");
   }

   // When name2 is no longer needed:
   if (name2) {
      free(name2);
   }

   // Unset TMP environment variable, then create a temporary filename in C:\tmp.
   if (_putenv("TMP=") != 0) {
      printf("Could not remove TMP environment variable.\n");
   }

   // With TMP unset, we will use C:\tmp as the temporary directory.
   // Create a temporary filename in C:\tmp with prefix "stq".
   if ((name3 = _tempnam("c:\\tmp", "stq")) != NULL) {
      printf("%s is safe to use as a temporary file.\n", name3);
   }
   else {
      printf("Cannot create a unique filename\n");
   }

   // When name3 is no longer needed:
   if (name3) {
      free(name3);
   }

   return 0;
}
```

```Output
C:\Users\LocalUser\AppData\Local\Temp\sriw.0 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\stq2 is safe to use as a temporary file.
c:\tmp\stq3 is safe to use as a temporary file.
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[malloc](malloc.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[tmpfile](tmpfile.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
