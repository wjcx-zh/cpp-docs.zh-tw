---
title: "iscsym、 iscsymf、 __iscsym、 __iswcsym、 __iscsymf、 __iswcsymf、 _iscsym_l、 _iswcsym_l、 _iscsymf_l、 _iswcsymf_l | Microsoft Docs"
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
  - "_iswcsym_l"
  - "__iswcsym"
  - "__iscsym"
  - "_iswcsymf_l"
  - "_iscsym_l"
  - "__iswcsymf"
  - "__iscsymf"
  - "_iscsymf_l"
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
  - "_iswcsym_l"
  - "_iswcsymf_l"
  - "iscsymf"
  - "iswcsymf"
  - "__iswcsym"
  - "__iswcsymf"
  - "iscsym"
  - "iswcsym"
  - "__iscsym"
  - "_iscsym_l"
  - "_iscsymf_l"
  - "__iscsymf"
  - "ctype/iscsym"
  - "ctype/iscsymf"
  - "ctype/__iscsym"
  - "ctype/__iscsymf"
  - "ctype/__iscsym_l"
  - "ctype/__iscsymf_l"
  - "ctype/__iswcsym"
  - "ctype/__iswcsymf"
  - "ctype/__iswcsym_l"
  - "ctype/__iswcsymf_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "iscsymf_l 函式"
  - "iswsym_l 函式"
  - "_iswcsym_l 函式"
  - "iscsym_l 函式"
  - "_iscsymf_l 函式"
  - "_iswcsymf_l 函式"
  - "_iscsym_l 函式"
  - "__iscsym 函式"
  - "__iswcsymf 函式"
  - "iswsymf_l 函式"
  - "__iscsymf 函式"
  - "__iswcsym 函式"
  - "iscsym 函式"
  - "iscsymf 函式"
ms.assetid: 944dfb99-f2b8-498c-9f55-dbcf370d0a2c
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# iscsym、 iscsymf、 __iscsym、 __iswcsym、 __iscsymf、 __iswcsymf、 _iscsym_l、 _iswcsym_l、 _iscsymf_l、 _iswcsymf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

決定是否整數，代表可用於識別項的字元。  
  
## 語法  
  
```  
int __iscsym(   
   int c   
);  
int __iswcsym(   
   wint_t c   
);  
int __iscsymf(   
   int c   
);  
int __iswcsymf(   
   wint_t c   
);  
int _iscsym_l(   
   int c,  
   _locale_t locale  
);  
int _iswcsym_l(   
   wint_t c,  
   _locale_t locale  
);  
int _iscsymf_l(   
   int c,  
   _locale_t locale  
);  
int _iswcsymf_l(   
   wint_t c,  
   _locale_t locale  
);  
#define iscsym __iscsym  
#define iscsymf __iscsymf  
```  
  
#### 參數  
 `c`  
 待測試整數。`c` 必須是 0\-255 窄字元版本的函式的範圍。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 同時 `__iscsym` 和 `__iswcsym` 傳回非零值，如果 `c` 是字母、 底線或數字。 同時 `__iscsymf` 和 `__iswcsymf` 傳回非零值，如果 `c` 是字母或底線。 這些常式都會傳回 0，如果 `c` 不符合測試條件。 尾碼為 `_l` 的這些函式版本是一樣的，只不過與地區設定相關的行為使用了傳入的地區設定，而不是目前的地區設定。 如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
## 備註  
 除非前置處理器巨集 \_CTYPE\_DISABLE\_MACROS 已定義，這些常式會定義為巨集。 當您使用這些常式的巨集版本時，引數可多次評估。 您使用有副作用的引數清單中的運算式時要小心。  
  
 回溯相容性， `iscsym` 和 `iscsymf` 定義為巨集時，才 [\_\_STDC\_\_](../../preprocessor/predefined-macros.md) 未定義或定義為 0; 否則，它們會未定義。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`iscsym`, `iscsymf`, `__iscsym`, `__iswcsym`, `__iscsymf`, `__iswcsymf`, `_iscsym_l`, `_iswcsym_l`, `_iscsymf_l`, `_iswcsymf_l`|C: \< ctype.h \><br /><br /> C \+ \+: \< cctype \> 或 \< ctype.h \>|  
  
 `iscsym`, ，`iscsymf`, ，`__iscsym`, ，`__iswcsym`, ，`__iscsymf`, ，`__iswcsymf`, ，`_iscsym_l`, ，`_iswcsym_l`, ，`_iscsymf_l`, ，和 `_iswcsymf_l` 為 Microsoft 特定的處理常式。 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [字元分類](../../c-runtime-library/character-classification.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [is、isw 常式](../../c-runtime-library/is-isw-routines.md)