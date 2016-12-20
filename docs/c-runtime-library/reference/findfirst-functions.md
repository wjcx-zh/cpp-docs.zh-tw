---
title: "_findfirst、_findfirst32、_findfirst32i64、_findfirst64、_findfirst64i32、_findfirsti64、_wfindfirst、_wfindfirst32、_wfindfirst32i64、_wfindfirst64、_wfindfirst64i32、_wfindfirsti64 | Microsoft Docs"
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
  - "_findfirst"
  - "_wfindfirst"
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
  - "findfirst32i64"
  - "wfindfirst32i64"
  - "tfindfirst64"
  - "_findfirst64i32"
  - "_wfindfirst32i64"
  - "_wfindfirsti64"
  - "wfindfirst"
  - "_tfindfirsti64"
  - "findfirst32"
  - "_tfindfirst32"
  - "_findfirsti64"
  - "findfirst"
  - "wfindfirst64"
  - "wfindfirst32"
  - "tfindfirst32"
  - "_wfindfirst64i32"
  - "findfirst64i32"
  - "tfindfirst64i32"
  - "_wfindfirst"
  - "findfirsti64"
  - "_findfirst32i64"
  - "wfindfirst64i32"
  - "_wfindfirst32"
  - "_findfirst32"
  - "_tfindfirst32i64"
  - "tfindfirst"
  - "_tfindfirst64i32"
  - "findfirst64"
  - "_tfindfirst"
  - "_findfirst64"
  - "_tfindfirst64"
  - "tfindfirst32i64"
  - "_findfirst"
  - "_wfindfirst64"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_tfindfirst64 函式"
  - "_wfindfirst64i32 函式"
  - "_wfindfirst32i64 函式"
  - "wfindfirst32 函式"
  - "_findfirst 函式"
  - "wfindfirst64 函式"
  - "_wfindfirst 函式"
  - "_findfirst64i32 函式"
  - "wfindfirst 函式"
  - "_findfirst64 函式"
  - "tfindfirst32 函式"
  - "_tfindfirst64i32 函式"
  - "findfirst 函式"
  - "findfirst32i64 函式"
  - "tfindfirst64 函式"
  - "_tfindfirst32 函式"
  - "tfindfirst32i64 函式"
  - "tfindfirst64i32 函式"
  - "_wfindfirsti64 函式"
  - "_findfirst32i64 函式"
  - "findfirst32 函式"
  - "findfirsti64 函式"
  - "findfirst64i32 函式"
  - "tfindfirsti64 函式"
  - "tfindfirst 函式"
  - "_wfindfirst32 函式"
  - "wfindfirsti64 函式"
  - "_tfindfirsti64 函式"
  - "_tfindfirst 函式"
  - "_tfindfirst32i64 函式"
  - "findfirst64 函式"
  - "_findfirst32 函式"
  - "_findfirsti64 函式"
  - "wfindfirst32i64 函式"
  - "wfindfirst64i32 函式"
  - "_wfindfirst64 函式"
ms.assetid: 9bb46d1a-b946-47de-845a-a0b109a33ead
caps.latest.revision: 25
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _findfirst、_findfirst32、_findfirst32i64、_findfirst64、_findfirst64i32、_findfirsti64、_wfindfirst、_wfindfirst32、_wfindfirst32i64、_wfindfirst64、_wfindfirst64i32、_wfindfirsti64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供與`filespec`引數所指定的檔案名稱相符的第一個執行個體的相關資訊。  
  
## 語法  
  
