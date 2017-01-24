---
title: "編譯器錯誤 C2351 | Microsoft Docs"
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
  - "C2351"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2351"
ms.assetid: 5439ccf6-66f6-4859-964c-c73f5eddfc1b
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2351
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

過時的 C\+\+ 建構函式初始化語法  
  
 在建構函式的新樣式初始化清單內，您必須明確地替每個直接基底類別 \(Base Class\) 命名，即使它是唯一的基底類別。  
  
 下列範例會產生 C2351：  
  
```  
// C2351.cpp  
// compile with: /c  
class B {  
public:   
   B() : () {}   // C2351  
   B() {}   // OK  
};  
```