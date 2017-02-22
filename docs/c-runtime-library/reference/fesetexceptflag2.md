---
title: "fesetexceptflag2 | Microsoft Docs"
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
  - "fesetexceptflag"
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
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "fesetexceptflag"
  - "fenv/fesetexceptflag"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "fesetexceptflag 函式"
ms.assetid: 2f7dad77-9e54-4097-a3e3-35176ace4de5
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# fesetexceptflag
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

目前的浮點環境中設定指定之浮點狀態旗標。  
  
## 語法  
  
```  
int fesetexceptflag(  
     const fexcept_t *pstatus,  
     int excepts  
);  
  
```  
  
#### 參數  
 `pstatus`  
 指標  `fexcept_t` 物件，其中包含要設為例外狀況狀態旗標的值。 物件可能會設定由先前呼叫 [fegetexceptflag](../Topic/fegetexceptflag1.md)。  
  
 `excepts`  
 若要設定的浮點例外狀況狀態旗標。  
  
## 傳回值  
 如果所有指定的例外狀況狀態旗標已設定成功，則傳回 0。 否則，傳回非零值。  
  
## 備註  
 `fesetexceptflag` 函式會將所指定的浮點例外狀況狀態旗標的狀態 `excepts` 設定中的對應值 `fexcept_t` 指向的物件 `pstatus`。  它不會引發例外狀況。`pstatus` 指標必須指向有效 `fexcept_t` 物件或後續的行為是未定義。`fesetexceptflag` 函式可支援這些例外狀況巨集值 `excepts`, ，定義在 \< fenv.h \>:  
  
|例外狀況巨集|描述|  
|------------|--------|  
|FE\_DIVBYZERO|獨一性或柵欄作業發生錯誤稍早浮點數。已建立為無限大值。|  
|FE\_INEXACT|函式已強制要捨入稍早的浮點運算的預存的結果。|  
|FE\_INVALID|在稍早浮點運算中發生網域錯誤。|  
|FE\_OVERFLOW|範圍錯誤發生。較早的浮點數運算結果就是太大，無法表示。|  
|FE\_UNDERFLOW|較早的浮點數運算結果是太小，表示在完整的精確度。已建立 denormal 值。|  
|FE\_ALLEXCEPT|所有的位元 OR 支援浮點例外狀況。|  
  
 `excepts` 引數可以是零，其中一個支援的浮點例外狀況巨集，或位元或是兩個或多個巨集。 未定義任何其他引數的值的效果。  
  
 若要使用此函式，您必須先關閉浮點最佳化作業可能會妨礙使用存取 `#pragma fenv_access(on)` 指示詞，在呼叫之前。 如需詳細資訊，請參閱[fenv\_access](../../preprocessor/fenv-access.md)。  
  
## 需求  
  
|函式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`fesetexceptflag`|\<fenv.h\>|\<cfenv\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fegetexceptflag](../../c-runtime-library/reference/fegetexceptflag2.md)