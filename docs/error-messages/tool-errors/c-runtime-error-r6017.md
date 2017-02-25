---
title: "C 執行階段錯誤 R6017 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "R6017"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6017"
ms.assetid: df3ec5f5-6771-4648-ba06-0e26c6a1cc6a
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# C 執行階段錯誤 R6017
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法預期的多執行緒鎖定錯誤  
  
 當處理序嘗試存取系統資源上的 C 執行階段多執行緒 \(Multithread\) 鎖定時，發生無法預期的錯誤。  
  
 當處理序不慎更改執行階段堆積 \(Heap\) 資料時，通常就會發生此錯誤。  然而，也可能是因為執行階段或作業系統程式碼的內部錯誤所造成。