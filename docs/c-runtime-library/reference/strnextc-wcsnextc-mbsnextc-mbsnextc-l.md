---
title: "_strnextc、_wcsnextc、_mbsnextc、_mbsnextc_l | Microsoft Docs"
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
  - "_strnextc"
  - "_mbsnextc_l"
  - "_mbsnextc"
  - "_wcsnextc"
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
apitype: "DLLExport"
f1_keywords: 
  - "strnextc"
  - "tcsnextc"
  - "_mbsnextc_l"
  - "_mbsnextc"
  - "mbsnextc_l"
  - "ftcsnextc"
  - "mbsnextc"
  - "_tcsnextc"
  - "_wcsnextc"
  - "_ftcsnextc"
  - "_strnextc"
  - "wcsnextc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbsnextc 函式"
  - "_mbsnextc_l 函式"
  - "_strnextc 函式"
  - "_tcsnextc 函式"
  - "_wcsnextc 函式"
  - "mbsnextc 函式"
  - "mbsnextc_l 函式"
  - "strnextc 函式"
  - "tcsnextc 函式"
  - "wcsnextc 函式"
ms.assetid: e3086173-9eb5-4540-a23a-5d866bd05340
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strnextc、_wcsnextc、_mbsnextc、_mbsnextc_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

尋找字串中的下一個字元。  
  
> [!IMPORTANT]
>  `_mbsnextc` and `_mbsnextc_l`不能用於在 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
unsigned int _strnextc(  
   const char *str  
);  
unsigned int _wscnextc(  
   const wchar_t *str  
);   
unsigned int _mbsnextc(  
   const unsigned char *str   
);  
unsigned int _mbsnextc_l(  
   const unsigned char *str,  
   _locale_t locale  
);  
  
```  
  
#### 參數  
 `str`  
 來源字串。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 這些函式都會傳回下一個字元的整數值的 `str`*。*  
  
## 備註  
 `_mbsnextc` 函式會傳回在 `str`的下一個多位元組字元的整數值，而不需前進字串指標。  `_mbsnextc` 根據目前使用的 [多位元組字碼頁](../../c-runtime-library/code-pages.md) 辨識多位元組字元序列。  
  
 如果 `str` 是 `NULL`，則叫用無效參數處理常式，如 [參數驗證](../../c-runtime-library/parameter-validation.md) 中所述。  如果允許繼續執行，這些函式會將 `errno` 設為 `EINVAL`，並傳回 0。  
  
 **安全性提示** 這個 API 會導致緩衝區滿溢問題而有潛在的威脅。  緩衝區溢位問題是系統攻擊的常見方法，它會導致權限不確定性的增加。  如需詳細資訊，請參閱 [Avoiding Buffer Overruns](http://msdn.microsoft.com/library/windows/desktop/ms717795) 。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_tcsnextc`|`_strnextc`|`_mbsnextc`|`_wcsnextc`|  
  
 `_strnextc` 和 `_wcsnextc` 是單一位元組字元以及 `_mbsnextc` 的寬字元字串版本。  `_wcsnextc` 傳回在 `string` 的寬字元的整數值; `_strnextc` 傳回在 `string` 的下單一位元組字元的整數值。  `_strnextc` 和 `_wcsnextc` 只提供這種對應使用，並且不應該為其他用途所使用。  如需詳細資訊，請參閱 [使用泛用文字對應](../../c-runtime-library/using-generic-text-mappings.md) 和 [泛用文字對應](../../c-runtime-library/generic-text-mappings.md)。  
  
 `_mbsnextc_l`  也相同，除了改用傳入的地區設定參數。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_mbsnextc`|\<mbstring.h\>|  
|`_mbsnextc_l`|\<mbstring.h\>|  
|`_strnextc`|\<tchar.h\>|  
|`_wcsnextc`|\<tchar.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [字串操作](../../c-runtime-library/string-manipulation-crt.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [\_strdec、\_wcsdec、\_mbsdec、\_mbsdec\_l](../../c-runtime-library/reference/strdec-wcsdec-mbsdec-mbsdec-l.md)   
 [\_strinc、\_wcsinc、\_mbsinc、\_mbsinc\_l](../../c-runtime-library/reference/strinc-wcsinc-mbsinc-mbsinc-l.md)   
 [\_strninc、\_wcsninc、\_mbsninc、\_mbsninc\_l](../../c-runtime-library/reference/strninc-wcsninc-mbsninc-mbsninc-l.md)