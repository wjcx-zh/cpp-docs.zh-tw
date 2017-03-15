---
title: "編譯器錯誤 C3485 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3485"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3485"
ms.assetid: d67536f9-67a1-4ad9-9a94-d8bbbca3d0dc
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器錯誤 C3485
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Lambda 定義不能有任何 cv 限定詞  
  
 您不能使用 `const` 或 `volatile` 限定詞作為 Lambda 運算式定義的一部分。  
  
### 更正這個錯誤  
  
-   請從 Lambda 運算式的定義中移除 `const` 或 `volatile` 限定詞。  
  
## 範例  
 下列範例會產生 C3485，因為它使用 `const` 限定詞作為 Lambda 運算式定義的一部分：  
  
```  
// C3485.cpp int main() { auto x = []() const mutable {}; // C3485 }  
```  
  
## 請參閱  
 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)