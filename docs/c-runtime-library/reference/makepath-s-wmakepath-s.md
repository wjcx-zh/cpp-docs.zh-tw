---
title: "_makepath_s、_wmakepath_s | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _wmakepath_s
- _makepath_s
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wmakepath_s
- makepath_s
- _makepath_s
- wmakepath_s
dev_langs:
- C++
helpviewer_keywords:
- _makepath_s function
- wmakepath_s function
- paths
- _wmakepath_s function
- makepath_s function
ms.assetid: 4405e43c-3d63-4697-bb80-9b8dcd21d027
caps.latest.revision: 29
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 0d3ac02a0ac8dfa7f681c8585be7e1b6f41f0f82
ms.contentlocale: zh-tw
ms.lasthandoff: 04/04/2017

---
# <a name="makepaths-wmakepaths"></a>_makepath_s、_wmakepath_s
從元件建立路徑名稱。 這些是 [_makepath、_wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md) 的版本，具有 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的安全性增強功能。  
  
## <a name="syntax"></a>語法  
  
```  
errno_t _makepath_s(  
   char *path,  
   size_t sizeInBytes,  
   const char *drive,  
   const char *dir,  
   const char *fname,  
   const char *ext   
);  
errno_t _wmakepath_s(  
   wchar_t *path,  
   size_t sizeInWords,  
   const wchar_t *drive,  
   const wchar_t *dir,  
   const wchar_t *fname,  
   const wchar_t *ext   
);  
template <size_t size>  
errno_t _makepath_s(  
   char (&path)[size],  
   const char *drive,  
   const char *dir,  
   const char *fname,  
   const char *ext   
); // C++ only  
template <size_t size>  
errno_t _wmakepath_s(  
   wchar_t (&path)[size],  
   const wchar_t *drive,  
   const wchar_t *dir,  
   const wchar_t *fname,  
   const wchar_t *ext   
); // C++ only  
```  
  
#### <a name="parameters"></a>參數  
 [輸出] `path`  
 完整路徑緩衝區。  
  
 [in] `sizeInWords`  
 以字組為單位的緩衝區大小。  
  
 [in] `sizeInBytes`  
 以位元組為單位的緩衝區大小。  
  
 [in] `drive`  
 包含對應至所需磁碟機的代號 (A、B 等) 及選擇性後置冒號。 `_makepath_s` 會在複合路徑中自動插入遺漏的冒號。 如果 `drive` 為 `NULL` 或指向空字串，複合 `path` 字串中就不會出現磁碟機代號。  
  
 [in] `dir`  
 包含目錄路徑，但不包含磁碟機指示項或實際檔案名稱。 後置斜線是選擇性的，而且可以在單一 `dir` 引數中使用正斜線 (/) 及 (或) 反斜線 (\\)。 如果未指定後置斜線 (/ 或\\)，則會自動插入。 如果 `dir` 為 `NULL` 或指向空字串，複合 `path` 字串中就不會插入目錄路徑。  
  
 [in] `fname`  
 包含基底檔案名稱，但不包含任何副檔名。 如果 `fname` 為 `NULL` 或指向空字串，複合 `path` 字串中就不會插入檔名。  
  
 [in] `ext`  
 包含實際副檔名，可包含或不含前置句號 (.)。 如果 `ext` 中沒有句號，`_makepath_s` 會自動插入句號。 如果 `ext` 為 `NULL` 或指向空字串，複合 `path` 字串中就不會插入副檔名。  
  
## <a name="return-value"></a>傳回值  
 如果成功，就是零，如果失敗，則為錯誤碼。  
  
### <a name="error-conditions"></a>錯誤狀況  
  
|`path`|`sizeInWords` / `sizeInBytes`|返回|`path` 的內容。|  
|------------|------------------------------------|------------|------------------------|  
|`NULL`|任何|`EINVAL`|未修改|  
|any|<= 0|`EINVAL`|未修改|  
  
 如果發生上述任何一種錯誤狀況，則這些函式會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，`errno` 會設定為 `EINVAL`，且函式會傳回 `EINVAL`。 參數 `drive`、`fname` 和 `ext` 可使用 `NULL`。 如需這些參數為 null 指標或空字串時之行為的資訊，請參閱＜備註＞一節。  
  
## <a name="remarks"></a>備註  
 `_makepath_s` 函式會從個別元件建立複合路徑字串，並將結果儲存在 `path` 中。 `path` 可能包含磁碟機代號、目錄路徑、檔案名稱和副檔名。 `_wmakepath_s` 是 `_makepath_s` 的寬字元版本；`_wmakepath_s` 的引數是寬字元字串。 否則，`_wmakepath_s` 和 `_makepath_s` 的行為即會相同。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tmakepath_s`|`_makepath_s`|`_makepath_s`|`_wmakepath_s`|  
  
 `path` 引數必須指向大小足以容納完整路徑的空白緩衝區。 複合 `path` 不得大於 `_MAX_PATH` 常數 (定義於 Stdlib.h 中)。  
  
 如果路徑為 `NULL`，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 此外，`errno` 會設定為 `EINVAL`。 所有其他參數都可使用 `NULL` 值。  
  
 C++ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 (因而不須指定大小引數)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。 如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
 這些函式的偵錯版本會先用 0xFD 填入緩衝區。 若要停用此行為，請使用 [_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_makepath_s`|\<stdlib.h>|  
|`_wmakepath_s`|\<stdlib.h> 或 \<wchar.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_makepath_s.c  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char path_buffer[_MAX_PATH];  
   char drive[_MAX_DRIVE];  
   char dir[_MAX_DIR];  
   char fname[_MAX_FNAME];  
   char ext[_MAX_EXT];  
   errno_t err;  
  
   err = _makepath_s( path_buffer, _MAX_PATH, "c", "\\sample\\crt\\",  
                      "crt_makepath_s", "c" );  
   if (err != 0)  
   {  
      printf("Error creating path. Error code %d.\n", err);  
      exit(1);  
   }  
   printf( "Path created with _makepath_s: %s\n\n", path_buffer );  
   err = _splitpath_s( path_buffer, drive, _MAX_DRIVE, dir, _MAX_DIR, fname,  
                       _MAX_FNAME, ext, _MAX_EXT );  
   if (err != 0)  
   {  
      printf("Error splitting the path. Error code %d.\n", err);  
      exit(1);  
   }  
   printf( "Path extracted with _splitpath_s:\n" );  
   printf( "  Drive: %s\n", drive );  
   printf( "  Dir: %s\n", dir );  
   printf( "  Filename: %s\n", fname );  
   printf( "  Ext: %s\n", ext );  
}  
```  
  
## <a name="output"></a>輸出  
  
```  
Path created with _makepath_s: c:\sample\crt\crt_makepath_s.c  
  
Path extracted with _splitpath_s:  
  Drive: c:  
  Dir: \sample\crt\  
  Filename: crt_makepath_s  
  Ext: .c  
```  
  
## <a name="see-also"></a>另請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [_fullpath、_wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [_splitpath_s、_wsplitpath_s](../../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)   
 [_makepath、_wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md)
