---
title: "_lock | Microsoft Docs"
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
  - "_lock"
apilocation: 
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr100.dll"
  - "msvcr90.dll"
  - "msvcr80.dll"
  - "msvcr110.dll"
  - "msvcrt.dll"
  - "msvcr120_clr0400.dll"
apitype: "DLLExport"
f1_keywords: 
  - "lock"
  - "_lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lock 函式"
  - "_lock 函式"
ms.assetid: 29f77c37-30de-4b3d-91b6-030216e645a6
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _lock
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取得多執行緒的鎖定。  
  
> [!IMPORTANT]
>  此函式已被取代。 自 Visual Studio 2015 起，此函式即無法在 CRT 中使用。  
  
## 語法  
  
```  
void __cdecl _lock  
   int locknum  
);  
```  
  
#### 參數  
 \[in\] `locknum`  
 要取得之鎖定的識別碼。  
  
## 備註  
 若已取得鎖定，此方法仍會取得鎖定，並因而導致內部的 C 執行階段 \(CRT\) 錯誤。 若方法無法取得鎖定，會結束並引發嚴重錯誤，同時將錯誤碼設為 `_RT_LOCK`。  
  
## 需求  
 **來源：**mlock.c  
  
## 請參閱  
 [依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [\_unlock](../c-runtime-library/unlock.md)