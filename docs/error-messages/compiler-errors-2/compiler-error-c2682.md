---
title: "編譯器錯誤 C2682 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2682"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2682"
ms.assetid: 30c6a7c4-f5f7-4fe8-81a8-c48938521ab4
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# 編譯器錯誤 C2682
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法使用 casting\_operator，從 'type1' 轉換為 'type2'  
  
 轉換運算子嘗試在不相容的型別間進行轉換。  例如，您不能使用 [dynamic\_cast](../../cpp/dynamic-cast-operator.md) 運算子來將指標轉換成參考。  不能使用 `dynamic_cast` 運算子移除限定詞 \(Qualifier\)。  型別上的所有限定詞必須相符。  
  
 您可以使用 `const_cast` 運算子移除屬性，例如 `const`、`volatile` 或 `__unaligned` 等。  
  
 下列範例會產生 C2682：  
  
```  
// C2682.cpp  
class A { virtual void f(); };  
class B: public A {};  
  
void g(A* pa) {  
    B& rb = dynamic_cast<B&>(pa); // C2682  
}  
```  
  
 下列範例會產生 C2682：  
  
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