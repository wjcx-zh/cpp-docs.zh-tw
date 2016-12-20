---
title: "nearbyint、 nearbyintf、 nearbyintl | Microsoft Docs"
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
  - "nearbyint"
  - "nearbyintf"
  - "nerabyintl"
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
  - "nearbyint"
  - "nearbyintf"
  - "nearbyintl"
  - "math/nearbyint"
  - "math/narbyintf"
  - "math/narbyintl"
dev_langs: 
  - "C"
  - "C++"
helpviewer_keywords: 
  - "nearbyint 函式"
  - "nearbyintf 函式"
  - "nearbyintl 函式"
ms.assetid: dd39cb68-96b0-434b-820f-6ff2ea65584f
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# nearbyint、 nearbyintf、 nearbyintl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定浮點數四捨五入成整數，並會將該值傳回浮點格式。  
  
## 語法  
  
```  
double nearbyint(  
   double x  
);  
  
float nearbyint(  
   float x  
); //C++ only  
  
long double nearbyint(  
   long double x  
); //C++ only  
  
float nearbyintf(  
   float x  
);  
  
long double nearbyintl(  
   long double x  
);  
  
```  
  
#### 參數  
 \[in\] `x`  
 要捨入的值。  
  
## 傳回值  
 如果成功，傳回 `x`, ，四捨五入至最接近的整數，目前的捨入格式使用 fegetround 所定義。 否則，函式可能會傳回下列值之一︰  
  
|問題|返回|  
|--------|--------|  
|`x` ±INFINITY \=|±INFINITY 修改|  
|`x` \= ±0|±0 修改|  
|`x` \= NaN|NaN|  
  
 透過將不會報告錯誤 [\_matherr](../../c-runtime-library/reference/matherr.md); 尤其是，此函式不會報告任何 FE\_INEXACT 例外狀況。  
  
## 備註  
 此函式的主要差異和 `rint` 是此函式不會產生不精確的浮動點例外狀況。  
  
 因為浮點數的最大值是正確的整數，這個函式將永不溢位來啦 ！相反地，輸出可能溢位的傳回值，在您使用函式的版本而定。  
  
## 需求  
  
|函式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`nearbyint`, `nearbyintf`,  `nearbyintl`|\<math.h\>|\<cmath\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)