---
title: _mktemp、_wmktemp
ms.date: 4/2/2020
api_name:
- _wmktemp
- _mktemp
- _o__mktemp
- _o__wmktemp
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
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 536a63841c6e29fa003eb8b99c896f6d1cf5519f
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919093"
---
# <a name="_mktemp-_wmktemp"></a>_mktemp、_wmktemp

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

所有這些函式都會傳回已修改之 nameTemplate 的指標。 如果*nameTemplate*的格式不正確，或無法從指定的 nameTemplate 建立更多的唯一名稱，此函數會傳回**Null** 。

## <a name="remarks"></a>備註

**_Mktemp**函式會藉由修改*nameTemplate*引數來建立唯一的檔案名。 **_mktemp**會自動將多位元組字元字串引數處理為適當，並根據執行時間系統目前使用的多位元組字碼頁來辨識多位元組字元序列。 **_wmktemp**是寬字元版本的 **_mktemp**;**_wmktemp**的引數和傳回值是寬字元字串。 **_wmktemp**和 **_mktemp**的行為完全相同，不同之處在于 **_wmktemp**不會處理多位元組字元字串。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp**|**_mktemp**|**_mktemp**|**_wmktemp**|

*NameTemplate*引數的格式為*base*XXXXXX，其中*base*是您所提供之新檔案名的一部分，而每個 X 是 **_mktemp**所提供之字元的預留位置。 *NameTemplate*中的每個預留位置字元都必須是大寫 x。 **_mktemp**會保留*基底*，並以字母字元取代第一個尾端 X。 **_mktemp**以五位數的值取代下列尾端 X：這個值是識別呼叫進程或多執行緒程式中呼叫執行緒的唯一數位。

每次成功呼叫 **_mktemp**都會修改*nameTemplate*。 在每次來自具有相同*nameTemplate*引數之相同進程或執行緒的後續呼叫中， **_mktemp**會檢查符合先前呼叫中 **_mktemp**所傳回之名稱的檔案名。 如果指定名稱的檔案不存在， **_mktemp**會傳回該名稱。 如果所有先前傳回的名稱都有檔案， **_mktemp**會藉由使用下一個可用的小寫字母（依序從 ' a ' 到 ' z '）來取代先前傳回的名稱中所用的字母字元，以建立新的名稱。 例如，如果*base*為：

> **fn**

**_mktemp**所提供的五位數值為12345，則傳回的第一個名稱為：

> **fna12345**

如果這個名稱是用來建立檔案 FNA12345，而且這個檔案仍然存在，則從相同進程或具有相同*nameTemplate* *基底*之執行緒的呼叫傳回的下一個名稱為：

> **fnb12345**

如果 FNA12345 不存在，下一個傳回的名稱仍然會是：

> **fna12345**

**_mktemp**最多可為*基底*和*nameTemplate*值的任何指定組合建立26個唯一的檔案名。 因此，FNZ12345 是最後一個唯一的檔案名， **_mktemp**可以為此範例中使用的*基底*和*nameTemplate*值建立此名稱。

失敗時，會設定**errno** 。 如果*nameTemplate*的格式無效（例如，少於 6 X）， **errno**會設定為**EINVAL**。 如果 **_mktemp**無法建立唯一的名稱，因為所有26個可能的檔案名已經存在， **_mktemp**將 nameTemplate 設定為空字串，並傳回**EEXIST**。

在 C++ 中，這些函式具有樣板多載，可以叫用這些函式的更新且安全的對應版本。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_mktemp**|\<io.h>|
|**_wmktemp**|\<io.h> 或 \<wchar.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

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
