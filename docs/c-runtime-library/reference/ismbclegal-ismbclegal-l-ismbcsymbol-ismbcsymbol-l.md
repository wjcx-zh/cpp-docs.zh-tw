---
title: "_ismbclegal、_ismbclegal_l、_ismbcsymbol、_ismbcsymbol_l | Microsoft Docs"
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
  - "_ismbclegal_l"
  - "_ismbclegal"
  - "_ismbcsymbol"
  - "_ismbcsymbol_l"
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
  - "api-ms-win-crt-multibyte-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "ismbcsymbol_l"
  - "_ismbcsymbol_l"
  - "_ismbcsymbol"
  - "_ismbclegal_l"
  - "_ismbclegal"
  - "ismbclegal_l"
  - "ismbcsymbol"
  - "ismbclegal"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ismbclegal 函式"
  - "_ismbclegal_l 函式"
  - "_ismbcsymbol 函式"
  - "_ismbcsymbol_l 函式"
  - "_istlegal 函式"
  - "_istlegal_l 函式"
  - "ismbclegal 函式"
  - "ismbclegal_l 函式"
  - "ismbcsymbol 函式"
  - "ismbcsymbol_l 函式"
  - "istlegal 函式"
  - "istlegal_l 函式"
ms.assetid: 31bf1ea5-b56f-4e28-b21e-b49a2cf93ffc
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ismbclegal、_ismbclegal_l、_ismbcsymbol、_ismbcsymbol_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

檢查一個多位元組字元是否為合法或符號字元。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int _ismbclegal(  
   unsigned int c   
);  
int _ismbclegal_l(  
   unsigned int c,   
   _locale_t locale  
);  
int _ismbcsymbol(  
   unsigned int c   
);  
int _ismbcsymbol_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `c`  
 待測試字元。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 如果字元符合測試條件，這些常式都會傳回非零值，如果不符合，則傳回 0。  如果 `c`\<\= 255 且有個對應 `_ismbb` 常式 \(例如， `_ismbcalnum` 對應於 `_ismbbalnum`\)，則結果為對應的 `_ismbb` 方法的傳回值。  
  
## 備註  
 這些函式每一個都會測試指定的多位元組字元是否符合指定的條件。  
  
 尾碼為 `_l` 的這些函式版本是一樣的，只不過與地區設定相關的行為使用了傳入的地區設定，而不是目前的地區設定。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
|常式|測試條件|字碼頁 932 範例|  
|--------|----------|----------------|  
|`_ismbclegal`|有效的多位元組|只有在`c`的第一個位元組範圍為 0x81 \- 0x9F 之間或 0xE0 – 0xFC 之間，而第二個位元組位於範圍 0x40 \- 0x7E 或 0x80 \- FC 之間才會傳回非零值。|  
|`_ismbcsymbol`|多位元組的符號|只有在 0x8141\=\<`c`\<\=0x81AC時才會傳回非零值。|  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_istlegal`|一律傳回 false|`_ismbclegal`|一律傳回 false。|  
|`_istlegal_l`|一律傳回 false|`_ismbclegal_l`|一律傳回 false。|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_ismbclegal,_ismbclegal_l`|\<mbstring.h\>|  
|`_ismbcsymbol,_ismbcsymbol_l`|\<mbstring.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [字元分類](../../c-runtime-library/character-classification.md)   
 [\_ismbc 常式](../../c-runtime-library/ismbc-routines.md)   
 [is、isw 常式](../../c-runtime-library/is-isw-routines.md)   
 [\_ismbb 常式](../../c-runtime-library/ismbb-routines.md)