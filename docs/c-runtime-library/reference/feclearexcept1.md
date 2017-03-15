---
title: "feclearexcept | Microsoft Docs"
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
  - "feclearexcept"
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
  - "feclearexcept"
  - "fenv/feclearexcept"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "feclearexcept 函式"
ms.assetid: ef419da3-c248-4432-b53c-8e7a475d9533
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# feclearexcept
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

嘗試清除引數所指定的浮點例外狀況旗標。  
  
## 語法  
  
```  
int feclearexcept(  
   int excepts  
);  
```  
  
#### 參數  
 `excepts`  
 若要清除例外狀況狀態旗標。  
  
## 傳回值  
 傳回零 `excepts` 為零，或如果已順利清除所有指定的例外狀況。 否則，傳回非零值。  
  
## 備註  
 `feclearexcept` 函式會嘗試清除浮點點所指定的例外狀況狀態旗標 `excepts`。 函式支援 fenv.h 中定義這些例外狀況巨集︰  
  
|例外狀況巨集|描述|  
|------------|--------|  
|FE\_DIVBYZERO|獨一性或柵欄作業發生錯誤稍早浮點數。已建立為無限大值。|  
|FE\_INEXACT|函式已強制要捨入稍早的浮點運算的預存的結果。|  
|FE\_INVALID|在稍早浮點運算中發生網域錯誤。|  
|FE\_OVERFLOW|範圍錯誤發生。較早的浮點數運算結果就是太大，無法表示。|  
|FE\_UNDERFLOW|較早的浮點數運算結果是太小，表示在完整的精確度。已建立 denormal 值。|  
|FE\_ALLEXCEPT|所有的位元 OR 支援浮點例外狀況。|  
  
 `excepts` 引數可以是零或一個或多個支援的例外狀況巨集的位元 OR。 未定義任何其他引數的值的結果。  
  
## 需求  
  
|函式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`feclearexcept`|\<fenv.h\>|\<cfenv\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [fetestexcept](../../c-runtime-library/reference/fetestexcept1.md)