---
title: "_ismbblead、_ismbblead_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_ismbblead_l"
  - "_ismbblead"
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
  - "ismbblead_l"
  - "istlead"
  - "_ismbblead"
  - "_ismbblead_l"
  - "ismbblead"
  - "_istlead"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ismbblead_l 函式"
  - "ismbblead 函式"
  - "_ismbblead 函式"
  - "istlead 函式"
  - "ismbblead_l 函式"
  - "_istlead 函式"
ms.assetid: 2abc6f75-ed5c-472e-bfd0-e905a1835ccf
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# _ismbblead、_ismbblead_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

測試字元以判斷是否為多位元組字元的的前導位元組。  
  
## 語法  
  
```  
int _ismbblead(  
   unsigned int c   
);  
int _ismbblead_l(  
   unsigned int c,  
   _locale_t locale  
);  
```  
  
#### 參數  
 `c`  
 待測試整數。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 如果整數 `c` 是多位元組字元的第一個位元組，則會傳回非零值。  
  
## 備註  
 多位元組字元是由一個前導位元組，後面接著一個後置位元組所組成。 前導位元組會以所處指定字元集的特定範圍來識別。 例如，單獨在字碼頁 932 中，前導位元組的範圍為 0x81\-0x9F 和 0xE0\-0xFC。  
  
 `_ismbblead` 使用目前的地區設定進行地區設定相關行為。`_ismbblead_l` 也相同，但是它會改用傳入的地區設定。 如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE 和 \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|----------------------------|----------------|-------------------|  
|`_istlead`|一律傳回 false|`_ismbblead`|一律傳回 false|  
  
## 需求  
  
|常式|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_ismbblead`|\<mbctype.h\> 或 \<mbstring.h\>|\<ctype.h\>、\* \<limits.h\>、\<stdlib.h\>|  
|`_ismbblead_l`|\<mbctype.h\> 或 \<mbstring.h\>|\<ctype.h\>、\* \<limits.h\>、\<stdlib.h\>|  
  
 \* 針對此測試條件的資訊清單常數。  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [位元組分類](../../c-runtime-library/byte-classification.md)   
 [\_ismbb 常式](../../c-runtime-library/ismbb-routines.md)