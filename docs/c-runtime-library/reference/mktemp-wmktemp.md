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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 8affd20ca7826f0d383f749567c9625d61dacd48
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338724"
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

*名稱範本*<br/>
檔案名稱模式。

## <a name="return-value"></a>傳回值

每個函數都返回指向修改的名稱範本的指標。 如果*名稱樣本*格式錯誤,或者無法從給定名稱範本創建更多唯一名稱,則函數將返回**NULL。**

## <a name="remarks"></a>備註

**_mktemp**函數通過修改*nameTemplate*參數創建唯一的檔名。 **_mktemp**根據需要自動處理多位元位元串參數,根據運行時系統當前使用的多位元組碼頁識別多位元組字串序列。 **_wmktemp**是 **_mktemp**的寬字元版本;**_wmktemp**的參數和返回值是寬字元字串。 **_wmktemp**和 **_mktemp**行為相同,只不過 **_wmktemp**不處理多位元組位元串。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp**|**_mktemp**|**_mktemp**|**_wmktemp**|

*nameTemplate*參數具有表單*基礎*XXXXXX,其中*base*是您提供的新檔名的一部分,每個 X 是 **_mktemp**提供的字元的佔位元。 *名稱範本*中的每個佔位元字元都必須是大寫**X,_mktemp**保留*基數*,並將第一個尾隨 X 替換為字母字元。 **_mktemp**將以下尾隨 X 替換為五位值;此值是標識調用過程的唯一編號,或在多線程程序中標識調用線程。

每次成功呼叫 **_mktemp**都會修改*名稱樣本*。 在來自具有相同*名稱Template*參數的同一進程或線程的每個後續調用中 **,_mktemp**檢查與 **_mktemp**在以前的調用中返回的名稱匹配的檔名。 如果給定名稱不存在檔 **,_mktemp**返回該名稱。 如果以前返回的所有名稱都有檔 **,_mktemp**通過將以前返回的名稱中使用的字母字元替換為下一個可用小寫字母(按順序從"a"到"z")來創建新名稱。 例如,如果*基為*:

> **Fn**

**_mktemp**提供的五位值為 12345,傳回的第一個名稱是:

> **fna12345**

如果此名稱用於建立檔案 FNA12345,並且此檔仍然存在,則從具有相同*名稱樣本**基礎*的同一行程或線程呼叫時傳回的下一個名稱是:

> **fnb12345**

如果 FNA12345 不存在，下一個傳回的名稱仍然會是：

> **fna12345**

**_mktemp**最多可以為*基本*值和*nameTemplate*值的任意給定組合創建 26 個唯一檔名。 因此,FNZ12345 是 **_mktemp可以為本**範例中使用*的基礎*和*名稱範本*值創建的最後一個唯一檔名。

失敗時,將設置**errno。** 如果*nameTemplate*的格式無效(例如,小於 6 X),**則 errno**設定為**EINVAL**。 如果 **_mktemp**無法建立唯一名稱,因為所有 26 個可能的檔案名稱都已存在 **,_mktemp**將 nameTemplate 設定到一個空字串,並傳回**EEXIST**。

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
