---
title: "_strlwr_s、_strlwr_s_l、_mbslwr_s、_mbslwr_s_l、_wcslwr_s、_wcslwr_s_l | Microsoft Docs"
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
  - "_strlwr_s_l"
  - "_mbslwr_s_l"
  - "_mbslwr_s"
  - "_wcslwr_s"
  - "_strlwr_s"
  - "_wcslwr_s_l"
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
  - "_strlwr_s_l"
  - "_strlwr_s"
  - "mbslwr_s_l"
  - "strlwr_s_l"
  - "_wcslwr_s"
  - "strlwr_s"
  - "mbslwr_s"
  - "_wcslwr_s_l"
  - "wcslwr_s_l"
  - "_tcslwr_s"
  - "_tcslwr_s_l"
  - "_mbslwr_s_l"
  - "wcslwr_s"
  - "_mbslwr_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbslwr_s 函式"
  - "_mbslwr_s_l 函式"
  - "_strlwr_s 函式"
  - "_strlwr_s_l 函式"
  - "_tcslwr_s 函式"
  - "_tcslwr_s_l 函式"
  - "_wcslwr_s 函式"
  - "_wcslwr_s_l 函式"
  - "大小寫, 轉換"
  - "轉換大小寫, CRT 函式"
  - "mbslwr_s 函式"
  - "mbslwr_s_l 函式"
  - "字串轉換 [C++], 大小寫"
  - "字串 [C++], 大小寫"
  - "字串 [C++], 轉換大小寫"
  - "strlwr_s 函式"
  - "strlwr_s_l 函式"
  - "tcslwr_s 函式"
  - "tcslwr_s_l 函式"
  - "wcslwr_s 函式"
  - "wcslwr_s_l 函式"
ms.assetid: 4883d31b-bdac-4049-83a1-91dfdeceee79
caps.latest.revision: 42
caps.handback.revision: 40
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strlwr_s、_strlwr_s_l、_mbslwr_s、_mbslwr_s_l、_wcslwr_s、_wcslwr_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用目前的地區設定或傳遞的地區設定物件，將字串轉換為小寫。  這些 [\_strlwr、\_wcslwr、\_mbslwr、\_strlwr\_l、\_wcslwr\_l、\_mbslwr\_l](../../c-runtime-library/reference/strlwr-wcslwr-mbslwr-strlwr-l-wcslwr-l-mbslwr-l.md) 版本有安全性增強功能，如 [CRT 中的安全性功能](../../c-runtime-library/security-features-in-the-crt.md)中所述。  
  
