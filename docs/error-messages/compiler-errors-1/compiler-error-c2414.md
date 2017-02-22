---
title: "編譯器錯誤 C2414 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2414"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2414"
ms.assetid: bbe94e03-862e-4990-b15e-544ae464727d
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 編譯器錯誤 C2414
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

運算元的數目不合法  
  
### 若要修正，請檢查下列可能原因  
  
1.  此 Opcode 並不支援使用的運算元個數。  請參閱組合語言的參考手冊，以確定正確的運算元個數。  
  
2.  較新的處理器可支援運算元個數不同的指令。  調整 [\/arch \(最小 CPU 架構\)](../../build/reference/arch-minimum-cpu-architecture.md) 選項來使用較新的處理器。