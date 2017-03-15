---
title: "編譯器警告 (層級 3) C4534 | Microsoft Docs"
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
  - "c4534"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4534"
ms.assetid: ec2adf3b-d7a1-4005-bb0c-5d219df78dc8
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 3) C4534
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

由於預設的引數，'constructor' 不是類別 'class' 的預設建構函式  
  
 Unmanaged 類別可以有一個有預設值參數的建構函式，而且編譯器會將它當做預設的建構函式使用。  以 `value` 關鍵字標示的類別不會將有參數預設值的建構函式當做預設的建構函式。  
  
 如需詳細資訊，請參閱[Classes and Structs](../../windows/classes-and-structs-cpp-component-extensions.md)。  
  
 下列範例會產生 C4534：  
  
```  
// C4534.cpp  
// compile with: /W3 /clr /WX  
value class MyClass {  
public:  
   int ii;  
   MyClass(int i = 9) {   // C4534, will not be the default constructor  
      i++;  
   }  
};  
  
int main() {  
   MyClass ^ xx = gcnew MyClass;  
   xx->ii = 0;  
}  
```