---
title: 編譯器錯誤 C2134 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2134
dev_langs:
- C++
ms.assetid: d45cb3e8-0be4-4bd6-8be9-5f8d2384363f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8390e720e1a4389e43c263faf0c7582eaccfceec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2134"></a>編譯器錯誤 C2134
'function': 呼叫未產生常數運算式中  
  
 宣告為 constexpr 只能呼叫其他函式的函式宣告為 constexpr。  
  
 下列範例會產生 C2134:  
  
```  
// C2134.cpp  
// compile with: /c  
int A() {  
    return 42;  
};  
  
constexpr int B() {  
    return A();  // Error C2134: 'A': call does not result in a constant expression.  
}  
```  
  
 可能的解決方式：  
  
```  
// C2134b.cpp  
constexpr int A() {  // add constexpr to A, since it meets the requirements of constexpr.  
    return 42;  
};  
  
constexpr int B() {  
    return A();  // No error  
}  
```