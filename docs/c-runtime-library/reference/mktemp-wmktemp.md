---
title: _mktemp、_wmktemp
ms.date: 11/04/2016
apiname:
- _wmktemp
- _mktemp
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
- _tmktemp
- wmktemp
- tmktemp
- _wmktemp
- _mktemp
helpviewer_keywords:
- _wmktemp function
- _mktemp function
- files [C++], temporary
- tmktemp function
- _tmktemp function
- wmktemp function
- mktemp function
- temporary files [C++]
ms.assetid: 055eb539-a8c2-4a7d-be54-f5b6d1eb5c85
ms.openlocfilehash: c1c5f0ee12c9e07d76405014bb4a6a6ecc7d97e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156508"
---
# <a name="mktemp-wmktemp"></a>_mktemp、_wmktemp

建立唯一的檔案名稱。 這些函式已有更安全的版本可用，請參閱 [_mktemp_s、_wmktemp_s](mktemp-s-wmktemp-s.md)。

## <a name="syntax"></a>語法

```C
char *_mktemp(
   char *nameTemplate
);
wchar_t *_wmktemp(
   wchar_t *nameTemplate
);
template <size_t size>
char *_mktemp(
   char (&nameTemplate)[size]
); // C++ only
template <size_t size>
wchar_t *_wmktemp(
   wchar_t (&nameTemplate)[size]
); // C++ only
```

### <a name="parameters"></a>參數

*nameTemplate*<br/>
檔案名稱模式。

## <a name="return-value"></a>傳回值

所有這些函式都會傳回已修改的 nameTemplate 的指標。 此函數會傳回**NULL**如果*nameTemplate*格式不正確，或從指定 nameTemplate 可以建立沒有其他的唯一名稱。

## <a name="remarks"></a>備註

**_Mktemp**函式會建立唯一的檔案名稱，藉由修改*nameTemplate*引數。 **_mktemp**自動多位元組字元字串引數處理為適當且由執行階段系統辨識多位元組字元序列，根據目前使用中的多位元組字碼頁。 **_wmktemp**是寬字元版本的 **_mktemp**; 的引數和傳回值 **_wmktemp**是寬字元字串。 **_wmktemp**並 **_mktemp**行為相同，不同之處在於 **_wmktemp**不會處理多位元組字元字串。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp**|**_mktemp**|**_mktemp**|**_wmktemp**|

*NameTemplate*引數的形式*基底*XXXXXX，其中*基底*是您所提供的新檔案名稱的一部分，而每個 X 是所提供的字元預留位置 **_mktemp**。 每個預留位置字元*nameTemplate*必須是大寫 x。 **_mktemp**保留*基底*，並以字母字元取代的第一個後置 X。 **_mktemp**取代的後置 x 的五位數的值，這個值是唯一的數字，識別呼叫處理序中，或在多執行緒程式中，呼叫的執行緒。

每次成功呼叫 **_mktemp**修改*nameTemplate*。 在每個後續的呼叫，從相同的程序或執行緒具有相同*nameTemplate*引數 **_mktemp**檢查所傳回的名稱相符的檔案名稱 **_mktemp**中先前的呼叫。 如果檔案不存在指定名稱時，請 **_mktemp**傳回該名稱。 如果檔案存在，所有先前傳回的名稱， **_mktemp**建立的新名稱來取代它使用於下一個可用的小寫字母，順序，從 'a' 到 'z' 先前傳回的名稱的字母字元。 例如，如果*基底*是：

> **fn**

與所提供的五位數值 **_mktemp**為 12345，傳回的第一個名稱為：

> **fna12345**

如果此名稱會用來建立檔案 FNA12345，而且此檔案仍然存在，在呼叫傳回相同的程序或執行緒具有相同的下一步 的名稱*基底*for *nameTemplate*是：

> **fnb12345**

如果 FNA12345 不存在，下一個傳回的名稱仍然會是：

> **fna12345**

**_mktemp**可以建立最多 26 的唯一檔案名稱，任何給定的組合*基底*並*nameTemplate*值。 因此，FNZ12345 是最後一個唯一的檔案名稱 **_mktemp**可以為建立*基底*並*nameTemplate*此範例中使用的值。

在失敗時， **errno**設定。 如果*nameTemplate*具有無效的格式 (例如，少於 6 X)， **errno**設定為**EINVAL**。 如果 **_mktemp**無法建立唯一的名稱，因為 26 的所有可能的檔案名稱已經存在，所以 **_mktemp** nameTemplate 設為空字串，並傳回**EEXIST**。

在 C++ 中，這些函式具有樣板多載，可以叫用這些函式的更新且安全的對應版本。 如需詳細資訊，請參閱 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_mktemp**|\<io.h>|
|**_wmktemp**|\<io.h> 或 \<wchar.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_mktemp.c
// compile with: /W3
/* The program uses _mktemp to create
* unique filenames. It opens each filename
* to ensure that the next name is unique.
*/

#include <io.h>
#include <string.h>
#include <stdio.h>
#include <errno.h>

char *template = "fnXXXXXX";
char *result;
char names[27][9];

int main( void )
{
   int i;
   FILE *fp;

   for( i = 0; i < 27; i++ )
   {
      strcpy_s( names[i], sizeof( names[i] ), template );
      /* Attempt to find a unique filename: */
      result = _mktemp( names[i] );  // C4996
      // Note: _mktemp is deprecated; consider using _mktemp_s instead
      if( result == NULL )
      {
         printf( "Problem creating the template\n" );
         if (errno == EINVAL)
         {
             printf( "Bad parameter\n");
         }
         else if (errno == EEXIST)
         {
             printf( "Out of unique filenames\n");
         }
      }
      else
      {
         fopen_s( &fp, result, "w" );
         if( fp != NULL )
            printf( "Unique filename is %s\n", result );
         else
            printf( "Cannot open %s\n", result );
         fclose( fp );
      }
   }
}
```

```Output
Unique filename is fna03912
Unique filename is fnb03912
Unique filename is fnc03912
Unique filename is fnd03912
Unique filename is fne03912
Unique filename is fnf03912
Unique filename is fng03912
Unique filename is fnh03912
Unique filename is fni03912
Unique filename is fnj03912
Unique filename is fnk03912
Unique filename is fnl03912
Unique filename is fnm03912
Unique filename is fnn03912
Unique filename is fno03912
Unique filename is fnp03912
Unique filename is fnq03912
Unique filename is fnr03912
Unique filename is fns03912
Unique filename is fnt03912
Unique filename is fnu03912
Unique filename is fnv03912
Unique filename is fnw03912
Unique filename is fnx03912
Unique filename is fny03912
Unique filename is fnz03912
Problem creating the template.
Out of unique filenames.
```

## <a name="see-also"></a>另請參閱

[檔案處理](../../c-runtime-library/file-handling.md)<br/>
[fopen、_wfopen](fopen-wfopen.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_getpid](getpid.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_tempnam、_wtempnam、tmpnam、_wtmpnam](tempnam-wtempnam-tmpnam-wtmpnam.md)<br/>
[tmpfile](tmpfile.md)<br/>
