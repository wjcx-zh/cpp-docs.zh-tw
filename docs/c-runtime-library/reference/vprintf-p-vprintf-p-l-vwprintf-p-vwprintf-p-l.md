---
title: "_vprintf_p、_vprintf_p_l、_vwprintf_p、_vwprintf_p_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_vwprintf_p"
  - "_vprintf_p"
  - "_vprintf_p_l"
  - "_vwprintf_p_l"
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
  - "_vwprintf_p_l"
  - "vprintf_p"
  - "_vprintf_p_l"
  - "_vwprintf_p"
  - "vprintf_p_l"
  - "vwprintf_p_l"
  - "vwprintf_p"
  - "vtprintf_p"
  - "_vtprintf_p"
  - "_vprintf_p"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_vprintf_p 函式"
  - "_vprintf_p_l 函式"
  - "_vtprintf_p 函式"
  - "_vtprintf_p_l 函式"
  - "_vwprintf_p 函式"
  - "_vwprintf_p_l 函式"
  - "格式化的文字 [C++]"
  - "vprintf_p 函式"
  - "vprintf_p_l 函式"
  - "vtprintf_p 函式"
  - "vtprintf_p_l 函式"
  - "vwprintf_p 函式"
  - "vwprintf_p_l 函式"
ms.assetid: 3f99bde3-c891-493d-908f-30559c421058
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _vprintf_p、_vprintf_p_l、_vwprintf_p、_vwprintf_p_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用指標引數的清單寫入格式化輸出，並啟用引數使用命令的規格。  
  
## 語法  
  
```  
int _vprintf_p(  
   const char *format,  
   va_list argptr   
);  
int _vprintf_p_l(  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);  
int _vwprintf_p(  
   const wchar_t *format,  
   va_list argptr   
);  
int _vwprintf_p_l(  
   const wchar_t *format,  
   locale_t locale,  
   va_list argptr   
);  
```  
  
#### 參數  
 `format`  
 格式規範。  
  
 `argptr`  
 參數清單的指標。  
  
 `locale`  
 使用的地區設定。  
  
 如需詳細資訊，請參閱[格式規格](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)。  
  
## 傳回值  
 `_vprintf_p` 和 `_vwprintf_p` 回傳寫入的字元數，不包含結尾的空字元，或者在輸出發生錯誤時回傳一個負值。  
  
## 備註  
 這些函式都接受指標引數清單，然後格式和寫入 `stdout`的特定資料。  這些函式與 `vprintf_s` 和 `vwprintf_s` 的不同在於它們只支援指定引數的命令。  如需詳細資訊，請參閱[printf\_p 位置參數](../../c-runtime-library/printf-p-positional-parameters.md)。  
  
 `_vwprintf_p` 是 `_vprintf_p`的寬字元版本;如果資料流在 ANSI 模式中開啟，則兩個函式的作用完全相同。  `_vprintf_p` 目前不支援輸出到 UNICODE 串流。  
  
 尾碼為 `_l` 的這些函式版本是一樣的，只不過它們使用傳入的地區設定，而不是目前執行緒的地區設定。  
  
> [!IMPORTANT]
>  確認 `format` 不是使用者定義的字串。  如需詳細資訊，請參閱 [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795) 。  
  
 如果 `format` 為 null 指標，或是如果格式字串包含無效的格式化字元，無效的參數會叫用處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，函式回傳 \-1 並將 `errno` 設置為 `EINVAL` 。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_vtprintf_p`|`_vprintf_p`|`_vprintf_p`|`_vwprintf_p`|  
|`_vtprintf_p_l`|`_vprintf_p_l`|`_vprintf_p_l`|`_vwprintf_p_l`|  
  
## 需求  
  
|常式|必要的標頭|選擇性的標頭檔|  
|--------|-----------|-------------|  
|`_vprintf_p`, `_vprintf_p_l`|\<stdio.h\> 和 \<stdarg.h\>|\<varargs.h\>\*|  
|`_vwprintf_p`, `_vwprintf_p_l`|\<stdio.h\> 或 \<wchar.h\>, 及 \<stdarg.h\>|\<varargs.h\>\*|  
  
 \* 要求 UNIX V 相容性。  
  
 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式不支援主控台。  與主控台關聯的標準資料流控制代碼 \(`stdin`、`stdout` 和 `stderr`\) 必須重新導向，然後 C 執行階段函式才能在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式中使用它們。  如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 [System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [vprintf 函式](../../c-runtime-library/vprintf-functions.md)   
 [\_fprintf\_p、\_fprintf\_p\_l、\_fwprintf\_p、\_fwprintf\_p\_l](../../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)   
 [\_printf\_p、\_printf\_p\_l、\_wprintf\_p、\_wprintf\_p\_l](../../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)   
 [\_sprintf\_p、\_sprintf\_p\_l、\_swprintf\_p、\_swprintf\_p\_l](../../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)   
 [vsprintf\_s、\_vsprintf\_s\_l、vswprintf\_s、\_vswprintf\_s\_l](../../c-runtime-library/reference/vsprintf-s-vsprintf-s-l-vswprintf-s-vswprintf-s-l.md)   
 [va\_arg、va\_copy、va\_end、va\_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)   
 [\_vfprintf\_p、\_vfprintf\_p\_l、\_vfwprintf\_p、\_vfwprintf\_p\_l](../../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)   
 [\_printf\_p、\_printf\_p\_l、\_wprintf\_p、\_wprintf\_p\_l](../../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)   
 [printf\_p 位置參數](../../c-runtime-library/printf-p-positional-parameters.md)