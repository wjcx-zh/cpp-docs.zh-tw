---
title: "_findnext、_findnext32、_findnext32i64、_findnext64、_findnext64i32、_findnexti64、_wfindnext、_wfindnext32、_wfindnext32i64、_wfindnext64、_wfindnext64i32、_wfindnexti64 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wfindnext"
  - "_findnext"
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
  - "findnext"
  - "_wfindnext32i64"
  - "_tfindnext64i32"
  - "findnext32"
  - "findnext32i64"
  - "wfindnext64i32"
  - "_wfindnext"
  - "tfindnext64"
  - "findnexti64"
  - "_findnexti64"
  - "_tfindnexti64"
  - "_findnext64i32"
  - "tfindnexti64"
  - "tfindnext32"
  - "_wfindnext64i32"
  - "findnext64i32"
  - "_findnext"
  - "_tfindnext32i64"
  - "_wfindnext64"
  - "wfindnext"
  - "wfindnext32"
  - "tfindnext32i64"
  - "_findnext64"
  - "_tfindnext64"
  - "_wfindnext32"
  - "findnext64"
  - "_findnext32i64"
  - "tfindnext"
  - "wfindnexti64"
  - "tfindnext64i32"
  - "_tfindnext32"
  - "wfindnext32i64"
  - "wfindnext64"
  - "_wfindnexti64"
  - "_tfindnext"
  - "_findnext32"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_wfindnexti64 函式"
  - "_tfindnext32 函式"
  - "wfindnexti64 函式"
  - "_wfindnext32i64 函式"
  - "findnext32i64 函式"
  - "tfindnext64i32 函式"
  - "_tfindnext64i32 函式"
  - "_findnext 函式"
  - "findnext64i32 函式"
  - "_tfindnext 函式"
  - "findnext32 函式"
  - "tfindnext32 函式"
  - "_findnext32 函式"
  - "_tfindnext32i64 函式"
  - "_wfindnext 函式"
  - "tfindnext 函式"
  - "_findnext64 函式"
  - "findnext64 函式"
  - "_findnext64i32 函式"
  - "wfindnext32i64 函式"
  - "findnext 函式"
  - "wfindnext32 函式"
  - "_wfindnext64i32 函式"
  - "findnexti64 函式"
  - "_wfindnext64 函式"
  - "_findnext32i64 函式"
  - "_findnexti64 函式"
  - "_tfindnext64 函式"
  - "wfindnext64i32 函式"
  - "tfindnexti64 函式"
  - "wfindnext64 函式"
  - "wfindnext 函式"
  - "tfindnext64 函式"
  - "_wfindnext32 函式"
  - "tfindnext32i64 函式"
  - "_tfindnexti64 函式"
ms.assetid: 75d97188-5add-4698-a46c-4c492378f0f8
caps.latest.revision: 17
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _findnext、_findnext32、_findnext32i64、_findnext64、_findnext64i32、_findnexti64、_wfindnext、_wfindnext32、_wfindnext32i64、_wfindnext64、_wfindnext64i32、_wfindnexti64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

尋找下一個名稱，因此若有，符合先前呼叫 `filespec` 引數傳遞至 [\_findfirst](../../c-runtime-library/reference/findfirst-functions.md)，然後修改 `fileinfo` 結構的內容。  
  
## 語法  
  
```  
int _findnext(  
   intptr_t handle,  
   struct _finddata_t *fileinfo   
);  
int _findnext32(  
   intptr_t handle,  
   struct _finddata32_t *fileinfo   
);  
int _findnext64(  
   intptr_t handle,  
   struct __finddata64_t *fileinfo   
);  
int _findnexti64(  
   intptr_t handle,  
   struct __finddatai64_t *fileinfo   
);  
int _findnext32i64(  
   intptr_t handle,  
   struct _finddata32i64_t *fileinfo   
);  
int _findnext64i32(  
   intptr_t handle,  
   struct _finddata64i32_t *fileinfo   
);  
int _wfindnext(  
   intptr_t handle,  
   struct _wfinddata_t *fileinfo   
);  
int _wfindnext32(  
   intptr_t handle,  
   struct _wfinddata32_t *fileinfo   
);  
int _wfindnext64(  
   intptr_t handle,  
   struct _wfinddata64_t *fileinfo   
);  
int _wfindnexti64(  
   intptr_t handle,  
   struct _wfinddatai64_t *fileinfo   
);  
int _wfindnext32i64(  
   intptr_t handle,  
   struct _wfinddatai64_t *fileinfo   
);  
int _wfindnext64i32(  
   intptr_t handle,  
   struct _wfinddata64i32_t *fileinfo   
);  
```  
  
#### 參數  
 `handle`  
 搜尋上一個呼叫傳回的 `_findfirst`的控制代碼。  
  
 `fileinfo`  
 檔案資訊的緩衝區。  
  
