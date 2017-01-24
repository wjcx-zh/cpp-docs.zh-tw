---
title: "vfscanf_s、vfwscanf_s | Microsoft Docs"
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
  - "vfscanf_s"
  - "vfwscanf_s"
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
  - "vfscanf_s"
  - "vfwscanf_s"
  - "_vftscanf_s"
dev_langs: 
  - "C++"
  - "C"
ms.assetid: 9b0133f0-9a18-4581-b24b-3b72683ad432
caps.latest.revision: 6
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# vfscanf_s、vfwscanf_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

從資料流讀取格式化的資料。  這些 vfscanf, vfwscanf 版本有安全性增強功能，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md) 中所述。  
  
## 語法  
  
```  
int vfscanf_s(   
   FILE *stream,  
   const char *format,  
   va_list arglist  
);  
int vfwscanf_s(   
   FILE *stream,  
   const wchar_t *format,  
   va_list arglist  
);  
  
```  
  
#### 參數  
 `stream`  
 指向 `FILE` 結構的指標。  
  
 `format`  
 格式控制字串。  
  
 `arglist`  
 變數引數清單。  
  
## 傳回值  
 每個這些函式都會傳回成功轉換和指派的欄位數；傳回值不包括已讀取但未指派的欄位。  傳回值 0 表示未指定欄位。  如果發生錯誤，或者在第一個轉換前就已經到達檔案檔案資料流結尾，則傳回值會是 `vfscanf_s` 和 `vfwscanf_s` 的 `EOF`。  
  
 這些函式會驗證它們的參數。  如果 `stream` 是無效的檔案指標，或者 `format` 是 null 指標，這些函式叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，這些函式會傳回 `EOF`，並將 `errno` 設為 `EINVAL`。  
  
## 備註  
 `vfscanf_s` 函式會將 `stream` 目前位置的資料讀取到 `arglist` 引數清單 \(如果有\) 所指定的位置。  清單中的所有引數都必須是變數的指標，這些變數的類型對應至 `format` 的類型規範。  `format` 控制輸入欄位的解譯，其與 `scanf_s` 的 `format` 引數有相同的形式和運作方式。如需 `format` 的描述，請參閱 [格式規格欄位：scanf 和 wscanf 函式](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)。  `vfwscanf_s` 是 `vfscanf_s` 的寬字元版本。 `vfwscanf_s` 的格式引數是寬字元字串。  如果資料流是以 ANSI 模式開啟，則這些函式的行為相同。  `vfscanf_s` 目前不支援從 UNICODE 資料流輸入。  
  
 更安全的函式 \(具有 `_s` 後置字元\) 和其他版本之間的主要差異在於，更安全的函式需要每個 `c`、`C`、`s`、`S` 和 `[` 類型欄位的大小 \(以字元為單位\)，當做變數之後的引數傳遞。  如需詳細資訊，請參閱[scanf\_s、\_scanf\_s\_l、wscanf\_s、\_wscanf\_s\_l](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)與[scanf 寬度規格](../../c-runtime-library/scanf-width-specification.md)。  
  
> [!NOTE]
>  大小參數的類型是 `unsigned`，不是 `size_t`。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_vftscanf_s`|`vfscanf_s`|`vfscanf_s`|`vfwscanf_s`|  
  
## 需求  
  
|Function|必要的標頭|  
|--------------|-----------|  
|`vfscanf_s`|\<stdio.h\>|  
|`vfwscanf_s`|\<stdio.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_vfscanf_s.c  
// compile with: /W3  
// This program writes formatted  
// data to a file. It then uses vfscanf_s to  
// read the various data back from the file.  
  
#include <stdio.h>  
#include <stdarg.h>  
#include <stdlib.h>  
  
FILE *stream;  
  
int call_vfscanf_s(FILE * istream, char * format, ...)  
{  
    int result;  
    va_list arglist;  
    va_start(arglist, format);  
    result = vfscanf_s(istream, format, arglist);  
    va_end(arglist);  
    return result;  
}  
  
int main(void)  
{  
    long l;  
    float fp;  
    char s[81];  
    char c;  
  
    if (fopen_s(&stream, "vfscanf_s.out", "w+") != 0)  
    {  
        printf("The file vfscanf_s.out was not opened\n");  
    }  
    else  
    {  
        fprintf(stream, "%s %ld %f%c", "a-string",  
            65000, 3.14159, 'x');  
        // Security caution!  
        // Beware loading data from a file without confirming its size,  
        // as it may lead to a buffer overrun situation.  
  
        // Set pointer to beginning of file:  
        fseek(stream, 0L, SEEK_SET);  
  
        // Read data back from file:  
        call_vfscanf_s(stream, "%s %ld %f%c", s, _countof(s), &l, &fp, &c, 1);  
  
        // Output data read:   
        printf("%s\n", s);  
        printf("%ld\n", l);  
        printf("%f\n", fp);  
        printf("%c\n", c);  
  
        fclose(stream);  
    }  
}  
  
```  
  
  **a\-string**  
**65000**  
**3.141590**  
**x**   
## .NET Framework 對等用法  
 [System::IO::StreamReader::ReadLine](https://msdn.microsoft.com/en-us/library/system.io.streamreader.readline.aspx).請參閱 `Parse` 方法，例如 [System::Double::Parse](https://msdn.microsoft.com/en-us/library/system.double.parse.aspx)。  
  
## 請參閱  
 [資料流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [\_cscanf\_s、\_cscanf\_s\_l、\_cwscanf\_s、\_cwscanf\_s\_l](../../c-runtime-library/reference/cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)   
 [fprintf\_s、\_fprintf\_s\_l、fwprintf\_s、\_fwprintf\_s\_l](../../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)   
 [scanf\_s、\_scanf\_s\_l、wscanf\_s、\_wscanf\_s\_l](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)   
 [sscanf\_s、\_sscanf\_s\_l、swscanf\_s、\_swscanf\_s\_l](../../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)   
 [fscanf、\_fscanf\_l、fwscanf、\_fwscanf\_l](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)   
 [vfscanf、vfwscanf](../../c-runtime-library/reference/vfscanf-vfwscanf.md)