---
title: 編譯器錯誤 C2490 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2490
dev_langs:
- C++
helpviewer_keywords:
- C2490
ms.assetid: 9de6bddd-b2e2-4ce6-b33b-201a8c2c8c54
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bc366178c31f900b031aacca278e39cc0c2eb493
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2490"></a>編譯器錯誤 C2490
具有 'naked' 屬性的函式中不允許 ' keyword'  
  
 函式定義為[naked](../../cpp/naked-cpp.md)無法使用結構化例外狀況處理。  
  
 下列範例會產生 C2490:  
  
```  
// C2490.cpp  
// processor: x86  
__declspec( naked ) int func() {  
   __try{}   // C2490, structured exception handling  
}  
```