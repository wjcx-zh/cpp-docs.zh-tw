---
title: 編譯器錯誤 C2509 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2509
dev_langs:
- C++
helpviewer_keywords:
- C2509
ms.assetid: 339c1fcd-ec4a-456c-9f18-a9b24d9921af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9dc6ed32246b662282bf6fa385f648df3635f3e3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2509"></a>編譯器錯誤 C2509
'identifier': 'class' 中未宣告的成員函式  
  
 在指定的類別未宣告的函式。  
  
## <a name="example"></a>範例  
 下列範例會產生 C2509。  
  
```  
// C2509.cpp  
// compile with: /c  
struct A {  
   virtual int vfunc() = 0;  
   virtual int vfunc2() = 0;  
};  
  
struct B : private A {  
   using A::vfunc;  
   virtual int vfunc2();  
};  
  
int B::vfunc() { return 1; }   // C2509  
int B::vfunc2() { return 1; }   // OK  
```