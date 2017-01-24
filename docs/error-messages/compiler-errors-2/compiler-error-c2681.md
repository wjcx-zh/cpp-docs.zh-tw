---
title: "編譯器錯誤 C2681 | Microsoft Docs"
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
  - "C2681"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2681"
ms.assetid: eb42da6d-8d2c-43fd-986b-e73e2b004885
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2681
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type' : name 的運算式型別無效  
  
 轉換運算子嘗試轉換一個無效型別。  例如，如果您使用 [dynamic\_cast](../../cpp/dynamic-cast-operator.md) 運算子來將運算式轉換成一個指標型別，則原始運算式必須是一個指標。  
  
 下列範例會產生 C2681：  
  
```  
// C2681.cpp  
class A { virtual void f(); };  
  
void g(int i) {  
    A* pa;  
    pa = dynamic_cast<A*>(i);  // C2681  
}  
```