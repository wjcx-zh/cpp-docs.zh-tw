---
title: "_mbctohira、_mbctohira_l、_mbctokata、_mbctokata_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mbctohira"
  - "_mbctohira_l"
  - "_mbctokata"
  - "_mbctokata_l"
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
  - "_mbctokata"
  - "mbctohira"
  - "_mbctohira"
  - "_mbctohira_l"
  - "mbctokata"
  - "mbctokata_l"
  - "mbctohira_l"
  - "_mbctokata_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_mbctohira 函式"
  - "_mbctohira_l 函式"
  - "_mbctokata 函式"
  - "_mbctokata_l 函式"
  - "mbctohira 函式"
  - "mbctohira_l 函式"
  - "mbctokata 函式"
  - "mbctokata_l 函式"
ms.assetid: f949afd7-44d4-4f08-ac8f-1fef2c915a1c
caps.latest.revision: 19
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _mbctohira、_mbctohira_l、_mbctokata、_mbctokata_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

轉換平假名和片假名字元。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
unsigned int _mbctohira(  
   unsigned int c   
);  
unsigned int _mbctohira_l(  
   unsigned int c,  
   _locale_t locale  
);  
unsigned int _mbctokata(  
   unsigned int c   
);  
unsigned int _mbctokata_l(  
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
 如果可能，所有這些函式都會傳回已轉換的字元 `c`。  否則會傳回未變更的字元 `c`。  
  
## 備註  
 `_mbctohira` 和 `_mbctokata` 函式會測試字元 `c`，如果可能的話，還會套用下列其中一個轉換。  
  
|常式|轉換|  
|--------|--------|  
|`_mbctohira,_mbctohira_l`|多位元組片假名到多位元組平假名。|  
|`_mbctokata,_mbctokata_l`|多位元組平假名到多位元組片假名。|  
  
 輸出值會受到地區設定的 `LC_CTYPE` 類別設定影響；如需詳細資訊，請參閱 [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)。  這些函式的版本均相同，除了沒有 `_l` 後置碼的函式會針對此地區設定的相關行為使用目前的地區設定，而具有 `_l` 後置詞的函式會改用傳入的地區設定參數。  如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
 在舊版中，`_mbctohira` 名為 `jtohira`，而 `_mbctokata` 名為 `jtokata`。  對於新的程式碼，請使用新名稱。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_mbctohira`|\<mbstring.h\>|  
|`_mbctohira_l`|\<mbstring.h\>|  
|`_mbctokata`|\<mbstring.h\>|  
|`_mbctokata_l`|\<mbstring.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [資料轉換](../../c-runtime-library/data-conversion.md)   
 [\_mbcjistojms、\_mbcjistojms\_l、\_mbcjmstojis、\_mbcjmstojis\_l](../../c-runtime-library/reference/mbcjistojms-mbcjistojms-l-mbcjmstojis-mbcjmstojis-l.md)   
 [\_mbctolower、\_mbctolower\_l、\_mbctoupper、\_mbctoupper\_l](../../c-runtime-library/reference/mbctolower-mbctolower-l-mbctoupper-mbctoupper-l.md)   
 [\_mbctombb、\_mbctombb\_l](../../c-runtime-library/reference/mbctombb-mbctombb-l.md)