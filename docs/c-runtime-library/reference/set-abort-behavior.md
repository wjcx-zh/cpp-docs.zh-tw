---
title: "_set_abort_behavior | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_set_abort_behavior"
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
  - "_set_abort_behavior"
  - "set_abort_behavior"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_set_abort_behavior 函式"
  - "中止程式"
  - "set_abort_behavior 函式"
ms.assetid: 43918766-e4ba-4b1f-80e8-1a4a910cd452
caps.latest.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 26
---
# _set_abort_behavior
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定當程式異常結束時，要採取的動作。  
  
> [!NOTE]
>  除非是在測試或偵錯情節中，否則不要使用 `abort` 函式關閉 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式。  根據 [Windows 8 應用程式認證需求](http://go.microsoft.com/fwlink/?LinkId=262889)，不允許以程式設計或 UI 方式關閉 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式。  如需詳細資訊，請參閱[應用程式週期 \(Windows 市集應用程式\)](http://go.microsoft.com/fwlink/?LinkId=262853)。  
  
## 語法  
  
```  
unsigned int _set_abort_behavior(  
   unsigned int flags,  
   unsigned int mask  
);  
```  
  
#### 參數  
 \[in\] `flags`  
 `abort` 旗標的新值。  
  
 \[in\] `mask`  
 要設定 `abort` 旗標位元的遮罩。  
  
## 傳回值  
 旗標的舊值。  
  
## 備註  
 有兩個 `abort` 旗標：`_WRITE_ABORT_MSG` 和 `_CALL_REPORTFAULT`。  `_WRITE_ABORT_MSG` 決定程式異常終止時是否要列印有用的文字訊息。  訊息表示，應用程式已呼叫 `abort` 函式。  預設行為是列印訊息。  `_CALL_REPORTFAULT`，如果有設定，則在呼叫 `abort` 時產生並報告 Watson 損毀傾印。  非 DEBUG 建置預設啟用損毀傾印報表。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_set_abort_behavior`|\<stdlib.h\>|  
  
 如需詳細的相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```c  
// crt_set_abort_behavior.c  
// compile with: /TC  
#include <stdlib.h>  
  
int main()  
{  
   printf("Suppressing the abort message. If successful, this message"  
          " will be the only output.\n");  
   // Suppress the abort message  
   _set_abort_behavior( 0, _WRITE_ABORT_MSG);  
   abort();  
}  
```  
  
  **隱藏中止訊息。  如果成功，這個訊息會是唯一的輸出內容。**    
## 請參閱  
 [abort](../../c-runtime-library/reference/abort.md)