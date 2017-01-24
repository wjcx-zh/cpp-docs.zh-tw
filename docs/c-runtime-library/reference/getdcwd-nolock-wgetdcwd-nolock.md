---
title: "_getdcwd_nolock、_wgetdcwd_nolock | Microsoft Docs"
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
  - "_wgetdcwd_nolock"
  - "_getdcwd_nolock"
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
apitype: "DLLExport"
f1_keywords: 
  - "_wgetdcwd_nolock"
  - "tgetdcwd_nolock"
  - "wgetdcwd_nolock"
  - "_getdcwd_nolock"
  - "_tgetdcwd_nolock"
  - "getdcwd_nolock"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_getdcwd_nolock 函式"
  - "_tgetdcwd_nolock 函式"
  - "_wgetdcwd_nolock 函式"
  - "目前工作目錄"
  - "目錄 [C++], 目前工作"
  - "getdcwd_nolock 函式"
  - "tgetdcwd_nolock 函式"
  - "wgetdcwd_nolock 函式"
  - "工作目錄"
ms.assetid: d9bdf712-43f8-4173-8f9a-844e82beaa97
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _getdcwd_nolock、_wgetdcwd_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

取得目前工作目錄的完整路徑在指定磁碟上。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
char *_getdcwd_nolock(   
   int drive,  
   char *buffer,  
   int maxlen   
);  
wchar_t *_wgetdcwd_nolock(   
   int drive,  
   wchar_t *buffer,  
   int maxlen   
);  
```  
  
#### 參數  
 `drive`  
 磁碟機  
  
 `buffer`  
 路徑的儲存位置。  
  
 `maxlen`  
 路徑的最大長度 \(以字元為單位\)：`_getdcwd` 的 `_wgetdcwd`的 `char` 和 `wchar_t` 。  
  
## 傳回值  
 請參閱 [\_getdcwd、\_wgetdcwd](../../c-runtime-library/reference/getdcwd-wgetdcwd.md)。  
  
## 備註  
 `_getdcwd_nolock` 和 `_wgetdcwd_nolock` 與 `_getdcwd` 和 `_wgetdcwd`分別是相同的，但不會防止由其他執行緒的功能。  因為它們不會造成鎖定其他執行緒的額外負荷，所以可能會比較快。  這些函式只能用在安全執行緒內容 \(例如單一執行緒應用程式\) 或呼叫範圍已經處理執行緒隔離的地方。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_tgetdcwd_nolock`|`_getdcwd_nolock`|`_getdcwd_nolock`|`_wgetdcwd_nolock`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_getdcwd_nolock`|\<direct.h\>|  
|`_wgetdcwd_nolock`|\<direct.h\> 或 \<wchar.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 [System::Environment::CurrentDirectory](https://msdn.microsoft.com/en-us/library/system.environment.currentdirectory.aspx)  
  
## 請參閱  
 [目錄控制](../../c-runtime-library/directory-control.md)   
 [\_chdir、\_wchdir](../../c-runtime-library/reference/chdir-wchdir.md)   
 [\_getcwd、\_wgetcwd](../../c-runtime-library/reference/getcwd-wgetcwd.md)   
 [\_getdrive](../../c-runtime-library/reference/getdrive.md)   
 [\_mkdir、\_wmkdir](../../c-runtime-library/reference/mkdir-wmkdir.md)   
 [\_rmdir、\_wrmdir](../../c-runtime-library/reference/rmdir-wrmdir.md)