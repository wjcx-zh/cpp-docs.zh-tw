---
title: "編譯器錯誤 C2030 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2030"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2030"
ms.assetid: 5806cead-64df-4eff-92de-52c9a3f5ee62
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器錯誤 C2030
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

具有 'protected private' 可及性的解構函式不可以是宣告為 'sealed' 之類別的成員  
  
 宣告為 `sealed` 的 Windows 執行階段類別不能有受保護的私用解構函式。  sealed 類型只允許公用虛擬和私用非虛擬解構函式。  如需詳細資訊，請參閱 [Ref 類別與結構](../Topic/Ref%20classes%20and%20structs%20\(C++-CX\).md)。  
  
 若要修正這個錯誤，請變更解構函式的存取範圍。