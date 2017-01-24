---
title: "編譯器警告 (層級 1) C4488 | Microsoft Docs"
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
  - "C4488"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4488"
ms.assetid: 55625e46-ddb5-4c7c-99c7-cd4aa9f879bd
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4488
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 需要 'keyword' 關鍵字來實作介面方法 'interface\_method'  
  
 類別必須實作其直接繼承的介面之所有成員。  實作成員必須有公用存取範圍，而且必須標記為虛擬。  
  
## 範例  
 如果實作成員不是公用，可能會發生 C4488。  下列範例會產生 C4488。  
  
```  
// C4488.cpp  
// compile with: /clr /c /W1 /WX  
interface struct MyI {  
   void f1();  
};  
  
// implemented member not public  
ref class B : MyI { virtual void f1() {} };  // C4488  
  
// OK  
ref class C : MyI {  
public:  
   virtual void f1() {}  
};  
```  
  
## 範例  
 如果實作成員未標記為虛擬，可能會發生 C4488。  下列範例會產生 C4488。  
  
```  
// C4488_b.cpp  
// compile with: /clr /c /W1 /WX  
interface struct MyI {  
   void f1();  
};  
  
ref struct B : MyI { void f1() {} };   // C4488  
ref struct C : MyI { virtual void f1() {} };   // OK  
```