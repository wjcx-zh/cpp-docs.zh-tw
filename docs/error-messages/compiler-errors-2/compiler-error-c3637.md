---
title: 編譯器錯誤 C3637 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3637
dev_langs:
- C++
helpviewer_keywords:
- C3637
ms.assetid: 72391377-8519-43d9-870a-73a6423deb74
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29ae2ddb9e55363c54451a0b30199d9ae7503f05
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33263592"
---
# <a name="compiler-error-c3637"></a>編譯器錯誤 C3637
'function': friend 函式定義不能為函式類型的特製化  
  
 Friend 函式的樣板或泛型定義不正確。  
  
 下列範例會產生 C3637:  
  
```  
// C3637.cpp  
template <class T>  
void f();  
  
struct S {  
   friend void f<int>() {}   // C3637  
};  
```  
  
 可能的解決方式：  
  
```  
// C3637b.cpp  
// compile with: /c  
template <class T>  
void f();  
  
struct S {  
   friend void f() {}  
};  
```  
  
 使用泛型時，也會發生 C3637:  
  
```  
// C3637c.cpp  
// compile with: /clr  
  
generic <class T>  
void gf();  
  
struct S {  
   friend void gf<int>() {}   // C3637  
};  
```  
  
 可能的解決方式：  
  
```  
// C3637d.cpp  
// compile with: /clr /c  
generic <class T>  
void gf();  
  
struct S {  
   friend void gf() {}  
};  
```