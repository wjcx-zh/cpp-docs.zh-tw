---
title: "_makepath_s、_wmakepath_s | Microsoft Docs"
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
  - "_wmakepath_s"
  - "_makepath_s"
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
  - "_wmakepath_s"
  - "makepath_s"
  - "_makepath_s"
  - "wmakepath_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_makepath_s 函式"
  - "wmakepath_s 函式"
  - "路徑"
  - "_wmakepath_s 函式"
  - "makepath_s 函式"
ms.assetid: 4405e43c-3d63-4697-bb80-9b8dcd21d027
caps.latest.revision: 29
caps.handback.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _makepath_s、_wmakepath_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從元件建立路徑名稱。  這些是[CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述的[\_makepath, \_wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md) 的安全性增強版本。  
  
## 語法  
  
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
  
#### 參數  
 \[out\] `path`  
 緩衝區完整路徑。  
  
 \[in\] `sizeInWords`  
 緩衝區以字元計算的大小。  
  
 \[in\] `sizeInBytes`  
 緩衝區的大小 \(以位元組為單位\)。  
  
 \[in\] `drive`  
 包含字母 \(A， B 等等\)，使用所需的磁碟和選擇性後面的冒號對應。  如果遺漏，則`_makepath_s` 在複合路徑自動插入冒號。  如果 `drive` 是 `NULL` 或指向空字串，則磁碟機代號不會出現在複合 `path` 字串。  
  
 \[in\] `dir`  
 包含目錄路徑，但不包括前移指定符號或實際的檔案名稱。  斜線是選擇性的，因此，正斜線 \(\/\) 或反斜線 \(\\\) 或兩個可以用於單一 `dir` 引數。  如果斜線 \(\\或\/\) 未指定，則會自動插入它。  如果 `dir` 是 `NULL` 或指向空字串，則目錄路徑不會插入複合 `path` 字串。  
  
 \[in\] `fname`  
 包含不含任何副檔名的基底檔案名稱。  如果 `fname` 是 `NULL` 或指向空字串，則 filename 不會插入在複合 `path` 字串。  
  
 \[in\] `ext`  
 包含實際副檔名，不論是否有前置句號 \(.\)。  如果沒有出現於 `ext`，則`_makepath_s` 會自動插入句點。  如果 `ext` 是 `NULL` 或指向空字串，則副檔名不會插入在複合 `path` 字串。  
  
## 傳回值  
 如果成功，就是零，如果失敗，則為錯誤碼。  
  
### 錯誤狀況  
  
|`path`|`sizeInWords` \/ `sizeInBytes`|傳回|`path` 的內容|  
|------------|------------------------------------|--------|----------------|  
|`NULL`|any|`EINVAL`|未修改|  
|any|\<\= 0|`EINVAL`|未修改|  
  
 如果任何上述錯誤狀況發生，這些函式叫用無效的參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果執行允許繼續，則 `errno` 設定為`EINVAL`，而且函式傳回`EINVAL`**.** `NULL` 允許`drive`、 `fname`和 `ext`參數。  如需行為的資訊，而這些參數是 NULL 指標或空字串時，請參閱 \< 備註 \> 一節。  
  
## 備註  
 `_makepath_s` 函式會從個別元件的複合路徑字串，將結果儲存在 `path`。  `path` 可包括磁碟機代號、目錄路徑、檔案名稱和副檔名。  `_wmakepath_s` 是 `_makepath_s` 的寬字元版本；`_wmakepath_s` 的引數是寬字元字串。  `_wmakepath_s` 和 `_makepath_s` 其餘行為相同。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|------------------------------|----------------|-------------------|  
|`_tmakepath_s`|`_makepath_s`|`_makepath_s`|`_wmakepath_s`|  
  
 `path` 引數必須指向足夠的空間緩衝區保存完整路徑。  複合 `path` 必須不大於定義在 Stdlib.h的 `_MAX_PATH` 常數。  
  
 如果路徑為 `NULL` ，則會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  此外， `errno` 設定為 `EINVAL`。  `NULL` 值允許其他參數。  
  
 C\+\+ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 \(因而不須指定大小引數\)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
 這些函式的偵錯版本會先用 0xFD 填入緩衝區。  若要停用此行為，請使用 [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_makepath_s`|\<stdlib.h\>|  
|`_wmakepath_s`|\<stdlib.h\> 或 \<wchar.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 範例  
  
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
  
## Output  
  
```  
Path created with _makepath_s: c:\sample\crt\crt_makepath_s.c  
  
Path extracted with _splitpath_s:  
  Drive: c:  
  Dir: \sample\crt\  
  Filename: crt_makepath_s  
  Ext: .c  
```  
  
## .NET Framework 對等用法  
 [System::IO::File::Create](https://msdn.microsoft.com/en-us/library/system.io.file.create.aspx)  
  
## 請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [\_fullpath、\_wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [\_splitpath\_s、\_wsplitpath\_s](../../c-runtime-library/reference/splitpath-s-wsplitpath-s.md)   
 [\_makepath、\_wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md)