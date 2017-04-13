---
title: "編譯器錯誤 C3375 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3375
dev_langs:
- C++
helpviewer_keywords:
- C3375
ms.assetid: f1df78c6-e6ca-48f3-8b29-4e1710002bf3
caps.latest.revision: 5
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: fdf91445a1a6594b8b708dfbf43ff8ad86993c51
ms.lasthandoff: 04/12/2017

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
