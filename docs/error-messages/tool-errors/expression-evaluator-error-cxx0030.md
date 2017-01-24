---
title: "運算式評估工具錯誤 CXX0030 | Microsoft Docs"
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
  - "CXX0030"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0030"
  - "CXX0030"
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 運算式評估工具錯誤 CXX0030
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法評估運算式  
  
 偵錯工具的運算式評估工具無法獲得所寫運算式的值。  可能的原因之一是此運算式參考到此程式位址空間以外的記憶體 \(解除參照 Null 指標就是一個例子\)。  Windows 不允許存取程式位址空間以外的記憶體。  
  
 您可能會希望重新撰寫運算式，並利用括號控制評估的順序。  
  
 此錯誤與 CAN0030 相同。