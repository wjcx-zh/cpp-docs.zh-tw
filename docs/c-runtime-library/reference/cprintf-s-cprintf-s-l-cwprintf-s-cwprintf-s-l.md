---
title: "_cprintf_s、_cprintf_s_l、_cwprintf_s、_cwprintf_s_l | Microsoft Docs"
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
  - "_cwprintf_s_l"
  - "_cprintf_s_l"
  - "_cprintf_s"
  - "_cwprintf_s"
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
  - "_cwprintf_s_l"
  - "_cprintf_s"
  - "cwprintf_s"
  - "_cprintf_s_l"
  - "cwprintf_s_l"
  - "cprintf_s_l"
  - "_tcprintf_s"
  - "cprintf_s"
  - "_cwprintf_s"
  - "tcprintf_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_cprintf_s 函式"
  - "_cprintf_s_l 函式"
  - "_cwprintf_s 函式"
  - "_cwprintf_s_l 函式"
  - "_tcprintf_s 函式"
  - "_tcprintf_s_l 函式"
  - "cprintf_s 函式"
  - "cprintf_s_l 函式"
  - "cwprintf_s 函式"
  - "cwprintf_s_l 函式"
  - "tcprintf_s 函式"
  - "tcprintf_s_l 函式"
ms.assetid: c28504fe-0d20-4f06-8f97-ee33225922ad
caps.latest.revision: 26
caps.handback.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _cprintf_s、_cprintf_s_l、_cwprintf_s、_cwprintf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

格式化並列印至主控台。  這些 [\_cprintf、\_cprintf\_l、\_cwprintf、\_cwprintf\_l](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md) 版本有安全性增強功能，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int _cprintf_s(   
   const char * format [,   
   argument] ...   
);  
int _cprintf_s_l(   
   const char * format,  
   locale_t locale [,   
   argument] ...   
);  
int _cwprintf_s(  
   const wchar * format [,   
   argument] ...  
);  
int _cwprintf_s_l(  
   const wchar * format,  
   locale_t locale [,   
   argument] ...  
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
 這些`_putch`函式格式化並列印一系列的字元與值直接寫入主控台，並使用 `_putwch` 函式 \( 的`_cwprintf_s` \) 輸出字元。  每個 `argument` \(如果有的話\) 是根據 `format`中的對應格式規格轉換和輸出。  格式有相同的表單和函式，如[printf\_s](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md) 函式的 `format` 參數。  不同於 `fprintf_s`、`printf_s`和 `sprintf_s`這三個函式， `_cprintf_s` 和 `_cwprintf_s` 在輸出時皆不會轉譯換行字元為托架傳回行摘要 \(CR\-LF\) 組合。  
  
 重要區別是 `_cwprintf_s` 在其用於 Windows NT 時顯示 Unicode 字元。  不同於 `_cprintf_s`， `_cwprintf_s` 表示使用目前控制台中的地區  
  
 這些以 `_l` 後綴的函式版本除了使用傳入的地區設定以外行為相同。  
  
> [!IMPORTANT]
>  確認 `format` 不是使用者定義的字串。  
  
 像不安全的版本 \(請參閱 [\_cprintf、\_cprintf\_l、\_cwprintf、\_cwprintf\_l](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)\)，這些函式會驗證它們的參數並叫用無效的參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述，否則，如果 `format` 為 null 指標。  這些函式是不安全的版本不同之處在於格式字串也會驗證。  如果有任何未知或格式錯誤的格式規範，這些函式叫用無效的參數處理常式。  在所有案例中，如果允許繼續執行，這些函式會傳回 \-1 ，並將  `errno`設為`EINVAL` 。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_tcprintf_s`|`_cprintf_s`|`_cprintf_s`|`_cwprintf_s`|  
|`_tcprintf_s_l`|`_cprintf_s_l`|`_cprintf_s_l`|`_cwprintf_s_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_cprintf_s`,`_cprintf_s_l`|\<conio.h\>|  
|`_cwprintf_s`, `_cwprintf_s_l`|\<conio.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
  
```  
// crt_cprintf_s.c  
// compile with: /c  
// This program displays some variables to the console.  
  
#include <conio.h>  
  
int main( void )  
{  
   int      i = -16, h = 29;  
   unsigned u = 62511;  
   char     c = 'A';  
   char     s[] = "Test";  
  
   /* Note that console output does not translate \n as  
    * standard output does. Use \r\n instead.  
    */  
   _cprintf_s( "%d  %.4x  %u  %c %s\r\n", i, h, u, c, s );  
}  
```  
  
## Output  
  
```  
-16  001d  62511  A Test  
```  
  
## 請參閱  
 [主控台和連接埠 I\/O](../../c-runtime-library/console-and-port-i-o.md)   
 [\_cscanf、\_cscanf\_l、\_cwscanf、\_cwscanf\_l](../../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md)   
 [fprintf\_s、\_fprintf\_s\_l、fwprintf\_s、\_fwprintf\_s\_l](../../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)   
 [printf\_s、\_printf\_s\_l、wprintf\_s、\_wprintf\_s\_l](../../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)   
 [sprintf\_s、\_sprintf\_s\_l、swprintf\_s、\_swprintf\_s\_l](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)   
 [vfprintf\_s、\_vfprintf\_s\_l、vfwprintf\_s、\_vfwprintf\_s\_l](../../c-runtime-library/reference/vfprintf-s-vfprintf-s-l-vfwprintf-s-vfwprintf-s-l.md)   
 [格式規格語法：printf 和 wprintf 函式](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)