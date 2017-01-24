---
title: "strtok_s、_strtok_s_l、wcstok_s、_wcstok_s_l、_mbstok_s、_mbstok_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wcstok_s_l"
  - "_mbstok_s_l"
  - "_mbstok_s"
  - "strtok_s"
  - "wcstok_s"
  - "_strtok_s_l"
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
  - "api-ms-win-crt-multibyte-l1-1-0.dll"
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_tcstok_s_l"
  - "_wcstok_s_l"
  - "_tcstok_s"
  - "_mbstok_s_l"
  - "strtok_s"
  - "wcstok_s"
  - "_mbstok_s"
  - "_strtok_s_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbstok_s 函式"
  - "_mbstok_s_l 函式"
  - "_strtok_s_l 函式"
  - "_tcstok_s 函式"
  - "_tcstok_s_l 函式"
  - "_wcstok_s_l 函式"
  - "mbstok_s 函式"
  - "mbstok_s_l 函式"
  - "字串 [C++], 搜尋"
  - "strtok_s 函式"
  - "strtok_s_l 函式"
  - "語彙基元, 在字串中尋找"
  - "wcstok_s 函式"
  - "wcstok_s_l 函式"
ms.assetid: 7696c972-f83b-4617-8c82-95973e9fdb46
caps.latest.revision: 28
caps.handback.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strtok_s、_strtok_s_l、wcstok_s、_wcstok_s_l、_mbstok_s、_mbstok_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用目前的地區設定或傳遞的地區設定尋找字串中的下一個語彙基元。  這些 [strtok、\_strtok\_l、wcstok、\_wcstok\_l、\_mbstok、\_mbstok\_l](../../c-runtime-library/reference/strtok-strtok-l-wcstok-wcstok-l-mbstok-mbstok-l.md) 版本有安全性增強功能，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
> [!IMPORTANT]
>  `_mbstok_s` and `_mbstok_s_l`不能用於在 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
  
      char *strtok_s(  
char *strToken,  
const char *strDelimit,  
   char **context  
);  
char *_strtok_s_l(  
char *strToken,  
const char *strDelimit,  
   char **context,  
_locale_tlocale  
);  
wchar_t *wcstok_s(  
wchar_t *strToken,  
const wchar_t *strDelimit,   
   wchar_t**context  
);  
wchar_t *_wcstok_s_l(  
wchar_t *strToken,  
const wchar_t *strDelimit,   
   wchar_t**context,  
_locale_tlocale  
);  
unsigned char *_mbstok_s(  
unsigned char*strToken,  
const unsigned char *strDelimit,   
   char **context  
);  
unsigned char *_mbstok_s(  
unsigned char*strToken,  
const unsigned char *strDelimit,   
   char **context,  
_locale_tlocale  
);  
```  
  
#### 參數  
 `strToken`  
 包含一個或多個語彙基元的字串。  
  
 `strDelimit`  
 分隔符號字元集。  
  
 `context`  
 用來儲存呼叫 `strtok_s` 之間的位置資訊。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 傳回在 `strToken` 中的下一個語彙基元之指標。  當找不到其他語彙基元時，會傳回 `NULL`。  每個呼叫會藉由將傳回的語彙基元之後第一個分隔符號取代為 `NULL` 字元來修改 `strToken`。  
  
### 錯誤狀況  
  
|`strToken`|`strDelimit`|`context`|傳回值|`errno`|  
|----------------|------------------|---------------|---------|-------------|  
|`NULL`|any|為 null 指標的指標。|`NULL`|`EINVAL`|  
|any|`NULL`|any|`NULL`|`EINVAL`|  
|any|any|`NULL`|`NULL`|`EINVAL`|  
  
 如果 `strToken` 是 `NULL` ，但是內容是指向有效的內容指標，則沒有任何錯誤。  
  
## 備註  
 `strtok_s` 函式會找到在 `strToken` 的下一個語彙基元。  `strDelimit` 中的字元集指定在目前呼叫中的 `strToken` 中找到的語彙基元之可能的分隔符號。  `wcstok_s` 和 `_mbstok_s`**是**`strtok_s`的寬字元和多位元組字元版本。  `wcstok_s` 和 `_wcstok_s_l` 的引數和傳回值是寬字元字串，而 `_mbstok_s` 和 `_mbstok_s_l` 的引數和傳回值則是多位元組字元字串。  這三個函式其餘部分的運作相同。  
  
 這個函式會驗證它的參數。  當如發生錯誤狀況表格中的錯誤條件發生時，無效的參數處理常式會被呼叫，如 [參數驗證](../../c-runtime-library/parameter-validation.md)中所述。  如果允許繼續執行，這些函式會將 `errno` 設定為 `EINVAL` 並傳回 `NULL`。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE & \_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcstok_s`|`strtok_s`|`_mbstok_s`|`wcstok_s`|  
