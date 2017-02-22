---
title: "編譯器錯誤 C3420 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3420"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3420"
ms.assetid: 99b53c77-f36b-4574-9199-b53111becccb
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# 編譯器錯誤 C3420
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'finalizer'：完成項不可為虛擬  
  
 完成項不可為虛擬，否則無法從它的封入類型進行呼叫。 因此，宣告虛擬完成項會造成錯誤。  
  
 如需詳細資訊，請參閱[Visual C\+\+ 中的解構函式和完成項](../../misc/destructors-and-finalizers-in-visual-cpp.md)。  
  
## 範例  
 下列範例會產生 C3420：  
  
```  
// C3420.cpp // compile with: /clr /c ref class R { virtual !R() {}   // C3420 };  
```