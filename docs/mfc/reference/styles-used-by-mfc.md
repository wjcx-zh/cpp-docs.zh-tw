---
title: "MFC 使用的樣式 | Microsoft Docs"
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
  - "vc.mfc.styles"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "按鈕, MFC 工具列"
  - "下拉式方塊, 樣式"
  - "編輯樣式 [MFC]"
  - "延伸的視窗樣式"
  - "框架視窗, 樣式"
  - "清單方塊, 樣式"
  - "訊息方塊樣式"
  - "捲軸樣式 [MFC]"
  - "靜態樣式"
  - "樣式"
  - "樣式, MFC"
  - "視窗樣式, 在 MFC 中"
ms.assetid: d3b9af37-31b5-4c97-a8ad-189fd724b04c
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC 使用的樣式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在建立對應的 MFC 物件時，請使用下列模式。  在大部分情況下，這些樣式類別 **Create** 函式的 `dwStyle` 參數設定為。  
  
### MFC 樣式  
  
|樣式|說明|  
|--------|--------|  
|[按鈕樣式](../../mfc/reference/button-styles.md)|要套用至 [CButton 類別](../../mfc/reference/cbutton-class.md) 物件，例如選項按鈕、核取方塊和按鈕。  指定樣式的組合在 [CButton::Create](../Topic/CButton::Create.md)`dwStyle` 參數。|  
|[下拉式方塊樣式](../../mfc/reference/combo-box-styles.md)|要套用至 [CComboBox 類別](../../mfc/reference/ccombobox-class.md) 物件。  指定樣式的組合在 [CComboBox::Create](../Topic/CComboBox::Create.md)`dwStyle` 參數。|  
|[編輯樣式](../../mfc/reference/edit-styles.md)|要套用至 [CEdit 類別](../../mfc/reference/cedit-class.md) 物件。  指定樣式的組合在 [CEdit::Create](../Topic/CEdit::Create.md)`dwStyle` 參數。|  
|[框架視窗樣式。](../../mfc/reference/frame-window-styles-mfc.md)|要套用至 [CFrameWnd 類別](../../mfc/reference/cframewnd-class.md) 物件。  指定樣式的組合在 [CFrameWnd::Create](../Topic/CFrameWnd::Create.md)`dwStyle` 參數。|  
|[清單方塊樣式](../../mfc/reference/list-box-styles.md)|要套用至 [CListBox 類別](../../mfc/reference/clistbox-class.md) 物件。  指定樣式的組合在 [CListBox::Create](../Topic/CListBox::Create.md)`dwStyle` 參數。|  
|[訊息方塊樣式](../../mfc/reference/message-box-styles.md)|要套用至 [AfxMessageBox](../Topic/AfxMessageBox.md) 項目。  指定樣式的組合在 `AfxMessageBox``nType` 參數。|  
|[捲動列樣式](../../mfc/reference/scroll-bar-styles.md)|要套用至 [CScrollBar 類別](../../mfc/reference/cscrollbar-class.md) 物件。  指定樣式的組合在 [CScrollBar::Create](../Topic/CScrollBar::Create.md)`dwStyle` 參數。|  
|[靜態樣式](../../mfc/reference/static-styles.md)|要套用至 [CStatic 類別](../../mfc/reference/cstatic-class.md) 物件。  指定樣式的組合在 [CStatic::Create](../Topic/CStatic::Create.md)`dwStyle` 參數。|  
|[視窗樣式](../../mfc/reference/window-styles.md)|要套用至 [CWnd 類別](../../mfc/reference/cwnd-class.md) 物件。  指定樣式的組合在 [CWnd::Create](../Topic/CWnd::Create.md) 或 [CWnd::CreateEx](../Topic/CWnd::CreateEx.md)`dwStyle` 參數。|  
|[延伸視窗樣式](../../mfc/reference/extended-window-styles.md)|要套用至 [CWnd 類別](../../mfc/reference/cwnd-class.md) 物件。  指定樣式的組合在 [CWnd::CreateEx](../Topic/CWnd::CreateEx.md)`dwExStyle` 參數。|  
  
## 請參閱  
 [類別概觀](../../mfc/class-library-overview.md)