---
title: "_ismbcalnum、_ismbcalnum_l、_ismbcalpha、_ismbcalpha_l、_ismbcdigit、_ismbcdigit_l | Microsoft Docs"
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
  - "_ismbcalpha"
  - "_ismbcalnum"
  - "_ismbcdigit"
  - "_ismbcalnum_l"
  - "_ismbcdigit_l"
  - "_ismbcalpha_l"
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
  - "_ismbcdigit"
  - "ismbcalnum_l"
  - "_ismbcdigit_l"
  - "_ismbcalpha"
  - "ismbcalnum"
  - "ismbcdigit"
  - "ismbcalpha"
  - "_ismbcalnum_l"
  - "_ismbcalnum"
  - "ismbcdigit_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ismbcalnum 函式"
  - "_ismbcalnum_l 函式"
  - "_ismbcalpha 函式"
  - "_ismbcalpha_l 函式"
  - "_ismbcdigit 函式"
  - "_ismbcdigit_l 函式"
  - "ismbcalnum 函式"
  - "ismbcalnum_l 函式"
  - "ismbcalpha 函式"
  - "ismbcalpha_l 函式"
  - "ismbcdigit 函式"
  - "ismbcdigit_l 函式"
ms.assetid: 12d57925-aebe-46e0-80b0-82b84c4c31ec
caps.latest.revision: 22
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ismbcalnum、_ismbcalnum_l、_ismbcalpha、_ismbcalpha_l、_ismbcdigit、_ismbcdigit_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

檢查多位元組字元是英數字元、Alpha 或數字字元。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int _ismbcalnum  
(  
   unsigned int c   
);  
int _ismbcalnum_l  
(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcalpha  
(  
   unsigned int c   
);  
int _ismbcalpha_l  
(  
   unsigned int c,  
   _locale_t locale  
);  
int _ismbcdigit  
(  
   unsigned int c   
);  
int _ismbcdigit_l  
(  
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
 這些常式每一個都會測試指定的多位元組字元是否符合指定的條件。  
  
 尾碼為 `_l` 的這些函式版本是一樣的，只不過與地區設定相關的行為使用了傳入的地區設定，而不是目前的地區設定。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
|常式|測試條件|字碼頁 932 範例|  
|--------|----------|----------------|  
|`_ismbcalnum,_ismbcalnum_l`|英數字元。|只有當 `c` 是 ASCII 英文字母的單一位元組表示才傳回非零：請參閱範例 `_ismbcdigit` 和 `_ismbcalpha`。|  
|`_ismbcalpha,_ismbcalpha_l`|字母順序|只有當 `c` 是 ASCII 英文字母的單一位元組表示才傳回非零：0x41\=\<`c`\<\=0x5A 或 0x61\=\<`c`\<\=0x7A;或片假名字母:0xA6\=\<`c`\<\=0xDF。|  
|`_ismbcdigit,_ismbcdigit`|數字順序|只有當 `c` 是 ASCII 數字的單一位元組表示才傳回非零：0x30\=\<`c`\<\=0x39。|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_ismbcalnum,_ismbcalnum_l`|\<mbstring.h\>|  
|`_ismbcalpha,_ismbcalpha_l`|\<mbstring.h\>|  
|`_ismbcdigit,_ismbcdigit_l`|\<mbstring.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
  
-   [System::Char::IsLetter](https://msdn.microsoft.com/en-us/library/system.char.isletter.aspx)  
  
-   [System::Char::IsDigit](https://msdn.microsoft.com/en-us/library/system.char.isdigit.aspx)  
  
-   不適用於`_ismbcalnum`。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [字元分類](../../c-runtime-library/character-classification.md)   
 [\_ismbc 常式](../../c-runtime-library/ismbc-routines.md)   
 [is、isw 常式](../../c-runtime-library/is-isw-routines.md)   
 [\_ismbb 常式](../../c-runtime-library/ismbb-routines.md)