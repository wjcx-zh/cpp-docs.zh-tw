---
title: "raise | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "raise"
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
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "Raise"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "程式 [C++], 將訊號傳送至執行程式"
  - "raise 函式"
  - "訊號"
  - "訊號, 傳送至執行程式"
ms.assetid: a3ccd3ad-f68f-4a7b-a005-c3ebfb217e8b
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# raise
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳送訊號至執行的程式。  
  
> [!NOTE]
>  除非是測試或偵錯的狀況，否則不要使用這個方法關閉 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式。  根據 [Windows 8 應用程式認證需求](http://go.microsoft.com/fwlink/?LinkId=262889)的章節 3.6，不允許以程式設計或 UI 方式關閉 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式。  如需詳細資訊，請參閱[應用程式週期 \(Windows 市集應用程式\)](http://go.microsoft.com/fwlink/?LinkId=262853)。  
  
## 語法  
  
```  
  
      int raise(  
int sig   
);  
```  
  
#### 參數  
 *sig*  
 引發信號。  
  
## 傳回值  
 如果成功，則 **raise** 傳回 true。  否則，會傳回非零的值。  
  
## 備註  
 **raise** 函式傳送 *sig* 給執行的程式。  如果先前 **signal** 的呼叫有安裝 *sig*的信號處理函式，則**raise**會執行此函式。  如果處理常式函式未安裝，預設動作與信號值 *sig* 會被取出，如下所示。  
  
|signal|意義|Default|  
|------------|--------|-------------|  
|`SIGABRT`|異常終止|以結束代碼 3 終止呼叫端|  
|`SIGFPE`|浮點數錯誤|結束呼叫程式|  
|`SIGILL`|不合法的指令|結束呼叫程式|  
|`SIGINT`|CTRL\+C 中斷|結束呼叫程式|  
|`SIGSEGV`|不合法的儲存體存取|結束呼叫程式|  
|`SIGTERM`|終止要求傳送至程式|忽略此信號。|  
  
 如果引數不是如上所述的有效信號，則無效的參數叫用處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果未處理，函式會將 `errno` 設定為 `EINVAL` 並傳回非零的值。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|**raise**|\<signal.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [signal](../../c-runtime-library/reference/signal.md)