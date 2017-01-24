---
title: "isascii __isascii、 iswascii | Microsoft Docs"
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
  - "iswascii"
  - "__isascii"
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
  - "iswascii"
  - "istascii"
  - "__isascii"
  - "_istascii"
  - "isascii"
  - "ctype/isascii"
  - "ctype/__isascii"
  - "corecrt_wctype/iswascii"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "__isascii 函式"
  - "_isascii 函式"
  - "isascii 函式"
  - "_istascii 函式"
  - "istascii 函式"
  - "iswascii 函式"
ms.assetid: ba4325ad-7cb3-4fb9-b096-58906d67971a
caps.latest.revision: 22
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# isascii __isascii、 iswascii
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

判斷特定字元是否為 ASCII 字元。  
  
## 語法  
  
```  
int __isascii(   
   int c   
);  
int iswascii(   
   wint_t c   
);  
#define isascii __isascii  
```  
  
#### 參數  
 `c`  
 待測試整數。  
  
## 傳回值  
 每個這些常式傳回非零值如果 `c` 是特定的表示法的 ASCII 字元。`__isascii` 傳回非零值，如果 `c` 是 ASCII 字元 （在範圍 0x00 – 0x7F）。`iswascii` 傳回非零值，如果 `c` 是 ASCII 字元的寬字元表示法。 這些常式都會傳回 0，如果 `c` 不符合測試條件。  
  
## 備註  
 同時 `__isascii` 和 `iswascii` 除非定義前置處理器巨集 \_CTYPE\_DISABLE\_MACROS 會實作成巨集。  
  
 回溯相容性， `isascii` 會實作成巨集才 [\_\_STDC\_\_](../../preprocessor/predefined-macros.md) 未定義或定義為 0; 否則為未定義。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_istascii`|`__isascii`|`__isascii`|`iswascii`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`isascii`, `__isascii`|C: \< ctype.h \><br /><br /> C \+ \+: \< cctype \> 或 \< ctype.h \>|  
|`iswascii`|C: \< wctype.h \>，\< ctype.h \>，\< wchar.h \> 或<br /><br /> C \+ \+: \< cwctype \>，\< cctype \>，\< wctype.h \>，\< ctype.h \>，\< wchar.h \> 或|  
  
 `isascii`, ，`__isascii` 和 `iswascii` 函式是 Microsoft 專有的。 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [字元分類](../../c-runtime-library/character-classification.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [is、isw 常式](../../c-runtime-library/is-isw-routines.md)