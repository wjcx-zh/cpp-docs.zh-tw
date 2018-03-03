---
title: "指定條件式編譯 A.2 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: de4a21b9-f987-4738-9f13-c4795f6f2dff
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 93557eaae2c8661697f7bda383b50f2e1ba9e2cb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="a2---specifying-conditional-compilation"></a>A.2 指定條件式編譯
下列範例說明使用 OpenMP 巨集的條件式編譯使用`_OPENMP`([2.2 節](../../parallel/openmp/2-2-conditional-compilation.md)在 8 頁面上)。 使用 /openmp 編譯`_OPENMP`會變成已定義巨集。  
  
```  
# ifdef _OPENMP   
    printf_s("Compiled by an OpenMP-compliant implementation.\n");  
# endif  
```  
  
 定義前置處理器運算子可讓多個測試在單一的指示詞中的巨集。  
  
```  
# if defined(_OPENMP) && defined(VERBOSE)  
    printf_s("Compiled by an OpenMP-compliant implementation.\n");  
# endif  
```