---
title: 編譯器錯誤 C3375 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3375
dev_langs:
- C++
helpviewer_keywords:
- C3375
ms.assetid: f1df78c6-e6ca-48f3-8b29-4e1710002bf3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 11805b7ef714c65ff9816828aeea10baa2217ff6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3375"></a>編譯器錯誤 C3375
'function' : 模稜兩可的委派函式  
  
 委派具現化可能已指派給靜態成員函式，或作為執行個體函式的未繫結委派，因此編譯器會發出這個錯誤。  
  
 如需詳細資訊，請參閱[委派 （c + + 元件擴充功能）](../../windows/delegate-cpp-component-extensions.md)。  
  
## <a name="example"></a>範例  
 下列範例會產生 C3375。  
  
```  
// C3375.cpp  
// compile with: /clr  
ref struct R {  
   static void f(R^) {}  
   void f() {}  
};  
  
delegate void Del(R^);  
  
int main() {  
   Del ^ a = gcnew Del(&R::f);   // C3375  
}  
```