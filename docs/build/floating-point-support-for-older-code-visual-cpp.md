---
title: "舊版程式碼的浮點支援 (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: a2a26b96-7bc2-418a-981a-51aa1a0294a2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 舊版程式碼的浮點支援 (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MMX 和浮點堆疊暫存器 \(MM0\-MM7\/ST0\-ST7\) 在內容切換時會保留。  這些暫存器沒有明確的呼叫慣例。  在核心 \(Kernel\) 模式程式碼中，嚴禁使用這些暫存器。  
  
## 請參閱  
 [呼叫慣例](../build/calling-convention.md)