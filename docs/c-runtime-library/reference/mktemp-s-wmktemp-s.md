---
title: _mktemp_s、_wmktemp_s
ms.date: 11/04/2016
apiname:
- _mktemp_s
- _wmktemp_s
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
ms.openlocfilehash: fef10f2cfbcc0332741d560a41a782b70ed14798
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156528"
---
# <a name="mktemps-wmktemps"></a>_mktemp_s、_wmktemp_s

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
在中的單一位元組字元的緩衝區大小 **_mktemp_s**寬字元 **_wmktemp_s**，包括 null 結束字元。

## <a name="return-value"></a>傳回值

如果成功，這兩個函式會傳回零；如果失敗，則傳回錯誤碼。

### <a name="error-conditions"></a>錯誤狀況

|*nameTemplate*|*sizeInChars*|傳回值|中的新值*nameTemplate*|
|----------------|-------------------|----------------------|-------------------------------|
|**NULL**|any|**EINVAL**|**NULL**|
|格式不正確 (請參閱 < 備註 > 一節以取得正確的格式)|any|**EINVAL**|空字串|
|any|<= X 的數目|**EINVAL**|空字串|

如果發生上述任何一種錯誤狀況，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續，請執行**errno**設為**EINVAL**和函式會傳回**EINVAL**。

## <a name="remarks"></a>備註

**_Mktemp_s**函式會建立唯一的檔案名稱，藉由修改*nameTemplate*引數，以便呼叫之後， *nameTemplate*指標會指向字串包含新的檔案名稱。 **_mktemp_s**自動多位元組字元字串引數處理為適當且由執行階段系統辨識多位元組字元序列，根據目前使用中的多位元組字碼頁。 **_wmktemp_s**是寬字元版本的 **_mktemp_s**; 的引數 **_wmktemp_s**是寬字元字串。 **_wmktemp_s**並 **_mktemp_s**行為相同，不同之處在於 **_wmktemp_s**不會處理多位元組字元字串。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp_s**|**_mktemp_s**|**_mktemp_s**|**_wmktemp_s**|

*NameTemplate*引數的形式**baseXXXXXX**，其中*基底*是您所提供的新檔案名稱的一部分，而每個 X 是所提供的字元預留位置 **_mktemp_s**。 每個預留位置字元*nameTemplate*必須是大寫 x。 **_mktemp_s**保留*基底*，並以字母字元取代的第一個後置 X。 **_mktemp_s**取代的後置 x 的五位數的值，這個值是唯一的數字，識別呼叫處理序中，或在多執行緒程式中，呼叫的執行緒。

每次成功呼叫 **_mktemp_s**修改*nameTemplate*。 在每個後續的呼叫，從相同的程序或執行緒具有相同*nameTemplate*引數 **_mktemp_s**檢查所傳回的名稱相符的檔案名稱 **_mktemp_s**在先前的呼叫。 如果檔案不存在指定名稱時，請 **_mktemp_s**傳回該名稱。 如果檔案存在，所有先前傳回的名稱， **_mktemp_s**建立的新名稱來取代它使用於下一個可用的小寫字母，順序，從 'a' 到 'z' 先前傳回的名稱的字母字元。 例如，如果*基底*是：

> **fn**

與所提供的五位數值 **_mktemp_s**為 12345，傳回的第一個名稱為：

> **fna12345**

如果此名稱會用來建立檔案 FNA12345，而且此檔案仍然存在，在呼叫傳回相同的程序或執行緒具有相同的下一步 的名稱*基底*for *nameTemplate*是：

> **fnb12345**

如果 FNA12345 不存在，下一個傳回的名稱仍然會是：

> **fna12345**

**_mktemp_s**可以建立最多 26 的唯一檔案名稱，任何給定的組合*基底*並*nameTemplate*值。 因此，FNZ12345 是最後一個唯一的檔案名稱 **_mktemp_s**可以為建立*基底*並*nameTemplate*此範例中使用的值。

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
