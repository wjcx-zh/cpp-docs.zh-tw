---
title: 編譯器錯誤 C2452 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2452
dev_langs:
- C++
helpviewer_keywords:
- C2452
ms.assetid: a4ec7642-6660-4c7a-9866-853d1cc67daf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f4d30de808600c34270c8576adb371497af169aa
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2452"></a>編譯器錯誤 C2452
'type': 對 safe_cast 無效的來源類型  
  
 來源類型[safe_cast](../../windows/safe-cast-cpp-component-extensions.md)不正確。  例如中的所有類型`safe_cast`作業必須是 CLR 型別。  
  
 下列範例會產生 C2452:  
  
```  
// C2452.cpp  
// compile with: /clr  
  
struct A {};  
struct B : public A {};  
  
ref struct C {};  
ref struct D : public C{};  
  
int main() {  
   A a;  
   safe_cast<B*>(&a);   // C2452  
  
   // OK  
   C ^ c = gcnew C;  
   safe_cast<D^>(c);  
}  
```