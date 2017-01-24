---
title: "isalpha、iswalpha、_isalpha_l、_iswalpha_l | Microsoft Docs"
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
  - "iswalpha"
  - "_iswalpha_l"
  - "isalpha"
  - "_isalpha_l"
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
  - "_istalpha"
  - "_ismbcalpha_l"
  - "isalpha"
  - "_isalpha_l"
  - "iswalpha"
  - "_istalpha_l"
  - "_iswalpha_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_isalpha_l 函式"
  - "_ismbcalpha 函式"
  - "_ismbcalpha_l 函式"
  - "_istalpha 函式"
  - "_istalpha_l 函式"
  - "_iswalpha_l 函式"
  - "isalpha 函式"
  - "istalpha 函式"
  - "iswalpha 函式"
ms.assetid: ed6cc2be-c4b0-4475-87ac-bc06d8c23064
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# isalpha、iswalpha、_isalpha_l、_iswalpha_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

判斷整數是否代表英文字元。  
  
## 語法  
  
```  
int isalpha(   
   int c   
);  
int iswalpha(   
   wint_t c   
);  
int _isalpha_l(   
   int c,  
   _locale_t locale   
);  
int _iswalpha_l(   
   wint_t c,  
   _locale_t locale   
);  
```  
  
#### 參數  
 `c`  
 要測試的整數。  
  
 `locale`  
 使用不是目前的地區設定的地區設定。  
  
## 傳回值  
 每一個這些常式在 `c` 是表示一個字母字元時回傳非零值。  `c` 如果在範圍 A\-Z 或 a\-z 內，`isalpha` 會傳回非零的值。  `iswalpha` 會傳回一個非零值只於 `iswupper` 或 `iswlower` 為非零的寬字元;也就是任何一個寬字元於實作環境定義的 `iswcntrl`、 `iswdigit`、 `iswpunct`或 `iswspace` 之中時都不是非零。  每一個這些常式在傳入 `c` 沒有達到測試條件時回傳零。  
  
 有 `_l` 尾碼的這些函式，其版本使用傳入的地區設定，而不使用目前的地區設定。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 如果 `c` 不是 EOF 或介於 0 到 0xFF \(含\) 之間，`isalpha` 和 `_isalpha_l` 的行為是未定義。  當使用 CRT 偵錯程式庫，而 `c` 不是其中一個值時，函式會引發判斷提示。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_istalpha`|`isalpha`|`_ismbcalpha`|`iswalpha`|  
|`_istalpha_l`|`_isalpha_l`|`_ismbcalpha_l`|`_iswalpha_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`isalpha`|\<ctype.h\>|  
|`iswalpha`|\<ctype.h\> 或 \<wchar.h\>|  
|`_isalpha_l`|\<ctype.h\>|  
|`_iswalpha_l`|\<ctype.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 [System::Char::IsLetter](https://msdn.microsoft.com/en-us/library/system.char.isletter.aspx)  
  
## 請參閱  
 [字元分類](../../c-runtime-library/character-classification.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [is、isw 常式](../../c-runtime-library/is-isw-routines.md)