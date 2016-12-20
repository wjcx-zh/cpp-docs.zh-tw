---
title: "_mbctombb、_mbctombb_l | Microsoft Docs"
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
  - "_mbctombb_l"
  - "_mbctombb"
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
  - "_mbctombb_l"
  - "_mbctombb"
  - "mbctombb_l"
  - "mbctombb"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbctombb 函式"
  - "_mbctombb_l 函式"
  - "mbctombb 函式"
  - "mbctombb_l 函式"
ms.assetid: d90970b8-71ff-4586-b6a2-f9ceb811f776
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mbctombb、_mbctombb_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

轉換雙位元組多位元組字元至對應的單一位元組、多位元組字元。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
unsigned int _mbctombb(  
   unsigned int c   
);  
unsigned int _mbctombb_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `c`  
 要轉換的多位元組字元。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 如果成功，則 `_mbctombb` 和 `_mbctombb_l`傳回對應於 `c`的單一位元組字元;否則會傳回 `c`。  
  
## 備註  
 `_mbctombb` 和 `_mbctombb_l`函式轉換指定多位元組字元至對應的單一位元組、多位元組字元。  字元必須對應於這個範圍 0x20 內的單一位元組字元– 0x7E 或 0xA1 –要轉換的 0xDF。  
  
 輸出值受地區設定的 `LC_CTYPE`  分類設定所影響。如需詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 。  沒有 `_l` 後綴的函式版本在這些地區相依的行為上使用目前的地區設定，而有 `_l`  後綴的函式版本也是相同的，除了它們會使用傳入的地區設定參數之外。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 在舊版中， `_mbctombb` 會呼叫 `zentohan`。  請改用\_ `mbctombb`。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_mbctombb`|\<mbstring.h\>|  
|`_mbctombb_l`|\<mbstring.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [\_mbbtombc、\_mbbtombc\_l](../../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)   
 [\_mbcjistojms、\_mbcjistojms\_l、\_mbcjmstojis、\_mbcjmstojis\_l](../../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)   
 [\_mbctohira、\_mbctohira\_l、\_mbctokata、\_mbctokata\_l](../../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)   
 [\_mbctolower、\_mbctolower\_l、\_mbctoupper、\_mbctoupper\_l](../../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)