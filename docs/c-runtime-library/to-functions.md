---
title: "to 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr120.dll"
  - "msvcr90.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr80.dll"
  - "msvcr100.dll"
apitype: "DLLExport"
f1_keywords: 
  - "To"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "大小寫, 轉換"
  - "字元, 轉換"
  - "小寫, 轉換字串"
  - "字串轉換, 大小寫"
  - "字串轉換, 到不同字元"
  - "to 函式"
  - "大寫, 轉換字串"
ms.assetid: f636a4c6-8c9f-4be2-baac-064f9dbae300
caps.latest.revision: 13
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# to 函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

任何 **to** 函式及其關聯的巨集中，如果有的話，轉換單一字元至另一個字元。  
  
|||  
|-|-|  
|[\_\_toascii](../c-runtime-library/reference/toascii-toascii.md)|[toupper， \_toupper， towupper](../c-runtime-library/reference/toupper-toupper-towupper-toupper-l-towupper-l.md)|  
|[tolower、\_tolower、towlower](../c-runtime-library/reference/tolower-tolower-towlower-tolower-l-towlower-l.md)||  
  
## 備註  
 **to** 函式和巨集轉換如下。  
  
|常式|巨集|說明|  
|--------|--------|--------|  
|`__toascii`|`__toascii`|將 `c` 轉換成 ASCII 字元|  
|`tolower`|`tolower`|將 `c` 轉換為小寫，如果適當|  
|`_tolower`|`_tolower`|將 `c` 轉換為小寫|  
|`towlower`|無|將 `c` 轉換為對應的寬字元小寫字母|  
|`toupper`|`toupper`|將 `c` 轉換為大寫，如果適當|  
|`_toupper`|`_toupper`|將 `c` 轉換成大寫|  
|`towupper`|無|轉換 c 為對應的寬字元大寫字母。|  
  
 若要使用也定義為巨集的 **to** 常式的函式版本，以 `#undef` 指示詞移除巨集定義或不要包含 CTYPE.H。  如果您使用 \/Za 編譯器選項，編譯器會使用 `toupper` 或 `tolower`函式版本。  `toupper` 和 `tolower` 函式的宣告於 STDLIB.H。  
  
 `__toascii` 常式設定所有，除了低位 7 位元 `c` 為 0，因此，轉換的值表示 ASCII 字元集的字元。  如果 `c` 已經表示 ASCII 字元， `c` 不會變更。  
  
 `tolower` 和 `toupper` 常式:  
  
-   根據目前地區設定的 `LC_CTYPE` 分類 \(`tolower` 呼叫 `isupper` ，而 `toupper` 呼叫 `islower`\)。  
  
-   如果 `c` 在目前地區設定代表適當大小寫而在該地區存在相反情況，請轉換 `c` 。  否則， `c` 不會變更。  
  
 `_tolower` 和 `_toupper` 常式:  
  
-   `tolower` 以及**toupper** 的更快速的版本是與地區設定無關的。  
  
-   只有在 **isascii\(**`c`**\)** 和 **isupper\(**`c`**\)** 或 **islower\(**`c`**\)** 分別為非零值時可以使用。  
  
-   如果 `c` 不是能適當轉換的 ASCII 字母，會導致未定義的結果。  
  
 `towlower` 和 `towupper` 函式會傳回 `c` 的已轉換拷貝，若且唯若以下兩個情況為非零值。  否則， `c` 不會變更。  
  
-   `c` 是適當大小寫的寬字元 \(也就是 `iswupper` 或 **iswlower,** 分別為非零值\)。  
  
-   具有對應目標大小寫的寬字元 \(也就是 `iswlower` 或 **iswupper,** 分別為非零值\)。  
  
## 範例  
  
```  
// crt_toupper.c  
/* This program uses toupper and tolower to  
 * analyze all characters between 0x0 and 0x7F. It also  
 * applies _toupper and _tolower to any code in this  
 * range for which these functions make sense.  
 */  
  
#include <ctype.h>  
#include <string.h>  
  
char msg[] = "Some of THESE letters are Capitals.";  
char *p;  
  
int main( void )  
{  
   printf( "%s\n", msg );  
  
   /* Reverse case of message. */  
   for( p = msg; p < msg + strlen( msg ); p++ )  
   {  
      if( islower( *p ) )  
         putchar( _toupper( *p ) );  
      else if( isupper( *p ) )  
         putchar( _tolower( *p ) );  
      else  
         putchar( *p );  
   }  
}  
```  
  
  **Some of THESE letters are Capitals.**  
**sOME OF these LETTERS ARE cAPITALS.**   
## 請參閱  
 [資料轉換](../c-runtime-library/data-conversion.md)   
 [地區設定](../c-runtime-library/locale.md)   
 [is、isw 常式](../c-runtime-library/is-isw-routines.md)