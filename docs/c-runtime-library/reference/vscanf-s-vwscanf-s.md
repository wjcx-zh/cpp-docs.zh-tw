---
title: "vscanf_s、vwscanf_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "vscanf_s"
  - "vwscanf_s"
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
  - "_vtscanf_s"
  - "vscanf_s"
  - "vwscanf_s"
dev_langs: 
  - "C++"
ms.assetid: 23a1c383-5b01-4887-93ce-534a1e38ed93
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# vscanf_s、vwscanf_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從標準輸入資料流讀取格式化的資料。  這些 [vscanf、vwscanf](../../c-runtime-library/reference/vscanf-vwscanf.md) 版本有安全性增強功能，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## 語法  
  
```  
int vscanf_s(  
   const char *format,  
   va_list arglist  
);   
int vwscanf_s(  
   const wchar_t *format,  
   va_list arglist  
);  
```  
  
#### 參數  
 `format`  
 格式控制字串。  
  
 `arglist`  
 變數引數清單。  
  
## 傳回值  
 傳回成功轉換和指定的欄位數；傳回值不包括讀取但未指定的欄位。  傳回值 0 表示未指定欄位。  如果發生錯誤，或者在第一次嘗試讀取字元時遇到檔案結尾字元或字串結尾字元，傳回值是 `EOF`。  如果 `format` 為 `NULL` 指標，則叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，則 `vscanf_s` 和 `vwscanf_s` 會傳回 `EOF`，並將 `errno` 設定為 `EINVAL`。  
  
 如需有關這些錯誤碼及其他錯誤碼的詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `vscanf_s` 函式會從標準輸入資料流 `stdin` 讀取資料並將資料寫入 `arglist` 引數清單所指定的位置。  清單中的所有引數都必須是變數的指標，這些變數的類型對應至 `format` 的類型規範。  如果在重疊的字串之間執行複製，則行為是未定義的。  
  
 `vwscanf_s` 是 `vscanf_s` 的寬字元版本。 `vwscanf_s` 的 `format` 引數是寬字元字串。  如果資料流是以 ANSI 模式開啟，則 `vwscanf_s` 和 `vscanf_s` 的行為相同。  `vscanf_s` 不支援從 UNICODE 資料流輸入。  
  
 不同於 `vscanf` 和 `vwscanf`，`vscanf_s` 和 `vwscanf_s` 要求類型 `c`、`C`、`s`、`S` 的所有輸入參數或用 `[]` 括住的字串控制項集合，必須指定緩衝區大小。  緩衝區大小 \(以字元為單位\) 當做緩衝區或變數指標後的額外參數傳遞。  `wchar_t` 字串的緩衝區大小 \(以字元為單位\) 不同於大小 \(以位元組為單位\)。  
  
 緩衝區大小包括終止 null。  您可以使用指定寬度欄位確保讀入的語彙基元會符合緩衝區。  如果沒有使用寬度規格欄位，而且讀入的語彙基元太大而無法放入緩衝區中，則沒有任何資料寫入該緩衝區。  
  
> [!NOTE]
>  大小參數的類型是 `unsigned`，不是 `size_t`。  
  
 如需詳細資訊，請參閱[scanf 寬度規格](../../c-runtime-library/scanf-width-specification.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_vtscanf_s`|`vscanf_s`|`vscanf_s`|`vwscanf_s`|  
  
 如需詳細資訊，請參閱[格式規格欄位：scanf 和 wscanf 函式](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`vscanf_s`|\<stdio.h\>|  
|`wscanf_s`|\<stdio.h\> 或 \<wchar.h\>|  
  
 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式不支援主控台。  與主控台關聯的標準資料流控制代碼 \(`stdin`、`stdout` 和 `stderr`\) 必須重新導向，然後 C 執行階段函式才能在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 應用程式中使用它們。  如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_vscanf_s.c  
// compile with: /W3  
// This program uses the vscanf_s and vwscanf_s functions  
// to read formatted input.  
  
#include <stdio.h>  
#include <stdarg.h>  
#include <stdlib.h>  
  
int call_vscanf_s(char *format, ...)  
{  
    int result;  
    va_list arglist;  
    va_start(arglist, format);  
    result = vscanf_s(format, arglist);  
    va_end(arglist);  
    return result;  
}  
  
int call_vwscanf_s(wchar_t *format, ...)  
{  
    int result;  
    va_list arglist;  
    va_start(arglist, format);  
    result = vwscanf_s(format, arglist);  
    va_end(arglist);  
    return result;  
}  
  
int main( void )  
{  
    int   i, result;  
    float fp;  
    char  c, s[81];  
    wchar_t wc, ws[81];  
    result = call_vscanf_s("%d %f %c %C %s %S", &i, &fp, &c, 1,  
                           &wc, 1, s, _countof(s), ws, _countof(ws) );  
    printf( "The number of fields input is %d\n", result );  
    printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c, wc, s, ws);  
    result = call_vwscanf_s(L"%d %f %hc %lc %S %ls", &i, &fp, &c, 2,  
                            &wc, 1, s, _countof(s), ws, _countof(ws) );  
    wprintf( L"The number of fields input is %d\n", result );  
    wprintf( L"The contents are: %d %f %C %c %hs %s\n", i, fp, c, wc, s, ws);  
}  
  
```  
  
 當提供範例輸入給這個程式時，會產生下列輸出：  
  
 `71 98.6 h z Byte characters`  
  
 `36 92.3 y n Wide characters`  
  
  **欄位輸入數目是 6。**  
**The contents are: 71 98.599998 h z Byte characters**  
**欄位輸入數目是 6。**  
**The contents are: 36 92.300003 y n Wide characters**   
## .NET Framework 對等用法  
  
-   [System::Console::Read](https://msdn.microsoft.com/en-us/library/system.console.read.aspx)  
  
-   [System::Console::ReadLine](https://msdn.microsoft.com/en-us/library/system.console.readline.aspx)  
  
-   請參閱 `Parse` 方法，例如 [System::Double::Parse](https://msdn.microsoft.com/en-us/library/system.double.parse.aspx)。  
  
## 請參閱  
 [浮點支援](../../c-runtime-library/floating-point-support.md)   
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [scanf、\_scanf\_l、wscanf、\_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [scanf\_s、\_scanf\_s\_l、wscanf\_s、\_wscanf\_s\_l](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)   
 [vscanf、vwscanf](../../c-runtime-library/reference/vscanf-vwscanf.md)