---
title: "與樹狀目錄控制項通訊 | Microsoft Docs"
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
  - "通訊, 樹狀目錄控制項"
  - "CTreeCtrl 類別, 呼叫成員函式"
  - "樹狀目錄控制項"
  - "樹狀目錄控制項, 與之通訊"
ms.assetid: 680ad9ee-b11f-452d-93fa-501ca7d7e069
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 與樹狀目錄控制項通訊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

您在 [CTreeCtrl](../mfc/reference/ctreectrl-class.md) 物件根據物件如何建立使用不同的方法呼叫成員函式。  
  
-   如果樹狀目錄控制項在對話方塊中，使用您在對話方塊類別建立的 `CTreeCtrl` 型別的成員變數。  
  
-   如果樹狀目錄控制項是子視窗，請使用您用來建構物件的 `CTreeCtrl` 物件 \(或指標\) 。  
  
-   如果您使用 `CTreeView` 物件，請使用 [CTreeView::GetTreeCtrl](../Topic/CTreeView::GetTreeCtrl.md) 函式取得此樹狀目錄控制項的參考。  您可以使用這個值初始化其他參考或指派參考的位址為 `CTreeCtrl` 指標。  
  
## 請參閱  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控制項](../mfc/controls-mfc.md)