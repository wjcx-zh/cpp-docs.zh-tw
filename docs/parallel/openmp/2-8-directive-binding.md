---
title: "2.8 Directive Binding | Microsoft Docs"
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
ms.assetid: 7bdac45e-ab55-42f0-bd47-a2e3d5bbab3e
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.8 Directive Binding
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

動態繫結的指示詞必須遵守下列規則：  
  
-   **的**， **章節**， **單一**， **主要**，和 **障盾** 指示詞將繫結到動態封入 **平行**，如果有的話，無論任何屬性的值 **如果**可能會出現在該指示詞的子句。  如果沒有平行區域目前正在執行中，指示詞被執行主要的執行緒所組成的小組。  
  
-   **訂購** 指示詞會繫結到動態封入 **的**。  
  
-   **不可部分完成** 指示詞強制大幅度地的獨占存取 **不可部分完成**指示詞中所有的執行緒，而不只是目前的小組。  
  
-   **要徑** 指示詞強制大幅度地的獨占存取 **重要**指示詞中所有的執行緒，而不只是目前的小組。  
  
-   指示詞可以永遠不會以最接近以外的任何指示詞動態繫結封入**平行**。