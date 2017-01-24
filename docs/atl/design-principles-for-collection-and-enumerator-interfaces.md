---
title: "Design Principles for Collection and Enumerator Interfaces | Microsoft Docs"
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
helpviewer_keywords: 
  - "collection interfaces"
  - "enumerator interfaces"
ms.assetid: ea19a39e-6333-41a1-be62-5435c236640e
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Design Principles for Collection and Enumerator Interfaces
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在介面之後的每種不同的設計原則:  
  
-   將介面傳遞 **項目** 方法提供對單一項目的隨機 *存取* 集合，可讓用戶端知道集合中有多少個項目透過 **計數** 屬性和經常允許用戶端加入和移除項目。  
  
-   列舉值介面的 *順序* 對集合的 *多* 個項目，所以不允許用戶端知道集合中有多少個項目 \(直到列舉程式停止傳回項目\)，因此，它不會提供將項目加入或移除任何模式。  
  
 介面的每個型別提供在存取扮演不同的角色對於在集合中的項目。  
  
## 請參閱  
 [集合和列舉程式](../atl/atl-collections-and-enumerators.md)