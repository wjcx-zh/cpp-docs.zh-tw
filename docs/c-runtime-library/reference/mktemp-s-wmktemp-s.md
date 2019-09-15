---
title: _mktemp_s、_wmktemp_s
ms.date: 11/04/2016
api_name:
- _mktemp_s
- _wmktemp_s
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
- wmktemp_s
- mktemp_s
- _mktemp_s
- _wmktemp_s
helpviewer_keywords:
- _tmktemp_s function
- mktemp_s function
- _wmktemp_s function
- _mktemp_s function
- files [C++], temporary
- tmktemp_s function
- wmktemp_s function
- temporary files [C++]
ms.assetid: 92a7e269-7f3d-4c71-bad6-14bc827a451d
ms.openlocfilehash: b0db1a50f638c6130e4beb6798431179edec153b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951588"
---
# <a name="_mktemp_s-_wmktemp_s"></a>_mktemp_s、_wmktemp_s

建立唯一的檔案名稱。 這些是 [_mktemp、_wmktemp](mktemp-wmktemp.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。

## <a name="syntax"></a>語法

```C
errno_t _mktemp_s(
   char *nameTemplate,
   size_t sizeInChars
);
errno_t _wmktemp_s(
   wchar_t *nameTemplate,
   size_t sizeInChars
);
template <size_t size>
errno_t _mktemp_s(
   char (&nameTemplate)[size]
); // C++ only
template <size_t size>
errno_t _wmktemp_s(
   wchar_t (&nameTemplate)[size]
); // C++ only
```

### <a name="parameters"></a>參數

*nameTemplate*<br/>
檔案名稱模式。

*sizeInChars*<br/>
緩衝區大小，以 **_mktemp_s**中的單一位元組字元為單位; **_wmktemp_s**中的寬字元，包括 null 結束字元。

## <a name="return-value"></a>傳回值

如果成功，這兩個函式會傳回零；如果失敗，則傳回錯誤碼。

### <a name="error-conditions"></a>錯誤狀況

|*nameTemplate*|*sizeInChars*|傳回值|*NameTemplate*中的新值|
|----------------|-------------------|----------------------|-------------------------------|
|**NULL**|any|**EINVAL**|**NULL**|
|不正確的格式（請參閱備註區段以取得正確的格式）|any|**EINVAL**|空字串|
|any|<= X 的數目|**EINVAL**|空字串|

如果發生上述任何一種錯誤狀況，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行， **errno**會設為**EINVAL** ，而函數會傳回**EINVAL**。

## <a name="remarks"></a>備註

**_Mktemp_s**函數會藉由修改*nameTemplate*引數來建立唯一的檔案名，因此在呼叫之後， *nameTemplate*指標會指向包含新檔案名的字串。 **_mktemp_s**會自動將多位元組字元字串引數處理為適當的，並根據執行時間系統目前使用的多位元組字碼頁來辨識多位元組字元序列。 **_wmktemp_s**是寬字元版本的 **_mktemp_s**; **_wmktemp_s**的引數是寬字元字串。 相反地， **_wmktemp_s**和 **_mktemp_s**的行為相同，不同之處在于 **_wmktemp_s**不會處理多位元組字元字串。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp_s**|**_mktemp_s**|**_mktemp_s**|**_wmktemp_s**|

*NameTemplate*引數的格式為**baseXXXXXX**，其中*base*是您所提供之新檔案名的一部分，而每個 X 是 **_mktemp_s**所提供之字元的預留位置。 *NameTemplate*中的每個預留位置字元都必須是大寫的 x。 **_mktemp_s**會保留*基底*，並以字母字元取代第一個尾端 X。 **_mktemp_s**會以五位數的值取代下列尾端 X：這個值是識別呼叫進程或多執行緒程式中呼叫執行緒的唯一數位。

每次成功呼叫 **_mktemp_s**都會修改*nameTemplate*。 在每次來自具有相同*nameTemplate*引數的相同進程或執行緒的後續呼叫中， **_mktemp_s**會檢查符合先前呼叫中 **_mktemp_s**所傳回之名稱的檔案名。 如果指定名稱的檔案不存在， **_mktemp_s**會傳回該名稱。 如果所有先前傳回的名稱都有檔案， **_mktemp_s**會藉由將先前傳回名稱中使用的字母字元取代為下一個可用的小寫字母（依序），從 ' a ' 到 ' z ' 來建立新名稱。 例如，如果*base*為：

> **fn**

**_mktemp_s**所提供的五位數值是12345，傳回的第一個名稱是：

> **fna12345**

如果這個名稱是用來建立檔案 FNA12345，而且這個檔案仍然存在，則從相同進程或具有相同*nameTemplate* *基底*之執行緒的呼叫傳回的下一個名稱為：

> **fnb12345**

如果 FNA12345 不存在，下一個傳回的名稱仍然會是：

> **fna12345**

針對任何指定的*base*和*nameTemplate*值組合， **_mktemp_s**最多可以建立26個唯一的檔案名。 因此，FNZ12345 是最後一個唯一檔案名 **_mktemp_s**可以針對此範例中使用的*基底*和*nameTemplate*值來建立的名稱。

C++ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_mktemp_s**|\<io.h>|
|**_wmktemp_s**|\<io.h> 或 \<wchar.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```cpp
// crt_mktemp_s.cpp
/* The program uses _mktemp to create
* five unique filenames. It opens each filename
* to ensure that the next name is unique.
*/

#include <io.h>
#include <string.h>
#include <stdio.h>

char *fnTemplate = "fnXXXXXX";
char names[5][9];

int main()
{
   int i, err, sizeInChars;
   FILE *fp;

   for( i = 0; i < 5; i++ )
   {
      strcpy_s( names[i], sizeof(names[i]), fnTemplate );
      /* Get the size of the string and add one for the null terminator.*/
      sizeInChars = strnlen(names[i], 9) + 1;
      /* Attempt to find a unique filename: */
      err = _mktemp_s( names[i], sizeInChars );
      if( err != 0 )
         printf( "Problem creating the template" );
      else
      {
         if( fopen_s( &fp, names[i], "w" ) == 0 )
            printf( "Unique filename is %s\n", names[i] );
         else
            printf( "Cannot open %s\n", names[i] );
         fclose( fp );
      }
   }

   return 0;
}
```

### <a name="sample-output"></a>範例輸出

```Output
Unique filename is fna03188
Unique filename is fnb03188
Unique filename is fnc03188
Unique filename is fnd03188
Unique filename is fne03188
```

## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_getpid](getpid.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_tempnam、_wtempnam、tmpnam、_wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[tmpfile_s](tmpfile-s.md)<br/>
