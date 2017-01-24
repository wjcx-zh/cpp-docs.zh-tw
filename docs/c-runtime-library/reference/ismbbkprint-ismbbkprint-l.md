---
title: "_ismbbkprint、_ismbbkprint_l | Microsoft Docs"
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
  - "_ismbbkprint"
  - "_ismbbkprint_l"
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
  - "_ismbbkprint_l"
  - "ismbbkprint"
  - "_ismbbkprint"
  - "ismbbkprint_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ismbbkprint 函式"
  - "ismbbkprint_l 函式"
  - "ismbbkprint 函式"
  - "_ismbbkprint_l 函式"
ms.assetid: 8d1d3258-1e34-4365-81ed-97c95de25475
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ismbbkprint、_ismbbkprint_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

判斷特定的多位元組字元是否為標點符號。  
  
## 語法  
  
```  
int _ismbbkprint(  
   unsigned int c   
);  
int _ismbbkprint_l(  
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
 如果整數 `c` 是非 ASCII 文字或非 ASCII 標點符號，則 `_ismbbkprint` 會傳回非零值；如果不是，則傳回 0。 例如，僅限字碼頁 932，`_ismbbkprint` 會測試片假名字母或片假名標點符號 \(範圍：0xA1 – 0xDF\)。 針對任何地區設定相關的字元設定，`_ismbbkprint` 會使用目前的地區設定。`_ismbbkprint_l`  也相同，除了它使用的是傳入的地區設定。 如需詳細資訊，請參閱 [地區設定](../../c-runtime-library/locale.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_ismbbkprint`|\<mbctype.h\>|  
|`_ismbbkprint_l`|\<mbctype.h\>|  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [位元組分類](../../c-runtime-library/byte-classification.md)   
 [\_ismbb 常式](../../c-runtime-library/ismbb-routines.md)