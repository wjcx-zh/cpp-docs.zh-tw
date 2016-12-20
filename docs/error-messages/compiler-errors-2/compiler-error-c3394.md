---
title: "編譯器錯誤 C3394 | Microsoft Docs"
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
  - "C3394"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3394"
ms.assetid: 4e025d79-27ba-43c8-b0d9-839ecef98126
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3394
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

條件約束子句中語法錯誤：找到 'identifier'，但必須是類型  
  
 條件約束的格式錯誤。  如需詳細資訊，請參閱[Constraints on Generic Type Parameters \(C\+\+\/CLI\)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md)。  
  
## 範例  
 下列範例會產生 C3394：  
  
```  
// C3394.cpp // compile with: /clr /c ref class MyClass {}; ref class R { generic<typename T> where T : static   // C3394 // try the following line instead // where T : MyClass void f() {} };  
```