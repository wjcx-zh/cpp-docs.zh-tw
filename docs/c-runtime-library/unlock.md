---
title: "_unlock | Microsoft Docs"
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
  - "_unlock"
apilocation: 
  - "msvcrt.dll"
  - "msvcr100.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr80.dll"
  - "msvcr120.dll"
  - "msvcr90.dll"
  - "msvcr120_clr0400.dll"
apitype: "DLLExport"
f1_keywords: 
  - "unlock"
  - "_unlock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unlock 函式"
  - "_unlock 函式"
ms.assetid: 2eda2507-a134-4997-aa12-f2f8cb319e14
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _unlock
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

取得多執行緒的鎖定。  
  
> [!IMPORTANT]
>  此函式已被取代。 自 Visual Studio 2015 起，此函式即無法在 CRT 中使用。  
  
## 語法  
  
```  
void __cdecl _unlock(  
   int locknum  
);  
```  
  
#### 參數  
 \[in\] `locknum`  
 要取得之鎖定的識別碼。  
  
## 需求  
 **來源：**mlock.c  
  
## 請參閱  
 [依字母順序排列的函式參考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [\_lock](../c-runtime-library/lock.md)