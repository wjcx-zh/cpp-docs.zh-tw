---
title: "isupper、_isupper_l、iswupper、_iswupper_l | Microsoft Docs"
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
  - "isupper"
  - "iswupper"
  - "_iswupper_l"
  - "_isupper_l"
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
  - "isupper"
  - "_istupper"
  - "iswupper"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_istupper 函式"
  - "_isupper_l 函式"
  - "_iswupper_l 函式"
  - "istupper 函式"
  - "isupper 函式"
  - "isupper_l 函式"
  - "iswupper 函式"
  - "iswupper_l 函式"
ms.assetid: da2bcc9f-241c-48c0-9a0e-ad273827e16a
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# isupper、_isupper_l、iswupper、_iswupper_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

判斷整數是否表示大寫字元。  
  
## 語法  
  
```  
int isupper(  
   int c   
);  
int _isupper_l (  
   int c,  
   _locale_t locale  
);  
int iswupper(  
   wint_t c   
);  
int _iwsupper_l(  
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
 如果 `c` 是大寫字母的特殊表示，這些常式都會傳回非零。  `isupper` 會傳回非零的值，如果 `c` 是大寫字母 \(A\-Z\)。  `iswupper` 會傳回非零的值，如果 `c` 是對應至一個大寫字母的寬字元，或者，如果 `c` 是一個由實作環境如 `iswcntrl`、 `iswdigit`、 `iswpunct`或 `iswspace` 等都不是零的寬字元。  每一個這些常式在傳入 `c` 沒有達到測試條件時回傳零。  
  
 尾碼為 `_l` 的這些函式版本與地區設定相關的行為使用了傳入的地區設定，而不是目前的地區設定。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 如果 `c` 不是 EOF 或介於 0 到 0xFF \(含\) 之間，`isupper` 和 `_isupper_l` 的行為是未定義。  當使用 CRT 偵錯程式庫，而 `c` 不是其中一個值時，函式會引發判斷提示。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE & \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_istupper`|`isupper`|[\_ismbcupper](../../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|`iswupper`|  
|`_istupper_l`|`_isupper_l`|[\_ismbclower、\_ismbclower\_l、\_ismbcupper、\_ismbcupper\_l](../../c-runtime-library/reference/ismbclower-ismbclower-l-ismbcupper-ismbcupper-l.md)|`_iswupper_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`isupper`|\<ctype.h\>|  
|`_isupper_l`|\<ctype.h\>|  
|`iswupper`|\<ctype.h\> 或 \<wchar.h\>|  
|`_iswupper_l`|\<ctype.h\>|  
  
 如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 [System::Char::IsUpper](https://msdn.microsoft.com/en-us/library/system.char.isupper.aspx)  
  
## 請參閱  
 [字元分類](../../c-runtime-library/character-classification.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [is、isw 常式](../../c-runtime-library/is-isw-routines.md)