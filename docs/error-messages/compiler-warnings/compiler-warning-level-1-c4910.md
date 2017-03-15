---
title: "編譯器警告 (層級 1) C4910 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4910"
ms.assetid: 67963560-fbca-4ca7-93db-06beaf7055f0
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# 編譯器警告 (層級 1) C4910
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'\<識別項\>'：'\_\_declspec\(dllexport\)' 和 'extern' 在明確具現化中不相容  
  
 名為 *\<識別項\>* 的明確樣板具現化已由 `__declspec(dllexport)` 和 `extern` 關鍵字修改。 不過，這些關鍵字是互斥的。`__declspec(dllexport)` 關鍵字表示具現化樣板類別，而 `extern` 關鍵字表示不會自動具現化樣板類別。  
  
## 請參閱  
 [明確初始化](../../cpp/explicit-instantiation.md)   
 [dllexport、dllimport](../../cpp/dllexport-dllimport.md)   
 [一般規則和限制](../../cpp/general-rules-and-limitations.md)