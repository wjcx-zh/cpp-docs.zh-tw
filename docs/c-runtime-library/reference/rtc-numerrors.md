---
title: "_RTC_NumErrors | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_RTC_NumErrors"
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
  - "_RTC_NumErrors"
  - "RTC_NumErrors"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "執行階段錯誤"
  - "_RTC_NumErrors 函式"
  - "RTC_NumErrors 函式"
ms.assetid: 7e82adae-38e2-4f8b-bc0b-37bda8109fd1
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# _RTC_NumErrors
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回執行階段錯誤檢查 \(RTC\) 可以偵測到的錯誤數總計。 您可以使用此數字作為 **for** 迴圈的控制項。在此迴圈中，每個值都會傳遞給 [\_RTC\_GetErrDesc](../../c-runtime-library/reference/rtc-geterrdesc.md)。  
  
## 語法  
  
```  
  
int _RTC_NumErrors( void );  
  
```  
  
## 傳回值  
 整數，其值代表 Visual C\+\+ 執行階段錯誤檢查可以偵測到的錯誤數總計。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_RTC_NumErrors`|\<rtcapi.h\>|  
  
 如需詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## .NET Framework 對等用法  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [\_RTC\_GetErrDesc](../../c-runtime-library/reference/rtc-geterrdesc.md)   
 [執行階段錯誤檢查](../../c-runtime-library/run-time-error-checking.md)