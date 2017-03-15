---
title: "編譯器錯誤 C3457 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3457"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3457"
ms.assetid: 5c1e366a-fa75-4cca-b9a3-86d4ebe4090e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器錯誤 C3457
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'attribute': 屬性不支援未具名引數  
  
 和 CLR 自訂屬性或編譯器屬性不同，來源附註屬性只支援具名引數。  
  
## 範例  
 下列範例會產生 C3457。  
  
```  
#include "SourceAnnotations.h" [vc_attributes::Post( 1 )] int f();   // C3457 [vc_attributes::Post( Valid=vc_attributes::Yes )] int f2();   // OK  
```