---
title: "運算錯誤 M6110 | Microsoft Docs"
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
  - "M6110"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "M6110"
ms.assetid: aac9ae37-6a6d-46e9-85d4-dfe03f1c3e11
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 運算錯誤 M6110
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

堆疊溢位  
  
 浮點運算式造成浮點堆疊溢位 \(Stack Overflow\)。  
  
 最多可以截取七層的堆疊溢位浮點例外狀況，而不是 8087\/287\/387 副處理器通常支援的八層。  
  
 程式以結束代碼 138 結束。