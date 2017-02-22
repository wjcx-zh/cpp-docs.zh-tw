---
title: "_mbcjistojms、_mbcjistojms_l、_mbcjmstojis、_mbcjmstojis_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbcjistojms"
  - "_mbcjmstojis"
  - "_mbcjistojms_l"
  - "_mbcjmstojis_l"
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
  - "mbcjistojms"
  - "_mbcjistojms"
  - "_mbcjistojms_l"
  - "_mbcjmstojis_l"
  - "_mbcjmstojis"
  - "mbcjmstojis_l"
  - "mbcjistojms_l"
  - "mbcjmstojis"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mbcjistojms 函式"
  - "_mbcjistojms_l 函式"
  - "_mbcjmstojis 函式"
  - "_mbcjmstojis_l 函式"
  - "mbcjistojms 函式"
  - "mbcjistojms_l 函式"
  - "mbcjmstojis 函式"
  - "mbcjmstojis_l 函式"
ms.assetid: dece5127-b337-40a4-aa10-53320a2c9432
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# _mbcjistojms、_mbcjistojms_l、_mbcjmstojis、_mbcjmstojis_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

日本業界標準的 \(JIS\) 之間轉換和日文 \(JMS\) Microsoft 字元。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
unsigned int _mbcjistojms(  
   unsigned int c   
);  
unsigned int _mbcjistojms_l(  
   unsigned int c,  
   _locale_t locale  
);  
unsigned int _mbcjmstojis(  
   unsigned int c   
);  
unsigned int _mbcjmstojis_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `c`  
 要進行轉換的字元。  
  
 `local`  
 要使用的地區設定。  
  
## 傳回值  
 日本地區設定，因此，如果不可能進行轉換，這些函式會傳回已轉換的字元或傳回 0。  在非日文地區設定，這些函式會傳回傳入的字元。  
  
## 備註  
 `_mbcjistojms` 函式轉換日本業界標準 \(JIS\) 的字元至 Microsoft 漢字 \(SHIFT JIS\) 字元。  只有與組織後隨位元組範圍 0x21 – 0x7E，字元轉換。  如果測試組長或位元組是在範圍內， `errno` 設定為 `EILSEQ`。  如需這項錯誤程式碼和其他變更的詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 `_mbcjmstojis` 函式會將移動 JIS 字元對 JIS 字元。  字元轉換，才前導位元組範圍 0x81 – 0x9F 或 0xE0 – 0xFC，而且後隨位元組範圍 0x40 – 0x7E 或 0x80 – 0xFC。  請注意在該範圍外的一些字碼指標沒有指定字元，因此不能轉換。  
  
 `c` 值應該是上方 8 位元代表字元前導位元組轉換，且下一個 8 位元表示後隨位元組的 16 位元值。  
  
 輸出值受地區設定的`LC_CTYPE` 分類設定所影響。如需詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 。  這些函式沒有以 `_l` 後綴的版本在這些地區相依的行為上使用目前的地區設定，而以 `_l` 後綴版本除了它們會使用傳入的地區設定參數之外運作相同。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 在舊版中， `_mbcjistojms` 和 `_mbcjmstojis` 呼叫`jistojms` 和 `jmstojis`，分別。  `_mbcjistojms`，`_mbcjistojms_l`，`_mbcjmstojis` 和`_mbcjmstojis_l`應該被取代。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_mbcjistojms`|\<mbstring.h\>|  
|`_mbcjistojms_l`|\<mbstring.h\>|  
|`_mbcjmstojis`|\<mbstring.h\>|  
|`_mbcjmstojis_l`|\<mbstring.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [\_ismbb 常式](../../c-runtime-library/ismbb-routines.md)