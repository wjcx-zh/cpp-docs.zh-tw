---
title: "如何：使用 gcnew 建立實值類型及使用隱含 Boxing | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Boxing, 隱含"
  - "gcnew 關鍵字 [C++], 建立實值類型"
  - "實值類型, 建立"
ms.assetid: ceb48841-d6bd-47be-a167-57f44c961603
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：使用 gcnew 建立實值類型及使用隱含 Boxing
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用在實值型別的 [請用"](../windows/ref-new-gcnew-cpp-component-extensions.md) 將建立 Boxed 實值型別，在 Managed 可放置，記憶體回收的堆積。  
  
## 範例  
  
```  
// vcmcppv2_explicit_boxing4.cpp  
// compile with: /clr  
public value class V {  
public:  
   int m_i;  
   V(int i) : m_i(i) {}  
};  
  
public ref struct TC {  
   void do_test(V^ v) {  
      if (v != nullptr)  
         ;  
      else  
         ;  
   }  
};  
  
int main() {  
   V^ v = gcnew V(42);  
   TC^ tc = gcnew TC;  
   tc->do_test(v);  
}  
```  
  
## 請參閱  
 [Boxing](../windows/boxing-cpp-component-extensions.md)