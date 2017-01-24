---
title: "_RTC_GetErrDesc | Microsoft Docs"
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
  - "_RTC_GetErrDesc"
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
  - "RTC_GetErrDesc"
  - "_RTC_GetErrDesc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "執行階段錯誤"
  - "_RTC_GetErrDesc 函式"
  - "RTC_GetErrDesc 函式"
ms.assetid: 7994ec2b-5488-4fd4-806d-a166c9a9f927
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _RTC_GetErrDesc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回執行階段錯誤檢查 \(RTC\) 類型的簡短描述。  
  
## 語法  
  
```  
  
const char * _RTC_GetErrDesc(  
   _RTC_ErrorNumber   
errnum  
);  
  
```  
  
#### 參數  
 *errnum*  
 數字，介於 0 與小於 `_RTC_NumErrors` 的值之間。  
  
## 傳回值  
 字元字串，包含一個執行階段錯誤檢查系統偵測到之錯誤類型之一的簡短描述。 若錯誤小於零或大於或等於 [\_RTC\_NumErrors](../../c-runtime-library/reference/rtc-numerrors.md) 傳回的值，`_RTC_GetErrDesc` 會傳回 NULL。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_RTC_GetErrDesc`|\<rtcapi.h\>|  
  
 如需詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## .NET Framework 對等用法  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [\_RTC\_NumErrors](../../c-runtime-library/reference/rtc-numerrors.md)   
 [執行階段錯誤檢查](../../c-runtime-library/run-time-error-checking.md)