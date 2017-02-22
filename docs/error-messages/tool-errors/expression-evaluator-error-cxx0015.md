---
title: "運算式評估工具錯誤 CXX0015 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "CXX0015"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CAN0015"
  - "CXX0015"
ms.assetid: 35efaf77-d578-48d8-bfc5-fdeb2a46a8b5
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 運算式評估工具錯誤 CXX0015
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

運算式太複雜 \(堆疊溢位\)  
  
 所輸入的運算式太複雜或是巢狀結構對 C 運算式評估工具的儲存量而言太深。  
  
 太多擱置的計算式通常會導致溢位。  
  
 重新安排運算式，使得遇到運算式的每一個元件時都可以被評估，而不須等待運算式的其他部分進行計算。  
  
 將運算式分割為多個命令。  
  
 此錯誤與 CAN0015 相同。