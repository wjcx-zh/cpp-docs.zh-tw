---
title: "編譯器錯誤 C3358 | Microsoft Docs"
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
  - "C3358"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3358"
ms.assetid: 180b93df-e78f-441a-91fb-1594c681f7f0
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C3358
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'symbol': 找不到符號  
  
 找不到必要的符號。  
  
 下列範例會產生 C3358：  
  
```  
// C3358.cpp #define __ATLEVENT_H__ 1   // remove this line to resolve the error #define _ATL_ATTRIBUTES 1 #include "atlbase.h" #include "atlcom.h" [event_receiver(com)] struct A   // C3358 { void func(); }; int main() { }  
```