> [!IMPORTANT]
>  `_mbslwr_s` and `_mbslwr_s_l`不能用於在 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
errno_t _strlwr_s(  
   char *str,  
   size_t numberOfElements  
);  
errno_t _strlwr_s_l(  
   char *str,  
   size_t numberOfElements,  
   _locale_t locale  
);  
errno_t _mbslwr_s(  
   unsigned char *str,  
   size_t numberOfElements  
);  
errno_t _mbslwr_s_l(  
   unsigned char *str,  
   size_t numberOfElements,  
   _locale_t locale  
);  
errno_t _wcslwr_s(  
   wchar_t *str,  
   size_t numberOfElements  
);  
errno_t _wcslwr_s_l(  
   wchar_t *str,  
   size_t numberOfElements,  
   _locale_t locale  
);  
template <size_t size>  
errno_t _strlwr_s(  
   char (&str)[size]  
); // C++ only  
template <size_t size>  
errno_t _strlwr_s_l(  
   char (&str)[size],  
   _locale_t locale  
); // C++ only  
template <size_t size>  
errno_t _mbslwr_s(  
   unsigned char (&str)[size]  
); // C++ only  
template <size_t size>  
errno_t _mbslwr_s_l(  
   unsigned char (&str)[size],  
   _locale_t locale  
); // C++ only  
template <size_t size>  
errno_t _wcslwr_s(  
   wchar_t (&str)[size]  
); // C++ only  
template <size_t size>  
errno_t _wcslwr_s_l(  
   wchar_t (&str)[size],  
   _locale_t locale  
); // C++ only  
```  
  
#### 參數  
 `str`  
 將以 Null 結束之字串轉換為小寫。  
  
 `numberOfElements`  
 緩衝區的大小。  
  
 `locale`  
 使用的地區設定。  
  
## 傳回值  
 如果成功則得到 0 值；如果失敗，則結果不為 0 的錯誤碼。  
  
 這些函式會驗證它們的參數。  如果 `str` 不是有效的 null 結尾的字串，則觸發無效參數叫用處理常式 ，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，函式會傳回 `EINVAL` 並將 `EINVAL` 設定為 `errno`。  如果 `numberOfElements` 小於字串長度，函式一樣傳回 `EINVAL` 並將 `errno` 設定為 `EINVAL`。  
  
## 備註  
 `_strlwr_s` 函式將所有在 `str` 中的大寫字母轉換為小寫。  `_mbslwr_s` 是 `_strlwr_s`多位元組字元版本。`_wcslwr_s` 是 `_strlwr_s`的寬字元版本。  
  
 輸出值受地區設定的`LC_CTYPE` 分類設定所影響。如需詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 。  這些函式沒有以 `_l` 後綴的版本在這些地區相依的行為上使用目前的地區設定，而以 `_l` 後綴版本除了它們會使用傳入的地區設定參數之外運作相同。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 C\+\+ 利用多載樣板簡化了這些函式的使用方式。多載可自動推斷緩衝區長度 \(因而不須指定大小引數\)，也可以將不安全的舊函式自動取代成較新且安全的對應函式。  如需詳細資訊，請參閱[安全範本多載](../../c-runtime-library/secure-template-overloads.md)。  
  
 這些函式的偵錯版本會先用 0xFD 填入緩衝區。  若要停用此行為，請使用 [\_CrtSetDebugFillThreshold](../../c-runtime-library/reference/crtsetdebugfillthreshold.md)。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcslwr_s`|`_strlwr_s`|`_mbslwr_s`|`_wcslwr_s`|  
|`_tcslwr_s_l`|`_strlwr_s_l`|`_mbslwr_s_l`|`_wcslwr_s_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_strlwr_s`, `_strlwr_s_l`|\<string.h\>|  
|`_mbslwr_s`, `_mbslwr_s_l`|\<mbstring.h\>|  
|`_wcslwr_s`, `_wcslwr_s_l`|\<string.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
  
```  
// crt_strlwr_s.cpp  
// This program uses _strlwr_s and _strupr_s to create  
// uppercase and lowercase copies of a mixed-case string.  
//  
  
#include <string.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
int main()  
{  
   char str[] = "The String to End All Strings!";  
   char *copy1, *copy2;  
   errno_t err;  
  
   err = _strlwr_s( copy1 = _strdup(str), strlen(str) + 1);  
   err = _strupr_s( copy2 = _strdup(str), strlen(str) + 1);  
  
   printf( "Mixed: %s\n", str );  
   printf( "Lower: %s\n", copy1 );  
   printf( "Upper: %s\n", copy2 );  
  
   free( copy1 );  
   free( copy2 );  
  
   return 0;  
}  
```  
  
  **Mixed: The String to End All Strings\!**  
**Lower: the string to end all strings\!**  
**Upper: THE STRING TO END ALL STRINGS\!**   
## .NET Framework 對等用法  
 [System::String::ToLower](https://msdn.microsoft.com/en-us/library/system.string.tolower.aspx)  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_strupr\_s、\_strupr\_s\_l、\_mbsupr\_s、\_mbsupr\_s\_l、\_wcsupr\_s、\_wcsupr\_s\_l](../../c-runtime-library/reference/strupr-s-strupr-s-l-mbsupr-s-mbsupr-s-l-wcsupr-s-wcsupr-s-l.md)