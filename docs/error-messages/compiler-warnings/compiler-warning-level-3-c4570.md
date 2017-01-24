---
title: "編譯器警告 (層級 3) C4570 | Microsoft Docs"
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
  - "C4570"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4570"
ms.assetid: feec1225-e6ad-4995-8d96-c22e864a77bd
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 3) C4570
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type' : 未明確宣告為抽象，但是擁有抽象函式  
  
 包含 [abstract](../../windows/abstract-cpp-component-extensions.md) 函式的型別本身也應該標示為抽象。  
  
## 範例  
 下列範例會產生 C4570。  
  
```  
// C4570.cpp  
// compile with: /clr /W3 /c  
ref struct X {   // C4570  
// try the following line instead  
// ref class X abstract {  
   virtual void f() abstract;  
};  
```