---
title: _mktemp_s、_wmktemp_s
ms.date: 4/2/2020
api_name:
- _mktemp_s
- _wmktemp_s
- _o__mktemp_s
- _o__wmktemp_s
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
ms.openlocfilehash: 061c5647b2c5a5e79b017cf93989f62ad19cfc0a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81338759"
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

*名稱範本*<br/>
檔案名稱模式。

*大小在查理斯*<br/>
**_mktemp_s**中以單位元位位元表示緩衝區的大小;**_wmktemp_s**中的寬字元,包括空終止符。

## <a name="return-value"></a>傳回值

如果成功，這兩個函式會傳回零；如果失敗，則傳回錯誤碼。

### <a name="error-conditions"></a>錯誤狀況

|*名稱範本*|*大小在查理斯*|傳回值|*名稱樣本*中的新值|
|----------------|-------------------|----------------------|-------------------------------|
|**空**|任意|**埃因瓦爾**|**空**|
|格式不正確(有關正確格式,請參閱備註部分)|任意|**埃因瓦爾**|空字串|
|任意|<= X 的數目|**埃因瓦爾**|空字串|

如果發生上述任何一種錯誤狀況，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許執行繼續 **,errno**設定為**EINVAL,** 函數傳回**EINVAL**。

## <a name="remarks"></a>備註

**_mktemp_s**函數透過修改*nameTemplate*參數建立唯一的檔名,以便在呼叫後 *,nameTemplate*指標指向包含新檔名的字串。 **_mktemp_s**根據需要自動處理多位元位元串參數,根據運行時系統當前使用的多位元組碼頁識別多位元組字串序列。 **_wmktemp_s**是 **_mktemp_s**的寬字元版本;**_wmktemp_s**的參數是寬字元字串。 **_wmktemp_s**和 **_mktemp_s**行為相同,除非 **_wmktemp_s**不處理多位元組位元串。

這些函數的調試庫版本首先用 0xFE 填充緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md)。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tmktemp_s**|**_mktemp_s**|**_mktemp_s**|**_wmktemp_s**|

*nameTemplate*參數具有表單**檔案 baseXXXXXX,** 其中*base*是您提供的新檔案名的一部分,每個 X 是 **_mktemp_s**提供的字元的佔位元。 *名稱樣本*中的每個佔位元字元都必須是大寫**X,_mktemp_s**保留*基,* 並將第一個尾隨 X 替換為字母字元。 **_mktemp_s**將以下尾隨 X 替換為五位值;此值是標識調用過程的唯一編號,或在多線程程序中標識調用線程。

每次成功呼叫 **_mktemp_s**變更*名稱樣本*。 在來自具有相同*名稱Template*參數的同一進程或線程的每個後續調用中 **,_mktemp_s**檢查與 **_mktemp_s**在以前的調用中返回的名稱匹配的檔名。 如果給定名稱不存在檔 **,_mktemp_s**返回該名稱。 如果以前返回的所有名稱都有檔 **,_mktemp_s**通過將以前返回的名稱中使用的字母字元替換為下一個可用小寫字母(按順序從"a"到"z")來創建新名稱。 例如,如果*基為*:

> **Fn**

**_mktemp_s**提供的五位值為 12345,傳回的第一個名稱是:

> **fna12345**

如果此名稱用於建立檔案 FNA12345,並且此檔仍然存在,則從具有相同*名稱樣本**基礎*的同一行程或線程呼叫時傳回的下一個名稱是:

> **fnb12345**

如果 FNA12345 不存在，下一個傳回的名稱仍然會是：

> **fna12345**

**_mktemp_s**最多可以為*基本*值和*nameTemplate*值的任意給定組合創建 26 個唯一檔名。 因此,FNZ12345 是最後一個唯一的檔名 **_mktemp_s**可以為本示例中使用*的基礎*和*名稱範本*值創建。

C++ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_mktemp_s**|\<io.h>|
|**_wmktemp_s**|\<io.h> 或 \<wchar.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

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