|`_tcstok_s_l`|`_strtok_s_l`|`_mbstok_s_l`|`_wcstok_s_l`|  
  
 在對 `strtok_s` 的第一次呼叫時，函式會略過前置分隔符號並傳回指向 `strToken` 的第一個以空字元結尾之語彙基元的指標。  多個語彙基元可以藉由一系列的呼叫 `strtok_s` 從 `strToken` 的剩餘項目中跳脫。  對 `strtok_s` 的每個呼叫都會透過在該呼叫傳回的語彙基元之後插入 null 字元修改 `strToken`。  `context` 指標記錄哪個字串正在被讀取及下一個語彙基元要讀取的地方。  要讀取 `strToken`的下一個語彙基元，請搭配 `NULL` 值作為`strToken` 的引數呼叫 `strtok_s` 的，並傳遞相同的 `context` 參數。  `NULL` `strToken` 引數會造成 `strtok_s` 搜尋已修改的 `strToken` 中的下一個語彙基元。  `strDelimit` 引數可以接受來自一個和下一個呼叫的任何值，因此分隔符號集可能會變更。  
  
 `context` 參數替換用於 `strtok` 和 `_strtok_l`的靜態緩衝區，因此在相同執行緒同時分析兩個字串是可能的。  
  
 輸出值受地區設定的`LC_CTYPE` 分類設定所影響。如需詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 。  這些函式沒有以 `_l` 後綴的版本在這些地區相依的行為上使用目前的地區設定，而以 `_l` 後綴版本除了它們會使用傳入的地區設定參數之外運作相同。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`strtok_s`|\<string.h\>|  
|`_strtok_s_l`|\<string.h\>|  
|`wcstok_s,`<br /><br /> `_wcstok_s_l`|\<string.h\> 或 \<wchar.h\>|  
|`_mbstok_s,`<br /><br /> `_mbstok_s_l`|\<mbstring.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_strtok_s.c  
// In this program, a loop uses strtok_s  
// to print all the tokens (separated by commas  
// or blanks) in two strings at the same time.  
//  
  
#include <string.h>  
#include <stdio.h>  
  
char string1[] =  
    "A string\tof ,,tokens\nand some  more tokens";  
char string2[] =  
    "Another string\n\tparsed at the same time.";  
char seps[]   = " ,\t\n";  
char *token1 = NULL;  
char *token2 = NULL;  
char *next_token1 = NULL;  
char *next_token2 = NULL;  
  
int main( void )  
{  
    printf( "Tokens:\n" );  
  
    // Establish string and get the first token:  
    token1 = strtok_s( string1, seps, &next_token1);  
    token2 = strtok_s ( string2, seps, &next_token2);  
  
    // While there are tokens in "string1" or "string2"  
    while ((token1 != NULL) || (token2 != NULL))  
    {  
        // Get next token:  
        if (token1 != NULL)  
        {  
            printf( " %s\n", token1 );  
            token1 = strtok_s( NULL, seps, &next_token1);  
        }  
        if (token2 != NULL)  
        {  
            printf("        %s\n", token2 );  
            token2 = strtok_s (NULL, seps, &next_token2);  
        }  
    }  
}  
```  
  
  **Tokens：**  
 **A**  
 **另一個**  
 **string**  
 **string**  
 **of**  
 **解析**  
 **tokens**  
 **at**  
 **和**  
 **的連接以便**  
 **some**  
 **same**  
 **more**  
 **時間的多個數列。**  
 **tokens**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strcspn、wcscspn、\_mbscspn、\_mbscspn\_l](../../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)   
 [strspn、wcsspn、\_mbsspn、\_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)