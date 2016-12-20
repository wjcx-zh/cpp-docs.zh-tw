---
title: "_ismbbkalnum、_ismbbkalnum_l | Microsoft Docs"
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
  - "_ismbbkalnum"
  - "_ismbbkalnum_l"
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
  - "_ismbbkalnum"
  - "ismbbkalnum"
  - "ismbbkalnum_l"
  - "_ismbbkalnum_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ismbbkalnum_l 函式"
  - "ismbbkalnum_l 函式"
  - "_ismbbkalnum 函式"
  - "ismbbkalnum 函式"
ms.assetid: e1d70e7b-29d0-469c-9d93-442b99de22ac
caps.latest.revision: 19
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _ismbbkalnum、_ismbbkalnum_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

判斷特定多位元組字元是否為非 ASCII 文字符號。  
  
## 語法  
  
```  
int _ismbbkalnum(  
   unsigned int c   
);  
int _ismbbkalnum_l(  
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
 如果整數 `c` 是標點符號以外的非 ASCII 文字符號，則 `_ismbbkalnum` 會傳回非零值，否則會傳回 0。 針對地區設定相關的字元資訊，`_ismbbkalnum` 會使用目前的地區設定。`_ismbbkalnum_l` 與 `_ismbbkalnum` 相同，差別在於它接受地區設定做為參數。 如需詳細資訊，請參閱[地區設定](../../c-runtime-library/locale.md)。  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|`_ismbbkalnum`|\<mbctype.h\>|  
|`_ismbbkalnum_l`|\<mbctype.h\>|  
  
 如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 對等用法  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [位元組分類](../../c-runtime-library/byte-classification.md)   
 [\_ismbb 常式](../../c-runtime-library/ismbb-routines.md)