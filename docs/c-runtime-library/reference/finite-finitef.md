---
title: "_finite、_finitef | Microsoft Docs"
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
  - "_finite"
  - "_finitef"
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
  - "finite"
  - "_finite"
  - "_finitef"
  - "math/_finite"
  - "math/_finitef"
  - "float/_finite"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "finite 函式"
  - "_finite 函式"
  - "_finitef 函式"
ms.assetid: 5a7d7ca7-befb-4e1f-831d-28713c6eb805
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _finite、_finitef
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

判斷指定的浮點數值是否有限。  
  
## 語法  
  
```  
int _finite(   
   double x   
);  
  
int _finitef(   
   float x   
); /* x64 and ARM/ARM64 only */  
```  
  
#### 參數  
 `x`  
 要測試的浮點值。  
  
## 傳回值  
 如果引數 *x* 為有限；也就是說，如果 –INF \< `x` \< \+INF，則 `_finite` 和 `_finitef` 皆會傳回非零值。 如果引數為無限或 NAN，它會傳回 0。  
  
## 備註  
 `_finite` 和 `_finitef` 函式是 Microsoft 專有的。`_finitef` 函式只是針對 x86、 ARM、 或 ARM64 編譯時，才能使用平台。  
  
## 需求  
  
|函式|必要的標頭 \(C\)|必要的標頭 \(C\+\+\)|  
|--------|-----------------|---------------------|  
|`_finite`|\<float.h\> 或 \<math.h\>|\<float.h\>、\<math.h\>、\<cfloat\> 或 \<cmath\>|  
|`_finitef`|\<math.h\>|\<math.h\> 或 \<cmath\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 [System::Double::IsInfinity](https://msdn.microsoft.com/en-us/library/system.double.isinfinity.aspx)  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [isnan \_isnan \_isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)   
 [\_fpclass \_fpclassf](../../c-runtime-library/reference/fpclass-fpclassf.md)