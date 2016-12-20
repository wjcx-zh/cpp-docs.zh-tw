---
title: "_ismbchira、_ismbchira_l、_ismbckata、_ismbckata_l | Microsoft Docs"
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
  - "_ismbckata"
  - "_ismbchira_l"
  - "_ismbchira"
  - "_ismbckata_l"
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
  - "ismbckata_l"
  - "_ismbckata_l"
  - "ismbckata"
  - "ismbchira"
  - "_ismbckata"
  - "ismbchira_l"
  - "_ismbchira_l"
  - "_ismbchira"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ismbchira 函式"
  - "_ismbchira_l 函式"
  - "_ismbckata 函式"
  - "_ismbckata_l 函式"
  - "平假名"
  - "ismbchira 函式"
  - "ismbchira_l 函式"
  - "ismbckata 函式"
  - "ismbdkata_l 函式"
  - "片假名"
ms.assetid: 2db388a2-be31-489b-81c8-f6bf3f0582d3
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ismbchira、_ismbchira_l、_ismbckata、_ismbckata_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**字碼頁 932 特定功能**  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int _ismbchira(  
   unsigned int c   
);  
int _ismbchira_l(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbckata(  
   unsigned int c   
);  
int _ismbckata_l(  
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
 如果字元符合測試條件，這些常式都會傳回非零值，如果不符合，則傳回 0。  如果 `c`\< \= 255 且有個對應 `_ismbb`  常式 \(例如， `_ismbcalnum`  對應於 `_ismbbalnum`\)，則結果為對應的 `_ismbb` 方法的傳回值。  
  
## 備註  
 這些函式每一個都會測試指定的多位元組字元是否符合指定的條件。  
  
 尾碼為 `_l` 的這些函式版本是一樣的，只不過與地區設定相關的行為使用了傳入的地區設定，而不是目前的地區設定。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
|常式|測試條件 \(唯獨字碼頁 932\)|  
|--------|------------------------|  
|`_ismbchira`|雙位元組平假名: 0x829F\=\<`c`\<\=0x82F1。|  
|`_ismbchira_l`|雙位元組平假名: 0x829F\=\<`c`\<\=0x82F1。|  
|`_ismbckata`|雙位元組片假名: 0x8340\=\<`c`\<\=0x8396。|  
|`_ismbckata_l`|雙位元組片假名: 0x8340\=\<`c`\<\=0x8396。|  
  
 **結束字碼頁 932 詳情**  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_ismbchira`|\<mbstring.h\>|  
|`_ismbchira_l`|\<mbstring.h\>|  
|`_ismbckata`|\<mbstring.h\>|  
|`_ismbckata_l`|\<mbstring.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [字元分類](../../c-runtime-library/character-classification.md)   
 [\_ismbc 常式](../../c-runtime-library/ismbc-routines.md)   
 [is、isw 常式](../../c-runtime-library/is-isw-routines.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)