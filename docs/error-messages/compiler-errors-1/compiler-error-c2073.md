---
title: "編譯器錯誤 C2073 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2073"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2073"
ms.assetid: 57908234-be7a-4ce9-b0a7-8b1ad621865e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2073
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 部分初始化之陣列的元素必須具有預設的建構函式  
  
 使用者定義具型別陣列或常數陣列所指定的初始設定式過少。  如果並未指定明確初始設定式 \(Explicit Initializer\) 和其對應的建構函式 \(Constructor\) 給陣列成員，便需提供預設的建構函式。  
  
 下列範例會產生 C2073：  
  
```  
// C2073.cpp  
class A {  
public:  
   A( int );   // constructor for ints only  
};  
A a[3] = { A(1), A(2) };   // C2073, no default constructor  
```  
  
```  
// C2073b.cpp  
// compile with: /c  
class B {  
public:  
   B();   // default constructor declared  
   B( int );  
};  
B b[3] = { B(1), B(2) };   // OK  
```