---
title: "常數和全域變數對應 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_tenviron"
  - "_TEOF"
  - "_tfinddata_t"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_tenviron 函式"
  - "_TEOF 類型"
  - "_tfinddata_t 函式"
  - "泛用文字對應"
  - "tenviron 函式"
  - "TEOF 類型"
  - "tfinddatat 函式"
ms.assetid: 3af4fd3e-9ed5-4ed9-96fd-7031e5126fd1
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 常數和全域變數對應
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

這些泛用文字常數、全域變數和在 TCHAR.H 定義標準型別對應視常數 `_UNICODE` 或 `_MBCS` 是否在程式中定義而定。  
  
### 泛用文字常數和全域變數對應  
  
|泛用文字\-物件名稱|SBCS \(\_UNICODE, \_MBCS 未定義\)|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|------------------------------------|----------------|-------------------|  
|`_TEOF`|`EOF`|`EOF`|`WEOF`|  
|`_tenviron`|`_environ`|`_environ`|`_wenviron`|  
|`_tpgmptr`|`_pgmptr`|`_pgmptr`|`_wpgmptr`|  
  
## 請參閱  
 [泛型文字對應](../c-runtime-library/generic-text-mappings.md)   
 [資料類型對應](../c-runtime-library/data-type-mappings.md)   
 [常式對應](../c-runtime-library/routine-mappings.md)   
 [泛型文字程式範例](../c-runtime-library/a-sample-generic-text-program.md)   
 [使用泛型文字對應](../c-runtime-library/using-generic-text-mappings.md)