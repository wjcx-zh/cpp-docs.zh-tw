---
title: "lrint、 lrintf、 lrintl、 llrint、 llrintf、 llrintl | Microsoft Docs"
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
  - "lrint"
  - "lrintl"
  - "lrintf"
  - "llrint"
  - "llrintf"
  - "llrintl"
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
  - "lrint"
  - "lrintf"
  - "lrintl"
  - "llrint"
  - "llrintf"
  - "llrintl"
  - "math/lrint"
  - "math/lrintf"
  - "math/lrintl"
  - "math/llrint"
  - "math/llrintf"
  - "math/llrintl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lrint 函式"
  - "lrintf 函式"
  - "lrintl 函式"
  - "llrint 函式"
  - "llrintf 函式"
  - "llrintl 函式"
ms.assetid: 28ccd5b3-5e6f-434f-997d-a21d51b8ce7f
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# lrint、 lrintf、 lrintl、 llrint、 llrintf、 llrintl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定浮點數四捨五入為最接近的整數值，使用目前的捨入模式和方向。  
  
## 語法  
  
```  
long int lrint(  
   double x  
);  
  
long int lrint(  
   float x  
); //C++ only  
  
long int lrint(  
   long double x  
); //C++ only  
  
long int lrintf(  
   float x  
);  
  
long int lrintl(  
   long double x  
);  
  
long long int llrint(  
   double x  
);  
  
long long int llrint(  
   float x  
); //C++ only  
  
long long int llrint(  
   long double x  
); //C++ only  
  
long long int llrintf(  
   float x  
);  
  
long long int llrintl(  
   long double x  
);  
  
```  
  
#### 參數  
 \[in\] `x`  
 要四捨五入的值。  
  
## 傳回值  
 如果成功，傳回的整數值捨入 `x`。  
  
|問題|返回|  
|--------|--------|  
|`x` 傳回的型別範圍之外<br /><br /> `x` \= ±∞<br /><br /> `x` \= NaN|引發 FE\_INVALID，並傳回零 \(0\)。|  
  
## 備註  
 因為 c \+ \+ 允許多載，所以您可以呼叫的多載 `lrint` 和 `llrint` 會浮點數和 long double 型別。 在 C 程式中， `lrint` 和 `llrint` 都需要雙精度浮點數。  
  
 如果 `x` 不代表浮點數的對等的整數值，這些函數會引發 FE\_INEXACT。  
  
 **Microsoft 特定的**︰ 結果的傳回型別範圍之外時，或當參數為 NaN 或無限大，則傳回值是實作所定義。 Microsoft 編譯器會傳回零 \(0\) 的值。  
  
## 需求  
  
|函式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`lrint`, `lrintf`, `lrintl`, `llrint`, `llrintf`, `llrintl`|\<math.h\>|\<cmath\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [依字母順序排列的函式參考](../../c-runtime-library/reference/crt-alphabetical-function-reference.md)