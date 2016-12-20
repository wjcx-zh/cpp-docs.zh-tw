---
title: "_get_tzname | Microsoft Docs"
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
  - "_get_tzname"
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
  - "_get_tzname"
  - "get_tzname"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_get_tzname 函式"
  - "get_tzname 函式"
  - "時區"
ms.assetid: df0065ff-095f-4237-832c-2fe9ab913875
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _get_tzname
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

擷取時區或日光節約時間的標準時區名稱 \(DST\) 的字串表示。  
  
## 語法  
  
```  
errno_t _get_tzname(  
    size_t* pReturnValue,  
    char* timeZoneName,  
    size_t sizeInBytes,  
    int index      
);  
```  
  
#### 參數  
 \[out\] `pReturnValue`  
 字串長度 `timeZoneName` 包括 null 結束字元。  
  
 \[out\] `timeZoneName`  
 一個表示時區或日光節約時間時區名稱 \(DST\)的字串的位址，根據 `index`。  
  
 \[in\] `sizeInBytes`  
 `timeZoneName` 字元字串的大小，以位元組為單位。  
  
 \[in\] `index`  
 索引擷取的兩個時區名稱之一。  
  
## 傳回值  
 如果成功為零，反之則為 `errno` 型別的值。  
  
 如果 `timeZoneName` 是 `NULL`，或者 `sizeInBytes` 為零或小於零 \(但不是兩個都是\)，將叫用無效的參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，函式將 `errno` 設置為 `EINVAL` 並回傳 `EINVAL` 。  
  
### 錯誤狀況  
  
|`pReturnValue`|`timeZoneName`|`sizeInBytes`|`index`|傳回值|`timeZoneName` 的內容|  
|--------------------|--------------------|-------------------|-------------|---------|------------------------|  
|TZ 名稱的大小|`NULL`|0|0 或 1|0|未修改|  
|TZ 名稱的大小|any|\> 0|0 或 1|0|TZ 命名|  
|未修改|`NULL`|\> 0|any|`EINVAL`|未修改|  
|未修改|any|零|any|`EINVAL`|未修改|  
|未修改|any|\> 0|\> 1|`EINVAL`|未修改|  
  
## 備註  
 `_get_tzname` 函式根據索引值擷取時區或日光節約時間時區名稱 \(DST\) 的字元字串至 `timeZoneName` 的位址，跟著表示字串大小的 `pReturnValue`。  如果 `timeZoneName` 是 `NULL` ，而且 `sizeInBytes` 為零，只有任一個時區資料的大小 \(以位元組為單位\) 會以 `pReturnValue` 傳回。  索引值必須是 0 代表標準時區時間或 1 代表日光節約標準時區;索引的任何其他值會導致不確定的結果。  
  
### 索引值  
  
|`index`|`timeZoneName` 的內容|`timeZoneName` 預設值。|  
|-------------|------------------------|-------------------------|  
|0|時區名稱|"PST"|  
|1|日光節約標準時區名稱|"PDT"|  
|\> 1 或 \< 0|將 `errno` 設為 `EINVAL`。|未修改|  
  
 在執行階段期間，除非值明確變更，預設值分別為「PST」和「PDT」。這些字元陣列的大小是由 `TZNAME_MAX` 值所控制。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_get_tzname`|\<time.h\>|  
  
 如需詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [時間管理](../../c-runtime-library/time-management.md)   
 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)   
 [\_get\_daylight](../../c-runtime-library/reference/get-daylight.md)   
 [\_get\_dstbias](../../c-runtime-library/reference/get-dstbias.md)   
 [\_get\_timezone](../../c-runtime-library/reference/get-timezone.md)   
 [TZNAME\_MAX](../../c-runtime-library/tzname-max.md)