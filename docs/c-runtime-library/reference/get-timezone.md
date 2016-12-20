---
title: "_get_timezone | Microsoft Docs"
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
  - "_get_timezone"
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
  - "api-ms-win-crt-time-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_get_timezone"
  - "get_timezone"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "時區"
  - "get_timezone 函式"
  - "_get_timezone 函式"
ms.assetid: 30ab0838-0ae9-4a2f-bfe6-a49ee443b21e
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _get_timezone
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 Coordinated Universal Time \(UTC\) 與本地時間的秒數擷取差異。  
  
## 語法  
  
```  
  
      error_t _get_timezone(   
    long* seconds  
);  
```  
  
#### 參數  
 `seconds`  
 UTC 與本地時間之間的秒數的差異 。  
  
## 傳回值  
 如果成功，則為零，如果發生錯誤， 則為 `errno` 值。  
  
## 備註  
 `_get_timezone` 函式擷取在 UTC 與本地時間的秒數差異為整數。  預設值為 28,800 秒，太平洋標準時間 \(以 UTC 後的八小時\)。  
  
 如果 `seconds` 是 `NULL`，則叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，函式將 `errno` 設置為 `EINVAL` 並回傳 `EINVAL` 。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_get_timezone`|\<time.h\>|  
  
 如需詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)   
 [\_get\_daylight](../../c-runtime-library/reference/get-daylight.md)   
 [\_get\_dstbias](../../c-runtime-library/reference/get-dstbias.md)   
 [\_get\_tzname](../../c-runtime-library/reference/get-tzname.md)