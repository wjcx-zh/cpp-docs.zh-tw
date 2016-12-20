---
title: "CMFCVisualManagerVS2005 Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCVisualManagerVS2005"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCVisualManagerVS2005 class"
ms.assetid: ea39b9ae-327e-4a51-bce7-dc84c78f005b
caps.latest.revision: 30
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCVisualManagerVS2005 Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCVisualManagerVS2005` 寫入應用程式一次 Microsoft Visual Studio 2005 隨即出現。  
  
## 語法  
  
```  
class CMFCVisualManagerVS2005 : public CMFCVisualManagerOffice2003  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCVisualManagerVS2005::GetDockingTabsBordersSize](../Topic/CMFCVisualManagerVS2005::GetDockingTabsBordersSize.md)|架構會呼叫這個方法，以繪製和內建索引標籤式窗格時。  \(覆寫 [CMFCVisualManager::GetDockingTabsBordersSize](../Topic/CMFCVisualManager::GetDockingTabsBordersSize.md)\)。|  
|[CMFCVisualManagerVS2005::GetMDITabsBordersSize](../Topic/CMFCVisualManagerVS2005::GetMDITabsBordersSize.md)|則繪製視窗之前，架構會呼叫這個方法會判斷 MDITabs 視窗的框線大小。  \(覆寫 [CMFCVisualManager::GetMDITabsBordersSize](../Topic/CMFCVisualManager::GetMDITabsBordersSize.md)\)。|  
|[CMFCVisualManagerVS2005::GetPropertyGridGroupColor](../Topic/CMFCVisualManagerVS2005::GetPropertyGridGroupColor.md)|\(覆寫 [CMFCVisualManagerOffice2003::GetPropertyGridGroupColor](../Topic/CMFCVisualManagerOffice2003::GetPropertyGridGroupColor.md)\)。|  
|[CMFCVisualManagerVS2005::GetTabFrameColors](../Topic/CMFCVisualManagerVS2005::GetTabFrameColors.md)|\(覆寫 [CMFCVisualManagerOffice2003::GetTabFrameColors](../Topic/CMFCVisualManagerOffice2003::GetTabFrameColors.md)\)。|  
|[CMFCVisualManagerVS2005::HasOverlappedAutoHideButtons](../Topic/CMFCVisualManagerVS2005::HasOverlappedAutoHideButtons.md)|傳回自動隱藏按鈕是否在目前視覺管理員重疊。  \(覆寫 [CMFCVisualManager::HasOverlappedAutoHideButtons](../Topic/CMFCVisualManager::HasOverlappedAutoHideButtons.md)\)。|  
|[CMFCVisualManagerVS2005::OnDrawAutoHideButtonBorder](../Topic/CMFCVisualManagerVS2005::OnDrawAutoHideButtonBorder.md)|\(覆寫 [CMFCVisualManagerOffice2003::OnDrawAutoHideButtonBorder](../Topic/CMFCVisualManagerOffice2003::OnDrawAutoHideButtonBorder.md)\)。|  
|[CMFCVisualManagerVS2005::OnDrawCaptionButton](../Topic/CMFCVisualManagerVS2005::OnDrawCaptionButton.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnDrawCaptionButton`\)。|  
|[CMFCVisualManagerVS2005::OnDrawPaneCaption](../Topic/CMFCVisualManagerVS2005::OnDrawPaneCaption.md)|\(覆寫 [CMFCVisualManagerOffice2003::OnDrawPaneCaption](../Topic/CMFCVisualManagerOffice2003::OnDrawPaneCaption.md)\)。|  
|[CMFCVisualManagerVS2005::OnDrawSeparator](../Topic/CMFCVisualManagerVS2005::OnDrawSeparator.md)|\(覆寫 [CMFCVisualManagerOffice2003::OnDrawSeparator](../Topic/CMFCVisualManagerOffice2003::OnDrawSeparator.md)\)。|  
|[CMFCVisualManagerVS2005::OnDrawTab](../Topic/CMFCVisualManagerVS2005::OnDrawTab.md)|\(覆寫 [CMFCVisualManagerOffice2003::OnDrawTab](../Topic/CMFCVisualManagerOffice2003::OnDrawTab.md)\)。|  
|[CMFCVisualManagerVS2005::OnDrawToolBoxFrame](../Topic/CMFCVisualManagerVS2005::OnDrawToolBoxFrame.md)|\(覆寫 [CMFCVisualManager::OnDrawToolBoxFrame](../Topic/CMFCVisualManager::OnDrawToolBoxFrame.md)\)。|  
|[CMFCVisualManagerVS2005::OnEraseTabsArea](../Topic/CMFCVisualManagerVS2005::OnEraseTabsArea.md)|\(覆寫 [CMFCVisualManagerOffice2003::OnEraseTabsArea](../Topic/CMFCVisualManagerOffice2003::OnEraseTabsArea.md)\)。|  
|[CMFCVisualManagerVS2005::OnFillAutoHideButtonBackground](../Topic/CMFCVisualManagerVS2005::OnFillAutoHideButtonBackground.md)|\(覆寫 [CMFCVisualManagerOffice2003::OnFillAutoHideButtonBackground](../Topic/CMFCVisualManagerOffice2003::OnFillAutoHideButtonBackground.md)\)。|  
|[CMFCVisualManagerVS2005::OnFillHighlightedArea](../Topic/CMFCVisualManagerVS2005::OnFillHighlightedArea.md)|\(覆寫 [CMFCVisualManagerOffice2003::OnFillHighlightedArea](../Topic/CMFCVisualManagerOffice2003::OnFillHighlightedArea.md)\)。|  
|[CMFCVisualManagerVS2005::OnFillMiniFrameCaption](../Topic/CMFCVisualManagerVS2005::OnFillMiniFrameCaption.md)|\(覆寫 `CMFCVisualManagerOfficeXP::OnFillMiniFrameCaption`\)。|  
|[CMFCVisualManagerVS2005::OnUpdateSystemColors](../Topic/CMFCVisualManagerVS2005::OnUpdateSystemColors.md)|\(覆寫 [CMFCVisualManagerOffice2003::OnUpdateSystemColors](../Topic/CMFCVisualManagerOffice2003::OnUpdateSystemColors.md)\)。|  
  
## 備註  
 您可以使用 CMFCVisualManagerVS2005 類別變更應用程式的視覺外觀類似 [!INCLUDE[vsprvsext](../Token/vsprvsext_md.md)]。  
  
 這個類別的所有成員都是自這個類別的祖系衍生的虛擬函式， [CMFCVisualManager Class](../../mfc/reference/cmfcvisualmanager-class.md)。  
  
## 範例  
 下列範例示範如何使用視覺管理員為 2005 年。  這個程式碼片段是 [桌面警示示範範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_DesktopAlertDemo#9](../../mfc/reference/codesnippet/CPP/cmfcvisualmanagervs2005-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCBaseVisualManager](../../mfc/reference/cmfcbasevisualmanager-class.md)  
  
 [CMFCVisualManager](../../mfc/reference/cmfcvisualmanager-class.md)  
  
 [CMFCVisualManagerOfficeXP](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)  
  
 [CMFCVisualManagerOffice2003](../../mfc/reference/cmfcvisualmanageroffice2003-class.md)  
  
 [CMFCVisualManagerVS2005](../../mfc/reference/cmfcvisualmanagervs2005-class.md)  
  
## 需求  
 **標題:** afxvisualmanagervs2005.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCVisualManager Class](../../mfc/reference/cmfcvisualmanager-class.md)   
 [CMFCVisualManagerOfficeXP Class](../../mfc/reference/cmfcvisualmanagerofficexp-class.md)   
 [CMFCVisualManagerWindows Class](../../mfc/reference/cmfcvisualmanagerwindows-class.md)   
 [CMFCVisualManagerOffice2003 Class](../../mfc/reference/cmfcvisualmanageroffice2003-class.md)   
 [CMFCVisualManager::SetDefaultManager](../Topic/CMFCVisualManager::SetDefaultManager.md)