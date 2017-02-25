---
title: "CReBarCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CReBarCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CReBarCtrl class"
  - "rebar controls, control bar"
  - "rebar controls, CReBarCtrl class"
ms.assetid: 154570d7-e48c-425d-8c7e-c64542bcb4cc
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CReBarCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封裝 Rebar 控制項的功能，是子視窗的容器。  
  
## 語法  
  
```  
class CReBarCtrl : public CWnd  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CReBarCtrl::CReBarCtrl](../Topic/CReBarCtrl::CReBarCtrl.md)|建構 `CReBarCtrl` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CReBarCtrl::BeginDrag](../Topic/CReBarCtrl::BeginDrag.md)|將 Rebar 控制項的拖放模式。|  
|[CReBarCtrl::Create](../Topic/CReBarCtrl::Create.md)|建立 Rebar 控制項並將其附加至 `CReBarCtrl` 物件。|  
|[CReBarCtrl::CreateEx](../Topic/CReBarCtrl::CreateEx.md)|建立擁有指定之視窗的延伸樣式的 Rebar 控制項並將其附加至 `CReBarCtrl` 物件。|  
|[CReBarCtrl::DeleteBand](../Topic/CReBarCtrl::DeleteBand.md)|刪除 Rebar 控制項的群組列。|  
|[CReBarCtrl::DragMove](../Topic/CReBarCtrl::DragMove.md)|在呼叫之後更新在 Rebar 控制項拖曳至 `BeginDrag`位置。|  
|[CReBarCtrl::EndDrag](../Topic/CReBarCtrl::EndDrag.md)|結束 Rebar 控制項的拖放作業。|  
|[CReBarCtrl::GetBandBorders](../Topic/CReBarCtrl::GetBandBorders.md)|擷取群組列的框線。|  
|[CReBarCtrl::GetBandCount](../Topic/CReBarCtrl::GetBandCount.md)|目前計數器中群組列 Rebar 控制項的。|  
|[CReBarCtrl::GetBandInfo](../Topic/CReBarCtrl::GetBandInfo.md)|擷取所指定的群組列的資訊 Rebar 控制項的。|  
|[CReBarCtrl::GetBandMargins](../Topic/CReBarCtrl::GetBandMargins.md)|擷取群組列的框線。|  
|[CReBarCtrl::GetBarHeight](../Topic/CReBarCtrl::GetBarHeight.md)|擷取 Rebar 控制項的高度。|  
|[CReBarCtrl::GetBarInfo](../Topic/CReBarCtrl::GetBarInfo.md)|擷取有關 Rebar 控制項及使用的影像清單的詳細資訊。|  
|[CReBarCtrl::GetBkColor](../Topic/CReBarCtrl::GetBkColor.md)|擷取 Rebar 控制項的預設背景色彩。|  
|[CReBarCtrl::GetColorScheme](../Topic/CReBarCtrl::GetColorScheme.md)|擷取 [COLORSCHEME](http://msdn.microsoft.com/library/windows/desktop/bb775502) 結構與 Rebar 控制項。|  
|[CReBarCtrl::GetDropTarget](../Topic/CReBarCtrl::GetDropTarget.md)|擷取 Rebar 控制項的 `IDropTarget` 介面指標。|  
|[CReBarCtrl::GetExtendedStyle](../Topic/CReBarCtrl::GetExtendedStyle.md)|取得目前 Rebar 控制項的延伸樣式。|  
|[CReBarCtrl::GetImageList](../Topic/CReBarCtrl::GetImageList.md)|擷取影像清單與 Rebar 控制項。|  
|[CReBarCtrl::GetPalette](../Topic/CReBarCtrl::GetPalette.md)|擷取 Rebar 控制項的目前調色盤。|  
|[CReBarCtrl::GetRect](../Topic/CReBarCtrl::GetRect.md)|擷取指定群組列的週框 \(Bounding Rectangle\) Rebar 控制項的。|  
|[CReBarCtrl::GetRowCount](../Topic/CReBarCtrl::GetRowCount.md)|擷取的群組列數目 Rebar 控制項的。|  
|[CReBarCtrl::GetRowHeight](../Topic/CReBarCtrl::GetRowHeight.md)|擷取指定之資料列的高度 \(以 Rebar 控制項的。|  
|[CReBarCtrl::GetTextColor](../Topic/CReBarCtrl::GetTextColor.md)|擷取 Rebar 控制項的預設文字色彩。|  
|[CReBarCtrl::GetToolTips](../Topic/CReBarCtrl::GetToolTips.md)|擷取控制代碼所有工具提示控制項與 Rebar 控制項。|  
|[CReBarCtrl::HitTest](../Topic/CReBarCtrl::HitTest.md)|判斷 Rebar 群組列的哪個部分是在畫面上的所指定的點，則為，如果 Rebar 群組列此時存在。|  
|[CReBarCtrl::IDToIndex](../Topic/CReBarCtrl::IDToIndex.md)|轉換群組列 Identifier \(ID\) 在 Rebar 控制項中群組列索引。|  
|[CReBarCtrl::InsertBand](../Topic/CReBarCtrl::InsertBand.md)|在 Rebar 控制項插入新的群組列。|  
|[CReBarCtrl::MaximizeBand](../Topic/CReBarCtrl::MaximizeBand.md)|調整 Rebar 控制項中群組列到其最大的大小。|  
|[CReBarCtrl::MinimizeBand](../Topic/CReBarCtrl::MinimizeBand.md)|調整 Rebar 控制項中群組列到最小。|  
|[CReBarCtrl::MoveBand](../Topic/CReBarCtrl::MoveBand.md)|從一個群組列索引移動至另一個。|  
|[CReBarCtrl::PushChevron](../Topic/CReBarCtrl::PushChevron.md)|以程式設計方式推入\>形箭號。|  
|[CReBarCtrl::RestoreBand](../Topic/CReBarCtrl::RestoreBand.md)|調整 Rebar 控制項中群組列到它所需要的大小。|  
|[CReBarCtrl::SetBandInfo](../Topic/CReBarCtrl::SetBandInfo.md)|設定現有的群組列的特性 Rebar 控制項的。|  
|[CReBarCtrl::SetBandWidth](../Topic/CReBarCtrl::SetBandWidth.md)|設定指定的內建群組列的寬度目前 Rebar 控制項的。|  
|[CReBarCtrl::SetBarInfo](../Topic/CReBarCtrl::SetBarInfo.md)|設定 Rebar 控制項的特性。|  
|[CReBarCtrl::SetBkColor](../Topic/CReBarCtrl::SetBkColor.md)|設定 Rebar 控制項的預設背景色彩。|  
|[CReBarCtrl::SetColorScheme](../Topic/CReBarCtrl::SetColorScheme.md)|將按鈕的色彩配置在 Rebar 控制項。|  
|[CReBarCtrl::SetExtendedStyle](../Topic/CReBarCtrl::SetExtendedStyle.md)|設定目前 Rebar 控制項的延伸樣式。|  
|[CReBarCtrl::SetImageList](../Topic/CReBarCtrl::SetImageList.md)|設定 Rebar 控制項的影像清單。|  
|[CReBarCtrl::SetOwner](../Topic/CReBarCtrl::SetOwner.md)|設定 Rebar 控制項的主控視窗。|  
|[CReBarCtrl::SetPalette](../Topic/CReBarCtrl::SetPalette.md)|設定 Rebar 控制項的目前調色盤。|  
|[CReBarCtrl::SetTextColor](../Topic/CReBarCtrl::SetTextColor.md)|設定 Rebar 控制項的預設文字色彩。|  
|[CReBarCtrl::SetToolTips](../Topic/CReBarCtrl::SetToolTips.md)|與工具提示控制項與 Rebar 控制項。|  
|[CReBarCtrl::SetWindowTheme](../Topic/CReBarCtrl::SetWindowTheme.md)|設定 Rebar 控制項的視覺化樣式。|  
|[CReBarCtrl::ShowBand](../Topic/CReBarCtrl::ShowBand.md)|顯示或隱藏 Rebar 控制項中指定的群組列。|  
|[CReBarCtrl::SizeToRect](../Topic/CReBarCtrl::SizeToRect.md)|調整 Rebar 控制項加入至指定的矩形。|  
  
## 備註  
 Rebar 控制項所在的應用程式指定 Rebar 控制項中的子視窗至 Rebar 群組列。  子視窗通常是另一個通用控制項。  
  
 Rebar 控制項包含一或多個群組列。  每一個群組列都可以包含移駐夾列、點陣圖、文字標籤和子視窗的組合。  群組列只能包含一個項目中。  
  
 Rebar 控制項可以顯示所指定的背景點陣圖的子視窗。  所有 Rebar 控制項範圍可以調整大小，除了使用 **RBBS\_FIXEDSIZE** 樣式的項目。  當您變更位置或調整一個 Rebar 控制項範圍， Rebar 控制項管理子視窗的大小和位置指派給該群組列。  調整大小或變更群組列命令在控制項中，按一下並拖曳內群組列的移駐夾列。  
  
 下圖顯示具有三個群組列的 Rebar 控制項:  
  
-   群組列 0 包含一層，透明工具列控制項。  
  
-   群組列 1 包含透明標準和透明下拉式按鈕。  
  
-   群組列 2 包含下拉式方塊和四個標準按鈕。  
  
     ![Rebar 功能表範例](../../mfc/reference/media/vc4scc1.png "vc4SCC1")  
  
## Rebar 控制項  
 Rebar 控制項支援:  
  
-   影像清單。  
  
-   訊息處理。  
  
-   自訂繪圖功能。  
  
-   除了標準視窗樣式之外的各種控制項模式。  如需這些模式清單，請參閱 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的 [Rebar 控制項模式](http://msdn.microsoft.com/library/windows/desktop/bb774377) 。  
  
 如需詳細資訊，請參閱 [使用 CReBarCtrl](../../mfc/using-crebarctrl.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CReBarCtrl`  
  
## 需求  
 **Header:** afxcmn.h  
  
## 請參閱  
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)