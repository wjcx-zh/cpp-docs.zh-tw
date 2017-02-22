---
title: "MFC 類別物件的類型轉換 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.macros.classes"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "轉換類型"
  - "巨集, 轉型指標"
  - "巨集, 類型轉換"
  - "指標, 類型轉換"
  - "類型轉換"
ms.assetid: e138465e-c35f-4e84-b788-bd200ccf2f0e
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 16
---
# MFC 類別物件的類型轉換
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

型別轉換巨集提供轉換為指定的指標指向特定類別物件的指標，包含或不含檢查轉型是合法的。  
  
 下表列出 MFC 型別轉換巨集。  
  
### 轉換為指標的 MFC 巨集輔助類別  
  
|||  
|-|-|  
|[DYNAMIC\_DOWNCAST](../Topic/DYNAMIC_DOWNCAST.md)|轉換為指標的類別物件時，會檢查時轉型是否是合法的。|  
|[STATIC\_DOWNCAST](../Topic/STATIC_DOWNCAST.md)|轉換為指標從某個類別的物件至相關型別的指標。  在偵錯組建，原因 **ASSERT** ，如果物件不是一種「目標型別。|  
  
## 請參閱  
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)