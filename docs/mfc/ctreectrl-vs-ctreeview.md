---
title: "CTreeCtrl 和 CTreeView 比較 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CTreeCtrl"
  - "CTreeView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTreeCtrl 類別, 和 CTreeView 類別比較"
  - "CTreeView 類別, 和 CTreeCtrl 類別比較"
  - "樹狀目錄控制項, 和樹狀檢視"
  - "樹狀檢視控制項"
ms.assetid: bba5af25-103f-4b53-84d3-071bc9bd6494
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTreeCtrl 和 CTreeView 比較
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC 提供封裝樹狀目錄控制項的兩個類別: [CTreeCtrl](../mfc/reference/ctreectrl-class.md) 和 [CTreeView](../mfc/reference/ctreeview-class.md)。  每個類別適用於不同的情況。  
  
 當您需要簡單的子視窗控制項時，請使用 `CTreeCtrl` ;例如，在對話方塊。  您在一般對話方塊特別會使用 `CTreeCtrl` ，則會在視窗中的其他子控制項。  
  
 例如，當您想要樹狀目錄控制項會在文件\/檢視架構以及樹狀目錄控制項時，系統檢視視窗中使用 `CTreeView` 。  `CTreeView` 會佔用框架視窗或分隔視窗的整個工作區。  它會自動調整大小，當其父視窗調整大小，因此，它可以處理從功能表、快速鍵和工具列的命令訊息。  因為樹狀目錄控制項包含必要的資料顯示樹狀結構中，對應的資料物件不一定是複雜的—您甚至可以使用 [CDocument](../mfc/reference/cdocument-class.md) 做為文件類型您的資料範本。  
  
## 請參閱  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控制項](../mfc/controls-mfc.md)