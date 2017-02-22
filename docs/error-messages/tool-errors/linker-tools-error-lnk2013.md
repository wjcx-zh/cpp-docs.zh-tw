---
title: "連結器工具錯誤 LNK2013 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2013"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2013"
ms.assetid: 21408e2d-3f56-4d1f-a031-00df70785ed4
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 連結器工具錯誤 LNK2013
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

修正型別修復溢位。目標 'symbol name' 超出範圍  
  
 連結器無法提供指定指令所需的位址或位移，因為目標符號離該指令位置太遠。  
  
 您可以建立多個映像或使用 [\/ORDER](../../build/reference/order-put-functions-in-order.md) 選項使指令與目標更接近，便可解決這個問題。  
  
 當符號名稱為使用者定義符號 \(且不是編譯器產生的符號\) 時，您也可以嘗試下列動作來解決錯誤：  
  
-   變更靜態函式為非靜態。  
  
-   重新將包含靜態函式的程式碼區段命名為與呼叫端相同的名稱。  
  
 使用 `DUMPBIN /SYMBOLS`，查看是否為靜態函式。