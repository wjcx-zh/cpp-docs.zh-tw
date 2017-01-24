---
title: "_get_daylight | Microsoft Docs"
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
  - "__daylight"
  - "_get_daylight"
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
  - "get_daylight"
  - "_get_daylight"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_get_daylight 函式"
  - "日光節約時間位移"
  - "get_daylight 函式"
ms.assetid: f85a6ba3-e187-4ca7-aed7-ffc694c8ac4c
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _get_daylight
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取日光節約時間位移 \(小時\)。  
  
## 語法  
  
```  
  
error_t _get_daylight(      int* hours );  
```  
  
#### 參數  
 `hours`  
 日光節約時間的位移 \(小時\)。  
  
## 傳回值  
 若成功，則為零；若發生錯誤，則為 `errno` 值。  
  
## 備註  
 `_get_daylight` 函式會將日光節約時間的小時數擷取為整數。  若日光節約時間已生效，則預設位移為一小時 \(但少數地區是遵循兩小時的位移\)。  
  
 若 `hours` 為 `NULL`，則會叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  若允許繼續執行，此函式會將 `errno` 設為 `EINVAL`，並傳回 `EINVAL`。  
  
 建議您使用此函式，而不是使用巨集 `_daylight` 或已遭取代的函式 `__daylight`。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_get_daylight`|\<time.h\>|  
  
 如需詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)   
 [\_get\_dstbias](../../c-runtime-library/reference/get-dstbias.md)   
 [\_get\_timezone](../../c-runtime-library/reference/get-timezone.md)   
 [\_get\_tzname](../../c-runtime-library/reference/get-tzname.md)