---
title: "進度控制項的設定 | Microsoft Docs"
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
  - "CProgressCtrl 類別, 設定"
  - "進度控制項 [C++], 設定"
ms.assetid: f4616e91-74fa-4000-ba0d-d3ddc0ee075b
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# 進度控制項的設定
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

進度控制項 \([CProgressCtrl](../mfc/reference/cprogressctrl-class.md)\) 基本設定為範圍和目前位置。  這個範圍表示作業的整個持續期間。  目前位置代表您的應用程式取得了往完成作業的進度。  對範圍或位置原因的任何變更重新繪製其本身的進度控制項。  
  
 根據預設，這個範圍設定為 0 – 100 和初始位置設定為 0。  若要擷取進度控制項的目前範圍設定，請使用 [GetRange](../Topic/CProgressCtrl::GetRange.md) 成員函式。  若要變更這個範圍，請使用 [SetRange](../Topic/CProgressCtrl::SetRange.md) 成員函式。  
  
 若要設定位置，請使用 [SetPos](../Topic/CProgressCtrl::SetPos.md)。  若要擷取目前位置，但不指定新的值，請使用 [GetPos](../Topic/CProgressCtrl::GetPos.md)。  例如，您可以在目前作業的狀態可能要查詢。  
  
 若要逐步執行進度控制項的目前位置，請使用 [StepIt](../Topic/CProgressCtrl::StepIt.md)。  若要設定數量每個步驟，請使用 [SetStep](../Topic/CProgressCtrl::SetStep.md)。  
  
## 請參閱  
 [使用 CProgressCtrl](../mfc/using-cprogressctrl.md)   
 [控制項](../mfc/controls-mfc.md)