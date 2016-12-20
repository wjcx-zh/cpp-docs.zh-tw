---
title: "_isctype、iswctype、_isctype_l、_iswctype_l | Microsoft Docs"
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
  - "_isctype_l"
  - "iswctype"
  - "_iswctype_l"
  - "_isctype"
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
  - "iswctype"
  - "_isctype"
  - "_isctype_l"
  - "_iswctype"
  - "isctype"
  - "iswctype_l"
  - "isctype_l"
  - "_iswctype_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_isctype 函式"
  - "_isctype_l 函式"
  - "_iswctype 函式"
  - "_iswctype_l 函式"
  - "isctype 函式"
  - "isctype_l 函式"
  - "iswctype 函式"
  - "iswctype_l 函式"
ms.assetid: cf7509b7-12fc-4d95-8140-ad2eb98173d3
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _isctype、iswctype、_isctype_l、_iswctype_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

為 `desc` 引數所指定的屬性來測試 `c` 。  針對 `desc`的每一個有效值，具有對等寬字元排序常式。  
  
## 語法  
  
```  
int _isctype(  
   int c,  
   _ctype_t desc  
);  
int _isctype_l(  
   int c,  
   _ctype_t desc,  
   _locale_t locale  
);  
int iswctype(  
   wint_t c,  
   wctype_t desc   
);  
int _iswctype_l(  
   wint_t c,  
   wctype_t desc,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `c`  
 要測試的整數。  
  
 `desc`  
 屬性測試。  通常使用 ctype 或 [wctype](../../c-runtime-library/reference/wctype.md)，來擷取。  
  
 `locale`  
 使用的地區設定為所有與地區設定相關的測試。  
  
## 傳回值  
 `_isctype` 和 `iswctype` 傳回非零的值，如果 `c` 有 `desc` 指定的屬性在目前地區設定或 0。  尾碼為 `_l` 的這些函式版本是一樣的，只不過與地區設定相關的行為使用了傳入的地區設定，而不是目前的地區設定。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 如果 `c` 不是 EOF 或介於 0 到 0xFF \(含\) 之間，`_isctype` 和 `_isctype_l` 的行為是未定義。  當使用 CRT 偵錯程式庫，而 `c` 不是其中一個值時，函式會引發判斷提示。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`n/a`|`_isctype`|`n/a`|`_iswctype`|  
|`n/a`|`_isctype_l`|`n/a`|`_iswctype_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_isctype`|\<ctype.h\>|  
|`iswctype`|\<ctype.h\> 或 \<wchar.h\>|  
|`_isctype_l`|\<ctype.h\>|  
|`_iswctype_l`|\<ctype.h\> 或 \<wchar.h\>|  
  
 如需更多關於相容性的資訊，請參閱入門介紹中的 [相容性 \(Compatibility\)](../../c-runtime-library/compatibility.md) 。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [字元分類](../../c-runtime-library/character-classification.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [is、isw 常式](../../c-runtime-library/is-isw-routines.md)