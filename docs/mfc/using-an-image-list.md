---
title: "使用影像清單 | Microsoft Docs"
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
  - "CImageList 類別, 使用"
  - "影像清單 [C++]"
  - "清單 [C++], 影像"
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用影像清單
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

影像清單的一般使用方式會遵循下列模式:  
  
-   [CImageList](../mfc/reference/cimagelist-class.md) 建構物件並呼叫其中一個 [建立](../Topic/CImageList::Create.md) 的函式多載建立影像清單並附加至 `CImageList` 物件。  
  
-   如果您沒有將影像，當您建立影像清單中的，對影像清單中的影像會藉由呼叫 [加入](../Topic/CImageList::Add.md) 或 [讀取](../Topic/CImageList::Read.md) 成員函式。  
  
-   使用影像清單的 [繪製](../Topic/CImageList::Draw.md) 成員函式，使影像清單的控制項會呼叫該控制項的適當的成員函式或從影像清單中繪製影像。  
  
-   使用影像清單的內建支援拖曳，或許可以讓使用者將影像。  
  
> [!NOTE]
>  如果影像清單建立 **new** 運算子，您必須在終結 `CImageList` 物件，當您變更時。  
  
## 請參閱  
 [使用 CImageList](../mfc/using-cimagelist.md)   
 [控制項](../mfc/controls-mfc.md)