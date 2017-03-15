---
title: "編譯器錯誤 C3285 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3285"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3285"
ms.assetid: 04e8f210-d67e-4810-b153-e1efe2986c8f
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 編譯器錯誤 C3285
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不能在類型 'type' 的變數上使用 for each 陳述式  
  
 `for each` 陳述式會為陣列或物件集合中的每個項目，重複一組內嵌陳述式。  
  
 如需詳細資訊，請參閱 [for each、in](../../dotnet/for-each-in.md)。  
  
## 範例  
 下列範例會產生 C3285。  
  
```  
// C3285.cpp // compile with: /clr int main() { for each (int i in 0) {}   // C3285 array<int> ^p = { 1, 2, 3 }; for each (int j in p) {}   // OK }  
```