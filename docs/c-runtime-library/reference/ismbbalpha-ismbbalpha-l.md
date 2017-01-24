---
title: "_ismbbalpha、_ismbbalpha_l | Microsoft Docs"
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
  - "_ismbbalpha"
  - "_ismbbalpha_l"
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
  - "ismbbalpha"
  - "ismbbalpha_l"
  - "_ismbbalpha"
  - "_ismbbalpha_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "ismbbalpha 函式"
  - "ismbbalpha_l 函式"
  - "_ismbbalpha 函式"
  - "_ismbbalpha_l 函式"
ms.assetid: 8e54cb92-fc2b-41f5-8ab4-b22ac8aa9ad0
caps.latest.revision: 18
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ismbbalpha、_ismbbalpha_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

判斷指定的多位元組字元是否為 alpha。  
  
## 語法  
  
```  
int _ismbbalpha(  
   unsigned int c   
);  
int _ismbbalpha_l(  
   unsigned int c   
);  
```  
  
#### 參數  
 `c`  
 待測試整數。  
  
 `locale`  
 要使用的地區設定。  
  
## 傳回值  
 `_ismbbalpha` 傳回非零值表示運算式：  
  
```  
isalpha || _ismbbkalnum  
```  
  
 非零代表 `c`，0 則代表不是。 針對任何地區設定相關的字元設定，`_ismbbalpha` 會使用目前的地區設定。`_ismbbalpha_l` 也相同，除了它使用的是傳入的地區設定。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_ismbbalpha`|\<mbctype.h\>|  
|`_ismbbalpha_l`|\<mbctype.h\>|  
  
 如需詳細的相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## .NET Framework 對等用法  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [位元組分類](../../c-runtime-library/byte-classification.md)   
 [\_ismbb 常式](../../c-runtime-library/ismbb-routines.md)