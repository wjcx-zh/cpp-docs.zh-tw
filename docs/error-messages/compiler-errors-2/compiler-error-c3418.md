---
title: "編譯器錯誤 C3418 | Microsoft Docs"
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
  - "C3418"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3418"
ms.assetid: 54042c04-3c45-41c1-bad7-90f9ee05a21b
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3418
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不支援存取規範 'specifier'  
  
 CLR 存取規範指定不正確。  如需詳細資訊，請參閱[類型和成員可視性](../../misc/type-and-member-visibility.md)。  
  
## 範例  
 下列範例會產生 C3418：  
  
```  
// C3418.cpp // compile with: /clr /c ref struct m { internal public:   // C3418 void test(){} }; ref struct n { internal:   // OK void test(){} };  
```