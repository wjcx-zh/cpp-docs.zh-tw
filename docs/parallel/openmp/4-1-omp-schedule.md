---
title: "4.1 OMP_SCHEDULE | Microsoft Docs"
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
ms.assetid: d0dce411-2351-4ee9-a1cc-c0322a58b65c
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 4.1 OMP_SCHEDULE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**OMP\_SCHEDULE** 只適用於**的** 和 **平行的** 指示詞，已排程類型 **執行階段**。  所有這類迴圈的排程類型和區塊大小可以在 run time 設定藉由設定這個環境變數，任何可辨識的排程類型以及一個選擇性 *chunk\_size*。  
  
 對於**的** 和 **平行的** 指示詞，而非已排程類型 **執行階段**，  **OMP\_SCHEDULE** 會被略過。  這個環境變數的預設值是由實作定義。  如果選擇性 *chunk\_size* 設定，此值必須是正數。  如果 *chunk\_size* 不是設定，會假設值為 1，例外的情況下**靜態**的排程。  對於**靜態**排程，預設區塊大小設定為 \[除以套用到迴圈的執行緒數目的迴圈反覆項目的空間。  
  
 範例：  
  
```  
setenv OMP_SCHEDULE "guided,4"  
setenv OMP_SCHEDULE "dynamic"  
```  
  
## 交互參照：  
  
-   **對於** 指示詞，請參閱 [一節 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) 11 頁上。  
  
-   **平行的** 指示詞，請參閱 [一節 2.5.1](../../parallel/openmp/2-5-1-parallel-for-construct.md) 在 16\] 頁面上。