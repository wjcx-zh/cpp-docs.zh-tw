---
title: "_cscanf_s、_cscanf_s_l、_cwscanf_s、_cwscanf_s_l | Microsoft Docs"
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
  - "_cwscanf_s_l"
  - "_cwscanf_s"
  - "_cscanf_s"
  - "_cscanf_s_l"
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
  - "cscanf_s"
  - "cscanf_s_l"
  - "cwscanf_s"
  - "_cwscanf_s"
  - "_tcscanf_s"
  - "_cscanf_s"
  - "_cwscanf_s_l"
  - "_cscanf_s_l"
  - "cwscanf_s_l"
  - "_tcscanf_s_l"
  - "tcscanf_s"
  - "tcscanf_s_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_cscanf_s 函式"
  - "_cscanf_s_l 函式"
  - "_cwscanf_s 函式"
  - "_cwscanf_s_l 函式"
  - "_tcscanf_s 函式"
  - "_tcscanf_s_l 函式"
  - "主控台 [C++], 讀取自"
  - "cscanf_s 函式"
  - "cscanf_s_l 函式"
  - "cwscanf_s 函式"
  - "cwscanf_s_l 函式"
  - "資料 [C++], 從主控台讀取"
  - "讀取資料 [C++], 從主控台"
  - "tcscanf_s 函式"
  - "tcscanf_s_l 函式"
ms.assetid: 9ccab74d-916f-42a6-93d8-920525efdf4b
caps.latest.revision: 24
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _cscanf_s、_cscanf_s_l、_cwscanf_s、_cwscanf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從主控台讀取格式化資料。  這些更安全的 [\_cscanf、\_cscanf\_l、\_cwscanf、\_cwscanf\_l](../../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md) 版本有安全性增強功能，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int _cscanf_s(   
   const char *format [,  
   argument] ...   
);  
int _cscanf_s_l(   
   const char *format,  
   locale_t locale [,  
   argument] ...   
);  
int _cwscanf_s(   
   const wchar_t *format [,  
   argument] ...   
);  
int _cwscanf_s_l(   
   const wchar_t *format,  
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
 已成功轉換和指定欄位的數目。  回傳值不包含位指定的欄位。  傳回值是嘗試的 `EOF` 可以讀取檔案的結尾。  當輸入重新導向在作業系統命令列層級時，就會發生。  傳回值 0 表示沒有意義的欄位。  
  
 這些函式會驗證它們的參數。  如果 `format` 或為 null 指標，則這些函示叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，這些函式會傳回 `EOF` 和 `errno` ，並將   設為 `EINVAL`。  
  
## 備註  
 `_cscanf_s` 函式會將資料直接從主控台輸入 `argument`指定的位置。  [\_getche](../../c-runtime-library/reference/getch-getwch.md) 函式用來讀取字元。  所有可選參數都必須是變數的指標，這些變數的類型對應至 `format` 的類型規範。  格式控制輸入字段的解釋和具有相同的形式和功能的`format` 參數為  [scanf\_s](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) 的函式。  當 `_cscanf_s` 通常回應輸入字元時，如果最後一次呼叫是 `_ungetch` 則它不這樣做。  
  
 就像在`scanf` `_cscanf_s` 和 `_cswscanf_s` 家族中的其他安全版本函式中，對型別欄位字元 `c`、 `C`、 `s`、 `S`和 `[` 要求參數大小。  如需詳細資訊，請參閱[scanf 寬度規格](../../c-runtime-library/scanf-width-specification.md)。  
  
> [!NOTE]
>  大小參數的類型是 `unsigned`，不是 `size_t`。  
  
 尾碼為 `_l` 的這些函式版本是一樣的，只不過它們使用傳入的地區設定，而不是目前執行緒的地區設定。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE and \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_tcscanf_s`|`_cscanf_s`|`_cscanf_s`|`_cwscanf_s`|  
|`_tcscanf_s_l`|`_cscanf_s_l`|`_cscanf_s_l`|`_cwscanf_s_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_cscanf_s`,`_cscanf_s_l`|\<conio.h\>|  
|`_cwscanf_s`, `_cwscanf_s_l`|\<conio.h\> 或 \<wchar.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例  
  
```  
// crt_cscanf_s.c  
// compile with: /c  
/* This program prompts for a string  
 * and uses _cscanf_s to read in the response.  
 * Then _cscanf_s returns the number of items  
 * matched, and the program displays that number.  
 */  
  
#include <stdio.h>  
#include <conio.h>  
  
int main( void )  
{  
   int result, n[3];  
   int i;  
  
   result = _cscanf_s( "%i %i %i", &n[0], &n[1], &n[2] );  
   _cprintf_s( "\r\nYou entered " );  
   for( i=0; i<result; i++ )  
      _cprintf_s( "%i ", n[i] );  
   _cprintf_s( "\r\n" );  
}  
```  
  
## 輸入  
  
```  
1 2 3  
```  
  
## Output  
  
```  
You entered 1 2 3  
```  
  
## 請參閱  
 [主控台和連接埠 I\/O](../../c-runtime-library/console-and-port-i-o.md)   
 [\_cprintf、\_cprintf\_l、\_cwprintf、\_cwprintf\_l](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)   
 [fscanf\_s、\_fscanf\_s\_l、fwscanf\_s、\_fwscanf\_s\_l](../../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)   
 [scanf\_s、\_scanf\_s\_l、wscanf\_s、\_wscanf\_s\_l](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)   
 [sscanf\_s、\_sscanf\_s\_l、swscanf\_s、\_swscanf\_s\_l](../../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)