---
title: 嚴重錯誤 C1020 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1020
dev_langs:
- C++
helpviewer_keywords:
- C1020
ms.assetid: 42f429e2-5e3b-4086-a10d-b99e032e51c5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1c70727b5e0d83b03099b637e0f768f65d271b05
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33224635"
---
# <a name="fatal-error-c1020"></a>嚴重錯誤 C1020
未預期的 #endif  
  
 `#endif` 指示詞沒有對應的 `#if`、 `#ifdef`或 `#ifndef` 指示詞。 每個 `#endif` 都一定要有對應的指示詞。  
  
 下列範例會產生 C1020：  
  
```  
// C1020.cpp  
#endif     // C1020  
```  
  
 可能的解決方式：  
  
```  
// C1020b.cpp  
// compile with: /c  
#if 1  
#endif  
```