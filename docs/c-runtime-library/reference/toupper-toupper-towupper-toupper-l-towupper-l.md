---
title: "toupper、_toupper、towupper、_toupper_l、_towupper_l | Microsoft Docs"
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
  - "_toupper_l"
  - "towupper"
  - "toupper"
  - "_towupper_l"
  - "_toupper"
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
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "towupper"
  - "_toupper"
  - "_totupper"
  - "toupper"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_totupper 函式"
  - "_toupper 函式"
  - "_toupper_l 函式"
  - "_towupper_l 函式"
  - "大小寫, 轉換"
  - "字元, 轉換"
  - "字串轉換, 大小寫"
  - "字串轉換, 到不同字元"
  - "totupper 函式"
  - "toupper 函式"
  - "toupper_l 函式"
  - "towupper 函式"
  - "towupper_l 函式"
  - "大寫, 轉換字串為"
ms.assetid: cdef1b0f-b19c-4d11-b7d2-cf6334c9b6cc
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# toupper、_toupper、towupper、_toupper_l、_towupper_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

要轉換為大寫的字元。  
  
## 語法  
  
```  
int toupper(  
   int c   
);  
int _toupper(  
   int c   
);  
int towupper(  
   wint_t c   
);  
int _toupper_l(  
   int c ,  
   _locale_t locale  
);  
int _towupper_l(  
   wint_t c ,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `c`  
 要進行轉換的字元。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 這些常式每個轉換的 `c`，如果可能，並傳回結果。  
  
 如果 `c` 是 `iswlower` 為非零的寬字元，且 `iswupper` 為非零，則 `towupper` 會傳回對應的寬字元的對應的寬字元;否則， `towupper` 會傳回未變更的 `c` 。  
  
 未保留表示錯誤的傳回值。  
  
 針對 `toupper` 中的預期結果， [\_\_isascii](../../c-runtime-library/reference/isascii-isascii-iswascii.md) 和 [islower](../../c-runtime-library/reference/islower-iswlower-islower-l-iswlower-l.md) 都必須為傳回非零。  
  
## 備註  
 這些常式若可能都會轉換成特定小寫字母的大寫字母和大小。  `towupper` 案例轉換是地區設定特性的。  使用目前的地區設定相關只變更字元。  沒有 `_l` 尾碼的函式使用目前設定的地區設定。  這些函式版本與 `_l` 結尾的會將地區設定做為參數並使用該控制項而不是目前設定的地區設定。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 針對 `toupper` 中的預期結果， [\_\_isascii](../../c-runtime-library/reference/isascii-isascii-iswascii.md) 和 [isupper](../../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md) 都必須為傳回非零。  
  
 [資料轉換常式](../../c-runtime-library/data-conversion.md)  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE &\_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|---------------------------|----------------|-------------------|  
|`_totupper`|`toupper`|`_mbctoupper`|`towupper`|  
|`_totupper_l`|`_toupper_l`|`_mbctoupper_l`|`_towupper_l`|  
  
> [!NOTE]
>  `_toupper_l` 和 `_towupper_l` 沒有地區設定相關屬性並不會直接呼叫。  它們提供內部所使用的 `_totupper_l`。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`toupper`|\<ctype.h\>|  
|`_toupper`|\<ctype.h\>|  
|`towupper`|\<ctype.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 請參閱 [對函式](../../c-runtime-library/to-functions.md)中的範例。  
  
## .NET Framework 對等用法  
 [System::Char::ToUpper](https://msdn.microsoft.com/en-us/library/system.char.toupper.aspx)  
  
## 請參閱  
 [is、isw 常式](../../c-runtime-library/is-isw-routines.md)   
 [to 函式](../../c-runtime-library/to-functions.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)