---
title: "CMultiPaneFrameWnd Class | Microsoft Docs"
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
  - "CMultiPaneFrameWnd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMultiPaneFrameWnd class"
ms.assetid: 989a548e-0d70-46b7-a513-8cf740e1be3e
caps.latest.revision: 36
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMultiPaneFrameWnd Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMultiPaneFrameWnd` 類別擴充 [CPaneFrameWnd Class](../../mfc/reference/cpaneframewnd-class.md)。  它可以支援多個窗格。  而不是控制列的單一內嵌控制代碼， `CMultiPaneFrameWnd` 包含可讓使用者一 `CMultiPaneFrameWnd` 停駐到另一個並動態建立多個浮動的 [CPaneContainerManager Class](../../mfc/reference/cpanecontainermanager-class.md) 物件，做為索引視窗。  
  
## 語法  
  
```  
class CMultiPaneFrameWnd : public CPaneFrameWnd  
```  
  
## 成員  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMultiPaneFrameWnd::AddPane](../Topic/CMultiPaneFrameWnd::AddPane.md)|加入一個窗格。  \(覆寫 [CPaneFrameWnd::AddPane](../Topic/CPaneFrameWnd::AddPane.md)\)。|  
|[CMultiPaneFrameWnd::AddRecentPane](../Topic/CMultiPaneFrameWnd::AddRecentPane.md)||  
|[CMultiPaneFrameWnd::AdjustLayout](../Topic/CMultiPaneFrameWnd::AdjustLayout.md)|調整小型框架視窗的配置。  \(覆寫 [CPaneFrameWnd::AdjustLayout](../Topic/CPaneFrameWnd::AdjustLayout.md)\)。|  
|[CMultiPaneFrameWnd::AdjustPaneFrames](../Topic/CMultiPaneFrameWnd::AdjustPaneFrames.md)|\(覆寫 [CPaneFrameWnd::AdjustPaneFrames](../Topic/CPaneFrameWnd::AdjustPaneFrames.md)\)。|  
|[CMultiPaneFrameWnd::CalcExpectedDockedRect](../Topic/CMultiPaneFrameWnd::CalcExpectedDockedRect.md)|計算一個停駐視窗的預期的矩形。  \(覆寫 [CPaneFrameWnd::CalcExpectedDockedRect](../Topic/CPaneFrameWnd::CalcExpectedDockedRect.md)\)。|  
|[CMultiPaneFrameWnd::CanBeAttached](../Topic/CMultiPaneFrameWnd::CanBeAttached.md)|判斷目前是否可以窗格停駐到另一個窗格或框架視窗。  \(覆寫 [CPaneFrameWnd::CanBeAttached](../Topic/CPaneFrameWnd::CanBeAttached.md)\)。|  
|[CMultiPaneFrameWnd::CanBeDockedToPane](../Topic/CMultiPaneFrameWnd::CanBeDockedToPane.md)|判斷小型框架視窗是否可停駐窗格。  \(覆寫 [CPaneFrameWnd::CanBeDockedToPane](../Topic/CPaneFrameWnd::CanBeDockedToPane.md)\)。|  
|[CMultiPaneFrameWnd::CheckGripperVisibility](../Topic/CMultiPaneFrameWnd::CheckGripperVisibility.md)|\(覆寫 [CPaneFrameWnd::CheckGripperVisibility](../Topic/CPaneFrameWnd::CheckGripperVisibility.md)\)。|  
|[CMultiPaneFrameWnd::CloseMiniFrame](../Topic/CMultiPaneFrameWnd::CloseMiniFrame.md)|\(覆寫 `CPaneFrameWnd::CloseMiniFrame`\)。|  
|[CMultiPaneFrameWnd::ConvertToTabbedDocument](../Topic/CMultiPaneFrameWnd::ConvertToTabbedDocument.md)|轉換窗格為索引標籤式文件。  \(覆寫 [CPaneFrameWnd::ConvertToTabbedDocument](../Topic/CPaneFrameWnd::ConvertToTabbedDocument.md)\)。|  
|[CMultiPaneFrameWnd::DockFrame](../Topic/CMultiPaneFrameWnd::DockFrame.md)||  
|[CMultiPaneFrameWnd::DockPane](../Topic/CMultiPaneFrameWnd::DockPane.md)|停駐窗格。  \(覆寫 [CPaneFrameWnd::DockPane](../Topic/CPaneFrameWnd::DockPane.md)\)。|  
|[CMultiPaneFrameWnd::DockRecentPaneToMainFrame](../Topic/CMultiPaneFrameWnd::DockRecentPaneToMainFrame.md)||  
|[CMultiPaneFrameWnd::GetCaptionText](../Topic/CMultiPaneFrameWnd::GetCaptionText.md)|傳回標題文字。  \(覆寫 [CPaneFrameWnd::GetCaptionText](../Topic/CPaneFrameWnd::GetCaptionText.md)\)。|  
|[CMultiPaneFrameWnd::GetPaneContainerManager](../Topic/CMultiPaneFrameWnd::GetPaneContainerManager.md)|傳回內部容器處理常式之物件的參考。|  
|[CMultiPaneFrameWnd::GetFirstVisiblePane](../Topic/CMultiPaneFrameWnd::GetFirstVisiblePane.md)|傳回在小型框架視窗包含的第一個可見的窗格。  \(覆寫 [CPaneFrameWnd::GetFirstVisiblePane](../Topic/CPaneFrameWnd::GetFirstVisiblePane.md)\)。|  
|[CMultiPaneFrameWnd::GetPane](../Topic/CMultiPaneFrameWnd::GetPane.md)|傳回在小型框架視窗中的窗格。  \(覆寫 [CPaneFrameWnd::GetPane](../Topic/CPaneFrameWnd::GetPane.md)\)。|  
|[CMultiPaneFrameWnd::GetPaneCount](../Topic/CMultiPaneFrameWnd::GetPaneCount.md)|傳回在小型框架視窗窗格中包含的項目數。  \(覆寫 [CPaneFrameWnd::GetPaneCount](../Topic/CPaneFrameWnd::GetPaneCount.md)\)。|  
|[CMultiPaneFrameWnd::GetVisiblePaneCount](../Topic/CMultiPaneFrameWnd::GetVisiblePaneCount.md)|傳回在小型框架視窗包含可見的窗格的數目。  \(覆寫 [CPaneFrameWnd::GetVisiblePaneCount](../Topic/CPaneFrameWnd::GetVisiblePaneCount.md)\)。|  
|[CMultiPaneFrameWnd::InsertPane](../Topic/CMultiPaneFrameWnd::InsertPane.md)||  
|[CMultiPaneFrameWnd::LoadState](../Topic/CMultiPaneFrameWnd::LoadState.md)|從登錄載入窗格的狀態。  \(覆寫 [CPaneFrameWnd::LoadState](../Topic/CPaneFrameWnd::LoadState.md)\)。|  
|[CMultiPaneFrameWnd::OnDockToRecentPos](../Topic/CMultiPaneFrameWnd::OnDockToRecentPos.md)|內建小型框架視窗在其新位置。  \(覆寫 [CPaneFrameWnd::OnDockToRecentPos](../Topic/CPaneFrameWnd::OnDockToRecentPos.md)\)。|  
|[CMultiPaneFrameWnd::OnKillRollUpTimer](../Topic/CMultiPaneFrameWnd::OnKillRollUpTimer.md)|停止彙總計時器。  \(覆寫 [CPaneFrameWnd::OnKillRollUpTimer](../Topic/CPaneFrameWnd::OnKillRollUpTimer.md)\)。|  
|[CMultiPaneFrameWnd::OnPaneRecalcLayout](../Topic/CMultiPaneFrameWnd::OnPaneRecalcLayout.md)|調整一個窗格的配置是小型框架視窗中顯示。  \(覆寫 [CPaneFrameWnd::OnPaneRecalcLayout](../Topic/CPaneFrameWnd::OnPaneRecalcLayout.md)\)。|  
|[CMultiPaneFrameWnd::OnSetRollUpTimer](../Topic/CMultiPaneFrameWnd::OnSetRollUpTimer.md)|設定彙總計時器。  \(覆寫 [CPaneFrameWnd::OnSetRollUpTimer](../Topic/CPaneFrameWnd::OnSetRollUpTimer.md)\)。|  
|[CMultiPaneFrameWnd::OnShowPane](../Topic/CMultiPaneFrameWnd::OnShowPane.md)|呼叫框架，在小型框架視窗的窗格隱藏或顯示。  \(覆寫 [CPaneFrameWnd::OnShowPane](../Topic/CPaneFrameWnd::OnShowPane.md)\)。|  
|[CMultiPaneFrameWnd::PaneFromPoint](../Topic/CMultiPaneFrameWnd::PaneFromPoint.md)|如果包含，它是小型框架視窗內的使用者，提供的點傳回窗格。  \(覆寫 [CPaneFrameWnd::PaneFromPoint](../Topic/CPaneFrameWnd::PaneFromPoint.md)\)。|  
|[CMultiPaneFrameWnd::RemoveNonValidPanes](../Topic/CMultiPaneFrameWnd::RemoveNonValidPanes.md)|呼叫框架移除非有效窗格。  \(覆寫 [CPaneFrameWnd::RemoveNonValidPanes](../Topic/CPaneFrameWnd::RemoveNonValidPanes.md)\)。|  
|[CMultiPaneFrameWnd::RemovePane](../Topic/CMultiPaneFrameWnd::RemovePane.md)|從小型框架視窗中移除窗格。  \(覆寫 [CPaneFrameWnd::RemovePane](../Topic/CPaneFrameWnd::RemovePane.md)\)。|  
|[CMultiPaneFrameWnd::ReplacePane](../Topic/CMultiPaneFrameWnd::ReplacePane.md)|取代另一個窗格。  \(覆寫 [CPaneFrameWnd::ReplacePane](../Topic/CPaneFrameWnd::ReplacePane.md)\)。|  
|[CMultiPaneFrameWnd::SaveState](../Topic/CMultiPaneFrameWnd::SaveState.md)|儲存窗格的狀態變更登錄。  \(覆寫 [CPaneFrameWnd::SaveState](../Topic/CPaneFrameWnd::SaveState.md)\)。|  
|[CMultiPaneFrameWnd::Serialize](../Topic/CMultiPaneFrameWnd::Serialize.md)|\(覆寫 `CPaneFrameWnd::Serialize`\)。|  
|[CMultiPaneFrameWnd::SetDockState](../Topic/CMultiPaneFrameWnd::SetDockState.md)|設定停駐狀態。  \(覆寫 [CPaneFrameWnd::SetDockState](../Topic/CPaneFrameWnd::SetDockState.md)\)。|  
|[CMultiPaneFrameWnd::SetLastFocusedPane](../Topic/CMultiPaneFrameWnd::SetLastFocusedPane.md)||  
|[CMultiPaneFrameWnd::SetPreDockState](../Topic/CMultiPaneFrameWnd::SetPreDockState.md)|設定這個 predocking 的狀態。  \(覆寫 [CPaneFrameWnd::SetPreDockState](../Topic/CPaneFrameWnd::SetPreDockState.md)\)。|  
|[CMultiPaneFrameWnd::StoreRecentDockSiteInfo](../Topic/CMultiPaneFrameWnd::StoreRecentDockSiteInfo.md)|\(覆寫 [CPaneFrameWnd::StoreRecentDockSiteInfo](../Topic/CPaneFrameWnd::StoreRecentDockSiteInfo.md)\)。|  
|[CMultiPaneFrameWnd::StoreRecentTabRelatedInfo](../Topic/CMultiPaneFrameWnd::StoreRecentTabRelatedInfo.md)|\(覆寫 [CPaneFrameWnd::StoreRecentTabRelatedInfo](../Topic/CPaneFrameWnd::StoreRecentTabRelatedInfo.md)\)。|  
  
## 備註  
 大部分在這個類別會覆寫方法的方法。 [CPaneFrameWnd Class](../../mfc/reference/cpaneframewnd-class.md) 類別。  
  
 如果窗格使用 `AFX_CBRS_AUTO_ROLLUP` 樣式和使用者修正不論其他停駐窗格的樣式設定，窗格加入多窗格框架視窗，使用者可以彙總視窗。  
  
 這個架構便會自動建立 `CMultiPaneFrameWnd` 物件，當使用者使用浮動 `CBRS_FLOAT_MULTI` 樣式的窗格時。  
  
 如需動態自類別衍生類別 `CPaneFrameWnd` 類別和建立它的詳細資訊，請參閱 [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)。  
  
## 範例  
 下列範例示範如何擷取指標 `CMultiPaneFrameWnd` 物件。  這個程式碼片段是 [將窗格大小範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_SetPaneSize#4](../../mfc/reference/codesnippet/CPP/cmultipaneframewnd-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CPaneFrameWnd](../../mfc/reference/cpaneframewnd-class.md)  
  
 [CMultiPaneFrameWnd](../../mfc/reference/cmultipaneframewnd-class.md)  
  
## 需求  
 **標題:** afxMultiPaneFrameWnd.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CPaneFrameWnd Class](../../mfc/reference/cpaneframewnd-class.md)