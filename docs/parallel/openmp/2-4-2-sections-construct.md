---
title: "2.4.2 sections Construct | Microsoft Docs"
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
ms.assetid: e9e6e3ea-7fc9-4925-8f68-92b8a5bb1e76
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.4.2 sections Construct
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**章節**指示詞會識別 noniterative 的工作共用建構，它指定一組會分割為小組中的執行緒之間的建構。  在小組中的執行緒中，每個區段會執行一次。  語法**章節**指示詞時，如下所示：  
  
```  
#pragma omp sections [clause[[,] clause] ...] new-line  
   {  
   [#pragma omp section new-line]  
      structured-block  
   [#pragma omp section new-line  
      structured-block ]  
...  
}  
```  
  
 此子句會是下列其中一項：  
  
 **私用 \(** *變數清單* **\)**  
  
 **firstprivate \(** *變數清單* **\)**  
  
 **lastprivate \(** *變數清單* **\)**  
  
 **reduction\(** *operator* **:**  *variable\-list* **\)**  
  
 **\[不等待**  
  
 每個區段前面加上**一節** 指示詞，雖然 **區段**指示詞都是選擇性的第一節。  **一節** 指示詞必須出現在語彙範圍的 **章節**指示詞。  沒有隱含的屏障，結尾的**章節** 建構，除非  **\[不等待**所指定。  
  
 若要限制**章節**指示詞，如下所示是：  
  
-   A **一節** 指示詞只能出現的語彙範圍外 **章節**指示詞。  
  
-   只會有一個 **nowait** 子句可以出現在**章節**指示詞。  
  
## 交互參照：  
  
-   **私用**，  **firstprivate**，  **lastprivate**，以及 **降低** 子句，請參閱 [區段 2.7.2](../../parallel/openmp/2-7-2-data-sharing-attribute-clauses.md) 在 25\] 頁面上。