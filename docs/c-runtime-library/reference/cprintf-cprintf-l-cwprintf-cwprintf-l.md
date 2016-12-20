---
title: "_cprintf、_cprintf_l、_cwprintf、_cwprintf_l | Microsoft Docs"
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
  - "_cwprintf_l"
  - "_cprintf_l"
  - "_cwprintf"
  - "_cprintf"
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
  - "_cwprintf"
  - "cwprintf"
  - "tcprintf"
  - "_tcprintf"
  - "_cprintf"
  - "cwprintf_l"
  - "tcprintf_l"
  - "_tcprintf_l"
  - "cprintf_l"
  - "_cprintf_l"
  - "_cwprintf_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_cprintf 函式"
  - "_cprintf_l 函式"
  - "_cwprintf 函式"
  - "_cwprintf_l 函式"
  - "_tcprintf 函式"
  - "_tcprintf_l 函式"
  - "字元, 列印到主控台"
  - "cprintf_l 函式"
  - "cwprintf 函式"
  - "cwprintf_l 函式"
  - "將字元列印到主控台"
  - "tcprintf 函式"
  - "tcprintf_l 函式"
ms.assetid: 67ffefd4-45b3-4be0-9833-d8d26ac7c4e2
caps.latest.revision: 34
caps.handback.revision: 32
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _cprintf、_cprintf_l、_cwprintf、_cwprintf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

格式化並列印至主控台。  可用更安全的版本；請參閱 [\_cprintf\_s、\_cprintf\_s\_l、\_cwprintf\_s、\_cwprintf\_s\_l](../../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int _cprintf(   
   const char * format [,   
   argument] ...   
);  
int _cprintf_l(   
   const char * format,  
   locale_t locale [,  
   argument] …   
);  
int _cwprintf(  
   const wchar * format [,   
   argument] …  
);  
int _cwprintf_l(  
   const wchar * format,  
   locale_t locale [,   
   argument] …  
);  
```  
  
#### 參數  
 `format`  
 格式控制字串。  
  
 `argument`  
 選擇性參數。  
  
 `locale`  
 使用的地區設定。  
  
## 傳回值  
 已列印的字元數。  
  
## 備註  
 這些 `` 函式格式化並列印一系列的字元與值直接寫入主控台，並使用 `_putch` 函式 \( `_cwprintf`的`_putwch` \) 輸出字元。  每個 `argument` \(如果有的話\) 是根據 `format`中的對應格式規格轉換和輸出。  格式有相同的表單和函式，如[printf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md) 函式的 `format` 參數。  不同於 `fprintf`、`printf`和 `sprintf`這三個函式， `_cprintf` 和 `_cwprintf` 在輸出時皆不會轉譯換行字元為托架傳回行摘要 \(CR\-LF\) 組合。  
  
 重要區別是 `_cwprintf` 在其用於Windows NT時顯示 Unicode 字元。  不同於 `_cprintf`， `_cwprintf` 表示使用目前控制台中的地區設定。  
  
 這些以 `_l` 後綴的函式版本除了使用傳入的地區設定以外行為相同。  
  
 `_cprintf`驗證`format`參數。  如果 `format`為 null 指標，則函式叫用無效參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，函式會傳回 \-1 並將 `errno` 設定為 `EINVAL`。  
  
> [!IMPORTANT]
>  確認 `format` 不是使用者定義的字串。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_tcprintf`|`_cprintf`|`_cprintf`|`_cwprintf`|  
|`_tcprintf_l`|`_cprintf_l`|`_cprintf_l`|`_cwprintf_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_cprintf`,`_cprintf_l`|\<conio.h\>|  
|`_cwprintf`, `_cwprintf_l`|\<conio.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
  **\-16 001d 62511 A Test**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [主控台和連接埠 I\/O](../../c-runtime-library/console-and-port-i-o.md)   
 [\_cscanf、\_cscanf\_l、\_cwscanf、\_cwscanf\_l](../../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md)   
 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [vfprintf、\_vfprintf\_l、vfwprintf、\_vfwprintf\_l](../../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)   
 [\_cprintf\_s、\_cprintf\_s\_l、\_cwprintf\_s、\_cwprintf\_s\_l](../../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)   
 [\_cprintf\_p、\_cprintf\_p\_l、\_cwprintf\_p、\_cwprintf\_p\_l](../../c-runtime-library/reference/cprintf-p-cprintf-p-l-cwprintf-p-cwprintf-p-l.md)   
 [格式規格語法：printf 和 wprintf 函式](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)