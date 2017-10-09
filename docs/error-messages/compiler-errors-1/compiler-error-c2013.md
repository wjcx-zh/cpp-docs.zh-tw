---
title: "編譯器錯誤 C2013 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2013
dev_langs:
- C++
helpviewer_keywords:
- C2013
ms.assetid: 6b5c955c-53da-48ee-8533-64ef5b905173
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 23fdceda3b40a657301e8909c6847e9d596eb24d
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2013"></a>編譯器錯誤 C2013
遺漏 '>'  
  
 `#include` 指示詞缺少右角括弧。 加入右角括弧，以解決錯誤。  
  
 下列範例會產生 C2013：  
  
```  
// C2013.cpp  
#include <stdio.h    // C2013  
```  
  
 可能的解決方式：  
  
```  
// C2013b.cpp  
// compile with: /c  
#include <stdio.h>  
```
