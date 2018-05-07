---
title: 編譯器錯誤 C2159 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2159
dev_langs:
- C++
helpviewer_keywords:
- C2159
ms.assetid: 925a2cbd-43c9-45ee-a373-84004350b380
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 412907d8c2f6c6f14adfb4f0799f3f2715a8381e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2159"></a>編譯器錯誤 C2159
已經指定一個以上的儲存類別  
  
 一個宣告包含多個儲存類別。  
  
 下列範例會產生 C2159：  
  
```  
// C2159.cpp  
// compile with: /c  
static int i;   // OK  
extern static int i;   // C2159  
```