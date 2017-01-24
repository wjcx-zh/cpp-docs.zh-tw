---
title: "CMFCTabCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCTabCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCTabCtrl class"
  - "CMFCTabCtrl constructor"
  - "CMFCTabCtrl::GetTabFromPoint method"
  - "CMFCTabCtrl::IsPtInTabArea method"
  - "CMFCTabCtrl::MoveTab method"
  - "CMFCTabCtrl::PreTranslateMessage method"
  - "CMFCTabCtrl::RecalcLayout method"
  - "CMFCTabCtrl::SwapTabs method"
ms.assetid: d441385d-2c72-4203-96fa-deae2273da35
caps.latest.revision: 33
caps.handback.revision: 22
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCTabCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CMFCTabCtrl` 類別針對索引標籤控制項的功能。  索引標籤控制項顯示具有平面或三個維度的索引標籤將停駐的視窗在它的上方或下方。  索引標籤會顯示文字和影像，並可變更色彩，在作用中。  
  
## 語法  
  
```  
class CMFCTabCtrl : public CMFCBaseTabCtrl  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|`CMFCTabCtrl::CMFCTabCtrl`|預設建構函式。|  
|`CMFCTabCtrl::~CMFCTabCtrl`|解構函式。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CMFCTabCtrl::ActivateMDITab](../Topic/CMFCTabCtrl::ActivateMDITab.md)|顯示目前的索引標籤控制項中指定的索引標籤並設定該索引標籤上的焦點。|  
|[CMFCTabCtrl::AllowDestroyEmptyTabbedPane](../Topic/CMFCTabCtrl::AllowDestroyEmptyTabbedPane.md)||  
|[CMFCTabCtrl::AutoSizeWindow](../Topic/CMFCTabCtrl::AutoSizeWindow.md)|指定這個框架是否為調整所有索引標籤控制項視窗的工作區時，索引標籤會變更的使用者介面項目。|  
|[CMFCTabCtrl::CalcRectEdit](../Topic/CMFCTabCtrl::CalcRectEdit.md)|釋放指定的索引標籤區域的大小。  \(覆寫 `CMFCBaseTabCtrl::CalcRectEdit`\)。|  
|[CMFCTabCtrl::Create](../Topic/CMFCTabCtrl::Create.md)|建立索引標籤控制項並將其附加至 `CMFCTabCtrl` 物件。|  
|`CMFCTabCtrl::CreateObject`|由架構建立這個類別型別的動態執行個體。|  
|[CMFCTabCtrl::EnableActiveTabCloseButton](../Topic/CMFCTabCtrl::EnableActiveTabCloseButton.md)|顯示或隱藏 \[關閉\] 按鈕 \(\[**x**\]\) 在作用中的索引標籤。|  
|[CMFCTabCtrl::EnableInPlaceEdit](../Topic/CMFCTabCtrl::EnableInPlaceEdit.md)|啟用或停用編輯索引標籤的標籤。  \(覆寫 [CMFCBaseTabCtrl::EnableInPlaceEdit](../Topic/CMFCBaseTabCtrl::EnableInPlaceEdit.md)\)。|  
|[CMFCTabCtrl::EnableTabDocumentsMenu](../Topic/CMFCTabCtrl::EnableTabDocumentsMenu.md)|取代移動與按鈕的視窗索引標籤以開啟索引標籤式視窗功能表的兩個按鈕。|  
|[CMFCTabCtrl::EnsureVisible](../Topic/CMFCTabCtrl::EnsureVisible.md)|確定索引標籤是可見的。|  
|[CMFCTabCtrl::GetDocumentIcon](../Topic/CMFCTabCtrl::GetDocumentIcon.md)|擷取與索引標籤式視窗快顯功能表的標籤的符號。|  
|[CMFCTabCtrl::GetFirstVisibleTabNum](../Topic/CMFCTabCtrl::GetFirstVisibleTabNum.md)|擷取會在目前的索引標籤控制項中的第一個索引標籤的索引。|  
|[CMFCTabCtrl::GetResizeMode](../Topic/CMFCTabCtrl::GetResizeMode.md)|擷取這個值指定目前的索引標籤控制項如何調整大小。|  
|[CMFCTabCtrl::GetScrollBar](../Topic/CMFCTabCtrl::GetScrollBar.md)|擷取指標與索引標籤控制項中的捲軸物件。|  
|[CMFCTabCtrl::GetTabArea](../Topic/CMFCTabCtrl::GetTabArea.md)|擷取索引標籤的標籤區域的週框 \(Bounding Rectangle\) 的索引標籤控制項的上方或下方。  \(覆寫 [CMFCBaseTabCtrl::GetTabArea](../Topic/CMFCBaseTabCtrl::GetTabArea.md)\)。|  
|`CMFCTabCtrl::GetTabFromPoint`|擷取包含指定點的索引標籤。  \(覆寫 [CMFCBaseTabCtrl::GetTabFromPoint](../Topic/CMFCBaseTabCtrl::GetTabFromPoint.md)\)。|  
|[CMFCTabCtrl::GetTabMaxWidth](../Topic/CMFCTabCtrl::GetTabMaxWidth.md)|擷取索引標籤的寬度上限。|  
|[CMFCTabCtrl::GetTabsHeight](../Topic/CMFCTabCtrl::GetTabsHeight.md)|擷取目前的索引標籤控制項的索引標籤範圍的高度。|  
|[CMFCTabCtrl::GetTabsRect](../Topic/CMFCTabCtrl::GetTabsRect.md)|擷取週框目前索引標籤控制項的索引標籤範圍的矩形。  \(覆寫 [CMFCBaseTabCtrl::GetTabsRect](../Topic/CMFCBaseTabCtrl::GetTabsRect.md)\)。|  
|`CMFCTabCtrl::GetThisClass`|由框架以取得指向與這個類別型別的 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) 物件。|  
|[CMFCTabCtrl::GetWndArea](../Topic/CMFCTabCtrl::GetWndArea.md)|擷取目前的索引標籤控制項工作區的界限。|  
|[CMFCTabCtrl::HideActiveWindowHorzScrollBar](../Topic/CMFCTabCtrl::HideActiveWindowHorzScrollBar.md)|隱藏水平捲軸，如果有的話，使用中視窗。|  
|[CMFCTabCtrl::HideInactiveWindow](../Topic/CMFCTabCtrl::HideInactiveWindow.md)|指定這個框架是否為顯示非現用視窗的索引標籤控制項。|  
|[CMFCTabCtrl::HideNoTabs](../Topic/CMFCTabCtrl::HideNoTabs.md)|如果沒有可見的選項，以啟用或停用繪製索引標籤區域。|  
|[CMFCTabCtrl::HideSingleTab](../Topic/CMFCTabCtrl::HideSingleTab.md)|當有單一索引標籤式視窗時，啟用或停用繪製索引標籤。  \(覆寫 [CMFCBaseTabCtrl::HideSingleTab](../Topic/CMFCBaseTabCtrl::HideSingleTab.md)\)。|  
|[CMFCTabCtrl::IsActiveInMDITabGroup](../Topic/CMFCTabCtrl::IsActiveInMDITabGroup.md)|表示索引標籤控制項的目前索引標籤是否為作用中的索引標籤在多重文件介面 \(MDI\) 索引標籤群組中。|  
|[CMFCTabCtrl::IsActiveTabBoldFont](../Topic/CMFCTabCtrl::IsActiveTabBoldFont.md)|表示使用中索引標籤的文字以粗體字型，是否已經顯示。|  
|[CMFCTabCtrl::IsActiveTabCloseButton](../Topic/CMFCTabCtrl::IsActiveTabCloseButton.md)|表示 \[關閉\] 按鈕 \(\[**x**\]\) 是否在作用中的索引標籤或索引標籤區域右上角顯示。|  
|[CMFCTabCtrl::IsDrawFrame](../Topic/CMFCTabCtrl::IsDrawFrame.md)|表示索引標籤式視窗是否在內嵌窗格周圍繪製框架矩形。|  
|[CMFCTabCtrl::IsFlatFrame](../Topic/CMFCTabCtrl::IsFlatFrame.md)|表示索引標籤區域周圍的框架是否為或 3D。|  
|[CMFCTabCtrl::IsFlatTab](../Topic/CMFCTabCtrl::IsFlatTab.md)|指示是否索引標籤會出現在目前的索引標籤控制項的是平面的。|  
|[CMFCTabCtrl::IsLeftRightRounded](../Topic/CMFCTabCtrl::IsLeftRightRounded.md)|表示索引標籤的左邊會出現在目前的索引標籤控制項是否會四捨五入。|  
|[CMFCTabCtrl::IsMDITabGroup](../Topic/CMFCTabCtrl::IsMDITabGroup.md)|指示目前的索引標籤控制項是否在多重文件介面 \(MDI\) 視窗的工作區中。|  
|[CMFCTabCtrl::IsOneNoteStyle](../Topic/CMFCTabCtrl::IsOneNoteStyle.md)|指示目前的索引標籤控制項是否顯示仿照 Microsoft OneNote 樣式。|  
|`CMFCTabCtrl::IsPtInTabArea`|判斷某個點是否在索引標籤區域內。  \(覆寫 [CMFCBaseTabCtrl::IsPtInTabArea](../Topic/CMFCBaseTabCtrl::IsPtInTabArea.md)\)。|  
|[CMFCTabCtrl::IsSharedScroll](../Topic/CMFCTabCtrl::IsSharedScroll.md)|指示目前的索引標籤控制項是否具有可以移動它的索引標籤顯示為群組的捲軸。|  
|[CMFCTabCtrl::IsTabDocumentsMenu](../Topic/CMFCTabCtrl::IsTabDocumentsMenu.md)|表示索引標籤控制項是否顯示捲軸按鈕或顯示索引標籤式視窗功能表的按鈕。|  
|[CMFCTabCtrl::IsVS2005Style](../Topic/CMFCTabCtrl::IsVS2005Style.md)|表示索引標籤是否已經顯示仿照 Visual Studio .NET 2005 年模式。|  
|[CMFCTabCtrl::ModifyTabStyle](../Topic/CMFCTabCtrl::ModifyTabStyle.md)|在目前的索引標籤控制項指定索引標籤隨即出現。|  
|`CMFCTabCtrl::MoveTab`|移動選取項目移至另一個索引標籤位置。  \(覆寫 [CMFCBaseTabCtrl::MoveTab](../Topic/CMFCBaseTabCtrl::MoveTab.md)\)。|  
|[CMFCTabCtrl::OnDragEnter](../Topic/CMFCTabCtrl::OnDragEnter.md)|呼叫框架時，游標會先被拖曳至索引標籤控制項的視窗。|  
|[CMFCTabCtrl::OnDragOver](../Topic/CMFCTabCtrl::OnDragOver.md)|呼叫由架構在拖曳作業期間，當滑鼠移到置放目標視窗。  \(覆寫 [CMFCBaseTabCtrl::OnDragOver](../Topic/CMFCBaseTabCtrl::OnDragOver.md)\)。|  
|[CMFCTabCtrl::OnShowTabDocumentsMenu](../Topic/CMFCTabCtrl::OnShowTabDocumentsMenu.md)|顯示索引標籤式視窗快顯功能表，等待，直到使用者選擇索引標籤，並將這個選項使用中的  索引標籤。|  
|`CMFCTabCtrl::PreTranslateMessage`|包含會分派給 [TranslateMessage](http://msdn.microsoft.com/library/windows/desktop/ms644955) 和 [DispatchMessage](http://msdn.microsoft.com/library/windows/desktop/ms644934) Windows 函式之前，將 Windows 訊息。  \(覆寫 [CMFCBaseTabCtrl::PreTranslateMessage](../Topic/CMFCBaseTabCtrl::PreTranslateMessage.md)\)。|  
|`CMFCTabCtrl::RecalcLayout`|重新計算索引標籤控制項的內部配置。  \(覆寫 [CMFCBaseTabCtrl::RecalcLayout](../Topic/CMFCBaseTabCtrl::RecalcLayout.md)\)。|  
|[CMFCTabCtrl::SetActiveInMDITabGroup](../Topic/CMFCTabCtrl::SetActiveInMDITabGroup.md)|在多重文件介面 \(MDI\) 索引標籤群組中設定的索引標籤控制項的目前選項，使用中的  索引標籤。|  
|[CMFCTabCtrl::SetActiveTab](../Topic/CMFCTabCtrl::SetActiveTab.md)|起始選項。  \(覆寫 [CMFCBaseTabCtrl::SetActiveTab](../Topic/CMFCBaseTabCtrl::SetActiveTab.md)\)。|  
|[CMFCTabCtrl::SetActiveTabBoldFont](../Topic/CMFCTabCtrl::SetActiveTabBoldFont.md)|啟用或變更使用中索引標籤的粗體字型中停用用法。|  
|[CMFCTabCtrl::SetDrawFrame](../Topic/CMFCTabCtrl::SetDrawFrame.md)|在內嵌列周圍啟用或停用 drawinga 框架矩形。|  
|[CMFCTabCtrl::SetFlatFrame](../Topic/CMFCTabCtrl::SetFlatFrame.md)|指定是否要在索引標籤區域周圍繪製一層或 3D 框架。|  
|[CMFCTabCtrl::SetImageList](../Topic/CMFCTabCtrl::SetImageList.md)|指定影像清單。  \(覆寫 [CMFCBaseTabCtrl::SetImageList](../Topic/CMFCBaseTabCtrl::SetImageList.md)\)。|  
|[CMFCTabCtrl::SetResizeMode](../Topic/CMFCTabCtrl::SetResizeMode.md)|指定目前的索引標籤控制項如何調整大小和重新顯示控制項。|  
|[CMFCTabCtrl::SetTabMaxWidth](../Topic/CMFCTabCtrl::SetTabMaxWidth.md)|在新索引標籤式視窗指定最大定位點寬度。|  
|[CMFCTabCtrl::StopResize](../Topic/CMFCTabCtrl::StopResize.md)|結束目前調整索引標籤控制項的作業。|  
|`CMFCTabCtrl::SwapTabs`|交換一對選項。  \(覆寫 [CMFCBaseTabCtrl::SwapTabs](../Topic/CMFCBaseTabCtrl::SwapTabs.md)\)。|  
|[CMFCTabCtrl::SynchronizeScrollBar](../Topic/CMFCTabCtrl::SynchronizeScrollBar.md)|以顯示一般索引標籤的索引標籤控制項的水平捲軸。|  
  
### 資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CMFCTabCtrl::m\_bEnableActivate](../Topic/CMFCTabCtrl::m_bEnableActivate.md)|在插入新的索引標籤並啟用時，防止現用檢視表失去焦點時。|  
  
## 備註  
 `CMFCTabCtrl` 類別支援:  
  
-   索引標籤包含的 3D 控制項模式，一般，和平展使用共用水平捲軸。  
  
-   索引標籤位於視窗頂端或底端。  
  
-   顯示文字、影像、文字和影像的索引標籤。  
  
-   變更色彩的索引標籤，選取這個選項為作用中。  
  
-   框線可調整的索引標籤的大小變更。  
  
-   可拆的索引標籤式視窗。  
  
 `CMFCTabCtrl` 類別可以搭配  對話方塊，不過，提供使用內建影像 [!INCLUDE[ofprexcel](../Token/ofprexcel_md.md)] 和 [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)]的控制列的應用程式使用。  如需詳細資訊，請參閱 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md)。  
  
 遵循下列步驟加入可調整大小，修正應用程式的索引標籤控制項:  
  
