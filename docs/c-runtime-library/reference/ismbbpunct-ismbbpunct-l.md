---
title: "_ismbbpunct、_ismbbpunct_l | Microsoft Docs"
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
  - "_ismbbpunct"
  - "_ismbbpunct_l"
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
  - "ismbbpunct"
  - "ismbbpunct_l"
  - "_ismbbpunct_l"
  - "_ismbbpunct"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "ismbbpunct 函式"
  - "_ismbbpunct 函式"
  - "ismbbpunct_l 函式"
  - "_ismbbpunct_l 函式"
ms.assetid: 1976c9d3-7d1a-415f-ac52-2715c7bb56eb
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ismbbpunct、_ismbbpunct_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

判斷特定字元是否為標點符號字元。  
  
## 語法  
  
```  
int _ismbbpunct(  
   unsigned int c   
);  
int _ismbbpunct_l(  
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
 如果整數 `c` 是非 ASCII 標點符號，則 `_ismbbpunct` 會傳回非零值。 針對任何地區設定相關的字元設定，`_ismbbpunct` 會使用目前的地區設定。`_ismbbpunct_l` 也相同，但是它會用傳入的地區設定。 如需詳細資訊，請參閱 [地區設定](../../c-runtime-library/locale.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_ismbbpunct`|\<mbctype.h\>|  
|`_ismbbpunct_l`|\<mbctype.h\>|  
  
 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [位元組分類](../../c-runtime-library/byte-classification.md)   
 [\_ismbb 常式](../../c-runtime-library/ismbb-routines.md)