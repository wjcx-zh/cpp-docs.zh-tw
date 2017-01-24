---
title: "_mbctolower、_mbctolower_l、_mbctoupper、_mbctoupper_l | Microsoft Docs"
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
  - "_mbctolower_l"
  - "_mbctoupper_l"
  - "_mbctoupper"
  - "_mbctolower"
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
  - "mbctoupper_l"
  - "mbctolower_l"
  - "_mbctolower"
  - "_mbctolower_l"
  - "_mbctoupper"
  - "mbctoupper"
  - "mbctolower"
  - "_mbctoupper_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbctolower 函式"
  - "_mbctolower_l 函式"
  - "_mbctoupper 函式"
  - "_mbctoupper_l 函式"
  - "_totlower 函式"
  - "_totupper 函式"
  - "mbctolower 函式"
  - "mbctolower_l 函式"
  - "mbctoupper 函式"
  - "mbctoupper_l 函式"
  - "totlower 函式"
  - "totupper 函式"
ms.assetid: 787fab71-3224-4ed7-bc93-4dcd8023fc54
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mbctolower、_mbctolower_l、_mbctoupper、_mbctoupper_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

測試和轉換多位元組字元的大小寫。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 Windows 執行階段執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
unsigned int _mbctolower(  
   unsigned int c   
);  
unsigned int _mbctolower_l(  
   unsigned int c,  
   _locale_t locale  
);  
unsigned int _mbctoupper(  
   unsigned int c   
);  
unsigned int _mbctoupper_l(  
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
 若轉換成功，這些函式會傳回轉換的字元 `c`。  否則會傳回未改變的字元 `c`。  
  
## 備註  
 這些函式測試字元 `c` ，並且，可能的話，會套用下列其中一個轉換。  
  
|常式|轉換|  
|--------|--------|  
|`_mbctolower,_mbctolower_l`|大寫字元轉換為小寫字元。|  
|`_mbctoupper,_mbctoupper_l`|小寫字元轉換為大寫字元。|  
  
 輸出值受地區設定的`LC_CTYPE` 分類設定所影響。如需詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md) 。  沒有 `_l` 後綴的函式版本在這些地區相依的行為上使用目前的地區設定，而有 `_l` 後綴的函式版本也是相同的，除了它們會使用傳入的地區設定參數之外。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 在舊版中， `_mbctolower` 稱為 `jtolower`，且 `_mbctoupper`  稱為 `jtoupper`。  如果是新的程式碼，請使用新的名稱。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|已定義 \_MBCS|已定義 \_UNICODE|  
|----------------|------------------------------|----------------|-------------------|  
|`_totlower`|`tolower`|`_mbctolower`|`towlower`|  
|`_totlower_l`|`_tolower_l`|`_mbctolower_l`|`_towlower_t`|  
|`_totupper`|`toupper`|`_mbctoupper`|`towupper`|  
|`_totupper_l`|`toupper_l`|`_mbctoupper_l`|`_towupper_l`|  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_mbctolower,_mbctolower_l`|\<mbstring.h\>|  
|`_mbctoupper,_mbctoupper_l`|\<mbstring.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [\_mbbtombc、\_mbbtombc\_l](../../c-runtime-library/reference/mbbtombc-mbbtombc-l.md)   
 [\_mbcjistojms、\_mbcjistojms\_l、\_mbcjmstojis、\_mbcjmstojis\_l](../../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)   
 [\_mbctohira、\_mbctohira\_l、\_mbctokata、\_mbctokata\_l](../../c-runtime-library/reference/mbctohira-mbctohira-l-mbctokata-mbctokata-l.md)   
 [\_mbctombb、\_mbctombb\_l](../../c-runtime-library/reference/mbctombb-mbctombb-l.md)