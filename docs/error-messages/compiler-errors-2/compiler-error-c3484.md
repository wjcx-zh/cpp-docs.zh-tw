---
title: "編譯器錯誤 C3484 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3484"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3484"
ms.assetid: 2fe847fa-f6ee-4978-bc1d-b6dc6ae906ac
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3484
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

傳回類型的前面必須是 '\-\>'  
  
 Lambda 運算式的傳回類型前面必須是 `->`。  
  
### 更正這個錯誤  
  
-   傳回類型前面請提供 `->`。  
  
## 範例  
 下列範例會產生 C3484：  
  
```  
// C3484a.cpp int main() { return []() . int { return 42; }(); // C3484 }  
```  
  
## 範例  
 下例藉由在 Lambda 運算式的傳回類型前面提供 `->` 來解決 C3484：  
  
```  
// C3484b.cpp int main() { return []() -> int { return 42; }(); }  
```  
  
## 請參閱  
 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)