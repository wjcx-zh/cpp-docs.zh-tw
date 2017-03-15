---
title: "_getdcwd、_wgetdcwd | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_getdcwd"
  - "_wgetdcwd"
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
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "wgetdcwd"
  - "getdcwd"
  - "_getdcwd"
  - "tgetdcwd"
  - "_wgetdcwd"
  - "_tgetdcwd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "wgetdcwd 函式"
  - "工作目錄"
  - "getdcwd 函式"
  - "_getdcwd 函式"
  - "_wgetdcwd 函式"
  - "目前工作目錄"
  - "目錄 [c + +]，目前工作"
ms.assetid: 184152f5-c7b0-495b-918d-f9a6adc178bd
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# _getdcwd、_wgetdcwd
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得指定磁碟機上目前工作目錄的完整路徑。  
  
## 語法  
  
```  
char *_getdcwd(   
   int drive,  
   char *buffer,  
   int maxlen   
);  
wchar_t *_wgetdcwd(   
   int drive,  
   wchar_t *buffer,  
   int maxlen   
);  
```  
  
#### 參數  
 `drive`  
 指定磁碟機的非負整數 \(0 \= 預設磁碟機、1 \= A、2 \= B，依此類推\)。  
  
 如果指定的磁碟機無法使用，或是無法判斷磁碟機類型 \(例如抽取式、固定、CD\-ROM、RAM 磁碟或網路磁碟機\)，則會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  
  
 `buffer`  
 儲存體位置的路徑，或 **NULL**。  
  
 如果 **NULL** 指定，則此函式會配置緩衝區的最少 `maxlen` 大小使用 **malloc**, ，而傳回值的 `_getdcwd` 為配置緩衝區的指標。 呼叫 `free` 並傳遞指標給它，即可釋放此緩衝區。  
  
 `maxlen`  
 指定路徑最大長度的非零正整數 \(以字元為單位\)：`_getdcwd` 為 `char`，`_wgetdcwd` 為 `wchar_t`。  
  
 如果 `maxlen` 小於或等於零，則會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  
  
## 傳回值  
 代表指定磁碟機上目前工作目錄之完整路徑的字串指標，或 `NULL` 以表示錯誤。  
  
 如果 `buffer` 指定為 `NULL` 且記憶體不足以配置 `maxlen` 個字元，則會發生錯誤且 `errno` 會設定為 `ENOMEM`。 如果路徑長度 \(包括結束的 null 字元\) 超過 `maxlen`，則會發生錯誤且 `errno` 會設定為 `ERANGE`。 如需這些錯誤碼的詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `_getdcwd` 函式會取得指定磁碟機上目前工作目錄的完整路徑，並將其儲存在 `buffer`。 如果目前的工作目錄設定為根目錄，字串會以反斜線 \(\\\) 結尾。 如果目前的工作目錄設定為根目錄以外的目錄，字串會以目錄名稱結尾，而不是反斜線。  
  
 `_wgetdcwd` 是寬字元版的 `_getdcwd`，且其 `buffer` 參數與傳回值均為寬字元字串。 否則 `_wgetdcwd` 和 `_getdcwd` 的行為相同。  
  
 此函式是安全執行緒，即使它相依於 **GetFullPathName**, ，這是本身不具備執行緒安全。 不過，違反執行緒安全，如果多執行緒的應用程式呼叫此函式和 **GetFullPathName**。 如需詳細資訊，請移至 [MSDN Library](http://go.microsoft.com/fwlink/?LinkID=150542) ，然後搜尋 **GetFullPathName**。  
  
 這個函式具有 `_nolock` 尾碼之版本的運作方式會與這個函式完全相同，但該版不是安全執行緒，而且無法防止其他執行緒的干擾。 如需詳細資訊，請參閱 [\_getdcwd\_nolock、\_wgetdcwd\_nolock](../../c-runtime-library/reference/getdcwd-nolock-wgetdcwd-nolock.md)。  
  
 定義 `_DEBUG` 和 `_CRTDBG_MAP_ALLOC` 之後，`_getdcwd` 和 `_wgetdcwd` 的呼叫會由 `_getdcwd_dbg` 和 `_wgetdcwd_dbg` 的呼叫所取代，以便對記憶體配置進行偵錯。 如需詳細資訊，請參閱 [\_getdcwd\_dbg、\_wgetdcwd\_dbg](../../c-runtime-library/reference/getdcwd-dbg-wgetdcwd-dbg.md)。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tgetdcwd`|`_getdcwd`|`_getdcwd`|`_wgetdcwd`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_getdcwd`|\<direct.h\>|  
|`_wgetdcwd`|\<direct.h\> 或 \<wchar.h\>|  
  
 如需詳細的相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 請參閱 [\_getdrive](../../c-runtime-library/reference/getdrive.md) 中的範例。  
  
## .NET Framework 對等用法  
 [System::Environment::CurrentDirectory](https://msdn.microsoft.com/en-us/library/system.environment.currentdirectory.aspx)  
  
## 請參閱  
 [目錄控制](../../c-runtime-library/directory-control.md)   
 [\_chdir、\_wchdir](../../c-runtime-library/reference/chdir-wchdir.md)   
 [\_getcwd、\_wgetcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)   
 [\_getdrive](../../c-runtime-library/reference/getdrive.md)   
 [\_mkdir、\_wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)   
 [\_rmdir、\_wrmdir](../../c-runtime-library/reference/rmdir-wrmdir.md)