---
title: "C 執行階段錯誤 R6018 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "R6018"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6018"
ms.assetid: f6dd40d1-a119-4d8b-b39e-97350ea23349
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# C 執行階段錯誤 R6018
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

未預期的堆積錯誤  
  
 當程式執行記憶體管理作業時，遇到未預期的錯誤。  
  
 當程式不慎更改執行階段堆積資料時，通常就會發生此錯誤。  然而，也可能是因為執行階段或作業系統程式碼的內部錯誤所造成。  
  
 如果您的編譯器提供包含 `_heapchk` 和 `_heapwalk` 的程式庫，則可以使用這些函式診斷此錯誤。