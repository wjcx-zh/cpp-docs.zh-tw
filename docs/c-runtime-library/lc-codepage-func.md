---
title: "___lc_codepage_func | Microsoft Docs"
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
  - "___lc_codepage_func"
apilocation: 
  - "msvcr120.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr80.dll"
  - "msvcr100.dll"
  - "msvcr90.dll"
  - "msvcr110.dll"
  - "msvcrt.dll"
apitype: "DLLExport"
f1_keywords: 
  - "lc_codepage_func"
  - "___lc_codepage_func"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "___lc_codepage_func"
ms.assetid: 6a663bd0-5a63-4a2f-9507-872ec1582aae
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ___lc_codepage_func
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

內部 CRT 函式。  擷取執行緒的目前字碼頁。  
  
## 語法  
  
```cpp  
UINT ___lc_codepage_func(void);  
```  
  
## 傳回值  
 執行緒的目前字碼頁。  
  
## 備註  
 `___lc_codepage_func` 是內部 CRT 函式，由其他 CRT 函式用於從 CRT 資料的執行緒區域儲存區取得目前的字碼頁。  也可以使用 [\_get\_current\_locale](../c-runtime-library/reference/get-current-locale.md) 函式取得此資訊。  
  
 *「字碼頁」*\(Code Page\) 是單一位元組或雙位元組字碼和個別字元的對應。  不同的字碼頁包含不同的特殊字元，一般而言是針對語言或語言群組進行自訂。  如需字碼頁的詳細資訊，請參閱 [字碼頁](../c-runtime-library/code-pages.md)。  
  
 內部 CRT 函式是特別針對實作，且會依每個版本而有所不同。  不建議將此函式用於您的程式碼中。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`___lc_codepage_func`|crt\\src\\setlocal.h|  
  
## 請參閱  
 [\_get\_current\_locale](../c-runtime-library/reference/get-current-locale.md)   
 [setlocale、\_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [\_create\_locale、\_wcreate\_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [\_free\_locale](../c-runtime-library/reference/free-locale.md)