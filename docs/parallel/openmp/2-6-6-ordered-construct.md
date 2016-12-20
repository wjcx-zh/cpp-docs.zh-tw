---
title: "2.6.6 ordered Construct | Microsoft Docs"
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
ms.assetid: 5b3c1ba5-cfb8-4b05-865b-f446ae1c9f7c
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.6.6 ordered Construct
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

結構化的封鎖下列**訂購**指示詞會在其中反覆項目就會執行在連續迴圈中的順序執行。  語法**訂購**指示詞時，如下所示：  
  
```  
#pragma omp ordered new-line  
   structured-block  
```  
  
 **訂購** 指示詞必須是動態的範圍內 **的** 或 **平行的**建構。  **的** 或 **平行的** 指示詞的 **訂購** 建構繫結必須有 **訂購** 子句指定述 [區段 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) 11 頁上。  執行中的**的** 或 **平行的** 建構包含 **訂購** 子句中， **訂購**建構會嚴格執行，它們會執行的循序執行迴圈 \(loop\) 中的順序。  
  
 若要限制**訂購**指示詞，如下所示是：  
  
-   反覆項目與迴圈 \(loop\) **的** 建構必須不會一次以上，同一個已排序的指示詞執行，而且它必須不會執行一個以上的 **訂購**指示詞。