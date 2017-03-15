---
title: "___lc_collate_cp_func | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "___lc_collate_cp_func"
apilocation: 
  - "msvcr120.dll"
  - "msvcrt.dll"
  - "msvcr100.dll"
  - "msvcr80.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr90.dll"
apitype: "DLLExport"
f1_keywords: 
  - "___lc_collate_cp_func"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "___lc_collate_cp_func"
ms.assetid: 46ccc084-7ac9-4e5d-9138-e12cb5845615
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# ___lc_collate_cp_func
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

內部 CRT 函式。  擷取執行緒的目前定序字碼頁。  
  
## 語法  
  
```cpp  
UINT ___lc_codepage_func(void);  
```  
  
## 傳回值  
 執行緒的目前定序字碼頁。  
  
## 備註  
 `___lc_collate_cp_func` 是內部 CRT 函式，由其他 CRT 函式用於從 CRT 資料的執行緒區域儲存區取得目前的定序字碼頁。  也可以使用 [\_get\_current\_locale](../c-runtime-library/reference/get-current-locale.md) 函式取得此資訊。  
  
 內部 CRT 函式是特別針對實作，且會依每個版本而有所不同。  不建議將此函式用於您的程式碼中。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`___lc_collate_cp_func`|crt\\src\\setlocal.h|  
  
## 請參閱  
 [\_get\_current\_locale](../c-runtime-library/reference/get-current-locale.md)   
 [setlocale、\_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [\_create\_locale、\_wcreate\_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [\_free\_locale](../c-runtime-library/reference/free-locale.md)