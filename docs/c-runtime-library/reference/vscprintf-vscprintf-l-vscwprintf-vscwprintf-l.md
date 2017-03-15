---
title: "_vscprintf、_vscprintf_l、_vscwprintf、_vscwprintf_l | Microsoft Docs"
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
  - "_vscprintf"
  - "_vscprintf_l"
  - "_vscwprintf_l"
  - "_vscwprintf"
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
apitype: "DLLExport"
f1_keywords: 
  - "vscprintf_l"
  - "vscwpeintf"
  - "_vscwprintf"
  - "_vsctprintf"
  - "_vscprintf"
  - "vscwprintf_l"
  - "vscprintf"
  - "_vscwprintf_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_vscprintf 函式"
  - "_vscprintf_l 函式"
  - "_vsctprintf 函式"
  - "_vsctprintf_l 函式"
  - "_vscwprintf 函式"
  - "_vscwprintf_l 函式"
  - "格式化的文字 [C++]"
  - "vscprintf 函式"
  - "vscprintf_l 函式"
  - "vsctprintf 函式"
  - "vsctprintf_l 函式"
  - "vscwprintf 函式"
  - "vscwprintf_l 函式"
ms.assetid: 1bc67d3d-21d5-49c9-ac8d-69e26b16a3c3
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _vscprintf、_vscprintf_l、_vscwprintf、_vscwprintf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在格式化字串中使用指標引數清單傳回字元數。  
  
## 語法  
  
```  
int _vscprintf(  
   const char *format,  
   va_list argptr   
);  
int _vscprintf_l(  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);  
int _vscwprintf(  
   const wchar_t *format,  
   va_list argptr   
);  
int _vscwprintf_l(  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
);  
```  
  
#### 參數  
 `format`  
 格式控制字串。  
  
 `argptr`  
 參數清單的指標。  
  
 `locale`  
 要使用的地區設定。  
  
 如需詳細資訊，請參閱[格式規格](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## 傳回值  
 若由引數清單指向的字串列印或傳送至檔案或緩衝區，使用特定的格式化程式碼，而產生字元，`_vscprintf` 傳回字元數。  傳回的值不包含結束的 null 字元。  `_vscwprintf` 實作寬字元的相同功能函式。  
  
 這些有 `_l` 尾碼的函式版本是一樣的，不同之處在於會使用傳入的地區設定，而不使用目前的執行緒地區設定。  
  
 如果 `format` 如  [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述為 null 指標，則叫用無效參數處理常式。  如果允許繼續執行，函式回傳 \-1 並將 `errno` 設置為 `EINVAL` 。  
  
## 備註  
 每個 `argument` \(如果有的話\) 是根據 `format` 中的對應格式規格進行轉換。  此格式包含一般字元，與 [printf](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) 的 `format` 引數具有相同的形式和功能。  
  
> [!IMPORTANT]
>  請確定，如果 `format` 是使用者定義的字串，它是 NULL 結尾並具有正確的參數數目和型別。  如需詳細資訊，請參閱 [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795) 。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE & \_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_vsctprintf`|`_vscprintf`|`_vscprintf`|`_vscwprintf`|  
|`_vsctprintf_l`|`_vscprintf_l`|`_vscprintf_l`|`_vscwprintf_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_vscprintf`, `_vscprintf_l`|\<stdio.h\>|  
|`_vscwprintf`, `_vscwprintf_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 如需範例，請參閱 [vsprintf](../../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)。  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [scanf、\_scanf\_l、wscanf、\_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf、\_sscanf\_l、swscanf、\_swscanf\_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [vprintf 函式](../../c-runtime-library/vprintf-functions.md)