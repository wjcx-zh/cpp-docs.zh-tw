---
title: 編譯器錯誤 C3644 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3644
dev_langs:
- C++
helpviewer_keywords:
- C3644
ms.assetid: 2e3f6c41-3ec5-4a01-82bc-f11b61ebe68e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a63f191251ecdc53ee082d69b9bbafb9e23b74c8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33264940"
---
# <a name="compiler-error-c3644"></a>編譯器錯誤 C3644
'function': 無法編譯要產生 managed 程式碼的函式  
  
 函式中的某些關鍵字會導致編譯為原生函式。  
  
 下列範例會產生 C3644:  
  
```  
// C3644.cpp  
// compile with: /clr  
// processor: x86  
  
void __clrcall Func2(int i) {  
   __asm {}   // C3644  
}  
```