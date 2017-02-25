---
title: "_RTC_SetErrorType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_RTC_SetErrorType"
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
  - "RTC_SetErrorType"
  - "_RTC_SetErrorType"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "執行階段錯誤"
  - "RTC_SetErrorType 函式"
  - "_RTC_SetErrorType 函式"
ms.assetid: f5f99be7-d357-4b11-b8f5-ddd3428f2b06
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# _RTC_SetErrorType
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

關聯的執行階段錯誤檢查 \(RTC\) 所偵測到的錯誤與類型。 錯誤處理常式會處理如何輸出指定類型的錯誤。  
  
## 語法  
  
```  
  
int _RTC_SetErrorType(  
   _RTC_ErrorNumber  
errnum  
,  
   int  
ErrType   
);  
  
```  
  
#### 參數  
 *errnum*  
 數字，介於 0 與 [\_RTC\_NumErrors](../../c-runtime-library/reference/rtc-numerrors.md) 傳回的值之間。  
  
 *ErrType*  
 值，會指派給此 *errnum*。 例如，您可以使用 **\_CRT\_ERROR**。 若是使用 `_CrtDbgReport` 做為您的錯誤處理常式，*ErrType*  可能會是 [\_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md) 中唯一定的符號。 若您有自己的錯誤處理常式 \([\_RTC\_SetErrorFunc](../../c-runtime-library/reference/rtc-seterrorfunc.md)\)，您可以有可以有和 *errnum* 等量的 *ErrType*。  
  
 \_RTC\_ERRTYPE\_IGNORE 的 *ErrType* 對 `_CrtSetReportMode` 而言有特殊意義；此錯誤會予忽略。  
  
## 傳回值  
 錯誤類型 `type` 先前的值。  
  
## 備註  
 所有錯誤的預設設定皆為 *ErrType* \= 1，與 **\_CRT\_ERROR** 相對應。 如需預設錯誤類型 \(例如 **\_CRT\_ERROR**\) 的詳細資訊，請參閱 [\_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md)。  
  
 您必須先呼叫任一個執行階段錯誤檢查初始化函式，才能呼叫此函式。請參閱 [使用執行階段檢查時不使用 C 執行階段程式庫](../Topic/Using%20Run-Time%20Checks%20Without%20the%20C%20Run-Time%20Library.md)  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_RTC_SetErrorType`|\<rtcapi.h\>|  
  
 如需詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## .NET Framework 對等用法  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [\_RTC\_GetErrDesc](../../c-runtime-library/reference/rtc-geterrdesc.md)   
 [執行階段錯誤檢查](../../c-runtime-library/run-time-error-checking.md)