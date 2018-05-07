---
title: 編譯器錯誤 C2735 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2735
dev_langs:
- C++
helpviewer_keywords:
- C2735
ms.assetid: 6ce45600-7148-4bc0-8699-af0ef137571e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ab970aa4e46ed0206f311e100f7ee777907aff8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2735"></a>編譯器錯誤 C2735
在型式參數類型規範中不允許 'keyword' 關鍵字  
  
 關鍵字在此內容中無效。  
  
 下列範例會產生 C2735:  
  
```  
// C2735.cpp  
void f(inline int){}   // C2735  
```