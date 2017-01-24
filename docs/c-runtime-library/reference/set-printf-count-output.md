---
title: "_set_printf_count_output | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_set_printf_count_output"
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
  - "set_printf_count_output"
  - "_set_printf_count_output"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "%n 格式"
  - "_set_printf_count_output 函式"
  - "set_printf_count_output 函式"
ms.assetid: d8259ec5-764e-42d0-9169-72172e95163b
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _set_printf_count_output
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

於 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)的家族函式啟用或停用 `%n` 格式支援。  
  
## 語法  
  
```  
int _set_printf_count_output(  
   int enable  
);  
```  
  
#### 參數  
 `enable`  
 使用非零值啟用 `%n` 支援， 0 停用 `%n` 支援。  
  
## 屬性值\/傳回值  
 在呼叫這個函式之前的 `%n` 支援狀態 : 如果為非零則啟用 `%n` 支援。  
  
## 備註  
 基於安全性考量，在 `printf` 及其所有變形預設停用 `%n` 格式規範支援 。  如果 `%n` 出現在 `printf` 格式規格，預設行為是叫用無效參數的處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  呼叫具有非零引數的 `_set_printf_count_output` 會導致 `printf` 的函式家族解譯 `%n` ，如 [printf 類型欄位字元](../../c-runtime-library/printf-type-field-characters.md)中所述。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_set_printf_count_output`|\<stdio.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_set_printf_count_output.c  
#include <stdio.h>  
  
int main()  
{  
   int e;  
   int i;  
   e = _set_printf_count_output( 1 );  
   printf( "%%n support was %sabled.\n",  
        e ? "en" : "dis" );  
   printf( "%%n support is now %sabled.\n",  
        _get_printf_count_output() ? "en" : "dis" );  
   printf( "12345%n6789\n", &i ); // %n format should set i to 5  
   printf( "i = %d\n", i );  
}  
```  
  
## Output  
  
```  
%n support was disabled.  
%n support is now enabled.  
123456789  
i = 5  
```  
  
## NET Framework 對等  
 不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [\_get\_printf\_count\_output](../../c-runtime-library/reference/get-printf-count-output.md)