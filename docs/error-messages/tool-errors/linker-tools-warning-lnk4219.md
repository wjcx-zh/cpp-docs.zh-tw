---
title: "連結器工具警告 LNK4219 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4219"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4219"
ms.assetid: 363fedf4-b10c-4985-811a-55a9fba688d6
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 連結器工具警告 LNK4219
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

fixup name 修復溢位。目標 'target symbol name' 超出範圍，插入 Thunk  
  
 連結器因目標符號離指示位置太遠，而將 Thunk 插入至位址或位移無法符合指定指令的位置。  
  
 您必須重新排列映像順序 \(例如使用 [\/ORDER](../../build/reference/order-put-functions-in-order.md) 選項\) 以避免額外的間接取值 \(Indirection\)。