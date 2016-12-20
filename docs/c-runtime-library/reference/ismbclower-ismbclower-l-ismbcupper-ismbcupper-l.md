---
title: "_ismbclower、_ismbclower_l、_ismbcupper、_ismbcupper_l | Microsoft Docs"
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
  - "_ismbclower"
  - "_ismbclower_l"
  - "_ismbcupper_l"
  - "_ismbcupper"
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
  - "_ismbcupper"
  - "_ismbclower"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ismbclower 函式"
  - "_ismbclower_l 函式"
  - "_ismbcupper 函式"
  - "_ismbcupper_l 函式"
  - "ismbclower 函式"
  - "ismbclower_l 函式"
  - "ismbcupper 函式"
  - "ismbcupper_l 函式"
ms.assetid: 17d89587-65bc-477c-ba8f-a84e63cf59e7
caps.latest.revision: 19
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ismbclower、_ismbclower_l、_ismbcupper、_ismbcupper_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

檢查多位元組字元為大寫或小寫。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
int _ismbclower(  
   unsigned int c   
);  
int _ismbclower_l(  
   unsigned int c,  
   _locale_t locale   
);  
int _ismbcupper(  
   unsigned int c   
);  
int _ismbcupper_l(  
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
|`_ismbclower`|小寫字母|傳回非零，在只有當 `c` 是 ASCII 小寫英文字母的單一位元組表示：0x61\=\<`c`\<\=0x7A。|  
|`_ismbclower_l`|小寫字母|傳回非零，在只有當 `c` 是 ASCII 小寫英文字母的單一位元組表示：0x61\=\<`c`\<\=0x7A。|  
|`_ismbcupper`|大寫字母|傳回非零，在只有當 `c` 是 ASCII 大寫英文字母的單一位元組表示：0x41\=\<`c`\<\=0x5A。|  
|`_ismbcupper_l`|大寫字母|傳回非零，在只有當 `c` 是 ASCII 大寫英文字母的單一位元組表示：0x41\=\<`c`\<\=0x5A。|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_ismbclower`|\<mbstring.h\>|  
|`_ismbclower_l`|\<mbstring.h\>|  
|`_ismbcupper`|\<mbstring.h\>|  
|`_ismbcupper_l`|\<mbstring.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
  
-   [System::Char::IsLower](https://msdn.microsoft.com/en-us/library/system.char.islower.aspx)  
  
-   [System::Char::IsUpper](https://msdn.microsoft.com/en-us/library/system.char.isupper.aspx)  
  
## 請參閱  
 [字元分類](../../c-runtime-library/character-classification.md)   
 [\_ismbc 常式](../../c-runtime-library/ismbc-routines.md)   
 [地區設定](../../c-runtime-library/locale.md)   
 [多位元組字元序列的解譯](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [is、isw 常式](../../c-runtime-library/is-isw-routines.md)   
 [\_ismbb 常式](../../c-runtime-library/ismbb-routines.md)