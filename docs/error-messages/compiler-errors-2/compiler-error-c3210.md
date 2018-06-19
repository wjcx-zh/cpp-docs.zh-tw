---
title: 編譯器錯誤 C3210 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3210
dev_langs:
- C++
helpviewer_keywords:
- C3210
ms.assetid: c6e9d309-fabc-4e7d-b526-be20d9fe3f6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 24146139fce7a1e42e112f913ab35ca425a9d5d7
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256515"
---
# <a name="compiler-error-c3210"></a>編譯器錯誤 C3210
'type': 存取宣告只能套用至基底類別成員  
  
 A [using 宣告](../../cpp/using-declaration.md)指定不正確。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3210。  
  
```  
// C3210.cpp  
// compile with: /c  
struct A {  
protected:  
   int i;  
};  
  
struct B {  
   using A::i;   // C3210  
};  
  
struct C : public A {  
   using A::i;   // OK  
};  
```