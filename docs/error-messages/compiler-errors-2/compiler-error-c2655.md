---
title: "編譯器錯誤 C2655 | Microsoft Docs"
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
  - "C2655"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2655"
ms.assetid: beaefa6e-51b3-4df9-9150-960f3fbf40e0
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2655
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier' : 在目前範圍中定義或重新宣告不合法  
  
 識別項只能在全域範圍內重新宣告。  
  
 下列範例會產生 C2655：  
  
```  
// C2655.cpp  
class A {};  
class B {  
public:  
   static int i;  
};  
  
int B::i;  // OK  
  
int main() {  
   A B::i;  // C2655  
}  
```