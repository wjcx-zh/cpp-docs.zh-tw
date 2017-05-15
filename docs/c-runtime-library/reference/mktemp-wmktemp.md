---
title: "_mktemp、_wmktemp | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs:
- C++
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
caps.latest.revision: 25
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 1e56ba6f238c62a220966701e7b1ced1dd2ec4ea
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="mktemp-wmktemp"></a>_mktemp、_wmktemp
建立唯一的檔案名稱。 這些函式已有更安全的版本可用，請參閱 [_mktemp_s、_wmktemp_s](../../c-runtime-library/reference/mktemp-s-wmktemp-s.md)。  
  
## <a name="syntax"></a>語法  
  
```  
char *_mktemp(  
   char *template   
);  
wchar_t *_wmktemp(  
   wchar_t *template   
);  
template <size_t size>  
char *_mktemp(  
   char (&template)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_wmktemp(  
   wchar_t (&template)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>參數  
 `template`  
 檔案名稱模式。  
  
## <a name="return-value"></a>傳回值  
 所有這些函式都會傳回已修改範本的指標。 如果 `template` 的格式不正確，或無法從指定的範本建立更多唯一的名稱，此函式會傳回 `NULL`。  
  
## <a name="remarks"></a>備註  
 `_mktemp` 函式會藉由修改 `template` 引數來建立唯一的檔案名稱。 `_mktemp` 會自動適當地處理多位元組字元字串引數，並根據執行階段系統目前使用的多位元組字碼頁來辨識多位元組字元序列。 `_wmktemp` 是 `_mktemp` 的寬字元版本，`_wmktemp` 的引數與傳回值是寬字元字串。 `_wmktemp` 和 `_mktemp` 的行為相同，只不過 `_wmktemp` 不會處理多位元組字元字串。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tmktemp`|`_mktemp`|`_mktemp`|`_wmktemp`|  
  
 `template`引數的形式`base` *XXXXXX*，其中`base`屬於您提供的新檔案名稱，而且每個 X 是所提供的字元預留位置`_mktemp`。 `template` 中的每個預留位置字元必須是大寫 X。`_mktemp` 會保留 `base`，並以字母字元取代後置 X 的第一個 X。 `_mktemp` 會以五位數值取代接著的後置 X；此值是識別呼叫處理序 (在多執行緒程式中則識別呼叫執行緒) 的唯一號碼。  
  
 每次成功呼叫 `_mktemp` 都會修改 `template`。 之後，每次使用相同的 `template` 引數從相同的處理序或執行緒呼叫時，`_mktemp` 都會檢查是否有任何檔案名稱符合先前呼叫中 `_mktemp` 所傳回的名稱。 如果指定的名稱不存在檔案，`_mktemp` 會傳回該名稱。 如果之前傳回的所有名稱都存在檔案，`_mktemp` 會以從 'a' 到 'z' 的順序中下一個可用的小寫字母，取代先前傳回的名稱中所使用的字母字元，以建立新的名稱。 例如，如果 `base` 是：  
  
```  
fn  
```  
  
 而且 `_mktemp` 所提供的五位數值為 12345，則第一個傳回的名稱會是：  
  
```  
fna12345  
```  
  
 如果此名稱會用來建立檔案 FNA12345，而且此檔案仍然存在，使用 `template` 的相同 `base` 從相同的處理序或執行緒呼叫時所傳回的下一個名稱會是：  
  
```  
fnb12345  
```  
  
 如果 FNA12345 不存在，下一個傳回的名稱仍然會是：  
  
```  
fna12345  
```  
  
 `_mktemp` 最多可為任何指定的基底和範本值組合建立 26 個唯一檔案名稱。 因此，FNZ12345 是 `_mktemp` 可為此範例中所使用的 `base` 和 `template` 值建立的最後一個唯一檔案名稱。  
  
 失敗時會設定 `errno`。 如果 `template` 的格式無效 (例如少於 6 X)，`errno` 會設定為 `EINVAL`。 如果 `_mktemp` 因所有 26 個可能的檔案名稱都存在，而無法建立唯一的名稱，`_mktemp` 會將範本設定為空字串，並傳回 `EEXIST`。  
  
 在 C++ 中，這些函式具有樣板多載，可以叫用這些函式的更新且安全的對應版本。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_mktemp`|\<io.h>|  
|`_wmktemp`|\<io.h> 或 \<wchar.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
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
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [fopen、_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [_getpid](../../c-runtime-library/reference/getpid.md)   
 [_open、_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [_tempnam、_wtempnam、tmpnam、_wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)   
 [tmpfile](../../c-runtime-library/reference/tmpfile.md)
