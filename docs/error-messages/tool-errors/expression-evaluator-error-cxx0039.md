---
title: "運算式評估工具錯誤 CXX0039 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "CXX0039"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0039"
  - "CXX0039"
ms.assetid: 8bf698d2-e015-4595-944f-72b81aa43d22
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 運算式評估工具錯誤 CXX0039
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

符號模稜兩可  
  
 C 運算式評估工具無法決定運算式中所使用的是符號的哪一個執行個體，  此符號在繼承樹狀結構中出現不只一次。  
  
 您必須使用範圍解析 \(Scope Resolution\) 運算子 \(`::`\) 確實地指定運算式中使用的執行個體。  
  
 此錯誤與 CAN0039 相同。