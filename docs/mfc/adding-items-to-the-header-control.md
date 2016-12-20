---
title: "將項目加入至標題控制項 | Microsoft Docs"
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
  - "CHeaderCtrl 類別, 加入項目"
  - "控制項 [MFC], 標題"
  - "標題控制項, 加入項目至"
ms.assetid: 2e9a28b1-7302-4a93-8037-c5a4183e589a
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 將項目加入至標題控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在建立自己的標題控制項 \([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)\) 在它的父視窗，請加入許多「標題項目」，您需要:通常每一行。  
  
### 若要加入標題項目  
  
1.  準備一 [HD\_ITEM](http://msdn.microsoft.com/library/windows/desktop/bb775247) 結構。  
  
2.  呼叫 [CHeaderCtrl::InsertItem](../Topic/CHeaderCtrl::InsertItem.md)，將結構。  
  
3.  迴圈其他項目的步驟 1 和 2。  
  
 如需詳細資訊，請參閱 [將項目加入至標題控制項](http://msdn.microsoft.com/library/windows/desktop/bb775238)在 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)] 。  
  
## 請參閱  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [控制項](../mfc/controls-mfc.md)