## 傳回值  
 如果成功則傳回 0。  否則，會傳回– 1 並將表示失敗的內建值設為 `errno` 。  可能的錯誤碼下表中所示。  
  
 `EINVAL`  
 無效的參數: `fileinfo` 是 `NULL` 。  或者，作業系統傳回未預期的錯誤。  
  
 `ENOENT`  
 找不到任何相符的檔案。  
  
 `ENOMEM`  
 沒有足夠的記憶體或檔案名稱的長度超過了 `MAX_PATH`。  
  
 如果傳入無效的參數，這些函式會呼叫無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 所述。  
  
## 備註  
 您必須呼叫 [\_findclose](../../c-runtime-library/reference/findclose.md) ，在完成使用 `_findfirst` 或 `_findnext` 函式後 \(或任何變數\)。  這個釋放您的應用程式中被這些函式所使用的資源。  
  
 具有 `w` 前置詞這些函式的變化是寬字元版本;否則，它們與對應的單一位元組函式是相同的。  
  
 這些函式的變形支援 32 位元或 64 位元的時間型別與 32 位元或 64 位元的檔案大小。  第一個數字後綴 \(`32` 或 `64`\) 表示使用的時間型別的大小，第二個後綴是 `i32` 或 `i64` ，表示檔案大小為 32 位元或 64 位元的整數。  如需的相關資訊版本支援 32 位元和 64 位元時間類型和檔案大小，請參閱下表。  使用一個 64 位元時間型別的變化允許檔案建立日期透過 23:59:59， 3000 年 12 月 31 日 UTC 來表示;而使用 32 位元時間型別傳遞只代表日期 19:14: 07，2038 年 1 月 18 日 UTC。  1970 年 1 月 1 日的午夜是這些函式的時間日期範圍的下界。  
  
 除非您有特殊原因需要使用明確指定時間大小的版本，請使用 `_findnext` 或 `_wfindnext` ，或者，如果您需要支援檔案大小大於 3 GB，使用 `_findnexti64` 或 `_wfindnexti64`。  這些函式會使用 64 位時間型別。  在舊版中，這些函式使用 32 位時間型別。  如果這是應用程式的重大變更，您可能會定義 `_USE_32BIT_TIME_T` 還原成舊版行為。  如果 `_USE_32BIT_TIME_T` 已定義， `_findnext`、 `_finnexti64`和其對應的 Unicode 版本會使用 32 位時間。  
  
### \_findnext 不同的時間型別和檔案長度型別  
  
|函式|`_USE_32BIT_TIME_T` 已定義?|時間型別|檔案長度型別|  
|--------|------------------------------|----------|------------|  
|`_findnext`, `_wfindnext`|未定義 \_MBCS|64 位元|32 位元|  
|`_findnext`, `_wfindnext`|已定義|32 位元|32 位元|  
|`_findnext32`, `_wfindnext32`|不受巨集定義影響|32 位元|32 位元|  
|`_findnext64`, `_wfindnext64`|不受巨集定義影響|64 位元|64 位元|  
|`_findnexti64`, `_wfindnexti64`|未定義 \_MBCS|64 位元|64 位元|  
|`_findnexti64`, `_wfindnexti64`|已定義|32 位元|64 位元|  
|`_findnext32i64`, `_wfindnext32i64`|不受巨集定義影響|32 位元|64 位元|  
|`_findnext64i32`, `_wfindnext64i32`|不受巨集定義影響|64 位元|32 位元|  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|------------------------------|----------------|-------------------|  
|`_tfindnext`|`_findnext`|`_findnext`|`_wfindnext`|  
|`_tfindnext32`|`_findnext32`|`_findnext32`|`_wfindnext32`|  
|`_tfindnext64`|`_findnext64`|`_findnext64`|`_wfindnext64`|  
|`_tfindnexti64`|`_findnexti64`|`_findnexti64`|`_wfindnexti64`|  
|`_tfindnext32i64`|`_findnext32i64`|`_findnext32i64`|`_wfindnext32i64`|  
|`_tfindnext64i32`|`_findnext64i32`|`_findnext64i32`|`_wfindnext64i32`|  
  
## 需求  
  
|功能|必要的標頭|  
|--------|-----------|  
|`_findnext`|\<io.h\>|  
|`_findnext32`|\<io.h\>|  
|`_findnext64`|\<io.h\>|  
|`_findnexti64`|\<io.h\>|  
|`_findnext32i64`|\<io.h\>|  
|`_findnext64i32`|\<io.h\>|  
|`_wfindnext`|\<io.h\> or \<wchar.h\>|  
|`_wfindnext32`|\<io.h\> or \<wchar.h\>|  
|`_wfindnext64`|\<io.h\> or \<wchar.h\>|  
|`_wfindnexti64`|\<io.h\> or \<wchar.h\>|  
|`_wfindnext32i64`|\<io.h\> or \<wchar.h\>|  
|`_wfindnext64i32`|\<io.h\> or \<wchar.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [系統呼叫](../../c-runtime-library/system-calls.md)   
 [檔案名稱搜尋函式](../../c-runtime-library/filename-search-functions.md)