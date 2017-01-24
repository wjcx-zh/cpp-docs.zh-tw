---
title: "_pclose | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_pclose"
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
  - "_pclose"
  - "pclose"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_pclose 函式"
  - "pclose 函式"
  - "管道, 關閉"
ms.assetid: e2e31a9e-ba3a-4124-bcbb-c4040110b3d3
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _pclose
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

等候新的命令處理器並關閉關聯的管道的資料流。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
  
      int _pclose(  
FILE *stream   
);  
```  
  
#### 參數  
 `stream`  
 將之前呼叫時的傳回值傳至 `_popen`。  
  
## 傳回值  
 則傳回結束的命令處理器的執行狀態，如果發生錯誤則為 \-1。  傳回值的格式同於 `_cwait`，除了低序位和高位位元組已被交換。  如果資料流是 **NULL**，`_pclose` 將 `errno` 設為 `EINVAL` 並傳回 \-1。  
  
 如需有關這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `_pclose` 函式搜尋由相關聯的 `_popen` 呼叫開啟的命令處理器 \(Cmd.exe\) 的處理序 ID ，在新命令處理器執行 [\_cwait](../../c-runtime-library/reference/cwait.md) 呼叫，並關閉關聯的管道的資料流。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_pclose`|\<stdio.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [\_pipe](../../c-runtime-library/reference/pipe.md)   
 [\_popen、\_wpopen](../../c-runtime-library/reference/popen-wpopen.md)