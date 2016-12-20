---
title: "_CrtSetReportHook | Microsoft Docs"
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
  - "_CrtSetReportHook"
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
  - "_CrtSetReportHook"
  - "CrtSetReportHook"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "CrtSetReportHook 函式"
  - "_CrtSetReportHook 函式"
ms.assetid: 1ae7c64f-8c84-4797-9574-b59f00f7a509
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CrtSetReportHook
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可以安裝一個客戶報告函示藉由將它安裝在 C 執行時間偵錯報告階段 \(僅偵錯版本\) 上。  
  
## 語法  
  
```  
_CRT_REPORT_HOOK _CrtSetReportHook(   
   _CRT_REPORT_HOOK reportHook   
);  
```  
  
#### 參數  
 `reportHook`  
 加入用戶端定義報告函式連結至 C 執行階段偵錯報告流程。  
  
## 傳回值  
 傳回目前的用戶端定義報告函式。  
  
## 備註  
 `_CrtSetReportHook` 可讓應用程式使用其報告函式進入 C 執行階段的偵錯程式庫報告流程。  因此，每當 [\_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) 呼叫產生偵錯報告，應用程式的報告函式會先呼叫。  這項功能可讓應用程式執行作業，例如篩選偵錯回報使用，因此它可以專注於特定配置類型或傳送報告到目的地，在`_CrtDbgReport`無法使用。  如果未定義 [\_DEBUG](../../c-runtime-library/debug.md)，在前置處理中，對 `_CrtSetReportHook` 的呼叫將被移除。  
  
 如需 `_CrtSetReportHook`更健全的版本，請參閱 [\_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md)。  
  
 `_CrtSetReportHook` 函式安裝在 `reportHook` 所指定的新用戶端定義的報告函式並傳回前用戶端定義的連結。  下列範例示範一個用戶端定義的報告攔截應該如何變為原型:  
  
```  
int YourReportHook( int reportType, char *message, int *returnValue );  
```  
  
 若 `reportType` 為偵錯報告型別 \(`_CRT_WARN`、 `_CRT_ERROR`或 `_CRT_ASSERT`\)， `message` 是完全載入組件的偵錯在報告中包含的使用者訊息，且 `returnValue` 應該是由 `_CrtDbgReport`傳回的用戶端定義的報告函式中所指定的值。  如需可用報告資料型別的完整說明，請參閱 [\_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md) 函式。  
  
 如果用戶端定義的報告函式完成處理偵錯訊息這類不需要進一步的報告，則函式會傳回 `TRUE`。  當函式傳回 `FALSE`時，`_CrtDbgReport` 會使用報告類型、模式和檔案的目前設定 呼叫產生偵錯報告。  此外，您可以指定 `_CrtDbgReport` 傳回 `returnValue`物件，應用程式也可以控制偵錯中斷是否發生。  如需完整說明如何設定偵錯報告並產生，請參閱 [\_CrtSetReportFile](../../c-runtime-library/reference/crtsetreportfile.md)、 `_CrtSetReportMode`和 `_CrtDbgReport`。  
  
 如需使用其他攔截功能的執行階段函式，以及撰寫自己的用戶端定義攔截函式的詳細資訊，請參閱 [撰寫偵錯攔截函式](../Topic/Debug%20Hook%20Function%20Writing.md)。  
  
> [!NOTE]
>  如果您的應用程式是 `/clr` 編譯的，並在應用程式結束主要函式之後回報函式呼叫， CLR 將會擲回例外狀況，如果報告函式呼叫任何 CRT 函式。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_CrtSetReportHook`|\<crtdbg.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 程式庫  
 [C run\-time libraries](../../c-runtime-library/crt-library-features.md) 版本的偵錯  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)   
 [\_CrtGetReportHook](../../c-runtime-library/reference/crtgetreporthook.md)