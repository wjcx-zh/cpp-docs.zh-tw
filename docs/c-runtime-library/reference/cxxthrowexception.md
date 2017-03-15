---
title: "_CxxThrowException | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CxxThrowException"
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
  - "CxxThrowException"
  - "_CxxThrowException"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CxxThrowException 函式"
  - "CxxThrowException 函式"
ms.assetid: 0b90bef5-b7d2-46e0-88e2-59e531e01a4d
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# _CxxThrowException
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

建立例外狀況記錄並呼叫執行階段環境以處理例外狀況。  
  
## 語法  
  
```  
extern "C" void __stdcall _CxxThrowException(  
   void* pExceptionObject  
   _ThrowInfo* pThrowInfo  
);  
```  
  
#### 參數  
 \[in\] `pExceptionObject`  
 產生例外狀況的物件。  
  
 \[in\] `pThrowInfo`  
 處理例外狀況所要求的資訊。  
  
## 備註  
 這個方法包含在編譯器唯讀檔以供編譯器使用來處理例外狀況。  請勿直接從您的程式碼裏呼叫此方法。  
  
## 需求  
 **來源：**  Throw.cpp  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)