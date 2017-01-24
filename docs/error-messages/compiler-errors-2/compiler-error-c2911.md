---
title: "編譯器錯誤 C2911 | Microsoft Docs"
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
  - "C2911"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2911"
ms.assetid: 83c7c01a-ab6a-4179-9fb0-289a9ec8d44e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2911
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'member' : 無法在目前的範圍中宣告或定義  
  
 您只能在命名空間、類別或函式之中，定義相同命名空間、類別或函式的成員，或者是由相同命名空間、類別或函式封入的成員。  
  
 下列範例會產生 C2911：  
  
```  
// C2911.cpp struct A; namespace M { struct D; } namespace N { struct C; namespace O { struct B; } // in N struct ::A {};   // C2911  A is member of global NS struct O::B{};   // OK B is in O, O is inside of N struct C {};     // OK C is member of N struct M::D {};  // C2911 D is member of M, M not enclosed by N }  
```