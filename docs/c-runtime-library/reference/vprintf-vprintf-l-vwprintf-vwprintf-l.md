---
title: "vprintf、_vprintf_l、vwprintf、_vwprintf_l | Microsoft Docs"
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
  - "vprintf"
  - "_vwprintf_l"
  - "_vprintf_l"
  - "vwprintf"
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
  - "vwprintf"
  - "_vtprintf"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_vprintf_l 函式"
  - "_vtprintf 函式"
  - "_vtprintf_l 函式"
  - "_vwprintf_l 函式"
  - "格式化的文字 [C++]"
  - "vprintf 函式"
  - "vprintf_l 函式"
  - "vtprintf 函式"
  - "vtprintf_l 函式"
  - "vwprintf 函式"
  - "vwprintf_l 函式"
ms.assetid: 44549505-00a0-4fa7-9a85-f2e666f55a38
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# vprintf、_vprintf_l、vwprintf、_vwprintf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用指向一個引數清單的指標輸出格式化的字串。  這些函式已有更安全的版本可用，請參閱 [vprintf\_s、\_vprintf\_s\_l、vwprintf\_s、\_vwprintf\_s\_l](../../c-runtime-library/reference/vprintf-s-vprintf-s-l-vwprintf-s-vwprintf-s-l.md)。  
  
## 語法  
  
```  
int vprintf(  
   const char *format,  
   va_list argptr   
);  
int _vprintf_l(  
   const char *format,  
   locale_t locale,  
   va_list argptr   
);  
int vwprintf(  
   const wchar_t *format,  
   va_list argptr   
);  
int _vwprintf_l(  
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
 `vprintf` 和 `vwprintf` 回傳寫入的字元數，不包含結尾的空字元，或者在輸出發生錯誤時回傳一個負值。  如果 `format` 為 null 指標，或是如果格式字串包含無效的格式化字元，無效的參數會叫用處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，函式回傳 \-1 並將 `errno` 設置為 `EINVAL` 。  
  
 如需有關這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 這些函式都接受指標引數清單，然後格式和寫入 `stdout`的特定資料。  
  
 `vwprintf` 是 `vprintf`的寬字元版本;如果資料流在 ANSI 模式中開啟，則兩個函式的作用完全相同。  `vprintf` 目前不支援輸出到 UNICODE 串流。  
  
 尾碼為 `_l` 的這些函式版本是一樣的，只不過它們使用傳入的地區設定，而不是目前執行緒的地區設定。  
  
> [!IMPORTANT]
>  確認 `format` 不是使用者定義的字串。  如需詳細資訊，請參閱 [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795) 。  請注意偵測到無效的格式字串和錯誤的結果。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_vtprintf`|`vprintf`|`vprintf`|`vwprintf`|  
|`_vtprintf_l`|`_vprintf_l`|`_vprintf_l`|`_vwprintf_l`|  
  
## 需求  
  
|常式|必要的標頭|選擇性的標頭檔|  
|--------|-----------|-------------|  
|`vprintf`, `_vprintf_l`|\<stdio.h\> 和 \<stdarg.h\>|\<varargs.h\>\*|  
|`vwprintf`, `_vwprintf_l`|\<stdio.h\> 或 \<wchar.h\>, 及 \<stdarg.h\>|\<varargs.h\>\*|  
  
 \* 要求 UNIX V 相容性。  
  
 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式不支援主控台。  與主控台關聯的標準資料流控制代碼 \(`stdin`、`stdout` 和 `stderr`\) 必須重新導向，然後 C 執行階段函式才能在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式中使用它們。  如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 [System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx)  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [vprintf 函式](../../c-runtime-library/vprintf-functions.md)   
 [fprintf、\_fprintf\_l、fwprintf、\_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [va\_arg、va\_copy、va\_end、va\_start](../../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md)