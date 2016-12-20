---
title: "_get_osfhandle | Microsoft Docs"
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
  - "_get_osfhandle"
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
  - "get_osfhandle"
  - "_get_osfhandle"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "作業系統, 取得檔案控制代碼"
  - "get_osfhandle 函式"
  - "_get_osfhandle 函式"
  - "檔案控制代碼 [C++], 作業系統"
ms.assetid: 0bdd728a-4fd8-410b-8c9f-01a121135196
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _get_osfhandle
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

以指定的檔案描述擷取相關聯的作業系統檔案處理常式。  
  
## 語法  
  
```  
intptr_t _get_osfhandle(   
   int fd   
);  
```  
  
#### 參數  
 `fd`  
 現有的檔案描述。  
  
## 傳回值  
 一個作業系統檔案處理常式，如果 `fd` 是有效的。  否則，將會呼叫無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，此函式回傳 `INVALID_HANDLE_VALUE` \(\-1\) 並設置 `errno` 為 `EBADF` ，表示無效的檔案處理常式。  
  
## 備註  
 若要關閉以 `_get_osfhandle` 開啟的檔案，請呼叫 `_close` 。  底下的處理常式也會透過呼叫 `_close` 被關閉，所以不需要呼叫 Win32 函式 `CloseHandle` 來關閉原本的處理常式。  
  
## 需求  
  
|程序|必要的標頭檔|  
|--------|------------|  
|`_get_osfhandle`|\<io.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## .NET Framework 對等用法  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需更多的資訊，請參閱 [平台調用範例 \(Platform Invoke Examples\)](../Topic/Platform%20Invoke%20Examples.md) 。  
  
## 請參閱  
 [檔案處理](../../c-runtime-library/file-handling.md)   
 [\_close](../../c-runtime-library/reference/close.md)   
 [\_creat、\_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [\_dup、\_dup2](../../c-runtime-library/reference/dup-dup2.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)