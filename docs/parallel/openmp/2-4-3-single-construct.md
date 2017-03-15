---
title: "2.4.3 single Construct | Microsoft Docs"
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
ms.assetid: 15c180cd-e462-4b41-bf8c-cb8b1afb1a9b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.4.3 single Construct
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**單一**指示詞會識別執行相關聯的結構化的區塊時，就只能由一個執行緒在小組 \(而不一定是主執行緒\) 中所指定的建構。  語法**單一**指示詞時，如下所示：  
  
```  
#pragma omp single [clause[[,] clause] ...] new-line  
   structured-block  
```  
  
 此子句會是下列其中一項：  
  
 **私用 \(** *變數清單* **\)**  
  
 **firstprivate \(** *變數清單* **\)**  
  
 **copyprivate \(** *變數清單* **\)**  
  
 **\[不等待**  
  
 沒有隱含的屏障之後, **單一** 建構，除非  **nowait** 子句所指定。  
  
 若要限制**單一**指示詞如下：  
  
-   只會有一個 **nowait** 子句可以出現在**單一**指示詞。  
  
-   **Copyprivate** 子句必須配合 **nowait** 子句。  
  
## 交互參照：  
  
-   **私用**，  **firstprivate**，以及  **copyprivate** 子句，請參閱[區段 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) 在 25\] 頁面上。