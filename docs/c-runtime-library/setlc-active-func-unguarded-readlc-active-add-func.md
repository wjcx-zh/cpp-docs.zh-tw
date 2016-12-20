---
title: "___setlc_active_func、___unguarded_readlc_active_add_func | Microsoft Docs"
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
  - "___setlc_active_func"
  - "___unguarded_readlc_active_add_func"
apilocation: 
  - "msvcr90.dll"
  - "msvcr110_clr0400.dll"
  - "msvcrt.dll"
  - "msvcr110.dll"
  - "msvcr80.dll"
  - "msvcr120.dll"
  - "msvcr100.dll"
apitype: "DLLExport"
f1_keywords: 
  - "___unguarded_readlc_active_add_func"
  - "___setlc_active_func"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "___setlc_active_func"
  - "___unguarded_readlc_active_add_func"
ms.assetid: 605ec4e3-81e5-4ece-935a-f434768cc702
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ___setlc_active_func、___unguarded_readlc_active_add_func
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

已過時。  CRT 只會為保留二進位相容性匯出這些內部函式。  
  
## 語法  
  
```cpp  
int ___setlc_active_func(void); int * ___unguarded_readlc_active_add_func(void);  
```  
  
## 傳回值  
 傳回的值並不重要。  
  
## 備註  
 雖然內部 CRT 函式 `___setlc_active_func` 和 `___unguarded_readlc_active_add_func` 已過時且不再提供使用，CRT 程式庫還是會為了保留二進位相容性匯出這些函式。  `___setlc_active_func` 的最初目的是要將目前作用中呼叫數傳回至 `setlocale` 函式。  `___unguarded_readlc_active_add_func` 的最初目的是要在不鎖定地區設定的情況下，傳回參考地區設定的函式數。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`___setlc_active_func`, `___unguarded_readlc_active_add_func`|無|  
  
## 請參閱  
 [setlocale、\_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)