---
title: "_fpclass _fpclassf | Microsoft Docs"
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
  - "_fpclass"
  - "_fpclassf"
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
  - "fpclass"
  - "_fpclass"
  - "_fpclassf"
  - "math/_fpclass"
  - "float/_fpclass"
  - "math/_fpclassf"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "fpclass 函式"
  - "浮點數，IEEE 表示"
  - "_fpclass 函式"
  - "_fpclassf 函式"
ms.assetid: 2774872d-3543-446f-bc72-db85f8b95a6b
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _fpclass _fpclassf
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回值，指出引數的浮點數的分類。  
  
## 語法  
  
```  
int _fpclass(   
   double x   
);  
  
int _fpclassf(   
   float x   
); /* x64 only */  
```  
  
#### 參數  
 `x`  
 要測試的浮點值。  
  
## 傳回值  
 `_fpclass` 和 `_fpclassf` 函式會傳回整數值，指出引數的浮點數的分類 `x`。 類別只能有一個以下的值，定義在 \<.h \>。  
  
|值|描述|  
|-------|--------|  
|`_FPCLASS_SNAN`|訊號 NaN|  
|`_FPCLASS_QNAN`|無訊息 NaN|  
|`_FPCLASS_NINF`|無限大的負數 \(\-INF\)|  
|`_FPCLASS_NN`|負正規化是非零值|  
|`_FPCLASS_ND`|負正規化|  
|`_FPCLASS_NZ`|零負值 （\-0）|  
|`_FPCLASS_PZ`|正 （\+ 0） 的 0|  
|`_FPCLASS_PD`|正規化的正數|  
|`_FPCLASS_PN`|正正規化是非零值|  
|`_FPCLASS_PINF`|正的無限大 （\+ INF）|  
  
## 備註  
 `_fpclass` 和 `_fpclassf` 函式是 Microsoft 專有的。 它們是類似於 [fpclassify](../../c-runtime-library/reference/fpclassify.md), ，但傳回更多詳細資訊的引數。`_fpclassf` 函式只適用於 x64 編譯時的平台。  
  
## 需求  
  
|函式|必要的標頭|  
|--------|-----------|  
|`_fpclass`|\<float.h\>|  
  
 如需相容性和一致性，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [isnan \_isnan \_isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)   
 [fpclassify](../../c-runtime-library/reference/fpclassify.md)