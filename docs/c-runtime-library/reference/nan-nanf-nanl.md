---
title: "nan、nanf、nanl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "nanf"
  - "nan"
  - "nanl"
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
  - "nan"
  - "nanl"
  - "nanf"
dev_langs: 
  - "C++"
ms.assetid: 790e9158-80ab-43e0-8f5a-096198553fd9
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# nan、nanf、nanl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回無訊息 NaN 值。  
  
## 語法  
  
```  
double nan(    const char* input  ); float nanf(    const char* input  ); long double nanl(    const char* input  );  
```  
  
#### 參數  
 `input`  
 字串值。  
  
## 傳回值  
 `nan` 函式會傳回無訊息 NaN 值。  
  
## 備註  
 `nan` 函式會傳回對應無訊息 \(非發出訊號\) NaN 值的浮點值。  會忽略 `input` 值。  如需 NaN 如何在輸出中表示的資訊，請參閱 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)。  
  
## 需求  
  
|函式|C 標頭|C\+\+ 標頭|  
|--------|----------|--------------|  
|`nan`, `nanf`, `nanl`|\<math.h\>|\<cmath\>|  
  
## .NET Framework 對等用法  
 [System::Double::NaN](https://msdn.microsoft.com/en-us/library/system.double.nan.aspx)  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [\_finite、\_finitef](../../c-runtime-library/reference/finite-finitef.md)   
 [\_fpclass \_fpclassf](../../c-runtime-library/reference/fpclass-fpclassf.md)   
 [isnan \_isnan \_isnanf](../../c-runtime-library/reference/isnan-isnan-isnanf.md)