---
title: "_makepath、_wmakepath | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _makepath
- _wmakepath
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
- _wmakepath
- _tmakepath
- makepath
- tmakepath
- wmakepath
- _makepath
dev_langs:
- C++
helpviewer_keywords:
- _makepath function
- wmakepath function
- makepath function
- _tmakepath function
- paths
- _wmakepath function
- tmakepath function
ms.assetid: 5930b197-a7b8-46eb-8519-2841a58cd026
caps.latest.revision: 22
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: e207ec2a158bbc311ae181e71b9170cf2e48e76d
ms.lasthandoff: 02/24/2017

---
# <a name="makepath-wmakepath"></a>_makepath、_wmakepath
從元件建立路徑名稱。 這些函式已有更安全的版本可用，請參閱 [_makepath_s、_wmakepath_s](../../c-runtime-library/reference/makepath-s-wmakepath-s.md)。  
  
## <a name="syntax"></a>語法  
  
```  
void _makepath(  
   char *path,  
   const char *drive,  
   const char *dir,  
   const char *fname,  
   const char *ext   
);  
void _wmakepath(  
   wchar_t *path,  
   const wchar_t *drive,  
   const wchar_t *dir,  
   const wchar_t *fname,  
   const wchar_t *ext   
);  
```  
  
#### <a name="parameters"></a>參數  
 `path`  
 完整路徑緩衝區。  
  
 `drive`  
 包含對應至所需磁碟機的代號 (A、B 等) 及選擇性後置冒號。 `_makepath` 會在複合路徑中自動插入遺漏的冒號。 如果 `drive` 為 `NULL` 或指向空字串，複合 `path` 字串中就不會出現磁碟機代號。  
  
 `dir`  
 包含目錄路徑，但不包含磁碟機指示項或實際檔案名稱。 後置斜線是選擇性的，而且可以在單一 `dir` 引數中使用正斜線 (/) 及 (或) 反斜線 (\\)。 如果未指定後置斜線 (/ 或\\)，則會自動插入。 如果 `dir` 為 `NULL` 或指向空字串，複合 `path` 字串中就不會插入目錄路徑。  
  
 `fname`  
 包含基底檔案名稱，但不包含任何副檔名。 如果 `fname` 為 `NULL` 或指向空字串，複合 `path` 字串中就不會插入檔名。  
  
 `ext`  
 包含實際副檔名，可包含或不含前置句號 (.)。 如果 `ext` 中沒有句號，`_makepath` 會自動插入句號。 如果 `ext` 為 `NULL` 或指向空字串，複合 `path` 字串中就不會插入副檔名。  
  
## <a name="remarks"></a>備註  
 `_makepath` 函式會從個別元件建立複合路徑字串，並將結果儲存在 `path` 中。 `path` 可能包含磁碟機代號、目錄路徑、檔名和副檔名。 `_wmakepath` 是 `_makepath` 的寬字元版本；`_wmakepath` 的引數是寬字元字串。 否則，`_wmakepath` 和 `_makepath` 的行為即會相同。  
  
 **安全性提示**：使用以 Null 結束的字串。 為了避免緩衝區溢位，以 Null 結束的字串不得超過 `path` 緩衝區的大小。 `_makepath` 無法確保複合路徑字串的長度不超過 `_MAX_PATH`。 如需詳細資訊，請參閱 [Avoiding Buffer Overruns (避免緩衝區滿溢)](http://msdn.microsoft.com/library/windows/desktop/ms717795)。  
  
### <a name="generic-text-routine-mappings"></a>一般文字常式對應  
  
|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tmakepath`|`_makepath`|`_makepath`|`_wmakepath`|  
  
 `path` 引數必須指向大小足以容納完整路徑的空白緩衝區。 複合 `path` 不得大於 `_MAX_PATH` 常數 (定義於 Stdlib.h 中)。  
  
 如果路徑為 `NULL`，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 此外，`errno` 會設定為 `EINVAL`。 所有其他參數都可使用 `NULL` 值。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_makepath`|\<stdlib.h>|  
|`_wmakepath`|\<stdlib.h> 或 \<wchar.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>範例  
  
```  
// crt_makepath.c  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char path_buffer[_MAX_PATH];  
   char drive[_MAX_DRIVE];  
   char dir[_MAX_DIR];  
   char fname[_MAX_FNAME];  
   char ext[_MAX_EXT];  
  
   _makepath( path_buffer, "c", "\\sample\\crt\\", "makepath", "c" ); // C4996  
   // Note: _makepath is deprecated; consider using _makepath_s instead  
   printf( "Path created with _makepath: %s\n\n", path_buffer );  
   _splitpath( path_buffer, drive, dir, fname, ext ); // C4996  
   // Note: _splitpath is deprecated; consider using _splitpath_s instead  
   printf( "Path extracted with _splitpath:\n" );  
   printf( "  Drive: %s\n", drive );  
   printf( "  Dir: %s\n", dir );  
   printf( "  Filename: %s\n", fname );  
   printf( "  Ext: %s\n", ext );  
}  
```  
  
```Output  
Path created with _makepath: c:\sample\crt\makepath.c  
  
Path extracted with _splitpath:  
  Drive: c:  
  Dir: \sample\crt\  
  Filename: makepath  
  Ext: .c  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 [System::IO::File::Create](https://msdn.microsoft.com/en-us/library/system.io.file.create.aspx)  
  
## <a name="see-also"></a>另請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [_fullpath、_wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [_splitpath、_wsplitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md)   
 [_makepath_s、_wmakepath_s](../../c-runtime-library/reference/makepath-s-wmakepath-s.md)
