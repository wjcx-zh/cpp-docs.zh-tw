---
title: "_splitpath_s、_wsplitpath_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wsplitpath_s"
  - "_splitpath_s"
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
  - "_wsplitpath_s"
  - "splitpath_s"
  - "_splitpath_s"
  - "wsplitpath_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_splitpath_s 函式"
  - "_wsplitpath_s 函式"
  - "路徑名稱"
  - "路徑名稱"
  - "splitpath_s 函式"
  - "wsplitpath_s 函式"
ms.assetid: 30fff3e2-cd00-4eb6-b5a2-65db79cb688b
caps.latest.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 29
---
# _splitpath_s、_wsplitpath_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

分解路徑名稱至元件。  這些是 [\_splitpath, \_wsplitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md) 的安全性增強版本，如[CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## 語法  
  
```  
errno_t _splitpath_s(  
   const char * path,  
   char * drive,  
   size_t driveNumberOfElements,  
   char * dir,  
   size_t dirNumberOfElements,  
   char * fname,  
   size_t nameNumberOfElements,  
   char * ext,   
   size_t extNumberOfElements  
);  
errno_t _wsplitpath_s(  
   const wchar_t * path,  
   wchar_t * drive,  
   size_t driveNumberOfElements,  
   wchar_t *dir,  
   size_t dirNumberOfElements,  
   wchar_t * fname,  
   size_t nameNumberOfElements,  
   wchar_t * ext,  
   size_t extNumberOfElements  
);  
template <size_t drivesize, size_t dirsize, size_t fnamesize, size_t extsize>  
errno_t _splitpath_s(  
   const char *path,  
   char (&drive)[drivesize],  
   char (&dir)[dirsize],  
   char (&fname)[fnamesize],  
   char (&ext)[extsize]  
); // C++ only  
template <size_t drivesize, size_t dirsize, size_t fnamesize, size_t extsize>  
errno_t _wsplitpath_s(  
   const wchar_t *path,  
   wchar_t (&drive)[drivesize],  
   wchar_t (&dir)[dirsize],  
   wchar_t (&fname)[fnamesize],  
   wchar_t (&ext)[extsize]  
); // C++ only  
```  
  
#### 參數  
 \[in\] `path`  
 完整路徑。  
  
 \[out\] `drive`  
 磁碟機代號，後面加上冒號 \(`:`\)。  如果不需要磁碟機代號，您可傳遞 `NULL` 作為這個參數。  
  
 \[in\] `driveNumberOfElements`  
 `drive` 緩衝區的大小 \(單一位元組字元或寬字元\)。  如果 `drive` 是 `NULL`，這個值必須是 0。  
  
 \[out\] `dir`  
 目錄路徑，包括斜線。  可以使用斜線 \( `/` \)，反斜線 \( `\` \)，或兩者。  如果不需要磁碟機代號，您可傳遞 `NULL` 作為這個參數。  
  
 \[in\] `dirNumberOfElements`  
 `dir` 緩衝區的大小 \(單一位元組字元或寬字元\)。  如果 `dir` 是 `NULL`，這個值必須是 0。  
  
 \[out\] `fname`  
 基底檔名 \(沒有副檔名\)。  如果不需要檔名，您可傳遞 `NULL` 作為這個參數。  
  
 \[in\] `nameNumberOfElements`  
 `fname` 緩衝區的大小 \(單一位元組字元或寬字元\)。  如果 `fname` 是 `NULL`，這個值必須是 0。  
  
 \[out\] `ext`  
 副檔名，包括前置句號 \(**.**\)。如果不需要副檔名，您可傳遞 `NULL` 作為這個參數。  
  
 \[in\] `extNumberOfElements`  
 `ext` 緩衝區的大小 \(單一位元組字元或寬字元\)。  如果 `ext` 是 `NULL`，這個值必須是 0。  
  
## 傳回值  
 如果成功，就是零，如果失敗，則為錯誤碼。  
  
### 錯誤狀況  
  
|條件|傳回值|  
|--------|---------|  
|`path` 為  `NULL`|`EINVAL`|  
|`drive` 是 `NULL`， `driveNumberOfElements` 為非零|`EINVAL`|  
|`drive` 是非 `NULL`， `driveNumberOfElements` 為零|`EINVAL`|  
|`dir` 是 `NULL`， `dirNumberOfElements` 為非零|`EINVAL`|  
|`dir` 是非 `NULL`， `dirNumberOfElements` 為零|`EINVAL`|  
|`fname` 是 `NULL`， `nameNumberOfElements` 為非零|`EINVAL`|  
|`fname` 是非 `NULL`， `nameNumberOfElements` 為零|`EINVAL`|  
|`ext` 是 `NULL`， `extNumberOfElements` 為非零|`EINVAL`|  
|`ext` 是非 `NULL`， `extNumberOfElements` 為零|`EINVAL`|  
  
 如果以上任何一個錯誤情況發生，無效的參數叫用處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這些函式會將 `errno` 設定為 `EINVAL` 並傳回 `EINVAL`。  
  
 如果任何緩衝區太小而無法保存這個結果，這些函式清除所有緩衝區初始化為空字串，將 `errno` 設為 `ERANGE`並傳回 `ERANGE`。  
  
## 備註  
 `_splitpath_s`  函式將路徑分給它的四個元件。  `_splitpath_s` 適時地自動處理多位元組字元的字串參數，根據目前使用的多位元組字碼頁來辨認多位元組字元序列。  `_wsplitpath_s`  是 `_splitpath_s` 的寬字元版本；`_``wsplitpath_s` ``  的引數是寬字元字串。  這些函式其餘部分的運作相同。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE & \_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tsplitpath_s`|`_splitpath_s`|`_splitpath_s`|`_wsplitpath_s`|  
  
 完整路徑的每個元件都在不同的緩衝區儲存；資訊清單常數 `_MAX_DRIVE`、 `_MAX_DIR`、 `_MAX_FNAME`和 `_MAX_EXT` \(定義於 STDLIB.H\) 為每個檔案組件中指定可允許的最大大小。  檔案組件大於對應的資訊清單常數會造成堆積損毀。  
  
 下表列出清單常數的值。  
  
|名稱|值|  
|--------|-------|  
|\_MAX\_DRIVE|3|  
|\_MAX\_DIR|256|  
|\_MAX\_FNAME|256|  
|\_MAX\_EXT|256|  
  
 如果完整路徑不含元件 \(例如檔名\)，`_splitpath_s` 將空字串指派給對應的緩衝區。  
  
 在 C\+\+ 中，這些函式的使用被簡化為使用樣板多載；使用多載可以自動推斷緩衝區的大小而不必在參數中指明大小。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
 這些函式的偵錯版本會先用 0xFD 填入緩衝區。  若要停用此行為，請使用 [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_splitpath_s`|\<stdlib.h\>|  
|`_wsplitpath_s`|\<stdlib.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 請參閱[\_makepath\_s、\_wmakepath\_s](../../c-runtime-library/reference/makepath-s-wmakepath-s.md)中的範例。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [\_splitpath、\_wsplitpath](../../c-runtime-library/reference/splitpath-wsplitpath.md)   
 [\_fullpath、\_wfullpath](../../c-runtime-library/reference/fullpath-wfullpath.md)   
 [\_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [\_makepath、\_wmakepath](../../c-runtime-library/reference/makepath-wmakepath.md)   
 [\_setmbcp](../../c-runtime-library/reference/setmbcp.md)