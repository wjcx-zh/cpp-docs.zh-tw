---
title: "呼叫端/被呼叫端儲存的暫存器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 0533bd4b-d6bb-4ce1-8201-495e16870cbb
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 呼叫端/被呼叫端儲存的暫存器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

RAX、RCX、RDX、R8、R9、R10 和 R11 等暫存器被視為變動 \(Volatile\) 暫存器，並在呼叫函式時必須視為已終結 \(除非經過整個程式最佳化等分析得到安全許可\)。  
  
 RBX、RBP、RDI、RSI、RSP、R12、R13、R14 和 R15 等暫存器被視為靜態 \(Nonvolatile\) 暫存器，並且必須由使用這些暫存器的函式加以儲存及還原。  
  
## 請參閱  
 [呼叫慣例](../build/calling-convention.md)