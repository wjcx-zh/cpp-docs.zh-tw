---
title: "編譯器警告 (層級 1) C4076 | Microsoft Docs"
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
  - "C4076"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4076"
ms.assetid: 04581066-313a-4a11-bb60-721e6d038d75
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4076
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'typemod': 無法與類型 'typename' 搭配使用  
  
 類型修飾詞 \(不論是 **signed** 還是 `unsigned`\) 不能與非整數類型搭配使用。 會忽略 ***typemod***。  
  
## 範例  
 下列範例會產生 C4076：  
  
```  
// C4076.cpp // compile with: /W1 /LD unsigned double x;   // C4076  
```