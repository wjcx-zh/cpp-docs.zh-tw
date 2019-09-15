---
title: _tempnam、_wtempnam、tmpnam、_wtmpnam
ms.date: 11/04/2016
api_name:
- _wtempnam
- _wtmpnam
- tmpnam
- _tempnam
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
- wtempnam
- _wtmpnam
- wtmpnam
- tmpnam
- _wtempnam
- _tempnam
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
ms.openlocfilehash: 9fd1eb9f2f718afec5b7d5555145fcd7e5cc17cf
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957524"
---
# <a name="_tempnam-_wtempnam-tmpnam-_wtmpnam"></a>_tempnam、_wtempnam、tmpnam、_wtmpnam

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
將針對 **_tempnam**傳回的名稱預先暫止的字串。

*dir*<br/>
若沒有 TMP 環境變數，或是 TMP 不是有效的目錄時，檔案名稱中所使用的路徑。

*str*<br/>
將保留所產生名稱，並且將與函式所傳回之名稱相同的指標。 這便於儲存產生的名稱。

## <a name="return-value"></a>傳回值

所有這些函式都會傳回所產生之名稱的指標，如果失敗，則傳回**Null** 。 如果您嘗試超過**TMP_MAX** ，可能會發生失敗（請參閱 stdio.h）。H）使用**tmpnam**呼叫，或如果您使用 **_tempnam** ，且在 TMP 環境變數和*dir*參數中指定了不正確目錄名稱。

> [!NOTE]
> **Tmpnam**和 **_wtmpnam**所傳回的指標會指向內部靜態緩衝區。 不應呼叫 [free](free.md) 來解除配置這些指標。 **_tempnam**和 **_wtempnam**所配置的指標必須呼叫**free** 。

## <a name="remarks"></a>備註

這些函式均會傳回目前不存在的檔案名稱。 **tmpnam**會傳回[GetTempPathW](/windows/win32/api/fileapi/nf-fileapi-gettemppathw)所傳回之指定 Windows 臨時目錄中唯一的名稱。 tempnam 會在指定的目錄中產生唯一的名稱。 **\_** 請注意，當檔案名稱前面附加反斜線且沒有路徑資訊時，例如 \fname21，這表示名稱對於目前工作目錄有效。

針對**tmpnam**，您可以將這個產生的檔案名儲存在*str*中。 如果*str*是**Null**，則**tmpnam**會將結果保留在內部靜態緩衝區中。 因此任何後續呼叫會終結這個值。 **Tmpnam**所產生的名稱包含程式所產生的檔案名，並在第一次呼叫**tmpnam**之後，即基底32（. 1-. vvu 中的序號副檔名，**而 TMP_MAX 則**為 stdio.h。H 為32767）。

**_tempnam**會針對下列規則所選擇的目錄，產生唯一的檔案名：

- 若已定義 TMP 環境變數，而且設定為有效的目錄名稱，則會針對 TMP 所指定的目錄產生唯一的檔案名稱。

- 如果未定義 TMP 環境變數，或是將它設定為不存在之目錄的名稱， **_tempnam**會使用*dir*參數作為它將產生唯一名稱的路徑。

- 如果未定義 TMP 環境變數，或是將它設定為不存在之目錄的名稱，而且如果*dir*是**Null**或設定為不存在之目錄的名稱， **_tempnam**會使用目前的工作目錄來 gene為唯一名稱評分。 目前，如果 TMP 和*dir*都指定不存在的目錄名稱， **_tempnam**函數呼叫將會失敗。

**_Tempnam**傳回的名稱會是*前置*詞和序號的串連，這會結合以建立指定目錄的唯一檔案名。 **_tempnam**會產生沒有副檔名的檔案名。 **_tempnam**會使用[malloc](malloc.md)來設定檔名的空間;程式會負責在不再需要時釋放此空間。

**_tempnam**和**tmpnam**會自動將多位元組字元字串引數處理為適當的，並根據從作業系統取得的 OEM 字碼頁辨識多位元組字元序列。 **_wtempnam**是寬字元版本的 **_tempnam**; **_wtempnam**的引數和傳回值是寬字元字串。 **_wtempnam**和 **_tempnam**的行為相同，不同之處在于 **_wtempnam**不會處理多位元組字元字串。 **_wtmpnam**是寬字元版本的**tmpnam**; **_wtmpnam**的引數和傳回值是寬字元字串。 **_wtmpnam**和**tmpnam**的行為相同，不同之處在于 **_wtmpnam**不會處理多位元組字元字串。

如果已定義 **_debug**和 **_CRTDBG_MAP_ALLOC** ，則 **_tempnam**和 **_wtempnam**會由呼叫[_tempnam_dbg 和 _wtempnam_dbg](tempnam-dbg-wtempnam-dbg.md)取代。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttmpnam**|**tmpnam**|**tmpnam**|**_wtmpnam**|
|**_ttempnam**|**_tempnam**|**_tempnam**|**_wtempnam**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_tempnam**|\<stdio.h>|
|**_wtempnam**、 **_wtmpnam**|\<stdio.h> 或 \<wchar.h>|
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
