---
title: "_RTC_SetErrorFunc | Microsoft Docs"
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
  - "_RTC_SetErrorFunc"
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
  - "RTC_SetErrorFunc"
  - "_RTC_SetErrorFunc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "RTC_SetErrorFunc 函式"
  - "_RTC_SetErrorFunc 函式"
ms.assetid: b2292722-0d83-4092-83df-3d5b19880666
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _RTC_SetErrorFunc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定函式做為報告執行階段錯誤檢查 \(RTC\) 的處理常式。 此函數已被取代。請改用 `_RTC_SetErrorFuncW`。  
  
## 語法  
  
```  
  
_RTC_error_fn _RTC_SetErrorFunc(  
   _RTC_error_fn  
 function   
);  
  
```  
  
#### 參數  
 *函式*  
 函式的位址，會處理執行階段錯誤檢查。  
  
## 傳回值  
 先前所定義的錯誤函式。 若先前未曾定義函式，會傳回 NULL。  
  
## 備註  
 請勿使用此函式。請改用 `_RTC_SetErrorFuncW`。 保留此函式的目的只在提供回溯相容性。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_RTC_SetErrorFunc`|\<rtcapi.h\>|  
  
 如需詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## .NET Framework 對等用法  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [\_CrtDbgReport、\_CrtDbgReportW](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)   
 [執行階段錯誤檢查](../../c-runtime-library/run-time-error-checking.md)