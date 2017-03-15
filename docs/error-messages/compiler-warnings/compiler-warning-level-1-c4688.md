---
title: "編譯器警告 (層級 1) C4688 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4688"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4688"
ms.assetid: a027df3c-b2b8-4c49-8539-c2bc42db74e8
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器警告 (層級 1) C4688
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'constraint': 條件約束清單含有組件私用類型 'type'，將無法由組件外部存取  
  
 條件約束清單具有組件的私用類型，這表示在組件外部存取類型時將無法使用它。 如需詳細資訊，請參閱[Generics](../../windows/generics-cpp-component-extensions.md)。  
  
## 範例  
 下列範例會產生 C4688。  
  
```  
// C4688.cpp // compile with: /clr /c /W1 ref struct A {};   // private type public ref struct B {}; // Delete the following 3 lines to resolve. generic <class T> where T : A   // C4688 public ref struct M {}; generic <class T> where T : B public ref struct N {};  
```