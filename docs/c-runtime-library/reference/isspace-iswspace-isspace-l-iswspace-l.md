---
title: "isspace、iswspace、_isspace_l、_iswspace_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "iswspace"
  - "_isspace_l"
  - "_iswspace_l"
  - "isspace"
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
  - "iswspace"
  - "_istspace"
  - "isspace"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_isspace_l 函式"
  - "_istspace 函式"
  - "_iswspace_l 函式"
  - "isspace 函式"
  - "isspace_l 函式"
  - "istspace 函式"
  - "iswspace 函式"
  - "iswspace_l 函式"
ms.assetid: b851e0c0-36bb-4dac-a1a3-533540939035
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# isspace、iswspace、_isspace_l、_iswspace_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

判斷整數是否表示空白字元。  
  
## 語法  
  
```  
int isspace(  
   int c   
);  
int iswspace(  
   wint_t c   
);  
int _isspace_l(  
   int c,  
   _locale_t locale  
);  
int _iswspace_l(  
   wint_t c,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `c`  
 要測試的整數。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 這些常式在 `c` 是表示一個空白字元時回傳非零值。  如果 `c` 為空白字元 \(0x09 – 0x0D or 0x20\)，則 `isspace` 傳回非零值。  `isspace` 函式的測試條件結果取決於地區設定的 `LC_CTYPE` 分類設定；如需詳細資訊，請參閱 [setlocale、\_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  這些函式 \(沒有 `_l` 後綴\) 的版本會使用任何地區設定相依行為的地區設定；而以 `_l` 為後綴的版本則相同，但會使用傳入的地區設定。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 如果 `c` 是對應至標準空白字元的寬字元，則 `iswspace` 傳回非零值。  
  
 如果 `c` 不是 EOF 或介於 0 到 0xFF \(含\) 之間，`isspace` 和 `_isspace_l` 的行為是未定義。  當使用 CRT 偵錯程式庫，而 `c` 不是其中一個值時，函式會引發判斷提示。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|**\_** `istspace`|`isspace`|[\_ismbcspace](../../c-runtime-library/reference/ismbcgraph-functions.md)|`iswspace`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`isspace`|\<ctype.h\>|  
|`iswspace`|\<ctype.h\> 或 \<wchar.h\>|  
|`_isspace_l`|\<ctype.h\>|  
|`_iswspace_l`|\<ctype.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 [System::Char::IsWhiteSpace](https://msdn.microsoft.com/en-us/library/system.char.iswhitespace.aspx)  
  
## 請參閱  
 [字元分類](../../c-runtime-library/character-classification.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [is、isw 常式](../../c-runtime-library/is-isw-routines.md)