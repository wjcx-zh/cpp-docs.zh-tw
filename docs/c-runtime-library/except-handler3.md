---
title: "_except_handler3 | Microsoft Docs"
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
  - "_except_handler3"
apilocation: 
  - "msvcrt.dll"
  - "msvcr90.dll"
  - "msvcr80.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr100.dll"
  - "msvcr110.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_except_handler3"
  - "except_handler3"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_except_handler3 函式"
  - "except_handler3 函式"
ms.assetid: b0c64898-0ae5-48b7-9724-80135a0813e2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _except_handler3
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

內部 CRT 函式。  供架構用於尋找適當的例外狀況處理常式以處理目前的例外狀況。  
  
## 語法  
  
```  
int _except_handler3(    PEXCEPTION_RECORD exception_record,    PEXCEPTION_REGISTRATION registration,    PCONTEXT context,    PEXCEPTION_REGISTRATION dispatcher );  
```  
  
#### 參數  
 \[in\] `exception_record`  
 特定例外狀況的資訊。  
  
 \[in\] `registration`  
 指出應該使用哪個範圍資料表尋找例外狀況處理常式的記錄。  
  
 \[in\] `context`  
 保留的。  
  
 \[in\] `dispatcher`  
 保留的。  
  
## 傳回值  
 若應關閉例外狀況，則傳回 `DISPOSITION_DISMISS`。  若應將例外狀況往上傳遞一個層級至封裝例外狀況處理常式，則傳回 `DISPOSITION_CONTINUE_SEARCH`。  
  
## 備註  
 若此方法找到適當的例外狀況處理常式，會將例外狀況傳遞至處理常式。  在此情況中，此方法不會回復至呼叫它的程式碼，且傳回值亦不相關。  
  
## 請參閱  
 [依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)