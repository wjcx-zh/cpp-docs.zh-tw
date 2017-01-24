---
title: "編譯器警告 (層級 1) C4662 | Microsoft Docs"
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
  - "C4662"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4662"
ms.assetid: 7efda273-d04a-47b7-ad65-ff1ff94b5ffc
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4662
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

明確具現化 \(Explicit Instantiation\)；樣板類別 'identifier1' 沒有特製化 'identifier2' 用的定義  
  
 指定的樣板類別已宣告，但未定義。  
  
## 範例  
  
```  
// C4662.cpp // compile with: /W1 /LD template<class T, int i> class MyClass; // no definition template MyClass< int, 1>;              // C4662  
```