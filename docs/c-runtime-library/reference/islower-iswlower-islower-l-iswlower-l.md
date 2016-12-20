---
title: "islower、iswlower、_islower_l、_iswlower_l | Microsoft Docs"
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
  - "iswlower"
  - "_islower_l"
  - "islower"
  - "_iswlower_l"
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
  - "_istlower"
  - "islower"
  - "_ismbclower_l"
  - "_liswlower_l"
  - "_istlower_l"
  - "_iswlower_l"
  - "_islower _l"
  - "_islower_l"
  - "iswlower"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_islower _l 函式"
  - "_islower_l 函式"
  - "_ismbclower_l 函式"
  - "_istlower 函式"
  - "_istlower_l 函式"
  - "_iswlower_l 函式"
  - "_liswlower_l 函式"
  - "islower 函式"
  - "istlower 函式"
  - "iswlower 函式"
ms.assetid: fcc3b70a-2b47-45fd-944d-e5c1942e6457
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# islower、iswlower、_islower_l、_iswlower_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

判斷整數是否表示小寫字元。  
  
## 語法  
  
```  
int islower(  
   int c   
);  
int iswlower(  
   wint_t c   
);  
int islower_l(  
   int c,  
   _locale_t locale  
);  
int _iswlower_l(  
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
 這些常式在 `c` 是表示一個小寫字元時回傳非零值。  `islower` 會傳回非零的值，如果 `c` 是小寫字母 \(a\-z\)。  `iswlower` 會傳回非零的值，如果 `c` 是對應至一個小寫字母的寬字元，或者，如果 `c` 是一個由實作環境如 `iswcntrl`、 `iswdigit`、 `iswpunct`或 `iswspace` 等都不是零的寬字元。  每一個這些常式在傳入 `c` 沒有達到測試條件時回傳零。  
  
 尾碼為 `_l` 的這些函式版本與地區設定相關的行為使用了傳入的地區設定，而不是目前的地區設定。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 如果 `c` 不是 EOF 或介於 0 到 0xFF \(含\) 之間，`islower` 和 `_islower_l` 的行為是未定義。  當使用 CRT 偵錯程式庫，而 `c` 不是其中一個值時，函式會引發判斷提示。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_istlower`|`islower`|[\_ismbclower](../../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|`iswlower`|  
|`_istlower_l`|`_islower _l`|[\_ismbclower\_l](../../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|`_liswlower_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`islower`|\<ctype.h\>|  
|`iswlower`|\<ctype.h\> 或 \<wchar.h\>|  
|`_islower_l`|\<ctype.h\>|  
|`_swlower_l`|\<ctype.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 [System::Char::IsLower](https://msdn.microsoft.com/en-us/library/system.char.islower.aspx)  
  
## 請參閱  
 [字元分類](../../c-runtime-library/character-classification.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [is、isw 常式](../../c-runtime-library/is-isw-routines.md)