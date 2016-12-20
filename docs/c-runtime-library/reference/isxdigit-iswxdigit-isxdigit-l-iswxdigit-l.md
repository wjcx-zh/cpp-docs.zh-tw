---
title: "isxdigit、iswxdigit、_isxdigit_l、_iswxdigit_l | Microsoft Docs"
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
  - "_iswxdigit_l"
  - "iswxdigit"
  - "isxdigit"
  - "_isxdigit_l"
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
  - "iswxdigit"
  - "isxdigit"
  - "_istxdigit"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_istxdigit 函式"
  - "_iswxdigit_l 函式"
  - "_isxdigit_l 函式"
  - "十六進位字元"
  - "istxdigit 函式"
  - "iswxdigit 函式"
  - "iswxdigit_l 函式"
  - "isxdigit 函式"
  - "isxdigit_l 函式"
ms.assetid: c8bc5146-0b58-4e3f-bee3-f2318dd0f829
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# isxdigit、iswxdigit、_isxdigit_l、_iswxdigit_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

判斷整數是否表示為十六進位數字的字元。  
  
## 語法  
  
```  
int isxdigit(  
   int c   
);  
int iswxdigit(  
   wint_t c   
);  
int _isxdigit_l(  
   int c,  
   _locale_t locale  
);  
int _iswxdigit_l(  
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
 這些常式在 `c` 是表示一個十六進位數字時回傳非零值。  `isxdigit` 會傳回非零的值，如果 `c` 是十六位元數字 \(A\-F 和 a\-f，或 0– 9\)。  `iswxdigit` 會傳回非零的值，如果 `c` 是對應至十六進位數字字元的寬字元。  每一個這些常式在傳入 `c` 沒有達到測試條件時回傳零。  
  
 對於「C」地區設定中， `iswxdigit` 函式不支援 Unicode 全形十六進位字元。  
  
 尾碼為 `_l` 的這些函式版本與地區設定相關的行為使用了傳入的地區設定，而不是目前的地區設定。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 如果 `c` 不是 EOF 或介於 0 到 0xFF \(含\) 之間，`isxdigit` 和 `_isxdigit_l` 的行為是未定義。  當使用 CRT 偵錯程式庫，而 `c` 不是其中一個值時，函式會引發判斷提示。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_istxdigit`|`isxdigit`|`isxdigit`|`iswxdigit`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`isxdigit`|\<ctype.h\>|  
|`iswxdigit`|\<ctype.h\> 或 \<wchar.h\>|  
|`_isxdigit_l`|\<ctype.h\>|  
|`_iswxdigit_l`|\<ctype.h\> 或 \<wchar.h\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 [System::Char::IsNumber](https://msdn.microsoft.com/en-us/library/system.char.isnumber.aspx)  
  
## 請參閱  
 [字元分類](../../c-runtime-library/character-classification.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [is、isw 常式](../../c-runtime-library/is-isw-routines.md)