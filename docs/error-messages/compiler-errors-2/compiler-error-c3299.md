---
title: "編譯器錯誤 C3299 | Microsoft Docs"
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
  - "C3299"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3299"
ms.assetid: 7cabdf01-bceb-404f-9401-cdd9c7fc1641
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3299
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'member\_function' : 無法指定條件約束，因為它們是繼承自基底方法  
  
 在覆寫泛型成員函式時，您無法指定條件約束子句 \(重複條件約束表示不會繼承條件約束\)。  
  
 將會繼承您正在覆寫的泛型函式上的條件約束子句。  
  
 如需詳細資訊，請參閱[Constraints on Generic Type Parameters \(C\+\+\/CLI\)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)。  
  
## 範例  
 下列範例會產生 C3299：  
  
```  
// C3299.cpp // compile with: /clr /c public ref struct R { generic<class T> where T : R virtual void f(); }; public ref struct S : R { generic<class T> where T : R   // C3299 virtual void f() override; };  
```