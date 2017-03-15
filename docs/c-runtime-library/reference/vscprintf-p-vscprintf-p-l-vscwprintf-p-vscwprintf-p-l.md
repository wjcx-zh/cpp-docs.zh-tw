---
title: "_vscprintf_p、_vscprintf_p_l、_vscwprintf_p、_vscwprintf_p_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_vscprintf_p_l"
  - "_vscprintf_p"
  - "_vscwprintf_p_l"
  - "_vscwprintf_p"
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
  - "_vscprintf_p"
  - "_vscprintf_p_l"
  - "vscwprintf_p"
  - "vscprintf_p"
  - "vscwprintf_p_l"
  - "_vscwprintf_p_l"
  - "vscprintf_p_l"
  - "_vscwprintf_p"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_vscprintf_p 函式"
  - "_vscprintf_p_l 函式"
  - "_vsctprintf_p 函式"
  - "_vsctprintf_p_l 函式"
  - "_vscwprintf_p 函式"
  - "_vscwprintf_p_l 函式"
  - "vscprintf_p 函式"
  - "vscprintf_p_l 函式"
  - "vsctprintf_p 函式"
  - "vsctprintf_p_l 函式"
  - "vscwprintf_p 函式"
  - "vscwprintf_p_l 函式"
ms.assetid: 5da920b3-8652-4ee9-b19e-5aac3ace9d03
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# _vscprintf_p、_vscprintf_p_l、_vscwprintf_p、_vscwprintf_p_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回字元數在格式化字串中使用指標引數清單，且能夠指定引數的命令。  
  
## 語法  
  
```  
int _vscprintf_p(  
   const char *format,  
   va_list argptr   
);  
int _vscprintf_p _l(  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);  
int _vscwprintf_p (  
   const wchar_t *format,  
   va_list argptr   
);  
int _vscwprintf_p _l(  
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
 若由引數清單指向的字串列印或傳送至檔案或緩衝區，使用特定的格式化程式碼，而產生字元，`_vscprintf_p` 傳回字元數。  傳回的值不包含結束的 null 字元。  `_vscwprintf_p` 實作寬字元的相同功能函式。  
  
## 備註  
 這些函式與 `_vscprintf` 和 `_vscwprintf` 的不同在於它們只支援指定引數的命令。  如需詳細資訊，請參閱[printf\_p 位置參數](../../c-runtime-library/printf-p-positional-parameters.md)。  
  
 這些有 `_l` 尾碼的函式版本是一樣的，不同之處在於會使用傳入的地區設定，而不使用目前的執行緒地區設定。  
  
 如果 `format` 如  [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述為 null 指標，則叫用無效參數處理常式。  如果允許繼續執行，函式回傳 \-1 並將 `errno` 設置為 `EINVAL` 。  
  
> [!IMPORTANT]
>  請確定，如果 `format` 是使用者定義的字串，它是 NULL 結尾並具有正確的參數數目和型別。  如需詳細資訊，請參閱 [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795) 。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE & \_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_vsctprintf_p`|`_vscprintf_p`|`_vscprintf_p`|`_vscwprintf_p`|  
|`_vsctprintf_p_l`|`_vscprintf_p_l`|`_vscprintf_p_l`|`_vscwprintf_p_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_vscprintf_p`, `_vscprintf_p_l`|\<stdio.h\>|  
|`_vscwprintf_p`, `_vscwprintf_p_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 如需範例，請參閱 [vsprintf](../../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)。  
  
## 請參閱  
 [vprintf 函式](../../c-runtime-library/vprintf-functions.md)   
 [\_scprintf\_p、\_scprintf\_p\_l、\_scwprintf\_p、\_scwprintf\_p\_l](../../c-runtime-library/reference/scprintf-p-scprintf-p-l-scwprintf-p-scwprintf-p-l.md)   
 [\_vscprintf、\_vscprintf\_l、\_vscwprintf、\_vscwprintf\_l](../../c-runtime-library/reference/vscprintf-vscprintf-l-vscwprintf-vscwprintf-l.md)