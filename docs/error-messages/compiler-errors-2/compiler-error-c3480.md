---
title: "編譯器錯誤 C3480 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3480"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3480"
ms.assetid: 7b2e055a-9604-4d13-861b-b38bda1a6940
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 編譯器錯誤 C3480
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'var': Lambda 擷取變數必須來自封入函式範圍  
  
 Lambda 擷取變數不是來自封入函式範圍。  
  
### 更正這個錯誤  
  
-   請從 Lambda 運算式的擷取清單移除變數。  
  
## 範例  
 下列範例會產生 C3480，因為變數 `global` 不是來自封入函式範圍：  
  
```  
// C3480a.cpp int global = 0; int main() { [&global] { global = 5; }(); // C3480 }  
```  
  
## 範例  
 下列範例會藉由從 Lambda 運算式的擷取清單移除變數 `global` 而解決 C3480：  
  
```  
// C3480b.cpp int global = 0; int main() { [] { global = 5; }(); }  
```  
  
## 請參閱  
 [Lambda 運算式](../../cpp/lambda-expressions-in-cpp.md)