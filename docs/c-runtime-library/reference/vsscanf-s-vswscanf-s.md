---
title: "vsscanf_s、vswscanf_s | Microsoft Docs"
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
  - "vswscanf_s"
  - "vsscanf_s"
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
  - "vsscanf_s"
  - "vswscanf_s"
  - "_vstscanf_s"
dev_langs: 
  - "C++"
ms.assetid: 7b732e68-c6f4-4579-8917-122f5a7876e1
caps.latest.revision: 6
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# vsscanf_s、vswscanf_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從字串讀取格式化的資料。  這些 [vsscanf、vswscanf](../../c-runtime-library/reference/vsscanf-vswscanf.md) 版本有安全性增強功能，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
## 語法  
  
```  
int vsscanf_s(  
   const char *buffer,  
   const char *format,  
   va_list argptr  
);   
int vswscanf_s(  
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
  
 如果 `buffer` 或 `format` 為 `NULL` 指標，則叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，這些函式會傳回 \-1 並將`errno` 設定為 `EINVAL`  
  
 如需有關這些錯誤碼及其他錯誤碼的詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `vsscanf_s` 函式會將 `buffer` 的資料讀取到 `arglist` 引數清單中的每個引數所指定的位置。  引數清單中的引數會指定變數的指標，這些變數的類型對應至 `format` 的類型規範。  不同於較不安全版本 `vsscanf`，當您使用類型欄位字元 `c`、`C`、`s`、`S` 或用 `[]` 括住的字串控制項集合時，需要緩衝區大小參數。  緩衝區大小 \(以字元為單位\) 必須當做在需要它的每個緩衝區參數之後的額外參數提供。  
  
 緩衝區大小包括終止 null。  寬度規格欄位可用來確保讀入的語彙基元會放入緩衝區。  如果沒有使用寬度規格欄位，而且讀入的語彙基元太大而無法放入緩衝區中，則沒有任何資料寫入該緩衝區。  
  
 如需詳細資訊，請參閱[scanf\_s、\_scanf\_s\_l、wscanf\_s、\_wscanf\_s\_l](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)與[scanf 類型欄位字元](../../c-runtime-library/scanf-type-field-characters.md)。  
  
> [!NOTE]
>  大小參數的類型是 `unsigned`，不是 `size_t`。  
  
 `format` 引數控制輸入欄位的解譯，而且在形式和功能上與 `scanf_s` 函式的 `format` 引數相同。  如果在重疊的字串之間執行複製，則行為是未定義的。  
  
 `vswscanf_s` 是 `vsscanf_s` 的寬字元版本，`vswscanf_s` 的引數是寬字元字串。  `vsscanf_s` 不會處理多位元組十六位元字元。  `vswscanf_s` 不會處理 Unicode 全形十六位元或「相容性區域」字元。  否則 `vswscanf_s` 和 `vsscanf_s` 的行為相同。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_vstscanf_s`|`vsscanf_s`|`vsscanf_s`|`vswscanf_s`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`vsscanf_s`|\<stdio.h\>|  
|`vswscanf_s`|\<stdio.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_vsscanf_s.c  
// compile with: /W3  
// This program uses vsscanf_s to read data items  
// from a string named tokenstring, then displays them.  
  
#include <stdio.h>  
#include <stdarg.h>  
#include <stdlib.h>  
  
int call_vsscanf_s(char *tokenstring, char *format, ...)  
{  
    int result;  
    va_list arglist;  
    va_start(arglist, format);  
    result = vsscanf_s(tokenstring, format, arglist);  
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
    call_vsscanf_s(tokenstring, "%80s", s, _countof(s));  
    call_vsscanf_s(tokenstring, "%c", &c, sizeof(char));  
    call_vsscanf_s(tokenstring, "%d", &i);  
    call_vsscanf_s(tokenstring, "%f", &fp);  
  
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
 [sscanf\_s、\_sscanf\_s\_l、swscanf\_s、\_swscanf\_s\_l](../../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [vsscanf、vswscanf](../../c-runtime-library/reference/vsscanf-vswscanf.md)