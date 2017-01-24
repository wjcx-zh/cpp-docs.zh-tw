---
title: "CPaneDivider Class | Microsoft Docs"
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
  - "CPaneDivider"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPaneDivider class"
ms.assetid: 8e828a5d-232f-4127-b8e3-7fa45a7a476e
caps.latest.revision: 25
caps.handback.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPaneDivider Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[!INCLUDE[cpp_fp_under_construction](../../mfc/reference/includes/cpp_fp_under_construction_md.md)]  
  
 `CPaneDivider` 類別分割成兩個窗格，分割窗格的兩個群組或從主框架視窗的工作區 \(Client Area\) 分隔窗格的群組。  
  
## 語法  
  
```  
class CPaneDivider : public CBasePane  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CPaneDivider::CPaneDivider](../Topic/CPaneDivider::CPaneDivider.md)||  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CPaneDivider::AddPaneContainer](../Topic/CPaneDivider::AddPaneContainer.md)||  
|[CPaneDivider::AddPane](../Topic/CPaneDivider::AddPane.md)||  
|[CPaneDivider::AddRecentPane](../Topic/CPaneDivider::AddRecentPane.md)||  
|[CPaneDivider::CalcExpectedDockedRect](../Topic/CPaneDivider::CalcExpectedDockedRect.md)||  
|[CPaneDivider::CalcFixedLayout](../Topic/CPaneDivider::CalcFixedLayout.md)|\(覆寫 [CBasePane::CalcFixedLayout](../Topic/CBasePane::CalcFixedLayout.md)\)。|  
|[CPaneDivider::CheckVisibility](../Topic/CPaneDivider::CheckVisibility.md)||  
|[CPaneDivider::CreateEx](../Topic/CPaneDivider::CreateEx.md)|\(覆寫 [CBasePane::CreateEx](../Topic/CBasePane::CreateEx.md)\)。|  
|[CPaneDivider::DoesAllowDynInsertBefore](../Topic/CPaneDivider::DoesAllowDynInsertBefore.md)|\(覆寫 [CBasePane::DoesAllowDynInsertBefore](../Topic/CBasePane::DoesAllowDynInsertBefore.md)\)。|  
|[CPaneDivider::DoesContainFloatingPane](../Topic/CPaneDivider::DoesContainFloatingPane.md)||  
|[CPaneDivider::FindPaneContainer](../Topic/CPaneDivider::FindPaneContainer.md)||  
|[CPaneDivider::FindTabbedPane](../Topic/CPaneDivider::FindTabbedPane.md)||  
|[CPaneDivider::GetDefaultWidth](../Topic/CPaneDivider::GetDefaultWidth.md)||  
|[CPaneDivider::GetFirstPane](../Topic/CPaneDivider::GetFirstPane.md)||  
|[CPaneDivider::GetPaneDividerStyle](../Topic/CPaneDivider::GetPaneDividerStyle.md)||  
|[CPaneDivider::GetRootContainerRect](../Topic/CPaneDivider::GetRootContainerRect.md)||  
|[CPaneDivider::GetWidth](../Topic/CPaneDivider::GetWidth.md)||  
|[CPaneDivider::Init](../Topic/CPaneDivider::Init.md)||  
|[CPaneDivider::InsertPane](../Topic/CPaneDivider::InsertPane.md)||  
|[CPaneDivider::IsAutoHideMode](../Topic/CPaneDivider::IsAutoHideMode.md)|\(覆寫 [CBasePane::IsAutoHideMode](../Topic/CBasePane::IsAutoHideMode.md)\)。|  
|[CPaneDivider::IsDefault](../Topic/CPaneDivider::IsDefault.md)||  
|[CPaneDivider::IsHorizontal](../Topic/CPaneDivider::IsHorizontal.md)|\(覆寫 [CBasePane::IsHorizontal](../Topic/CBasePane::IsHorizontal.md)\)。|  
|[CPaneDivider::Move](../Topic/CPaneDivider::Move.md)||  
|[CPaneDivider::NotifyAboutRelease](../Topic/CPaneDivider::NotifyAboutRelease.md)||  
|[CPaneDivider::OnShowPane](../Topic/CPaneDivider::OnShowPane.md)||  
|[CPaneDivider::ReleaseEmptyPaneContainers](../Topic/CPaneDivider::ReleaseEmptyPaneContainers.md)||  
|[CPaneDivider::RemovePane](../Topic/CPaneDivider::RemovePane.md)||  
|[CPaneDivider::ReplacePane](../Topic/CPaneDivider::ReplacePane.md)||  
|[CPaneDivider::RepositionPanes](../Topic/CPaneDivider::RepositionPanes.md)||  
|[CPaneDivider::Serialize](../Topic/CPaneDivider::Serialize.md)|\(覆寫 `CBasePane::Serialize`\)。|  
|[CPaneDivider::SetAutoHideMode](../Topic/CPaneDivider::SetAutoHideMode.md)||  
|[CPaneDivider::SetPaneContainerManager](../Topic/CPaneDivider::SetPaneContainerManager.md)||  
|[CPaneDivider::ShowWindow](../Topic/CPaneDivider::ShowWindow.md)||  
|[CPaneDivider::StoreRecentDockSiteInfo](../Topic/CPaneDivider::StoreRecentDockSiteInfo.md)||  
|[CPaneDivider::StoreRecentTabRelatedInfo](../Topic/CPaneDivider::StoreRecentTabRelatedInfo.md)||  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CPaneDivider::GetPanes](../Topic/CPaneDivider::GetPanes.md)|傳回位於 [CPaneContainer Class](../../mfc/reference/cpanecontainer-class.md)窗格的清單中。  應為預設窗格分割線才能呼叫這個方法。|  
|[CPaneDivider::GetPaneDividers](../Topic/CPaneDivider::GetPaneDividers.md)|傳回位於 [CPaneContainer Class](../../mfc/reference/cpanecontainer-class.md)窗格的分割線清單。  應為預設窗格分割線才能呼叫這個方法。|  
  
### 資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CPaneDivider::m\_nDefaultWidth](../Topic/CPaneDivider::m_nDefaultWidth.md)|在所有窗格分割線像素指定預設寬度在應用程式中。|  
|[CPaneDivider::m\_pSliderRTC](../Topic/CPaneDivider::m_pSliderRTC.md)|會保留該指標。如需 `CPaneDivider`的執行階段類別資訊衍生物件。|  
  
## 備註  
 當窗格停駐時，架構會自動建立 `CPaneDivider` 物件。  
  
 具有窗格分割線的兩種類型:  
  
-   在  窗格中，將一組停駐在主框架視窗時，預設的右邊窗格分割線建立。  預設窗格分割線保有指標 [CPaneContainerManager Class](../../mfc/reference/cpanecontainermanager-class.md) 並在  窗格中的  群組中的大部分作業方向 \(例如調整窗格或內建的另一個窗格或容器\) 給容器的處理常式。  每個停駐窗格維護指標為其預設窗格分割線。  
  
-   一個規則窗格分割線分割在容器的兩個窗格。  如需詳細資訊，請參閱 [CPaneContainer Class](../../mfc/reference/cpanecontainer-class.md)。  
  
## 範例  
 下列範例示範如何從物件取得 `CWorkspaceBar``CPaneDivider` 物件。  這個程式碼片段是 [索引標籤式 MDI 示範範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_MDITabsDemo#5](../../mfc/reference/codesnippet/CPP/cpanedivider-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md) [CCmdTarget](../../mfc/reference/ccmdtarget-class.md) [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CBasePane](../../mfc/reference/cbasepane-class.md) [CPaneDivider](../../mfc/reference/cpanedivider-class.md)  
  
## 需求  
 **標題:** afxPaneDivider.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CPaneContainerManager Class](../../mfc/reference/cpanecontainermanager-class.md)   
 [CPaneContainer Class](../../mfc/reference/cpanecontainer-class.md)   
 [CDockingManager Class](../../mfc/reference/cdockingmanager-class.md)   
 [CBasePane Class](../../mfc/reference/cbasepane-class.md)