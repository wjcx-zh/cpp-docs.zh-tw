---
title: "_purecall | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_purecall"
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
  - "purecall"
  - "_purecall"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_purecall 函式"
  - "purecall 函式"
ms.assetid: 56135d9b-3403-4e22-822d-e714523801cc
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _purecall
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

預設純虛擬函式呼叫錯誤處理常式。 編譯器產生的程式碼呼叫此函式，當呼叫純虛擬成員函式。  
  
## 語法  
  
```  
extern "C" int __cdecl _purecall();  
```  
  
## 備註  
 `_purecall` 函式是 Microsoft Visual c \+ \+ 編譯器的 Microsoft 特定實作詳細資料。 此函式不是由您的程式碼直接呼叫，它有沒有公用的標頭宣告。 它是本文所述因為它是 C 執行階段程式庫的公用匯出。  
  
 純虛擬函式呼叫會產生錯誤，因為它有沒有實作。 編譯器會產生程式碼叫用 `_purecall` 錯誤處理常式函式呼叫純虛擬函式時。 根據預設， `_purecall` 結束程式。 之前終止， `_purecall` 函式叫用 `_purecall_handler` 函式在已設定其中一個程序。 您可以安裝您自己的錯誤處理常式函式的純虛擬函式呼叫，攔截它們，偵錯或報告之用。 若要使用您自己的錯誤處理常式，建立具有的函式 `_purecall_handler` 簽章，然後使用 [\_set\_purecall\_handler](../../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md) 使其目前的處理常式。  
  
## 需求  
 `_purecall` 函式沒有標頭宣告。`_purecall_handler` \< Stdlib.h \> 中所定義的 typedef。  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [\_get\_purecall\_handler \_set\_purecall\_handler](../../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md)