```  
intptr_t _findfirst(  
   const char *filespec,  
   struct _finddata_t *fileinfo   
);  
intptr_t _findfirst32(  
   const char *filespec,  
   struct _finddata32_t *fileinfo   
);  
intptr_t _findfirst64(  
   const char *filespec,  
   struct _finddata64_t *fileinfo   
);  
intptr_t _findfirsti64(  
   const char *filespec,  
   struct _finddatai64_t *fileinfo   
);  
intptr_t _findfirst32i64(  
   const char *filespec,  
   struct _finddata32i64_t *fileinfo   
);  
intptr_t _findfirst64i32(  
   const char *filespec,  
   struct _finddata64i32_t *fileinfo   
);  
intptr_t _wfindfirst(  
   const wchar_t *filespec,  
   struct _wfinddata_t *fileinfo   
);  
intptr_t _wfindfirst32(  
   const wchar_t *filespec,  
   struct _wfinddata32_t *fileinfo   
);  
intptr_t _wfindfirst64(  
   const wchar_t *filespec,  
   struct _wfinddata64_t *fileinfo   
);  
intptr_t _wfindfirsti64(  
   const wchar_t *filespec,  
   struct _wfinddatai64_t *fileinfo   
);  
intptr_t _wfindfirst32i64(  
   const wchar_t *filespec,  
   struct _wfinddata32i64_t *fileinfo   
);  
intptr_t _wfindfirst64i32(  
   const wchar_t *filespec,  
   struct _wfinddata64i32_t *fileinfo   
);  
```  
  
