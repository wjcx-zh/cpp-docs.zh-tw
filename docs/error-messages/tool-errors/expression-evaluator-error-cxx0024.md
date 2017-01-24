---
title: "運算式評估工具錯誤 CXX0024 | Microsoft Docs"
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
  - "CXX0024"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0024"
  - "CXX0024"
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 運算式評估工具錯誤 CXX0024
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

運算需要左值  
  
 在需要使用左值 \(L\-Value\) 的作業中指定不被評估為左值的運算式。  
  
 左值，如此稱呼是因為它出現在指派陳述式 \(Assignment Statement\) 的左側，是參考記憶體位置的運算式。  
  
 例如，`buffer[count]` 是有效的左值，因為它指向特定的記憶體位置。  邏輯比較 `zed != 0` 不是有效的左值，因為它被評估為 TRUE 或 FALSE，而不是記憶體位址。  
  
 此錯誤與 CAN0024 相同。