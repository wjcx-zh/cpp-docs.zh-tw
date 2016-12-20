---
title: "_query_new_handler | Microsoft Docs"
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
  - "_query_new_handler"
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
  - "api-ms-win-crt-heap-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_query_new_handler"
  - "query_new_handler"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_query_new_handler 函式"
  - "錯誤處理"
  - "處理常式"
  - "query_new_handler 函式"
ms.assetid: 9a84b5c3-fe33-4c01-83a0-be87dc3ec518
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _query_new_handler
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回目前新處理常式常式的位址。  
  
## 語法  
  
```  
  
      _PNH _query_new_handler(  
   void   
);  
```  
  
## 傳回值  
 傳回目前新處理常式常式的位址如同由 `_set_new_handler` 設置一般。  
  
## 備註  
 C\+\+ `_query_new_handler` 函式由 C\+\+ [\_set\_new\_handler](../../c-runtime-library/reference/set-new-handler.md) 函式會傳回目前的例外狀況處理函式集的位址。  `_set_new_handler` 用來取得指定為控制項的例外狀況處理函式，如果 **new** 運算子無法配置記憶體。  如需詳細資訊，請參閱 [new 運算子](../../misc/operator-new-function.md) 和 [運算子刪除函式的討論參考](../../misc/operator-delete-function.md) 中有關 *C\+\+ 語言的參考* 。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_query_new_handler`|\<new.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [記憶體配置](../../c-runtime-library/memory-allocation.md)   
 [free](../../c-runtime-library/reference/free.md)