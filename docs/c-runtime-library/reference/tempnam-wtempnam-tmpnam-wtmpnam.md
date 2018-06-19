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
ms.openlocfilehash: 55ff069d72d68493eee524ea2f9c012d2fc7f534
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32417009"
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
將會附加到傳回的名稱的字串 **_tempnam**。

*dir*<br/>
若沒有 TMP 環境變數，或是 TMP 不是有效的目錄時，檔案名稱中所使用的路徑。

*str*<br/>
將保留所產生名稱，並且將與函式所傳回之名稱相同的指標。 這便於儲存產生的名稱。

## <a name="return-value"></a>傳回值

所有這些函式會傳回產生的名稱的指標或**NULL**失敗時。 如果您嘗試使用，就會發生失敗超過**TMP_MAX** （請參閱 STDIO。H） 呼叫**tmpnam**或如果您使用 **_tempnam** ，而且沒有指定在 TMP 環境變數和不正確的目錄名稱*dir*參數。

> [!NOTE]
> 所傳回的指標**tmpnam**和 **_wtmpnam**指向內部靜態緩衝區。 不應呼叫 [free](free.md) 來解除配置這些指標。 **免費**所配置的指標呼叫 **_tempnam**和 **_wtempnam**。

## <a name="remarks"></a>備註

這些函式均會傳回目前不存在的檔案名稱。 **tmpnam**傳回目前工作目錄中唯一的名稱和 **_tempnam**可讓您在目前以外的目錄中產生唯一的名稱。 請注意，當檔案名稱前面附加反斜線且沒有路徑資訊時，例如 \fname21，這表示名稱對於目前工作目錄有效。

如**tmpnam**，您可以儲存在此產生的檔案名稱*str*。 如果*str*是**NULL**，然後**tmpnam**離開內部的靜態緩衝區中的結果。 因此任何後續呼叫會終結這個值。 所產生的名稱**tmpnam**包含程式所產生的檔案名稱，以及之後的第一個呼叫**tmpnam**，副檔名為循序數字基底的 32 (.1-.vvu 時**TMP_MAX** STDIO 中。H 是 32767）。

**_tempnam**會產生唯一的檔名的目錄，下列規則來選擇：

- 若已定義 TMP 環境變數，而且設定為有效的目錄名稱，則會針對 TMP 所指定的目錄產生唯一的檔案名稱。

- 若 TMP 環境變數未定義，或設的目錄不存在，名稱為 **_tempnam**將使用*dir*參數，它會產生唯一名稱的路徑。

- 如果 TMP 環境變數未定義或如果設定不存在的目錄名稱而且*dir*是**NULL**或設定的目錄不存在，名稱為 **_tempnam**會使用目前的工作目錄，來產生唯一的名稱。 目前，如果這兩個 TMP 和*dir*指定名稱的目錄不存在， **_tempnam**函式呼叫將會失敗。

所傳回的名稱 **_tempnam**會串連*前置詞*和序號，可相結合，以建立唯一的檔名指定的目錄。 **_tempnam**會產生不具有任何副檔名的檔案名稱。 **_tempnam**使用[malloc](malloc.md)配置空間的檔案名稱; 此程式會負責在不再需要時釋放此空間。

**_tempnam**和**tmpnam**控制代碼多位元組字元字串引數為適當且可辨識的多位元組字元序列的 OEM 字碼頁根據自動從作業系統取得。 **_wtempnam**是寬字元版本的 **_tempnam**; 引數和傳回值 **_wtempnam**是寬字元字串。 **_wtempnam**和 **_tempnam**行為相同，除了 **_wtempnam**不會處理多位元組字元字串。 **_wtmpnam**是寬字元版本的**tmpnam**; 的引數和傳回值 **_wtmpnam**是寬字元字串。 **_wtmpnam**和**tmpnam**行為相同，除了 **_wtmpnam**不會處理多位元組字元字串。

如果 **_DEBUG**和 **_CRTDBG_MAP_ALLOC**所定義， **_tempnam**和 **_wtempnam**會呼叫所取代[_tempnam_dbg 和 _wtempnam_dbg](tempnam-dbg-wtempnam-dbg.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|TCHAR.H 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_ttmpnam**|**tmpnam**|**tmpnam**|**_wtmpnam**|
|**_ttempnam**|**_tempnam**|**_tempnam**|**_wtempnam**|

## <a name="requirements"></a>需求

|常式|必要的標頭|
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
// current working directory, then uses _tempnam to create
// a unique filename with a prefix of stq.

#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   char* name1 = NULL;
   char* name2 = NULL;

   // Create a temporary filename for the current working directory:
   if( ( name1 = tmpnam( NULL ) ) != NULL ) // C4996
   // Note: tmpnam is deprecated; consider using tmpnam_s instead
      printf( "%s is safe to use as a temporary file.\n", name1 );
   else
      printf( "Cannot create a unique filename\n" );

   // Create a temporary filename in temporary directory with the
   // prefix "stq". The actual destination directory may vary
   // depending on the state of the TMP environment variable and
   // the global variable P_tmpdir.

   if( ( name2 = _tempnam( "c:\\tmp", "stq" ) ) != NULL )
      printf( "%s is safe to use as a temporary file.\n", name2 );
   else
      printf( "Cannot create a unique filename\n" );

   // When name2 is no longer needed :
   if(name2)
     free(name2);

}
```

```Output
\s1gk. is safe to use as a temporary file.
C:\DOCUME~1\user\LOCALS~1\Temp\2\stq2 is safe to use as a temporary file.
```

## <a name="see-also"></a>另請參閱

[資料流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[malloc](malloc.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[tmpfile](tmpfile.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