1.  建立 [CTabbedPane Class](../../mfc/reference/ctabbedpane-class.md) 的執行個體。  
  
2.  請呼叫 [CDockablePane::Create](../Topic/CDockablePane::Create.md)。  
  
3.  使用 [CBaseTabbedPane::AddTab](../Topic/CBaseTabbedPane::AddTab.md) 或 [CMFCBaseTabCtrl::InsertTab](../Topic/CMFCBaseTabCtrl::InsertTab.md) 加入新的索引標籤。  
  
4.  呼叫 [CBasePane::EnableDocking](../Topic/CBasePane::EnableDocking.md) ，讓目前的索引標籤控制項可以停駐在主框架視窗。  
  
5.  呼叫 [CFrameWndEx::DockPane](../Topic/CFrameWndEx::DockPane.md) 內建索引標籤式視窗在主要畫面格。  
  
 如需如何建立索引標籤式視窗為 Pin 控制列，請參閱 [CTabbedPane Class](../../mfc/reference/ctabbedpane-class.md)。  若要使用 `CMFCTabCtrl` 做為非停駐控制項，請建立 `CMFCTabCtrl` 物件然後呼叫 [CMFCTabCtrl::Create](../Topic/CMFCTabCtrl::Create.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md)  
  
 [CMFCTabCtrl](../../mfc/reference/cmfctabctrl-class.md)  
  
## 範例  
 下列範例會在 `CMFCTabCtrl` 類別會示範如何使用各種方法設定 `CMFCTabCtrl` 物件。  範例會說明如何將索引標籤，顯示在使用中索引標籤的 \[關閉\] 按鈕，可讓您編輯索引標籤的標籤和顯示索引標籤式視窗標籤快顯功能表。  這個範例是 [狀態集合範例](../../top/visual-cpp-samples.md)的一部分。  
  
 [!code-cpp[NVC_MFC_StateCollection#1](../../mfc/reference/codesnippet/CPP/cmfctabctrl-class_1.h)]  
[!code-cpp[NVC_MFC_StateCollection#3](../../mfc/reference/codesnippet/CPP/cmfctabctrl-class_2.cpp)]  
  
## 需求  
 **標題:** afxtabctrl.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md)   
 [CDockablePane Class](../../mfc/reference/cdockablepane-class.md)   
 [CMFCBaseTabCtrl Class](../../mfc/reference/cmfcbasetabctrl-class.md)