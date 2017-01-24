---
title: "vsscanf、vswscanf | Microsoft Docs"
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
  - "vsscanf"
  - "vswscanf"
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
  - "_vstscanf"
  - "vsscanf"
  - "vswscanf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "vsscanf 函式"
  - "vswscanf 函式"
ms.assetid: e96180f2-df46-423d-b4eb-0a49ab819bde
caps.latest.revision: 9
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# vsscanf、vswscanf
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從字串讀取格式化的資料。  更多這些函式的可用安全版本，請參閱 [vsscanf\_s、vswscanf\_s](../../c-runtime-library/reference/vsscanf-s-vswscanf-s.md)。  
  
## 語法  
  
```  
int vsscanf(  
   const char *buffer,  
   const char *format,  
   va_list arglist  
);  
int vswscanf(  
   const wchar_t *buffer,  
   const wchar_t *format,  
   va_list arglist  
);  
```  
  
#### 參數  
 `buffer`  
 預存資料  
  
 `format`  
 格式控制字串。  如需詳細資訊，請參閱[格式規格欄位：scanf 和 wscanf 函式](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)。  
  
 `arglist`  
 變數引數清單。  
  
## 傳回值  
 每個這些函式都會傳回成功轉換和指派的欄位數；傳回值不包括已讀取但未指派的欄位。  傳回值 0 表示未指定欄位。  如果發生錯誤，或者在第一個轉換前就已經到達字串結尾，則傳回值是 `EOF`。  
  
 如果 `buffer` 或 `format` 為 `NULL` 指標，則叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，這些函式會傳回 \-1 並將`errno` 設定為 `EINVAL`。  
  
 如需有關這些錯誤碼及其他錯誤碼的詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `vsscanf` 函式會將 `buffer` 的資料讀取到 `arglist` 引數清單中的每個引數所指定的位置。  清單中的所有引數都必須是變數的指標，這些變數的類型對應至 `format` 的類型規範。  `format` 引數控制輸入欄位的說明，而且表單和函式與 `scanf` `format` 函式的引數相同。  如果在重疊的字串之間執行複製，則行為是未定義的。  
  
> [!IMPORTANT]
>  當您使用 `vsscanf` 讀取字串時，為 `%s` 格式永遠指定寬度 \(例如 `"%32s"` 而不是`"%s"`\);否則，格式化不正確的輸入可能會造成緩衝區滿溢。  
  
 `vswscanf` 是 `vsscanf` 的寬字元版本，`vswscanf` 的引數是寬字元字串。  `vsscanf` 不會處理多位元組十六位元字元。  `vswscanf` 不會處理 Unicode 全形十六位元或「相容性區域」字元。  否則 `vswscanf` 和 `vsscanf` 的行為相同。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_vstscanf`|`vsscanf`|`vsscanf`|`vswscanf`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`vsscanf`|\<stdio.h\>|  
|`vswscanf`|\<stdio.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_vsscanf.c  
// compile with: /W3  
// This program uses vsscanf to read data items  
// from a string named tokenstring, then displays them.  
  
#include <stdio.h>  
#include <stdarg.h>  
  
int call_vsscanf(char *tokenstring, char *format, ...)  
{  
    int result;  
    va_list arglist;  
    va_start(arglist, format);  
    result = vsscanf(tokenstring, format, arglist);  
    va_end(arglist);  
    return result;  
}  
  
int main( void )  
{  
    char  tokenstring[] = "15 12 14...";  
    char  s[81];  
    char  c;  
    int   i;  
    float fp;  
  
    // Input various data from tokenstring:  
    // max 80 character string:  
    call_vsscanf(tokenstring, "%80s", s);  
    call_vsscanf(tokenstring, "%c", &c);  
    call_vsscanf(tokenstring, "%d", &i);  
    call_vsscanf(tokenstring, "%f", &fp);  
  
    // Output the data read  
    printf("String    = %s\n", s);  
    printf("Character = %c\n", c);  
    printf("Integer:  = %d\n", i);  
    printf("Real:     = %f\n", fp);  
}  
```  
  
  **字串    \= 15**  
**字元 \= 1**  
**整數：\= 15**  
**Real:     \= 15.000000**   
## .NET Framework 對等用法  
 請參閱 `Parse` 方法，例如 [System::Double::Parse](https://msdn.microsoft.com/en-us/library/system.double.parse.aspx)。  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [scanf、\_scanf\_l、wscanf、\_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf、\_sscanf\_l、swscanf、\_swscanf\_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [vsscanf\_s、vswscanf\_s](../../c-runtime-library/reference/vsscanf-s-vswscanf-s.md)