---
title: "_get_printf_count_output | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_get_printf_count_output"
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
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "get_printf_count_output"
  - "_get_printf_count_output"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "%n 格式"
  - "_get_printf_count_output 函式"
  - "get_printf_count_output 函式"
ms.assetid: 850f9f33-8319-433e-98d8-6a694200d994
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _get_printf_count_output
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指出 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)\-函式家族支援 `%n` 格式。  
  
## 語法  
  
```  
int _get_printf_count_output();  
```  
  
## 傳回值  
 若 `%n` 支援則為非 0，如果 `%n` 不支援則為0。  
  
## 備註  
 如果 `%n` 不支援 \(預設值\)，會在格式字串的任何 `%n` `printf` 函式將叫用無效的參數處理常式如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  `%n` 支援有效 \(請參閱 [\_set\_printf\_count\_output](../../c-runtime-library/reference/set-printf-count-output.md)\) `%n` 會表現如 [printf 類型欄位字元](../../c-runtime-library/printf-type-field-characters.md)中所述。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_get_printf_count_output`|\<stdio.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 請參閱[\_set\_printf\_count\_output](../../c-runtime-library/reference/set-printf-count-output.md)中的範例。  
  
## NET Framework 對等  
 不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。