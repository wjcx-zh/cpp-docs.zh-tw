---
title: "編譯器錯誤 C2533 | Microsoft Docs"
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
  - "C2533"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2533"
ms.assetid: 5b335652-076c-4824-87c8-a741f64a3ce0
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2533
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identifier'：建構函式不允許傳回類型  
  
 建構函式不能有傳回類型 \(甚至是 `void` 傳回類型也不可以\)。  
  
 此錯誤的常見來源是類別定義結尾與第一個建構函式實作之間遺漏分號。  編譯器會將類別視為建構函式的傳回類型定義，並產生 C2533。  
  
 下列範例會產生 C2533，並示範如何修正此問題：  
  
```  
// C2533.cpp  
// compile with: /c  
class X {  
public:  
   X();     
};  
  
int X::X() {}   // C2533 - constructor return type not allowed  
X::X() {}   // OK - fix by using no return type  
```