---
title: "2.4 Work-sharing Constructs | Microsoft Docs"
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
ms.assetid: 25bb4ded-8466-4daa-a863-766b5a99b995
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.4 Work-sharing Constructs
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

工作共用的建構分配相關的陳述式，在發生這個情形的團隊成員間執行。  工作共用的指示詞不會啟動新的執行緒，而且沒有任何默示的障盾到工作共用的建構函式的項目。  
  
 工作共用的順序會建構及**障盾**發生的指示詞必須是相同的小組中的每一個執行緒。  
  
 OpenMP 定義下列工作共用的結構，並在章節中將會加以說明：  
  
-   **對於**指示詞  
  
-   **章節**指示詞  
  
-   **單一**指示詞