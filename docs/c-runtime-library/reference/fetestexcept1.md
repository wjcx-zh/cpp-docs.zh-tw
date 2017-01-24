---
title: "fetestexcept | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "cpp"
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "fetestexcept"
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
  - "fetestexcept"
  - "fenv/fetestexcept"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "fetestexept 函式"
ms.assetid: ca4dc43f-5573-440d-bc19-ead7571b13dc
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# fetestexcept
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

決定哪一個指定的浮點例外狀況狀態旗標，目前設定。  
  
## 語法  
  
```  
int fetestexcept(  
   int excepts  
);  
  
```  
  
#### 參數  
 `excepts`  
 浮點狀態旗標位元 OR，用來測試。  
  
## 傳回值  
 如果成功，傳回包含目前對應到的例外狀況狀態旗標的浮點例外狀況巨集的位元的 OR 位元遮罩設定。 設定傳回 0，如果所有的例外狀況。  
  
## 備註  
 使用 fetestexcept 函數來判斷浮點所引發的例外狀況的點作業。 使用 `excepts` 參數來指定要測試的例外狀況狀態旗標。`fetestexcept` 函式會使用 \< fenv.h \> 中定義這些例外狀況巨集 `excepts` 和傳回值︰  
  
|例外狀況巨集|描述|  
|------------|--------|  
|FE\_DIVBYZERO|獨一性或柵欄作業發生錯誤稍早浮點數。已建立為無限大值。|  
|FE\_INEXACT|函式已強制要捨入稍早的浮點運算的預存的結果。|  
|FE\_INVALID|在稍早浮點運算中發生網域錯誤。|  
|FE\_OVERFLOW|範圍錯誤發生。較早的浮點數運算結果就是太大，無法表示。|  
|FE\_UNDERFLOW|較早的浮點數運算結果是太小，表示在完整的精確度。已建立 denormal 值。|  
|FE\_ALLEXCEPT|所有的位元 OR 支援浮點例外狀況。|  
  
 指定 `excepts` 引數可以是 0，其中一個支援的浮點例外狀況巨集，或位元或是兩個或多個巨集。 任何其他的效果 `excepts` 引數的值未定義。  
  
 若要使用此函式，您必須先關閉浮點最佳化作業可能會妨礙使用存取 `#pragma fenv_access(on)` 指示詞，在呼叫之前。 如需詳細資訊，請參閱[fenv\_access](../../preprocessor/fenv-access.md)。  
  
## 需求  
  
|函式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`fetestexcept`|\<fenv.h\>|\<cfenv\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [feclearexcept](../../c-runtime-library/reference/feclearexcept1.md)   
 [feraiseexcept](../../c-runtime-library/reference/feraiseexcept.md)