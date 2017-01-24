---
title: "編譯器錯誤 C3493 | Microsoft Docs"
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
  - "C3493"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3493"
ms.assetid: 734b4257-12a3-436f-8488-c8c55ec81634
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3493
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法隱含擷取 'var'，因為未指定預設的擷取模式  
  
 空的 Lambda 運算式擷取 `[]`，指定 Lambda 運算式不明確或隱含擷取任何變數。  
  
### 更正這個錯誤  
  
-   提供預設的擷取模式，或  
  
-   明確擷取一或多個變數。  
  
## 範例  
 下例會產生 C3493，因為它會修改外部變數，但指定空白的擷取子句：  
  
```  
// C3493a.cpp int main() { int m = 55; [](int n) { m = n; }(99); // C3493 }  
```  
  
## 範例  
 下例會以依參考指定為預設擷取模式的方式解析 C3493。  
  
```  
// C3493b.cpp int main() { int m = 55; [&](int n) { m = n; }(99); }  
```  
  
## 請參閱  
 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)