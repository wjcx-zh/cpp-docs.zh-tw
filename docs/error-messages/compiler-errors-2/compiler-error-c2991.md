---
title: "編譯器錯誤 C2991 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2991"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2991"
ms.assetid: a87e4404-26e8-4927-b3ee-5d02b3b8bee1
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 編譯器錯誤 C2991
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

重複定義類型參數 'parameter'  
  
 `parameter` 的兩個泛型或樣板定義之間發生類型衝突。 定義多個泛型或樣板參數時，您必須使用對等的類型。  
  
 下列範例會產生 C2991：  
  
```  
// C2991.cpp // compile with: /c template<class T, class T> struct TC {};   // C2991 // try the following line instead // template<class T, class T2> struct TC {};  
```  
  
 使用泛型時，也會發生 C2991：  
  
```  
// C2991b.cpp // compile with: /clr /c generic<class T,class T> ref struct GC {};   // C2991 // try the following line instead // generic<class T,class T2> ref struct GC {};  
```