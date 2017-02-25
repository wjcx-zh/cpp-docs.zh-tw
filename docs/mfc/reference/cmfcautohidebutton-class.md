---
title: "CMFCAutoHideButton Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCAutoHideButton"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCAutoHideButton class"
ms.assetid: c80e6b8b-25ca-4d12-9d27-457731028ab0
caps.latest.revision: 33
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 35
---
# CMFCAutoHideButton Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可顯示或隱藏 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md) \(設定為隱藏\) 的按鈕。  
  
## 語法  
  
```  
class CMFCAutoHideButton : public CObject  
```  
  
## 成員  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCAutoHideButton::BringToTop](../Topic/CMFCAutoHideButton::BringToTop.md)||  
|[CMFCAutoHideButton::Create](../Topic/CMFCAutoHideButton::Create.md)|建立並初始化自動隱藏按鈕。|  
|[CMFCAutoHideButton::GetAlignment](../Topic/CMFCAutoHideButton::GetAlignment.md)|擷取自動隱藏按鈕的對齊方式。|  
|[CMFCAutoHideButton::GetAutoHideWindow](../Topic/CMFCAutoHideButton::GetAutoHideWindow.md)|傳回與自動隱藏按鈕相關聯的 [CDockablePane](../../mfc/reference/cdockablepane-class.md) 物件。|  
|[CMFCAutoHideButton::GetParentToolBar](../Topic/CMFCAutoHideButton::GetParentToolBar.md)||  
|[CMFCAutoHideButton::GetRect](../Topic/CMFCAutoHideButton::GetRect.md)||  
|[CMFCAutoHideButton::GetSize](../Topic/CMFCAutoHideButton::GetSize.md)|決定自動隱藏按鈕的大小。|  
|[CMFCAutoHideButton::GetTextSize](../Topic/CMFCAutoHideButton::GetTextSize.md)|傳回自動隱藏按鈕文字標籤的大小。|  
|[CMFCAutoHideButton::HighlightButton](../Topic/CMFCAutoHideButton::HighlightButton.md)|反白顯示自動隱藏按鈕。|  
|[CMFCAutoHideButton::IsActive](../Topic/CMFCAutoHideButton::IsActive.md)|指出自動隱藏按鈕是否為作用中。|  
|[CMFCAutoHideButton::IsHighlighted](../Topic/CMFCAutoHideButton::IsHighlighted.md)|傳回自動隱藏按鈕反白顯示的狀態。|  
|[CMFCAutoHideButton::IsHorizontal](../Topic/CMFCAutoHideButton::IsHorizontal.md)|判斷自動隱藏按鈕是水平或垂直。|  
|[CMFCAutoHideButton::IsTop](../Topic/CMFCAutoHideButton::IsTop.md)||  
|[CMFCAutoHideButton::IsVisible](../Topic/CMFCAutoHideButton::IsVisible.md)|指出是否顯示按鈕。|  
|[CMFCAutoHideButton::Move](../Topic/CMFCAutoHideButton::Move.md)||  
|[CMFCAutoHideButton::OnDraw](../Topic/CMFCAutoHideButton::OnDraw.md)|當它繪製自動隱藏按鈕時，架構會呼叫這個方法。|  
|[CMFCAutoHideButton::OnDrawBorder](../Topic/CMFCAutoHideButton::OnDrawBorder.md)|當它繪製自動隱藏按鈕的邊框時，架構會呼叫這個方法。|  
|[CMFCAutoHideButton::OnFillBackground](../Topic/CMFCAutoHideButton::OnFillBackground.md)|當它填入自動隱藏按鈕的背景時，架構會呼叫這個方法。|  
|[CMFCAutoHideButton::ReplacePane](../Topic/CMFCAutoHideButton::ReplacePane.md)||  
|[CMFCAutoHideButton::ShowAttachedWindow](../Topic/CMFCAutoHideButton::ShowAttachedWindow.md)|顯示或隱藏相關聯的 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md)。|  
|[CMFCAutoHideButton::ShowButton](../Topic/CMFCAutoHideButton::ShowButton.md)|顯示或隱藏自動隱藏按鈕。|  
|[CMFCAutoHideButton::UnSetAutoHideMode](../Topic/CMFCAutoHideButton::UnSetAutoHideMode.md)||  
  
## 備註  
 建立時，`CMFCAutoHideButton` 物件會附加到 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md)。  `CDockablePane` 物件會隨著使用者與 `CMFCAutoHideButton` 物件的互動隱藏或顯示。  
  
 根據預設，當使用者開啟自動隱藏時，架構會自動建立 `CMFCAutoHideButton`。  架構可以建立自訂 UI 類別而不是 `CMFCAutoHideButton` 類別的項目。  若要指定架構應該使用的自訂 UI 類別，請將靜態成員變數 `CMFCAutoHideBar::m_pAutoHideButtonRTS` 設定為等於自訂 UI 類別。  根據預設，此變數會設為 `CMFCAutoHideButton`。  
  
## 範例  
 下列範例示範如何建構 `CMFCAutoHideButton` 物件，以及使用 `CMFCAutoHideButton` 類別中的各種方法。  此範例示範如何初始化 `CMFCAutoHideButton` 物件 \(使用其 `Create` 方法\)，顯示相關聯的 `CDockablePane` 類別，並顯示自動隱藏按鈕。  
  
 [!code-cpp[NVC_MFC_RibbonApp#32](../../mfc/reference/codesnippet/CPP/cmfcautohidebutton-class_1.cpp)]  
  
## 繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCAutoHideButton](../../mfc/reference/cmfcautohidebutton-class.md)  
  
## 需求  
 **標頭：**afxautohidebutton.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCAutoHideBar Class](../../mfc/reference/cmfcautohidebar-class.md)   
 [CAutoHideDockSite Class](../../mfc/reference/cautohidedocksite-class.md)