---
title: "編譯器錯誤 C2682 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2682
dev_langs:
- C++
helpviewer_keywords:
- C2682
ms.assetid: 30c6a7c4-f5f7-4fe8-81a8-c48938521ab4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bb8015b580958fd8bd70488f2894360708ccf30c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2682"></a>編譯器錯誤 C2682
無法使用 casting_operator 要從 'type1' 轉換成 'type2'  
  
 轉型運算子嘗試以不相容的類型之間轉換。 例如，您不能使用[dynamic_cast](../../cpp/dynamic-cast-operator.md)運算子將指標轉換為參考。 `dynamic_cast`運算子無法用來轉換離開限定詞。 必須符合所有類型的限定詞。  
  
 您可以使用`const_cast`運算子，例如移除屬性`const`， `volatile`，或`__unaligned`。  
  
 下列範例會產生 C2682:  
  
```  
// C2682.cpp  
class A { virtual void f(); };  
class B: public A {};  
  
void g(A* pa) {  
    B& rb = dynamic_cast<B&>(pa); // C2682  
}  
```  
  
 下列範例會產生 C2682:  
  
```  
// C2682b.cpp  
// compile with: /clr  
ref struct R{};  
ref struct RR : public R{};  
ref struct H {  
   RR^ r ;  
   short s;  
   int i;  
};  
  
int main() {  
   H^ h = gcnew H();    
   interior_ptr<int>lr = &(h->i);  
   interior_ptr<short>ssr = safe_cast<interior_ptr<short> >(lr);   // C2682  
   interior_ptr<short>ssr = reinterpret_cast<interior_ptr<short> >(lr);   // OK  
}  
```