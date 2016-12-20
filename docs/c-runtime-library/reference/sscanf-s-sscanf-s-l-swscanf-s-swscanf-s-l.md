---
title: "sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_sscanf_s_l"
  - "sscanf_s"
  - "_swscanf_s_l"
  - "swscanf_s"
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
  - "_stscanf_s"
  - "sscanf_s"
  - "swscanf_s"
  - "_swscanf_s_l"
  - "_stscanf_s_l"
  - "_sscanf_s_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_sscanf_s_l 函式"
  - "_stscanf_s 函式"
  - "_stscanf_s_l 函式"
  - "_swscanf_s_l 函式"
  - "讀取資料, 字串"
  - "sscanf_s 函式"
  - "sscanf_s_l 函式"
  - "字串 [C++], 讀取"
  - "字串 [C++], 讀取資料來源"
  - "stscanf_s 函式"
  - "stscanf_s_l 函式"
  - "swscanf_s 函式"
  - "swscanf_s_l 函式"
ms.assetid: 956e65c8-00a5-43e8-a2f2-0f547ac9e56c
caps.latest.revision: 30
caps.handback.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

讀取格式化的資料來源的字串。 這些版本 [sscanf、\_sscanf\_l、swscanf、\_swscanf\_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md) 中所述，具有安全性增強功能， [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)。  
  
## 語法  
  
```  
int sscanf_s(  
   const char *buffer,  
   const char *format [,  
   argument ] ...  
);  
int _sscanf_s_l(  
   const char *buffer,  
   const char *format,  
   locale_t locale [,  
   argument ] ...  
);  
int swscanf_s(  
   const wchar_t *buffer,  
   const wchar_t *format [,  
   argument ] ...  
);  
int _swscanf_s_l(  
   const wchar_t *buffer,  
   const wchar_t *format,  
   locale_t locale [,  
   argument ] ...  
);  
```  
  
#### 參數  
 `buffer`  
 儲存的資料  
  
 `format`  
 格式控制字串。 如需詳細資訊，請參閱[格式規格欄位：scanf 和 wscanf 函式](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)。  
  
 `argument`  
 選擇性引數  
  
 `locale`  
 要使用的地區設定  
  
## 傳回值  
 這些函式會傳回成功轉換並指派的欄位數目傳回值不包含已讀取但未指派的欄位。 傳回值 0 表示未指派任何欄位。 傳回值是 `EOF` 錯誤或如果字串的結尾已到達第一個轉換之前。  
  
 如果 `buffer` 或 `format` 是 `NULL` 指標、 無效參數處理常式叫用時，所述 [參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，則這些函式會傳回 \-1，並將 `errno` 設為 `EINVAL`。  
  
 如需這些錯誤碼及其他錯誤碼的詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `sscanf_s` 函式會將資料從 `buffer` 至的位置由每個提供 `argument`。 格式字串後面的引數指定具有對應至型別規範中的型別變數的指標 `format`。 不同於較不安全版本 `sscanf`, ，緩衝區的大小參數時，需要使用類型欄位字元 `c`, ，`C`, ，`s`, ，`S`, ，或字串中包含的控制項集合 `[]`。 以字元為單位的緩衝區大小必須提供做為額外的參數，後面需要每個緩衝區參數。 例如，如果您讀取到字串，該字串的緩衝區大小傳遞，如下所示︰  
  
 `wchar_t ws[10];`  
  
 `swscanf_s(in_str, L"%9s", ws, (unsigned)_countof(ws)); // buffer size is 10, width specification is 9`  
  
 緩衝區大小包含結束的 null。 若要確保讀取中的權杖將放入緩衝區可用寬度規格欄位。 如果沒有使用寬度規格欄位，則讀取的語彙基元太大而無法納入緩衝區中，並且不會寫入該緩衝區。  
  
 如果是字元，則單一字元可能會以下列方式讀取：  
  
 `wchar_t wc;`  
  
 `swscanf_s(in_str, L"%c", &wc, 1);`  
  
 這個範例會從輸入字串中讀取單一字元，並將其儲存在寬字元緩衝區。 當您讀取多個非 null 終止字串的字元時，不帶正負號的整數做為寬度規格和緩衝區大小。  
  
 `char c[4];`  
  
 `sscanf_s(input, "%4c", &c, (unsigned)_countof(c)); // not null terminated`  
  
 如需詳細資訊，請參閱[scanf\_s、\_scanf\_s\_l、wscanf\_s、\_wscanf\_s\_l](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)與[scanf 類型欄位字元](../../c-runtime-library/scanf-type-field-characters.md)。  
  
> [!NOTE]
>  大小參數為型別 `unsigned`，而非 `size_t`。 64 位元目標編譯時使用靜態轉型轉換 `_countof` 或 `sizeof` 結果，以正確的大小。  
  
 `format` 引數控制項解譯的輸入欄位，並具有相同的形式和功能 `format` 引數 `scanf_s` 函式。 如果在重疊的字串之間進行複製，則行為是未定義的。  
  
 `swscanf_s` 是寬字元版本的 `sscanf_s;` 的引數 `swscanf_s` 是寬字元字串。`sscanf_s` 不會處理多位元組的十六進位字元。`swscanf_s` 不會處理 Unicode 全形十六進位或 「 相容性區 」 字元。 否則 `swscanf_s` 和 `sscanf_s` 的行為相同。  
  
 這些有 `_l` 尾碼的函式版本是一樣的，不同之處在於會使用傳入的地區設定參數，而不使用目前的執行緒地區設定。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_stscanf_s`|`sscanf_s`|`sscanf_s`|`swscanf_s`|  
|`_stscanf_s_l`|`_sscanf_s_l`|`_sscanf_s_l`|`_swscanf_s_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`sscanf_s`、 `_sscanf_s_l`|\<stdio.h\>|  
|`swscanf_s`、 `_swscanf_s_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_sscanf_s.c  
// This program uses sscanf_s to read data items  
// from a string named tokenstring, then displays them.  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   char  tokenstring[] = "15 12 14...";  
   char  s[81];  
   char  c;  
   int   i;  
   float fp;  
  
   // Input various data from tokenstring:  
   // max 80 character string plus NULL terminator  
   sscanf_s( tokenstring, "%s", s, (unsigned)_countof(s) );  
   sscanf_s( tokenstring, "%c", &c, (unsigned)sizeof(char) );  
   sscanf_s( tokenstring, "%d", &i );  
   sscanf_s( tokenstring, "%f", &fp );  
  
   // Output the data read  
   printf_s( "String    = %s\n", s );  
   printf_s( "Character = %c\n", c );  
   printf_s( "Integer:  = %d\n", i );  
   printf_s( "Real:     = %f\n", fp );  
}  
```  
  
```Output  
字串 = 15 個字元 = 1 的整數︰ 實際 = 15: = 15.000000  
```  
  
## .NET Framework 對等用法  
 請參閱 `Parse` 方法，例如 [System::Double::Parse](https://msdn.microsoft.com/en-us/library/system.double.parse.aspx)。  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fscanf、\_fscanf\_l、fwscanf、\_fwscanf\_l](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)   
 [scanf、\_scanf\_l、wscanf、\_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [snprintf、\_snprintf、\_snprintf\_l、\_snwprintf、\_snwprintf\_l](../../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)