---
title: "isdigit、iswdigit、_isdigit_l、_iswdigit_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_isdigit_l"
  - "iswdigit"
  - "_iswdigit_l"
  - "isdigit"
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
  - "_iswdigit_l"
  - "_isdigit_l"
  - "iswdigit"
  - "isdigit"
  - "_istdigit"
  - "_istdigit_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "iswdigit 函式"
  - "iswdigit_l 函式"
  - "_iswdigit_l 函式"
  - "_istdigit_l 函式"
  - "_istdigit 函式"
  - "istdigit 函式"
  - "isdigit 函式"
  - "isdigit_l 函式"
  - "_ismbcdigit_l 函式"
  - "_isdigit_l 函式"
ms.assetid: 350b0093-843a-47b0-954e-c1776e8a3853
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# isdigit、iswdigit、_isdigit_l、_iswdigit_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

判斷整數是否表示十進位字元。  
  
## 語法  
  
```  
int isdigit(   
   int c   
);  
int iswdigit(   
   wint_t c   
);  
int _isdigit_l(   
   int c,  
   _locale_t locale  
);  
int _iswdigit_l(   
   wint_t c,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `c`  
 要測試的整數。  
  
 `locale`  
 使用的地區設定。  
  
## 傳回值  
 這些常式在 `c` 是表示一個十進位字元時回傳非零值。  `isdigit` 會傳回非零的值，如果 `c` 是十進位數字 \(0 – 9\)。  `iswdigit` 會傳回非零的值，如果 `c` 是對應至十進位數字字元的寬字元。  每一個這些常式在傳入 `c` 沒有達到測試條件時回傳零。  
  
 尾碼為 `_l` 的這些函式版本與地區設定相關的行為使用了傳入的地區設定，而不是目前的地區設定。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 如果 `c` 不是 EOF 或介於 0 到 0xFF \(含\) 之間，`isdigit` 和 `_isdigit_l` 的行為是未定義。  當使用 CRT 偵錯程式庫，而 `c` 不是其中一個值時，函式會引發判斷提示。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_istdigit`|`isdigit`|[\_ismbcdigit](../../c-runtime-library/reference/ismbcalnum-functions.md)|`iswdigit`|  
|`_istdigit_l`|`_isdigit_l`|[\_ismbcdigit\_l](../../c-runtime-library/reference/ismbcalnum-functions.md)|`_iswdigit_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`isdigit`|\<ctype.h\>|  
|`iswdigit`|\<ctype.h\> 或 \<wchar.h\>|  
|`_isdigit_l`|\<ctype.h\>|  
|`_iswdigit_l`|\<ctype.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 [System::Char::IsDigit](https://msdn.microsoft.com/en-us/library/system.char.isdigit.aspx)  
  
## 請參閱  
 [字元分類](../../c-runtime-library/character-classification.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [is、isw 常式](../../c-runtime-library/is-isw-routines.md)