#### 參數  
 `filespec`  
 目標檔案規格 \(可以包括萬用字元 \(Wildcard Character\)。  
  
 `fileinfo`  
 檔案資訊的緩衝區。  
  
## 傳回值  
 如果成功，則 `_findfirst` 會傳回識別符合 `filespec` 規格，可用於後續呼叫對 [\_findnext](../../c-runtime-library/reference/findnext-functions.md) 或對 `_findclose`檔案或群組的唯一搜尋控制代碼。  否則， `_findfirst` 會傳回– 1 並將 `errno` 設定為下列其中一個值。  
  
 `EINVAL`  
 無效的參數: `filespec` 或 `fileinfo` 是 `NULL`。  或者，作業系統傳回未預期的錯誤。  
  
 `ENOENT`  
 無法符合檔案規格。  
  
 `ENOMEM`  
 記憶體不足。  
  
 `EINVAL`  
 無效的檔名規格或指定的檔案名稱大於 `MAX_PATH`。  
  
 如需更多關於這些和其他回傳碼的資訊，請參閱 [\_doserrno 、 errno 、 \_sys\_errlist 、和 \_sys\_nerr \(\_doserrno, errno, \_sys\_errlist, and \_sys\_nerr\)](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 。  
  
 如果傳入無效的參數，這些函式會呼叫無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 所述。  
  
## 備註  
 您必須呼叫 [\_findclose](../../c-runtime-library/reference/findclose.md) ，在完成與 `_findfirst` 或 `_findnext` 函式後 \(或任何變數\)。  這個釋放這些函式所使用的資源在您的應用程式。  
  
 具有 `w` 前置詞這些函式的變化是寬字元版本;否則，它們與對應的單一位元組函式是相同的。  
  
 這些函式的變形支援 32 位元或 64 位元的時間型別與 32 位元或 64 位元的檔案大小。  第一個數字後綴 \(`32` 或 `64`\) 表示使用的時間型別的大小，第二個後綴是 `i32` 或 `i64` ，表示檔案大小為 32 位元或 64 位元的整數。  如需的相關資訊版本支援 32 位元和 64 位元時間類型和檔案大小，請參閱下表。  `i32` 或 `i64` 結尾省略，則與時間型別的大小，因此， `_findfirst64` 也支援 64 位元檔案長度，且 `_findfirst32` 只支援 32 位元檔案長度。  
  
 這些函式的 `fileinfo` 參數使用各種 `_finddata_t` 結構。  如需 更多類別的詳細資訊，請參閱 [檔案名稱搜尋函式](../../c-runtime-library/filename-search-functions.md)。  
  
 使用一個 64 位元時間型別的變數可讓檔案建立日期透過 23:59 來表示: 59， 3000 年 12 月 31 日， UTC。  使用 32 位元時間型別的那些透過 19:14 只代表日期: 07 年 1 月 18 日 2038， UTC。  1970 年 1 月 1 日的午夜是這些函式的時間日期範圍的下界。  
  
 除非您有特殊原因需要使用明確指定時間大小的版本，請使用 `_findfirst` 或 `_wfindfirst` ，或者，如果您需要支援檔案大小大於 3 GB，使用 `_findfirsti64` 或 `_wfindfirsti64`。  這些函式會使用 64 位時間型別。  在舊版中，這些函式使用 32 位時間型別。  如果這是應用程式的重大變更，您可能會定義 `_USE_32BIT_TIME_T` 還原成舊版行為。  如果 `_USE_32BIT_TIME_T` 已定義， `_findfirst`、 `_finfirsti64`和其對應的 Unicode 版本會使用 32 位時間。  
  
### \_findfirst 不同的時間型別和檔案長度型別  
  
|函式|`_USE_32BIT_TIME_T` 已定義?|時間型別|檔案長度型別|  
|--------|------------------------------|----------|------------|  
|`_findfirst`, `_wfindfirst`|未定義 \_MBCS|64 位元|32 位元|  
|`_findfirst`, `_wfindfirst`|已定義|32 位元|32 位元|  
|`_findfirst32`, `_wfindfirst32`|不受巨集定義影響|32 位元|32 位元|  
|`_findfirst64`, `_wfindfirst64`|不受巨集定義影響|64 位元|64 位元|  
|`_findfirsti64`, `_wfindfirsti64`|未定義 \_MBCS|64 位元|64 位元|  
|`_findfirsti64`, `_wfindfirsti64`|已定義|32 位元|64 位元|  
|`_findfirst32i64`, `_wfindfirst32i64`|不受巨集定義影響|32 位元|64 位元|  
|`_findfirst64i32`, `_wfindfirst64i32`|不受巨集定義影響|64 位元|32 位元|  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|------------------------------|----------------|-------------------|  
|`_tfindfirst`|`_findfirst`|`_findfirst`|`_wfindfirst`|  
|`_tfindfirst32`|`_findfirst32`|`_findfirst32`|`_wfindfirst32`|  
|`_tfindfirst64`|`_findfirst64`|`_findfirst64`|`_wfindfirst64`|  
|`_tfindfirsti64`|`_findfirsti64`|`_findfirsti64`|`_wfindfirsti64`|  
|`_tfindfirst32i64`|`_findfirst32i64`|`_findfirst32i64`|`_wfindfirst32i64`|  
|`_tfindfirst64i32`|`_findfirst64i32`|`_findfirst64i32`|`_wfindfirst64i32`|  
  
## 需求  
  
|功能|必要的標頭|  
|--------|-----------|  
|`_findfirst`|\<io.h\>|  
|`_findfirst32`|\<io.h\>|  
|`_findfirst64`|\<io.h\>|  
|`_findfirsti64`|\<io.h\>|  
|`_findfirst32i64`|\<io.h\>|  
|`_findfirst64i32`|\<io.h\>|  
|`_wfindfirst`|\<io.h\> or \<wchar.h\>|  
|`_wfindfirst32`|\<io.h\> or \<wchar.h\>|  
|`_wfindfirst64`|\<io.h\> or \<wchar.h\>|  
|`_wfindfirsti64`|\<io.h\> or \<wchar.h\>|  
|`_wfindfirst32i64`|\<io.h\> or \<wchar.h\>|  
|`_wfindfirst64i32`|\<io.h\> or \<wchar.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## .NET Framework 對等用法  
 [System::IO::DirectoryInfo::GetFiles](https://msdn.microsoft.com/en-us/library/system.io.directoryinfo.getfiles.aspx)  
  
## 請參閱  
 [系統呼叫](../../c-runtime-library/system-calls.md)   
 [檔案名稱搜尋函式](../../c-runtime-library/filename-search-functions.md)