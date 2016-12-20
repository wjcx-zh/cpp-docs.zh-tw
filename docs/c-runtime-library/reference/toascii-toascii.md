---
title: "toascii __toascii | Microsoft Docs"
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
  - "__toascii"
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
  - "api-ms-win-crt-convert-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__toascii"
  - "toascii"
  - "ctype/toascii"
  - "ctype/__toascii"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "toascii 函式"
  - "為 ASCII 字元的字串轉換"
  - "__toascii 函式"
  - "若要轉換的 ASCII 字元"
ms.assetid: a07c0608-b0e2-4da2-a20c-7b64d6a9b77c
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# toascii __toascii
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

透過截斷進行將 7 位元 ASCII 字元。  
  
## 語法  
  
```  
int __toascii(  
   int c   
);  
#define toascii __toascii  
```  
  
#### 參數  
 `c`  
 要轉換的字元。  
  
## 傳回值  
 `__toascii` 值轉換 `c` 到 7 位元 ASCII 範圍，並傳回結果。 沒有保留表示錯誤的傳回值。  
  
## 備註  
 `__toascii` 常式將指定的字元轉換為 ASCII 字元，則會截斷為低序位 7 位元。 會不套用任何其他轉換。  
  
 `__toascii` 常式已定義為巨集，除非已定義的前置處理器巨集 \_CTYPE\_DISABLE\_MACROS。 回溯相容性， `toascii` 定義為巨集時，才 [\_\_STDC\_\_](../../preprocessor/predefined-macros.md) 未定義或定義為 0; 否則為未定義。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`toascii`, `__toascii`|C: \< ctype.h \><br /><br /> C \+ \+: \< cctype \> 或 \< ctype.h \>|  
  
 `toascii` 巨集是 POSIX 延伸模組和 `__toascii` 是 POSIX 擴充功能的 Microsoft 特定實作。 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [is、isw 常式](../../c-runtime-library/is-isw-routines.md)   
 [to 函式](../../c-runtime-library/to-functions.md)