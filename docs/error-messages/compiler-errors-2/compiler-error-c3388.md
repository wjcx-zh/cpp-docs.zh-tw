---
title: "編譯器錯誤 C3388 | Microsoft Docs"
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
  - "C3388"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3388"
ms.assetid: 34336545-ed13-4d81-ab5f-f869799fe4c2
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3388
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': 不允許作為條件約束，假設是 'ref class' 以繼續剖析  
  
 已在泛型類型上指定條件約束，但未正確地指定條件約束。 如需詳細資訊，請參閱 [Constraints on Generic Type Parameters \(C\+\+\/CLI\)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)。  
  
## 範例  
 下列範例會產生 C3388。  
  
```  
// C3388.cpp // compile with: /clr /c interface class AA {}; generic <class T> where T : interface class   // C3388 ref class C {}; // OK generic <class T> where T : AA ref class D {};  
```