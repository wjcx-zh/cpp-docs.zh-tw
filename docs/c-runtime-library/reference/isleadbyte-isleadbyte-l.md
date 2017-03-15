---
title: "isleadbyte、_isleadbyte_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_isleadbyte_l"
  - "isleadbyte"
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
  - "_istleadbyte"
  - "_isleadbyte_l"
  - "isleadbyte"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "前導位元組"
  - "_isleadbyte_l 函式"
  - "_istleadbyte 函式"
  - "istleadbyte 函式"
  - "isleadbyte 函式"
ms.assetid: 3b2bcf09-d82b-4803-9e80-59d04942802a
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# isleadbyte、_isleadbyte_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

判斷某個字元是否為多位元組字元的前導位元組。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int isleadbyte(  
   int c   
);  
int _isleadbyte_l(  
   int c   
);  
```  
  
#### 參數  
 `c`  
 待測試整數。  
  
## 傳回值  
 如果引數符合測試條件，`isleadbyte` 會傳回非零值，否則會傳回 0。 在 "C" 地區設定和單一位元組字元集 \(SBCS\) 地區設定中，`isleadbyte` 一律會傳回 0。  
  
## 備註  
 如果 `isleadbyte` 巨集的引數是多位元組字元的第一個位元組，則該巨集會傳回非零值。 針對 \-1 \(`EOF`\) 到 `UCHAR_MAX` \(0xFF\) \(含\) 的任何整數引數，`isleadbyte` 會產生有意義的結果。  
  
 `isleadbyte` 的預期引數類型為 `int`；如果傳遞了帶正負號的字元，編譯器可能會將其轉換成帶正負號的整數，而產生無法預期的結果。  
  
 尾碼為 `_l` 的這個函式版本是一樣的，只不過與地區設定相關的行為使用了傳入的地區設定，而不是目前的地區設定。  
  
### 一般文字常式對應  
  
|TCHAR.H 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_istleadbyte`|一律傳回 false|**\_** `isleadbyte`|一律傳回 false|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`isleadbyte`|\<ctype.h\>|  
|`_isleadbyte_l`|\<ctype.h\>|  
  
 如需其他相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 不適用，但請參閱 [System::Globalization::CultureInfo](https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx)。  
  
## 請參閱  
 [位元組分類](../../c-runtime-library/byte-classification.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [\_ismbb 常式](../../c-runtime-library/ismbb-routines.md)