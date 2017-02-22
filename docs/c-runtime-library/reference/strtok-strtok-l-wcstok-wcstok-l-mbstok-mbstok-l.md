---
title: "strtok、_strtok_l、wcstok、_wcstok_l、_mbstok、_mbstok_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbstok_l"
  - "_mbstok"
  - "wcstok"
  - "_mbstok"
  - "strtok"
  - "_wcstok_l"
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
  - "_mbstok"
  - "strtok"
  - "_tcstok"
  - "wcstok"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbstok 函式"
  - "_mbstok_l 函式"
  - "_strtok_l 函式"
  - "_tcstok 函式"
  - "_tcstok_l 函式"
  - "_wcstok_l 函式"
  - "mbstok 函式"
  - "mbstok_l 函式"
  - "字串 [C++], 搜尋"
  - "strtok 函式"
  - "strtok_l 函式"
  - "tcstok 函式"
  - "tcstok_l 函式"
  - "語彙基元, 在字串中尋找"
  - "wcstok 函式"
  - "wcstok_l 函式"
ms.assetid: 904cb734-f0d7-4d77-ba81-4791ddf461ae
caps.latest.revision: 34
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 34
---
# strtok、_strtok_l、wcstok、_wcstok_l、_mbstok、_mbstok_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用目前位置或傳遞進來的指定位置，找到字串的下一個語彙基元。  更多這些函式的可用安全版本，請參閱 [strtok\_s、\_strtok\_s\_l、wcstok\_s、\_wcstok\_s\_l、\_mbstok\_s、\_mbstok\_s\_l](../../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md)。  
  
> [!IMPORTANT]
>  `_mbstok` 和 `_mbstok_l` 不能用於在 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
char *strtok(  
   char *strToken,  
   const char *strDelimit   
);  
wchar_t *wcstok(  
   wchar_t *strToken,  
   const wchar_t *strDelimit   
);  
unsigned char *_mbstok(  
   unsigned char*strToken,  
   const unsigned char *strDelimit   
);  
unsigned char *_mbstok(  
   unsigned char*strToken,  
   const unsigned char *strDelimit,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `strToken`  
 包含一個或多個語彙基元的字串。  
  
 `strDelimit`  
 分隔符號字元集。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 傳回在 `strToken` 中的下一個語彙基元之指標。  當找不到其他語彙基元時，會傳回 `NULL`。  每個呼叫會藉由將傳回的語彙基元之後第一個分隔符號取代為 `NULL` 字元來修改 `strToken`。  
  
## 備註  
 `strtok` 函式會找到在 `strToken` 的下一個語彙基元。  `strDelimit` 中的字元集指定在目前呼叫中的 `strToken` 中找到的語彙基元之可能的分隔符號。  `wcstok` 和 `_mbstok` 是 `strtok` 的寬字元和多位元組字元版本。  `wcstok` 的引數和傳回值是寬字元字串，而 `_mbstok` 的引數和傳回值則是多位元組字元字串。  這三個函式其餘部分的運作相同。  
  
> [!IMPORTANT]
>  這些函式有導致緩衝區溢位問題的潛在威脅。  緩衝區溢位問題是系統攻擊的常見方法，它會導致權限不確定性的增加。  如需詳細資訊，請參閱 [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795) 。  
  
 在對 `strtok` 的第一次呼叫時，函式會略過前置分隔符號並傳回指向 `strToken` 的第一個以空字元結尾之語彙基元的指標。  多個語彙基元可以藉由一系列的呼叫 `strtok` 從 `strToken` 的剩餘項目中跳脫。  對 `strtok` 的每個呼叫都會透過在該呼叫傳回的 `token` 之後插入 null 字元來修改 `strToken` 。  要讀取 `strToken`的下一個語彙基元，請搭配 `NULL` 值為 `strToken` 引數呼叫 `strtok`。  `NULL` `strToken` 引數會造成 `strtok` 搜尋已修改的 `strToken` 中的下一個語彙基元。  `strDelimit` 引數可以接受來自一個和下一個呼叫的任何值，因此分隔符號集可能會變更。  
  
 輸出值受地區設定的`LC_CTYPE` 分類設定所影響。如需詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 。  這些函式沒有以 `_l` 後綴的版本在這些地區相依的行為上使用目前的地區設定，而以 `_l` 後綴版本除了它們會使用傳入的地區設定參數之外運作相同。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
> [!NOTE]
>  每個函式為剖析字串成語彙基元，使用執行緒區域靜態變數。  因此，多個執行緒可以同時呼叫這些函式，且沒有不想要的影響。  不過，在單一執行緒內容，交錯呼叫這些函式之一很可能會導致資料損毀和不正確的結果。  當剖析不同字串時，請先完成剖析一個字串在開始下一個剖析。  此外，從另一個函式呼叫的迴圈內呼叫這些函式之一時，請注意潛在的危險，。  如果另一個函式使用這些函式之一作為結束，呼叫的交錯順序會造成、觸發資料毀損。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcstok`|`strtok`|`_mbstok`|`wcstok`|  
|`_tcstok`|`_strtok_l`|`_mbstok_l`|`_wcstok_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`strtok`|\<string.h\>|  
|`wcstok`|\<string.h\> 或 \<wchar.h\>|  
|`_mbstok`, `_mbstok_l`|\<mbstring.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_strtok.c  
// compile with: /W3  
// In this program, a loop uses strtok  
// to print all the tokens (separated by commas  
// or blanks) in the string named "string".  
//  
#include <string.h>  
#include <stdio.h>  
  
char string[] = "A string\tof ,,tokens\nand some  more tokens";  
char seps[]   = " ,\t\n";  
char *token;  
  
int main( void )  
{  
   printf( "Tokens:\n" );  
  
   // Establish string and get the first token:  
   token = strtok( string, seps ); // C4996  
   // Note: strtok is deprecated; consider using strtok_s instead  
   while( token != NULL )  
   {  
      // While there are tokens in "string"  
      printf( " %s\n", token );  
  
      // Get next token:   
      token = strtok( NULL, seps ); // C4996  
   }  
}  
```  
  
  **Tokens：**  
 **A**  
 **string**  
 **of**  
 **tokens**  
 **and**  
 **some**  
 **more**  
 **tokens**   
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [strcspn、wcscspn、\_mbscspn、\_mbscspn\_l](../../c-runtime-library/reference/strcspn-wcscspn-mbscspn-mbscspn-l.md)   
 [strspn、wcsspn、\_mbsspn、\_mbsspn\_l](../../c-runtime-library/reference/strspn-wcsspn-mbsspn-mbsspn-l.md)