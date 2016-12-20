---
title: "編譯器錯誤 C3454 | Microsoft Docs"
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
  - "C3454"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3454"
ms.assetid: dc4e6d57-5b4d-4114-8d6f-22f9ae62925b
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3454
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

類別宣告上不允許 \[attribute\]  
  
 必須定義類別，它才能是屬性。  
  
 如需詳細資訊，請參閱[attribute](../../windows/attribute.md)。  
  
## 範例  
 下列範例會產生 C3454。  
  
```  
// C3454.cpp // compile with: /clr /c using namespace System; [attribute]   // C3454 ref class Attr1; [attribute]   // OK ref class Attr2 {};  
```