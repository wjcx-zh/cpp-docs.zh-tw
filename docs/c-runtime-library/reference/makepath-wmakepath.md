---
title: "_makepath、_wmakepath | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_makepath"
  - "_wmakepath"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-filesystem-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_wmakepath"
  - "_tmakepath"
  - "makepath"
  - "tmakepath"
  - "wmakepath"
  - "_makepath"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_makepath 函式"
  - "_tmakepath 函式"
  - "_wmakepath 函式"
  - "makepath 函式"
  - "路徑"
  - "tmakepath 函式"
  - "wmakepath 函式"
ms.assetid: 5930b197-a7b8-46eb-8519-2841a58cd026
caps.latest.revision: 22
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _makepath、_wmakepath
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從元件建立路徑名稱。  這些函式已有更安全的版本可用，請參閱 [\_makepath\_s、\_wmakepath\_s](../../c-runtime-library/reference/makepath-s-wmakepath-s.md)。  
  
## 語法  
  
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
  
#### 參數  
 `path`  
 緩衝區完整路徑。  
  
 `drive`  
 包含字母 \(A， B 等等\)，使用所需的磁碟和選擇性後面的冒號對應。  如果遺漏，則`_makepath` 在複合路徑自動插入冒號。  如果 `drive` 是 `NULL` 或指向空字串，則磁碟機代號不會出現在複合 `path` 字串。  
  
 `dir`  
 包含目錄路徑，但不包括前移指定符號或實際的檔案名稱。  斜線是選擇性的，因此，正斜線 \(\/\) 或反斜線 \(\\\) 或兩個可以用於單一 `dir` 引數。  如果斜線 \(\\或\/\) 未指定，則會自動插入它。  如果 `dir` 是 `NULL` 或指向空字串，則目錄路徑不會插入複合 `path` 字串。  
  
 `fname`  
 包含不含任何副檔名的基底檔案名稱。  如果 `fname` 是 `NULL` 或指向空字串，則 filename 不會插入在複合 `path` 字串。  
  
 `ext`  
 包含實際副檔名，不論是否有前置句號 \(.\)。  如果沒有出現於 `ext`，則`_makepath` 會自動插入句點。  如果 `ext` 是 `NULL` 或指向空字串，則副檔名不會插入在複合 `path` 字串。  
  
## 備註  
 `_makepath` 函式會從個別元件的複合路徑字串，將結果儲存在 `path`。  `path` 可包括磁碟機代號、目錄路徑、檔案名稱和副檔名。  `_wmakepath` 是 `_makepath` 的寬字元版本；`_wmakepath` 的引數是寬字元字串。  `_wmakepath` 和 `_makepath` 其餘行為相同。  
  
 **Security Note** 使用 null 結尾的字串。  若要避免緩衝區滿溢，則 null 結尾字串不能超過 `path` 緩衝區的大小。  `_makepath` 並不保證複合路徑字串的長度不超過 `_MAX_PATH`。  如需詳細資訊，請參閱 [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795) 。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|------------------------------|----------------|-------------------|  
|`_tmakepath`|`_makepath`|`_makepath`|`_wmakepath`|  
  
 `path` 引數必須指向足夠的空間緩衝區保存完整路徑。  複合 `path` 必須不大於定義在 Stdlib.h的 `_MAX_PATH` 常數。  
  
 如果路徑為 `NULL` ，則會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  此外， `errno` 設定為 `EINVAL`。  `NULL` 值允許其他參數。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_makepath`|\<stdlib.h\>|  
|`_wmakepath`|\<stdlib.h\> 或 \<wchar.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
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
  
  **路徑以 \_makepath:c:\\sample\\crt\\makepath.c 建立**  
**路徑以 \_splitpath擷取 :**  
 **磁碟機: c:**  
 **Dir: \\sample\\crt\\**  
 **檔名:makepath**  
 **Ext:.c**   
## .NET Framework 對等用法  
 [System::IO::File::Create](https://msdn.microsoft.com/en-us/library/system.io.file.create.aspx)  
  
## 請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [\_fullpath、\_wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [\_splitpath、\_wsplitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md)   
 [\_makepath\_s、\_wmakepath\_s](../../c-runtime-library/reference/makepath-s-wmakepath-s.md)