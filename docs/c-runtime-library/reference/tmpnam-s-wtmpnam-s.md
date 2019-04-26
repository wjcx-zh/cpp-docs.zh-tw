---
title: tmpnam_s、_wtmpnam_s
ms.date: 11/04/2016
apiname:
- tmpnam_s
- _wtmpnam_s
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
- tmpnam_s
- _wtmpnam_s
- L_tmpnam_s
helpviewer_keywords:
- tmpnam_s function
- file names [C++], creating temporary
- _wtmpnam_s function
- L_tmpnam_s constant
- temporary files, creating
- file names [C++], temporary
- wtmpnam_s function
ms.assetid: e70d76dc-49f5-4aee-bfa2-f1baa2bcd29f
ms.openlocfilehash: 9bf994d16362ef461d8d25d72466721ba9a5890f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62155533"
---
# <a name="tmpnams-wtmpnams"></a>tmpnam_s、_wtmpnam_s

產生可用來建立暫存檔的名稱。 這些是 [tmpnam 和 _wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

## <a name="syntax"></a>語法

```C
errno_t tmpnam_s(
   char * str,
   size_t sizeInChars
);
errno_t _wtmpnam_s(
   wchar_t *str,
   size_t sizeInChars
);
template <size_t size>
errno_t tmpnam_s(
   char (&str)[size]
); // C++ only
template <size_t size>
errno_t _wtmpnam_s(
   wchar_t (&str)[size]
); // C++ only
```

### <a name="parameters"></a>參數

*str*<br/>
將保留所產生名稱的指標。

*sizeInChars*<br/>
緩衝區的大小 (以字元為單位)。

## <a name="return-value"></a>傳回值

這些函式成功時均會傳回 0，或在失敗時傳回錯誤號碼。

### <a name="error-conditions"></a>錯誤狀況

|||||
|-|-|-|-|
|*str*|*sizeInChars*|**傳回值**|**內容***str*|
|**NULL**|any|**EINVAL**|未修改|
|不**NULL** （指向有效的記憶體）|太短|**ERANGE**|未修改|

如果*str*是**NULL**，無效參數處理常式會叫用，如中所述[Parameter Validation](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，這些函式會將**errno**要**EINVAL** ，並傳回**EINVAL**。

## <a name="remarks"></a>備註

這些函式均會傳回目前不存在的檔案名稱。 **tmpnam_s**傳回的名稱指定 Windows 暫存目錄中所傳回的唯一[GetTempPathW](/windows/desktop/api/fileapi/nf-fileapi-gettemppathw)。 請注意，當檔案名稱前面附加反斜線且沒有路徑資訊時，例如 \fname21，這表示名稱對於目前工作目錄有效。

針對**tmpnam_s**，您可以儲存在此產生的檔案名稱*str*。 所傳回的字串的最大長度**tmpnam_s**是**L_tmpnam_s**STDIO 中定義。H. 如果*str*是**NULL**，然後**tmpnam_s**將結果保留在內部靜態緩衝區。 因此任何後續呼叫會終結這個值。 所產生的名稱**tmpnam_s**包含的程式所產生的檔案名稱，以及在第一次呼叫之後**tmpnam_s**，副檔名為循序數字基底的 32 (.1.1vvvvvu，當**TMP_MAX_S** STDIO 中。H 是**INT_MAX**)。

**tmpnam_s**處理多位元組字元字串引數適當地辨識多位元組字元序列，根據的 OEM 字碼頁從作業系統取得的自動。 **_wtmpnam_s**是寬字元版本的**tmpnam_s**; 的引數和傳回值 **_wtmpnam_s**是寬字元字串。 **_wtmpnam_s**並**tmpnam_s**運作方式完全相同，不同之處在於 **_wtmpnam_s**不會處理多位元組字元字串。

在 C++ 中，使用這些函式已透過範本多載簡化；多載可自動推斷緩衝區長度，因而不需要指定大小引數。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttmpnam_s**|**tmpnam_s**|**tmpnam_s**|**_wtmpnam_s**|

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**tmpnam_s**|\<stdio.h>|
|**_wtmpnam_s**|\<stdio.h> 或 \<wchar.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_tmpnam_s.c
// This program uses tmpnam_s to create a unique filename in the
// current working directory.
//

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char name1[L_tmpnam_s];
   errno_t err;
   int i;

   for (i = 0; i < 15; i++)
   {
      err = tmpnam_s( name1, L_tmpnam_s );
      if (err)
      {
         printf("Error occurred creating unique filename.\n");
         exit(1);
      }
      else
      {
         printf( "%s is safe to use as a temporary file.\n", name1 );
      }
   }
}
```

```Output
C:\Users\LocalUser\AppData\Local\Temp\u19q8.0 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.1 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.2 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.3 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.4 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.5 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.6 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.7 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.8 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.9 is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.a is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.b is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.c is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.d is safe to use as a temporary file.
C:\Users\LocalUser\AppData\Local\Temp\u19q8.e is safe to use as a temporary file.
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[malloc](malloc.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
