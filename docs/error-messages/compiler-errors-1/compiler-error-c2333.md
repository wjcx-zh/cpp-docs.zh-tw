---
title: 編譯器錯誤 C2333 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2333
dev_langs:
- C++
helpviewer_keywords:
- C2333
ms.assetid: 2636fc1e-d3e7-4e68-8628-3c81a99ba813
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a1613d560ef22c33ca1a19ac63584138a18c19c4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2333"></a>編譯器錯誤 C2333
'function': 函式宣告; 中的錯誤略過函式主體  
  
 在類別內定義的成員函式的另一個錯誤之後，會發生這個錯誤。  
  
 下列範例會產生 C2333:  
  
```  
// C2333.cpp  
struct s1 {  
   s1(s1) {}   // C2333  
};  
```