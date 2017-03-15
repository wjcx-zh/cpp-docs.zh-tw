---
title: "編譯器錯誤 C2106 | Microsoft Docs"
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
  - "C2106"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2106"
ms.assetid: d5c91a2e-04e4-4770-8478-788b98c52a53
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2106
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operator' : 左運算元必須是左值 \(l\-value\)  
  
 運算子必須擁有左值做為其左運算元。  
  
 下列範例會產生 C2106：  
  
```  
// C2106.cpp  
int main() {  
   int a;  
   1 = a;   // C2106  
   a = 1;   // OK  
}  
```