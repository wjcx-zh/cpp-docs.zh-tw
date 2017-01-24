---
title: "towctrans | Microsoft Docs"
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
  - "towctrans"
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
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "towctrans"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "towctrans 函式"
ms.assetid: 1ed1e70d-7b31-490f-a7d9-42564b5924ca
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# towctrans
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

轉換字元。  
  
## 語法  
  
```  
wint_t towctrans(  
   wint_t c,  
   wctrans_t category   
);  
```  
  
#### 參數  
 `c`  
 要轉換的字元。  
  
 `category`  
 包含 [wctrans](../../c-runtime-library/reference/wctrans.md) 傳回值之的識別項。  
  
## 傳回值  
 在 `towctrans` 之後的字元則為 `c`，在 `category`使用的轉換規則。  
  
## 備註  
 必須由 [wctrans](../../c-runtime-library/reference/wctrans.md)的較早的成功呼叫 `category` 所傳回的值。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`towctrans`|\<wctype.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 如需使用 `towctrans`的範例，請參閱 `wctrans` 。  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)