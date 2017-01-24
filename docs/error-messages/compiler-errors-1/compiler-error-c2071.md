---
title: "編譯器錯誤 C2071 | Microsoft Docs"
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
  - "C2071"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2071"
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2071
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier'：儲存類別不合法  
  
 使用了無效的[儲存類別](../../c-language/c-storage-classes.md)宣告 `identifier`。  當指定了一個以上的儲存類別給識別項，或是定義與儲存類別宣告不相容時，可能會造成這個錯誤。  
  
 若要修正這個問題，請了解識別項的預定儲存類別，例如，`static` 或  `extern`，並更正宣告以符合該類別。  
  
## 範例  
 下列範例會產生 C2071。  
  
```  
// C2071.cpp  
// compile with: /c  
struct C {  
   extern int i;   // C2071  
};  
struct D {  
   int i;   // OK, no extern on an automatic  
};  
```  
  
## 範例  
 下列範例會產生 C2071。  
  
```  
// C2071_b.cpp  
// compile with: /c  
typedef int x(int i) { return i; }   // C2071  
typedef int (x)(int);   // OK, no local definition in typedef  
```