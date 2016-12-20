---
title: "編譯器警告 (層級 1) C4620 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4620"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4620"
ms.assetid: fed29934-b797-47e8-bbea-c7e5f8dd6e93
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4620
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

找不到類型 'type' 後置格式的 'operator \+\+'，已改用前置格式  
  
 未定義指定類型的後置遞增運算子。 編譯器使用多載的前置運算子。  
  
 定義後置 `++` 運算子即可避免這個警告。 請如下所示建立 `++` 運算子的雙引數版本：  
  
```  
// C4620.cpp // compile with: /W1 class A { public: A(int nData) : m_nData(nData) { } A operator++() { m_nData -= 1; return *this; } // A operator++(int) // { //    A tmp = *this; //    m_nData -= 1; //    return tmp; // } private: int m_nData; }; int main() { A a(10); ++a; a++;   // C4620 }  
```