---
title: 編譯器錯誤 C2344 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2344
dev_langs:
- C++
helpviewer_keywords:
- C2344
ms.assetid: a84c7b37-c84e-4345-8691-c23abb2dc193
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cdbe2ac9c1533a22e5e77f1d3f2db5c73ef93a3e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2344"></a>編譯器錯誤 C2344
align(#): 使用 align 規範必須是 2 的乘冪  
  
 使用 [align](../../cpp/align-cpp.md) 關鍵字時，您傳遞的值必須是 2 的乘冪。  
  
 例如，下列程式碼會產生 C2344，因為 3 不是 2 的乘冪：  
  
```  
// C2344.cpp  
// compile with: /c  
__declspec(align(3)) int a;   // C2344  
__declspec(align(4)) int b;   // OK  
```