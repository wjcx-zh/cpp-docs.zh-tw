---
title: 編譯器錯誤 C2293 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2293
dev_langs:
- C++
helpviewer_keywords:
- C2293
ms.assetid: 17e7b4e2-368b-4dd7-a01b-d82be60f8e56
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6b3f395199a1621d507683aa6c79b1212888145
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2293"></a>編譯器錯誤 C2293
'identifier': 將 __based 規範作為成員變數不合法  
  
 `__based` 修飾詞的規範必須是非成員的指標。  
  
 下列範例會產生 C2293：  
  
```  
// C2293.cpp  
// compile with: /c  
class A {  
   static int *i;  
   void __based(i) *bp;   // C2293  
   void *bp2;   // OK  
};  
```