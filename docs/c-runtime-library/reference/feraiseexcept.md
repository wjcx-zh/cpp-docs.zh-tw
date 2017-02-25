---
title: "feraiseexcept | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "feraiseexcept"
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
apitype: "HeaderDef"
f1_keywords: 
  - "feraiseexcept"
  - "fenv/feraiseexcept"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "feraiseexcept 函式"
ms.assetid: 87e89151-83c2-4563-9a9a-45666245d437
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# feraiseexcept
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

引發指定之浮點例外狀況。  
  
## 語法  
  
```  
int feraiseexcept(  
   int excepts  
);  
```  
  
#### 參數  
 `excepts`  
 浮點例外狀況，用來引發。  
  
## 傳回值  
 如果所有指定的例外狀況產生成功，傳回 0。  
  
## 備註  
 `feraiseexcept` 函式會嘗試引發浮點例外狀況，由指定 `excepts`。`feraiseexcept` 函式支援 \< fenv.h \> 中定義這些例外狀況巨集︰  
  
|例外狀況巨集|描述|  
|------------|--------|  
|FE\_DIVBYZERO|獨一性或柵欄作業發生錯誤稍早浮點數。已建立為無限大值。|  
|FE\_INEXACT|函式已強制要捨入稍早的浮點運算的預存的結果。|  
|FE\_INVALID|在稍早浮點運算中發生網域錯誤。|  
|FE\_OVERFLOW|範圍錯誤發生。較早的浮點數運算結果就是太大，無法表示。|  
|FE\_UNDERFLOW|較早的浮點數運算結果是太小，表示在完整的精確度。已建立 denormal 值。|  
|FE\_ALLEXCEPT|所有的位元 OR 支援浮點例外狀況。|  
  
 `excepts` 引數可以是零，其中一個例外狀況巨集值，或位元，或是兩個或多個支援的例外狀況巨集。 如果其中一個指定的例外狀況巨集，FE\_OVERFLOW 或 FE\_UNDERFLOW FE\_INEXACT 例外狀況可能會發生副作用。  
  
 若要使用此函式，您必須先關閉浮點最佳化作業可能會妨礙使用存取 `#pragma fenv_access(on)` 指示詞，在呼叫之前。 如需詳細資訊，請參閱[fenv\_access](../../preprocessor/fenv-access.md)。  
  
 **Microsoft 特定的︰** 中指定的例外狀況 `excepts` 會依照順序 FE\_INVALID，引發 FE\_DIVBYZERO、 FE\_OVERFLOW、 FE\_UNDERFLOW、 FE\_INEXACT。 不過，FE\_INEXACT 可以產生 FE\_OVERFLOW 或 FE\_UNDERFLOW 引發時，即使未在指定 `excepts`。**結束 Microsoft 專有**  
  
## 需求  
  
|函式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`feraiseexcept`|\<fenv.h\>|\<cfenv\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fesetexceptflag](../../c-runtime-library/reference/fesetexceptflag2.md)   
 [feholdexcept](../../c-runtime-library/reference/feholdexcept2.md)   
 [fetestexcept](../../c-runtime-library/reference/fetestexcept1.md)   
 [feupdateenv](../../c-runtime-library/reference/feupdateenv.md)