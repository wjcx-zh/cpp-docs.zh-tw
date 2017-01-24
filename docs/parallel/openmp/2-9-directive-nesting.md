---
title: "2.9 Directive Nesting | Microsoft Docs"
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
ms.assetid: 6565a43c-fd2d-4366-8322-8d75e1b06600
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.9 Directive Nesting
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

動態的巢狀指示詞必須遵守下列規則：  
  
-   A **平行** 指示詞，以動態方式在另一個 **平行**邏輯上會建立新的小組，由目前的執行緒，除非巢狀化平行處理原則已啟用。  
  
-   **對於**， **章節**，和 **單一** 繫結至相同的指示詞 **平行**不允許在彼此進行巢狀。  
  
-   **要徑**不允許有相同名稱的指示詞巢狀方式置於彼此。  請注意這項限制並不足夠用來避免死結。  
  
-   **為**， **區段**，和 **單一** 指示詞的動態範圍內不允許 **重要**， **訂購**，和 **主版** 區域指示詞繫結至相同，如果 **平行**視為區域。  
  
-   **障盾** 指示詞的動態範圍內不允許 **的**， **訂購**， **區段**， **單一**， **主版**，和 **重要** 區域指示詞繫結至相同，如果 **平行**視為的區域。  
  
-   **主版** 指示詞的動態範圍內不允許 **的**， **章節**，和 **單一** 指示詞如果 **主** 指示詞繫結至相同 **平行**為工作共用的指示詞。  
  
-   **已排序的** 指示詞的動態範圍中不允許 **重要** 區域指示詞繫結至相同，如果 **平行**視為的區域。  
  
-   在平行區域之外執行時，也會允許任何動態執行平行區域內時所允許的指示詞。  在執行時以動態方式在使用者指定的平行區域之外，指示詞被執行主要的執行緒所組成的小組。