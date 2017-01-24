---
title: "sscanf、_sscanf_l、swscanf、_swscanf_l | Microsoft Docs"
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
  - "swscanf"
  - "sscanf"
  - "_sscanf_l"
  - "_swscanf_l"
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
  - "_sscanf_l"
  - "_stscanf"
  - "swscanf"
  - "_stscanf_l"
  - "sscanf"
  - "_swscanf_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_sscanf_l 函式"
  - "_stscanf 函式"
  - "_stscanf_l 函式"
  - "_swscanf_l 函式"
  - "讀取資料, 字串"
  - "sscanf 函式"
  - "sscanf_l 函式"
  - "字串 [C++], 讀取"
  - "字串 [C++], 讀取資料來源"
  - "stscanf 函式"
  - "stscanf_l 函式"
  - "swscanf 函式"
  - "swscanf_l 函式"
ms.assetid: c2dcf0d2-9798-499f-a4a8-06f7e2b9a80c
caps.latest.revision: 26
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# sscanf、_sscanf_l、swscanf、_swscanf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從字串讀取格式化的資料。  這些函式已有更安全的版本可用，請參閱 [sscanf\_s、\_sscanf\_s\_l、swscanf\_s、\_swscanf\_s\_l](../../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)。  
  
## 語法  
  
```  
int sscanf(  
   const char *buffer,  
   const char *format [,  
   argument ] ...   
);  
int _sscanf_l(  
   const char *buffer,  
   const char *format,  
   locale_t locale [,  
   argument ] ...   
);  
int swscanf(  
   const wchar_t *buffer,  
   const wchar_t *format [,  
   argument ] ...   
);  
int _swscanf_l(  
   const wchar_t *buffer,  
   const wchar_t *format,  
   locale_t locale [,  
   argument ] ...   
);  
```  
  
#### 參數  
 `buffer`  
 預存資料  
  
 `format`  
 格式控制字串。  如需詳細資訊，請參閱[格式規格](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)。  
  
 `argument`  
 選擇性引數  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 每個這些函式都會傳回成功轉換和指派的欄位數；傳回值不包括已讀取但未指派的欄位。  傳回值 0 表示未指定欄位。  如果發生錯誤，或者在第一個轉換前就已經到達字串結尾，則傳回值是 `EOF`。  
  
 如果 `buffer` 或 `format` 為 `NULL` 指標，則叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，這些函式會傳回 \-1 並將`errno` 設定為 `EINVAL`。  
  
 如需有關這些錯誤碼和其他錯誤碼的詳細資訊，請參閱 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `sscanf` 函式會將 `buffer` 的資料寫入 `argument`指定的位置。  清單中的所有 `argument` 都必須是變數的指標，這些變數的類型對應至 `format` 的類型規範。  `format` 引數控制輸入欄位的說明，而且表單和函式與 `scanf` `format` 函式的引數相同。  如果在重疊的字串之間執行複製，則行為是未定義的。  
  
> [!IMPORTANT]
>  當您使用 `sscanf` 讀取字串時，通常要為 `%s` 格式指定寬度 \(例如 `"%32s"` 而不是`"%s"`\)；否則，格式化不適當的輸入可能容易造成緩衝區滿溢。  
  
 `swscanf` 是 `sscanf` 的寬字元版本；`swscanf` 的引數是寬字元字串。  `sscanf` 不會處理多位元組十六位元字元。  `swscanf` 不會處理 Unicode 全形十六位元或「相容性區域」字元。  否則 `swscanf` 和 `sscanf` 的行為相同。  
  
 這些有 `_l` 尾碼的函式版本是一樣的，不同之處在於會使用傳入的地區設定，而不使用目前的執行緒地區設定。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE & \_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_stscanf`|`sscanf`|`sscanf`|`swscanf`|  
|`_stscanf_l`|`_sscanf_l`|`_sscanf_l`|`_swscanf_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`sscanf`, `_sscanf_l`|\<stdio.h\>|  
|`swscanf`, `_swscanf_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_sscanf.c  
// compile with: /W3  
// This program uses sscanf to read data items  
// from a string named tokenstring, then displays them.  
  
#include <stdio.h>  
  
int main( void )  
{  
   char  tokenstring[] = "15 12 14...";  
   char  s[81];  
   char  c;  
   int   i;  
   float fp;  
  
   // Input various data from tokenstring:  
   // max 80 character string:  
   sscanf( tokenstring, "%80s", s ); // C4996  
   sscanf( tokenstring, "%c", &c );  // C4996  
   sscanf( tokenstring, "%d", &i );  // C4996  
   sscanf( tokenstring, "%f", &fp ); // C4996  
   // Note: sscanf is deprecated; consider using sscanf_s instead  
  
   // Output the data read  
   printf( "String    = %s\n", s );  
   printf( "Character = %c\n", c );  
   printf( "Integer:  = %d\n", i );  
   printf( "Real:     = %f\n", fp );  
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
 [fscanf、\_fscanf\_l、fwscanf、\_fwscanf\_l](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)   
 [scanf、\_scanf\_l、wscanf、\_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [snprintf、\_snprintf、\_snprintf\_l、\_snwprintf、\_snwprintf\_l](../../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)