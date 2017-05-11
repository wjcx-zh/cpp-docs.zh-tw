---
title: "_mktemp_s、_wmktemp_s | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
apitype: DLLExport
f1_keywords:
- wmktemp_s
- mktemp_s
- _mktemp_s
- _wmktemp_s
dev_langs:
- C++
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
caps.latest.revision: 23
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
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 6231031dd0bbc5b455e3555731f711ee7de971e7
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="mktemps-wmktemps"></a>_mktemp_s、_wmktemp_s
建立唯一的檔案名稱。 這些是 [_mktemp、_wmktemp](../../c-runtime-library/reference/mktemp-wmktemp.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。  
  
## <a name="syntax"></a>語法  
  
```  
errno_t _mktemp_s(  
   char *template,  
   size_t sizeInChars  
);  
errno_t _wmktemp_s(  
   wchar_t *template,  
   size_t sizeInChars  
);  
template <size_t size>  
errno_t _mktemp_s(  
   char (&template)[size]  
); // C++ only  
template <size_t size>  
errno_t _wmktemp_s(  
   wchar_t (&template)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>參數  
 `template`  
 檔案名稱模式。  
  
 `sizeInChars`  
 緩衝區的大小 (以 `_mktemp_s` 中的單一位元組字元數或 `_wmktemp_s` 中的寬字元數為單位)，包括 Null 結束字元。  
  
## <a name="return-value"></a>傳回值  
 如果成功，這兩個函式會傳回零；如果失敗，則傳回錯誤碼。  
  
### <a name="error-conditions"></a>錯誤狀況  
  
|`template`|`sizeInChars`|**傳回值**|**範本中的新值**|  
|----------------|-------------------|----------------------|-------------------------------|  
|`NULL`|任何|`EINVAL`|`NULL`|  
|格式不正確 (如需正確的格式，請參閱＜`Remarks`＞一節)|任何|`EINVAL`|空字串|  
|any|<= X 的數目|`EINVAL`|空字串|  
  
 如果發生上述任何一種錯誤狀況，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，`errno` 會設定為 `EINVAL`，且函式會傳回 `EINVAL`。  
  
## <a name="remarks"></a>備註  
 `_mktemp_s` 函式會藉由修改 `template` 引數來建立唯一的檔案名稱，因此在呼叫後，`template` 指標會指向包含新檔案名稱的字串。 `_mktemp_s` 會自動適當地處理多位元組字元字串引數，並根據執行階段系統目前使用的多位元組字碼頁來辨識多位元組字元序列。 `_wmktemp_s` 是 `_mktemp_s` 的寬字元版本；`_wmktemp_s` 的引數是寬字元字串。 `_wmktemp_s` 和 `_mktemp_s` 的行為相同，只不過 `_wmktemp_s` 不會處理多位元組字元字串。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tmktemp_s`|`_mktemp_s`|`_mktemp_s`|`_wmktemp_s`|  
  
 `template` 引數的格式為 `baseXXXXXX`，其中 `base` 是您所提供之新檔案名稱的一部分，而每個 X 是 `_mktemp_s` 所提供的字元預留位置。 `template` 中的每個預留位置字元必須是大寫 X。`_mktemp_s` 會保留 `base`，並以字母字元取代後置 X 的第一個 X。 `_mktemp_s` 會以五位數值取代接著的後置 X；此值是識別呼叫處理序 (在多執行緒程式中則識別呼叫執行緒) 的唯一號碼。  
  
 每次成功呼叫 `_mktemp_s` 都會修改 `template`。 之後，每次使用相同的 `template` 引數從相同的處理序或執行緒呼叫時，`_mktemp_s` 都會檢查是否有任何檔案名稱符合先前呼叫中 `_mktemp_s` 所傳回的名稱。 如果指定的名稱不存在檔案，`_mktemp_s` 會傳回該名稱。 如果之前傳回的所有名稱都存在檔案，`_mktemp_s` 會以從 'a' 到 'z' 的順序中下一個可用的小寫字母，取代先前傳回的名稱中所使用的字母字元，以建立新的名稱。 例如，如果 `base` 是：  
  
```  
fn  
```  
  
 而且 `_mktemp_s` 所提供的五位數值為 12345，則第一個傳回的名稱會是：  
  
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
  
 `_mktemp_s` 最多可為任何指定的基底和範本值組合建立 26 個唯一檔案名稱。 因此，FNZ12345 是 `_mktemp_s` 可為此範例中所使用的 `base` 和 `template` 值建立的最後一個唯一檔案名稱。  
  
 C++ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_mktemp_s`|\<io.h>|  
|`_wmktemp_s`|\<io.h> 或 \<wchar.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
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
  
## <a name="sample-output"></a>範例輸出  
  
```  
Unique filename is fna03188  
Unique filename is fnb03188  
Unique filename is fnc03188  
Unique filename is fnd03188  
Unique filename is fne03188  
```  
  
## <a name="see-also"></a>另請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [fopen、_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [_getpid](../../c-runtime-library/reference/getpid.md)   
 [_open、_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [_tempnam、_wtempnam、tmpnam、_wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)   
 [tmpfile_s](../../c-runtime-library/reference/tmpfile-s.md)
