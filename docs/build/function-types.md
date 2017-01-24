---
title: "函式類型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 7e33d5f4-dabb-406d-afb3-13777b995028
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 函式類型
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

基本上有兩種類型的函式：  需要堆疊框架 \(Stack Frame\) 的函式稱為框架函式 \(Frame Function\)。  不需要堆疊框架的函式稱為分葉函式 \(Leaf Function\)。  
  
 框架函式是會配置堆疊空間、呼叫其他函式、儲存靜態暫存器或使用例外狀況處理 \(Exception Handling\) 的函式。  此種函式也需要函式表項目。  框架函式需要初構和終解。  框架函式可以動態配置堆疊空間，並使用框架指標。  框架函式在處置時具有這個呼叫標準的完整能力。  
  
 如果框架函式不呼叫另一個函式，就不需要對齊堆疊 \(在[堆疊配置](../build/stack-allocation.md)一節中提及\)。  
  
 分葉函式是不需要函式表項目的函式。  它無法呼叫任何函式、配置空間或儲存任何靜態暫存器。  但在函式執行時允許堆疊保持未對齊的狀態。  
  
## 請參閱  
 [堆疊使用方式](../build/stack-usage.md)