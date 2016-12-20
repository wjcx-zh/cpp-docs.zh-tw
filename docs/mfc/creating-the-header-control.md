---
title: "建立標題控制項 | Microsoft Docs"
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
  - "CHeaderCtrl 類別, 建立"
  - "標題控制項, 建立"
ms.assetid: 7864d9d2-4a2c-4622-b58b-7b110a1e28d2
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 建立標題控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

標題控制項本身不是在對話方塊編輯器中可用 \(雖然您可以將清單控制項，包括標題控制項\)。  
  
### 將標題控制項在對話方塊  
  
1.  請手動將型別 [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md) 的成員變數插入在您的對話方塊類別。  
  
2.  在 [OnInitDialog](../Topic/CDialog::OnInitDialog.md)中，請建立並設定 `CHeaderCtrl`的樣式，請將它，並加以顯示。  
  
3.  將項目加入至標題控制項  
  
4.  使用屬性視窗對應至對話方塊類別中處理函式需要處理的所有標題控制項告知訊息 \(請參閱 [對應訊息至函式](../mfc/reference/mapping-messages-to-functions.md)\)。  
  
### 將標題控制項在檢視 \(非 CListView\)  
  
1.  嵌入 [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md) 物件中的檢視類別。  
  
2.  樣式，位置，並在檢視的 [OnInitialUpdate](../Topic/CView::OnInitialUpdate.md) 成員函式的標題控制項視窗。  
  
3.  將項目加入至標題控制項  
  
4.  使用屬性視窗對應至觀看類別中處理函式需要處理的所有標題控制項告知訊息 \(請參閱 [對應訊息至函式](../mfc/reference/mapping-messages-to-functions.md)\)。  
  
 當檢視或對話物件建立時，在任何情況下，內嵌控制項建立物件。  然後您必須呼叫 [CHeaderCtrl::Create](../Topic/CHeaderCtrl::Create.md) 建立主控視窗。  要放置控制項，請呼叫 [CHeaderCtrl::Layout](../Topic/CHeaderCtrl::Layout.md) 來判斷控制項的初始設定想要的位置的大小和位置和 [SetWindowPos](../Topic/CWnd::SetWindowPos.md) 。  然後依照 [將項目加入至標題控制項](../mfc/adding-items-to-the-header-control.md)中所述的加入項目。  
  
 在 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]\(如需詳細資訊，請參閱 [建立索引標頭控制項](http://msdn.microsoft.com/library/windows/desktop/bb775238) 。  
  
## 請參閱  
 [使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [控制項](../mfc/controls-mfc.md)