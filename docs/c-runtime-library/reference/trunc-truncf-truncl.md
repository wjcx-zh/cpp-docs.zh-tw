---
title: "trunc、 truncf、 truncl | Microsoft Docs"
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
  - "trunc"
  - "truncf"
  - "truncl"
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
  - "api-ms-win-crt-math-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "trunc"
  - "truncf"
  - "truncl"
  - "math/trunc"
  - "math/truncf"
  - "math/truncl"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "trunc 函式"
  - "truncf 函式"
  - "truncl 函式"
ms.assetid: de2038ac-ac0b-483e-870c-e8992dcd4fd0
caps.latest.revision: 13
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# trunc、 truncf、 truncl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

判斷小於或等於指定之浮點值最接近的整數。  
  
## 語法  
  
```  
double trunc(  
   double x  
);  
  
float trunc(  
   float x  
); //C++ only  
  
long double trunc(  
   long double x  
); //C++ only  
  
float trunc(  
   float x  
); //C++ only  
  
long double truncl(  
   long double x  
);  
  
```  
  
#### 參數  
 \[in\] `x`  
 要截斷的值。  
  
## 傳回值  
 如果成功，傳回的整數值 `x`, ，朝向零四捨五入。  
  
 否則，可能會傳回下列其中一項︰  
  
|問題|返回|  
|--------|--------|  
|`x` ±INFINITY \=|x|  
|`x` \=  ±0|x|  
|`x` \= NaN|NaN|  
  
 錯誤報告中所指定 [\_matherr](../../c-runtime-library/reference/matherr.md)。  
  
## 備註  
 因為 c \+ \+ 允許多載，所以您可以呼叫的多載 `trunc` 採用並傳回浮點和長雙精度浮點型別。 在 C 程式中， `trunc` 一律採用並傳回雙精度浮點數。  
  
 因為浮點數的最大值是正確的整數，這個函式不溢位在它自己。 不過，您可能會造成溢位的傳回值為整數型別函式。  
  
 您可以也無條件捨去透過隱含地轉換從浮點數到整數。不過，這麼做是限制為可以儲存在 \[目標類型的值。  
  
## 需求  
  
|函式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`trunc`, `truncf`,  `truncl`|\<math.h\>|\<cmath\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [floor、floorf、floorl](../../c-runtime-library/reference/floor-floorf-floorl.md)   
 [ceil、ceilf、ceill](../../c-runtime-library/reference/ceil-ceilf-ceill.md)   
 [round、roundf、roundl](../../c-runtime-library/reference/round-roundf-roundl.md)