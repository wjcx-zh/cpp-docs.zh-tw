---
title: "tolower、_tolower、towlower、_tolower_l、_towlower_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_tolower_l"
  - "towlower"
  - "tolower"
  - "_tolower"
  - "_towlower_l"
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
  - "ntdll.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_totlower"
  - "tolower"
  - "_tolower"
  - "towlower"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_tolower 函式"
  - "_tolower_l 函式"
  - "_totlower 函式"
  - "_towlower_l 函式"
  - "大小寫, 轉換"
  - "字元, 轉換"
  - "小寫, 轉換為"
  - "字串轉換, 大小寫"
  - "字串轉換, 到不同字元"
  - "tolower 函式"
  - "tolower_l 函式"
  - "totlower 函式"
  - "towlower 函式"
  - "towlower_l 函式"
ms.assetid: 86e0fc02-94ae-4472-9631-bf8e96f67b92
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# tolower、_tolower、towlower、_tolower_l、_towlower_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

將一個字元轉換成小寫。  
  
## 語法  
  
```  
int tolower(  
   int c   
);  
int _tolower(  
   int c   
);  
int towlower(  
   wint_t c   
);  
int _tolower_l(  
   int c,  
   _locale_t locale   
);  
int _towlower_l(  
   wint_t c,  
   _locale_t locale   
);  
```  
  
#### 參數  
 \[in\] `c`  
 要進行轉換的字元。  
  
 \[in\] `locale`  
 使用的地區設定為地區設定特性轉換。  
  
## 傳回值  
 這些常式中轉換 `c` 複製為小寫，如果可進行轉換，並傳回結果。  未保留表示錯誤的傳回值。  
  
## 備註  
 如果可能且相對應，這些常式可能轉換特定大寫字母成小寫字母。  `towlower` 案例轉換是地區設定特性的。  使用目前的地區設定相關只變更字元。  沒有 `_l`尾碼的函式使用目前設定的地區設定。  這些函式版本與 `_l`結尾的會將地區設定做為參數並使用該控制項而不是目前設定的地區設定。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 針對 `_tolower` 中的預期結果， [\_\_isascii](../../c-runtime-library/reference/isascii-isascii-iswascii.md) 和 [isupper](../../c-runtime-library/reference/isupper-isupper-l-iswupper-iswupper-l.md) 都必須為傳回非零。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|\_UNICODE & \_MBCS 未定義|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_totlower`|`tolower`|`_mbctolower`|`towlower`|  
|`_totlower_l`|`_tolower_l`|`_mbctolower_l`|`_towlower_l`|  
  
> [!NOTE]
>  `_tolower_l` 和 `_towlower_l` 沒有地區設定相關屬性並不會直接呼叫。  它們提供內部所使用的 `_totlower_l`。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`tolower`|\<ctype.h\>|  
|`_tolower`|\<ctype.h\>|  
|`towlower`|\<ctype.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## 範例  
 請參閱 [對函式](../../c-runtime-library/to-functions.md)中的範例。  
  
## .NET Framework 對等用法  
 [System::Char::ToLower](https://msdn.microsoft.com/en-us/library/system.char.tolower.aspx)  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [is、isw 常式](../../c-runtime-library/is-isw-routines.md)   
 [to 函式](../../c-runtime-library/to-functions.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)