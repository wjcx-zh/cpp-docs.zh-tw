---
title: "樹狀目錄控制項拖放作業 | Microsoft Docs"
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
  - "CTreeCtrl 類別, 拖放作業"
  - "拖放, CTreeCtrl"
  - "樹狀目錄控制項, 拖放作業"
ms.assetid: 3cf78b4c-4579-4fe1-9bc9-c5ab876e4af1
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 樹狀目錄控制項拖放作業
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當使用者開始拖曳項目時，樹狀控制項 \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) 傳送通知。  當使用者以滑鼠左鍵開始拖曳項目時，控制項傳送 [TVN\_BEGINDRAG](http://msdn.microsoft.com/library/windows/desktop/bb773504) 通知訊息，並在使用者以右鍵開始拖曳時 傳送 [TVN\_BEGINRDRAG](http://msdn.microsoft.com/library/windows/desktop/bb773509) 通知訊息。  您可以設定樹狀控制項 **TVS\_DISABLEDRAGDROP** 樣式，防止樹狀控制項傳送這些通知訊息。  
  
 藉由呼叫 [CreateDragImage](../Topic/CTreeCtrl::CreateDragImage.md) 成員函式，在拖曳作業期間取得影像來顯示。  樹狀控制項會根據被拖曳的項目之標籤產生拖曳點陣圖。  然後樹狀控制項建立影像清單、加入點陣圖至其中，並將指標傳回 [CImageList](../mfc/reference/cimagelist-class.md) 物件。  
  
 您必須提供實際拖曳項目的程式碼。  這通常需要使用影像清單函式的拖曳功能，並在拖曳作業開始後處理 [WM\_MOUSEMOVE](http://msdn.microsoft.com/library/windows/desktop/ms645616) 和 [WM\_LBUTTONUP](http://msdn.microsoft.com/library/windows/desktop/ms645608) \(或 [WM\_RBUTTONUP](http://msdn.microsoft.com/library/windows/desktop/ms646243)\) 訊息傳送。  如需影像清單函式的詳細資訊，請參閱 *MFC 參考* 的 [CImageList](../mfc/reference/cimagelist-class.md) 和 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)] 的 [影像清單](http://msdn.microsoft.com/library/windows/desktop/bb761389)。  如需拖曳樹狀控制項的詳細資訊，請參閱也在 [!INCLUDE[winsdkshort](../atl/reference/includes/winsdkshort_md.md)] 的 [拖曳樹狀檢視項目](http://msdn.microsoft.com/library/windows/desktop/bb760017)。  
  
 如果在樹狀控制項中的項目是拖放作業的目標，您需要知道滑鼠游標何時在目標項目上。  您可以藉由呼叫 [HitTest](../Topic/CTreeCtrl::HitTest.md) 成員函式找到。  您指定的點和整數，或包含滑鼠游標目前座標的 [TVHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb773448) 結構的位址。  當函式傳回時，整數或結構包含表示相對於樹狀控制項的滑鼠游標位置之旗標。  如果游標在樹狀控制項中的項目上，結構也會包含項目的控制代碼。  
  
 您可以藉由呼叫 [SetItem](../Topic/CTreeCtrl::SetItem.md) 成員函式，將狀態設定為 `TVIS_DROPHILITED` 值，指出項目是拖放作業的目標。  具有這個狀態的項目在會繪製為用來表示拖放目標的樣式。  
  
## 請參閱  
 [使用 CTreeCtrl](../mfc/using-ctreectrl.md)   
 [控制項](../mfc/controls-mfc.md)