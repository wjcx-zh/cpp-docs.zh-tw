---
title: "編譯器錯誤 C2415 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2415"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2415"
ms.assetid: f225c913-2bea-46b1-b096-3d358ac94a15
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2415
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不適當的運算元型別  
  
 此 Opcode 無法使用該型別的運算元。  
  
### 若要修正，請檢查下列可能原因  
  
1.  此 Opcode 並不支援使用的運算元個數。  請參閱組合語言的參考手冊，以確定正確的運算元個數。  
  
2.  較新的處理器可支援其他型別的指令。  調整 [\/arch \(最小 CPU 架構\)](../../build/reference/arch-minimum-cpu-architecture.md) 選項來使用較新的處理器。