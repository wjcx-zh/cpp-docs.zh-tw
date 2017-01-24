---
title: "編譯器錯誤 C2253 | Microsoft Docs"
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
  - "C2253"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2253"
ms.assetid: bd6445ae-b2c1-4669-9657-a8f4acf80b16
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2253
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 純虛擬函式規範或抽象覆寫規範只適用於虛擬函式  
  
 將非虛擬函式指定為純 `virtual`。  
  
 下列範例會產生 C2253：  
  
```  
// C2253.cpp  
// compile with: /c  
class A {  
public:  
   void func1() = 0;   // C2253 not virtual  
   virtual void func2() = 0;   // OK  
};  
```  
  
 下列範例會產生 C2253：  
  
```  
// C2253_2.cpp  
// compile with: /clr /c  
ref struct A {  
   property int Prop_3 {  
      int get() abstract;   // C2253  
      // try the following line instead  
      // virtual int get() abstract;  
  
      void set(int i) abstract;   // C2253  
      // try the following line instead  
      // virtual void set(int i) abstract;  
   }  
};  
```