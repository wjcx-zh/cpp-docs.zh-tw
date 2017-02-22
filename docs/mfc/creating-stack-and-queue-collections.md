---
title: "建立堆疊和佇列集合 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "集合類別, 建立"
  - "集合, 佇列"
  - "集合, 堆疊"
  - "MFC 集合類別, 佇列集合"
  - "MFC 集合類別, 堆疊集合"
  - "佇列集合"
  - "堆疊"
  - "堆疊集合"
ms.assetid: 3c7bc198-35f0-4fc3-aaed-6005a0f22638
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 建立堆疊和佇列集合
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明如何從 MFC 清單類別建立其他資料結構，例如 [堆疊](#_core_stacks) 和 [佇列](#_core_queues)。  範例會使用衍生自 `CList` 的類別，不過您可以直接使用 `CList`，除非您需要加入功能。  
  
##  <a name="_core_stacks"></a> 堆疊  
 因為標準清單集合有一個箭號和行尾，建立模擬後進先出的堆疊行為之衍生清單集合是很容易的。  堆疊就像自助餐館的一疊盤子。  當餐盤加入堆疊時，它們會在堆疊的上方。  最後加入的盤子是第一個被移除的。  清單集合成員函式 `AddHead` 和 `RemoveHead` 可用來從清單的開頭明確地加入和移除項目；因此，最新加入的項目會最先被移除。  
  
#### 若要建立堆疊集合  
  
1.  從其中一個現有的 MFC 清單類別衍生新的清單類別，並加入多個成員函式支援堆疊作業的功能。  
  
     下列範例顯示如何加入成員函式，以推入項目至堆疊、檢視堆疊的最上層項目，並從堆疊最上方彈出項目：  
  
     [!code-cpp[NVC_MFCCollections#20](../mfc/codesnippet/CPP/creating-stack-and-queue-collections_1.h)]  
  
 請注意這種方法會公開基底 `CObList` 類別。  使用者可以呼叫任何 `CObList` 成員函式，無論它是否對堆疊具有意義。  
  
##  <a name="_core_queues"></a> 佇列  
 因為標準清單集合有一個箭號和行尾，建立模擬先進先出的佇列行為之衍生清單集合也是很容易的。  佇列就像是在自助餐館排隊的人。  隊伍中的第一個人會是第一個被服務的。  當更多人來的時候，他們走到隊伍的尾端等待。  清單集合成員函式 `AddTail` 和 `RemoveHead` 可用來從清單的開頭或尾端明確地加入和移除項目；因此，最新加入的項目會最後被移除。  
  
#### 若要建立佇列集合  
  
1.  從其中一個預先定義的清單類別衍生隨附 MFC 程式庫之新的清單類別，並加入多個成員函式支援佇列作業。  
  
     下列範例顯示如何附加成員函式，將項目加入至佇列的末端，並從佇列的前端取得項目。  
  
     [!code-cpp[NVC_MFCCollections#21](../mfc/codesnippet/CPP/creating-stack-and-queue-collections_2.h)]  
  
## 請參閱  
 [集合](../mfc/collections.md)