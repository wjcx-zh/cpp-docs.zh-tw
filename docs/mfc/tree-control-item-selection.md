---
title: "樹狀目錄控制項目選取 | Microsoft Docs"
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
  - "控制項 [MFC], 在其中選取項目"
  - "CTreeCtrl 類別, 項目選取"
  - "樹狀目錄控制項中的項目選取"
  - "樹狀目錄控制項, 項目選取"
ms.assetid: 7bcb3b16-b9c8-4c06-9350-7bc3c1c5009b
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 樹狀目錄控制項目選取
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當選取範圍從某個項目變更為另一個時，樹狀目錄控制項 \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) 傳送 [TVN\_SELCHANGING](http://msdn.microsoft.com/library/windows/desktop/bb773547) 和 [TVN\_SELCHANGED](http://msdn.microsoft.com/library/windows/desktop/bb773544) 告知訊息。  兩個告知包含指出變更是否是按一下滑鼠或按鍵動作的結果。  通知還包含擷取選取項目和項目會遺失選取項目的相關資訊。  您可以使用這項資訊來設定由項目的選取狀態的項目屬性。  傳回以回應 **TVN\_SELCHANGING** 的 **TRUE** 防止變更選取範圍;傳回 **FALSE** 允許變更。  
  
 應用程式可以藉由呼叫 [SelectItem](../Topic/CTreeCtrl::SelectItem.md) 成員函式變更選取範圍。  
  
## 請參閱  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控制項](../mfc/controls-mfc.md)