---
title: "將索引標籤加入至索引標籤控制項 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "CTabCtrl 類別, 加入索引標籤"
  - "在 CTabCtrls 上放置索引標籤"
  - "索引標籤控制項, 加入索引標籤"
  - "索引標籤, 加入至 CTabCtrl 類別"
ms.assetid: 7f3d9340-e3c7-4c71-9912-be57534ecc78
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 將索引標籤加入至索引標籤控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在建立索引標籤控制項 \([CTabCtrl](../mfc/reference/ctabctrl-class.md)\)，將多個選項，您需要。  
  
### 若要加入標籤項目  
  
1.  準備一 [TCITEM](http://msdn.microsoft.com/library/windows/desktop/bb760554) 結構。  
  
2.  呼叫 [CTabCtrl::InsertItem](../Topic/CTabCtrl::InsertItem.md)，將結構。  
  
3.  迴圈其他選項項目的步驟 1 和 2。  
  
 在 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]\(如需詳細資訊，請參閱 [建立索引標籤控制項](http://msdn.microsoft.com/library/windows/desktop/bb760550) 。  
  
## 請參閱  
 [使用 CTabCtrl](../mfc/using-ctabctrl.md)   
 [控制項](../mfc/controls-mfc.md)