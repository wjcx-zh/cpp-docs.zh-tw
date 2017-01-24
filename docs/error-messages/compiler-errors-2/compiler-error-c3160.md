---
title: "編譯器錯誤 C3160 | Microsoft Docs"
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
  - "C3160"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3160"
ms.assetid: a250c433-8adf-43b9-8dee-c3794e09b0a5
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3160
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'pointer': Managed 或 WinRT 類別的資料成員不能有這種類型  
  
 內部記憶體回收指標可能指向 Managed 或 WinRT 類別的內部。  因為它們比完整物件指標更慢，而且需要記憶體回收行程進行特殊處理，您無法將內部 Managed 指標宣告為類別的成員。  
  
 下列範例會產生 C3160：  
  
```  
// C3160.cpp  
// compile with: /clr  
ref struct A {  
   // cannot create interior pointers inside a class  
   interior_ptr<int> pg;   // C3160  
   int g;   // OK  
   int* pg2;   // OK  
};  
  
int main() {  
   interior_ptr<int> pg2;   // OK  
}  
```  
  
 **Managed Extensions for C\+\+**  
  
 下列範例會產生 C3160：  
  
```  
// C3160b.cpp  
// compile with: /clr:oldSyntax  
  
__gc struct A {  
   // cannot create interior pointers inside a class  
   int __gc* pg; // C3160  
   int g;   // OK  
   int __nogc *pg2;   // OK  
};  
  
int main() {  
   int __gc* pg2;   // OK  
}  
```