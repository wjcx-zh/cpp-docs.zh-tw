---
title: "常數和全域變數對應 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _tenviron
- _TEOF
- _tfinddata_t
dev_langs:
- C++
helpviewer_keywords:
- tfinddatat function
- tenviron function
- TEOF type
- _TEOF type
- generic-text mappings
- _tenviron function
- _tfinddata_t function
ms.assetid: 3af4fd3e-9ed5-4ed9-96fd-7031e5126fd1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bb767bb3dbfbde8d73ab81acc444a772a05e7880
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="constant-and-global-variable-mappings"></a>常數和全域變數對應
這些泛型文字常數、全域變數和標準類型對應都是在 TCHAR.H 中定義，並視程式中是否定義常數 `_UNICODE` 或 `_MBCS` 而定。  
  
### <a name="generic-text-constant-and-global-variable-mappings"></a>泛型文字常數和全域變數對應  
  
|泛型文字 - 物件名稱|SBCS (_UNICODE、_MBCS 未定義)|_MBCS 已定義|_UNICODE 已定義|  
|----------------------------------|--------------------------------------------|--------------------|-----------------------|  
|`_TEOF`|`EOF`|`EOF`|`WEOF`|  
|`_tenviron`|`_environ`|`_environ`|`_wenviron`|  
|`_tpgmptr`|`_pgmptr`|`_pgmptr`|`_wpgmptr`|  
  
## <a name="see-also"></a>請參閱  
 [泛型文字對應](../c-runtime-library/generic-text-mappings.md)   
 [資料類型對應](../c-runtime-library/data-type-mappings.md)   
 [常式對應](../c-runtime-library/routine-mappings.md)   
 [泛型文字程式範例](../c-runtime-library/a-sample-generic-text-program.md)   
 [使用泛型文字對應](../c-runtime-library/using-generic-text-mappings.md)