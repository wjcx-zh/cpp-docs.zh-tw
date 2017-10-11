---
title: "嚴重錯誤 C1020 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C1020
dev_langs:
- C++
helpviewer_keywords:
- C1020
ms.assetid: 42f429e2-5e3b-4086-a10d-b99e032e51c5
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: c2689b2526b2cf9dc513052e292aca429113c129
ms.contentlocale: zh-tw
ms.lasthandoff: 10/10/2017

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
