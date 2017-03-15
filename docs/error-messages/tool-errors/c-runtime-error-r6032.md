---
title: "C 執行階段錯誤 R6032 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "R6032"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6032"
ms.assetid: 52092a63-cc51-444a-bfc3-fad965a3558e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# C 執行階段錯誤 R6032
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

沒有足夠空間供地區設定資訊使用  
  
 執行階段會維護有關每個執行緒的地區設定資訊，使它能夠處理區分地區設定的函式呼叫。  如果供這項資訊使用的記憶體配置失敗，執行階段就無法繼續處理，因為它的許多基本功能都要靠它。