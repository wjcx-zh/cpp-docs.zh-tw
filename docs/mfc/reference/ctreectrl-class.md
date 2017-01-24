---
title: "CTreeCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CTreeCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTreeCtrl class"
  - "directory lists"
  - "file lists [C++]"
  - "tree view controls"
ms.assetid: 96e20031-6161-4143-8c12-8d1816c66d90
caps.latest.revision: 23
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CTreeCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供視窗樹狀檢視控制項的功能。  
  
## 語法  
  
```  
class CTreeCtrl : public CWnd  
```  
  
## 成員  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CTreeCtrl::CTreeCtrl](../Topic/CTreeCtrl::CTreeCtrl.md)|建構 `CTreeCtrl` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CTreeCtrl::Create](../Topic/CTreeCtrl::Create.md)|建立樹狀檢視控制項並將其附加至 `CTreeCtrl` 物件。|  
|[CTreeCtrl::CreateDragImage](../Topic/CTreeCtrl::CreateDragImage.md)|建立指定的樹狀檢視項目的拖曳的點陣圖。|  
|[CTreeCtrl::CreateEx](../Topic/CTreeCtrl::CreateEx.md)|建立具有指定之視窗的延伸樣式的樹狀目錄控制項並將其附加至 `CTreeCtrl` 物件。|  
|[CTreeCtrl::DeleteAllItems](../Topic/CTreeCtrl::DeleteAllItems.md)|刪除在樹狀檢視控制項中的所有項目。|  
|[CTreeCtrl::DeleteItem](../Topic/CTreeCtrl::DeleteItem.md)|刪除在樹狀檢視控制項的新項目。|  
|[CTreeCtrl::EditLabel](../Topic/CTreeCtrl::EditLabel.md)|就地編譯指定的樹狀檢視中的項目。|  
|[CTreeCtrl::EndEditLabelNow](../Topic/CTreeCtrl::EndEditLabelNow.md)|移除樹狀檢視項目的標籤 \(Label\) 的編輯作業目前樹狀檢視控制項。|  
|[CTreeCtrl::EnsureVisible](../Topic/CTreeCtrl::EnsureVisible.md)|確定樹狀檢視中可見的項目在其樹狀檢視控制項。|  
|[CTreeCtrl::Expand](../Topic/CTreeCtrl::Expand.md)|展開或摺疊，指定的樹狀檢視項目的子項目。|  
|[CTreeCtrl::GetBkColor](../Topic/CTreeCtrl::GetBkColor.md)|擷取目前控制項的背景色彩。|  
|[CTreeCtrl::GetCheck](../Topic/CTreeCtrl::GetCheck.md)|擷取樹狀目錄控制項項目的選取狀態。|  
|[CTreeCtrl::GetChildItem](../Topic/CTreeCtrl::GetChildItem.md)|擷取指定的樹狀檢視項目的子系。|  
|[CTreeCtrl::GetCount](../Topic/CTreeCtrl::GetCount.md)|擷取樹狀目錄項目數目與樹狀檢視控制項。|  
|[CTreeCtrl::GetDropHilightItem](../Topic/CTreeCtrl::GetDropHilightItem.md)|擷取拖放作業的目標。|  
|[CTreeCtrl::GetEditControl](../Topic/CTreeCtrl::GetEditControl.md)|擷取編輯控制項的控制代碼用於編輯指定的樹狀檢視項目。|  
|[CTreeCtrl::GetExtendedStyle](../Topic/CTreeCtrl::GetExtendedStyle.md)|擷取延伸樣式目前樹狀檢視控制項使用。|  
|[CTreeCtrl::GetFirstVisibleItem](../Topic/CTreeCtrl::GetFirstVisibleItem.md)|擷取指定的樹狀檢視項目的第一個可見的項目。|  
|[CTreeCtrl::GetImageList](../Topic/CTreeCtrl::GetImageList.md)|擷取影像清單的控制代碼與樹狀檢視控制項。|  
|[CTreeCtrl::GetIndent](../Topic/CTreeCtrl::GetIndent.md)|從其父代 \(Parent\) 擷取位移 \(以像素為單位\) 的樹狀檢視項目。|  
|[CTreeCtrl::GetInsertMarkColor](../Topic/CTreeCtrl::GetInsertMarkColor.md)|擷取色彩來繪製樹狀檢視中插入標記。|  
|[CTreeCtrl::GetItem](../Topic/CTreeCtrl::GetItem.md)|擷取指定的樹狀檢視項目的屬性。|  
|[CTreeCtrl::GetItemData](../Topic/CTreeCtrl::GetItemData.md)|傳回 32 位元的應用程式專屬值與項目。|  
|[CTreeCtrl::GetItemExpandedImageIndex](../Topic/CTreeCtrl::GetItemExpandedImageIndex.md)|擷取影像的索引顯示目前樹狀檢視控制項的指定項目時處於展開狀態。|  
|[CTreeCtrl::GetItemHeight](../Topic/CTreeCtrl::GetItemHeight.md)|擷取樹狀檢視項目的目前高度。|  
|[CTreeCtrl::GetItemImage](../Topic/CTreeCtrl::GetItemImage.md)|擷取影像相關聯的項目。|  
|[CTreeCtrl::GetItemPartRect](../Topic/CTreeCtrl::GetItemPartRect.md)|擷取指定之項目的指定部分的週框 \(Bounding Rectangle\) 目前樹狀檢視控制項的。|  
|[CTreeCtrl::GetItemRect](../Topic/CTreeCtrl::GetItemRect.md)|擷取樹狀檢視項目的週框 \(Bounding Rectangle\)。|  
|[CTreeCtrl::GetItemState](../Topic/CTreeCtrl::GetItemState.md)|傳回項目的狀態。|  
|[CTreeCtrl::GetItemStateEx](../Topic/CTreeCtrl::GetItemStateEx.md)|擷取指定之項目的擴充的狀態儲存在目前樹狀檢視控制項的。|  
|[CTreeCtrl::GetItemText](../Topic/CTreeCtrl::GetItemText.md)|傳回項目的文字。|  
|[CTreeCtrl::GetLastVisibleItem](../Topic/CTreeCtrl::GetLastVisibleItem.md)|擷取目前樹狀檢視控制項中的最後一個展開的項目。|  
|[CTreeCtrl::GetLineColor](../Topic/CTreeCtrl::GetLineColor.md)|擷取樹狀檢視控制項中的目前行色彩。|  
|[CTreeCtrl::GetNextItem](../Topic/CTreeCtrl::GetNextItem.md)|擷取符合指定之的關聯性的樹狀檢視項目。|  
|[CTreeCtrl::GetNextSiblingItem](../Topic/CTreeCtrl::GetNextSiblingItem.md)|擷取指定的樹狀檢視項目的下一個同層級項目。|  
|[CTreeCtrl::GetNextVisibleItem](../Topic/CTreeCtrl::GetNextVisibleItem.md)|擷取指定的樹狀檢視項目的下一個可見的項目。|  
|[CTreeCtrl::GetParentItem](../Topic/CTreeCtrl::GetParentItem.md)|擷取指定的樹狀檢視項目的父代。|  
|[CTreeCtrl::GetPrevSiblingItem](../Topic/CTreeCtrl::GetPrevSiblingItem.md)|擷取指定的樹狀檢視項目的上一個同層級項目。|  
|[CTreeCtrl::GetPrevVisibleItem](../Topic/CTreeCtrl::GetPrevVisibleItem.md)|擷取指定的樹狀檢視項目的上一個可見的項目。|  
|[CTreeCtrl::GetRootItem](../Topic/CTreeCtrl::GetRootItem.md)|擷取指定的樹狀檢視項目的根目錄。|  
|[CTreeCtrl::GetScrollTime](../Topic/CTreeCtrl::GetScrollTime.md)|擷取樹狀檢視控制項的最大捲動頁面。|  
|[CTreeCtrl::GetSelectedCount](../Topic/CTreeCtrl::GetSelectedCount.md)|擷取選取的項目數目目前樹狀檢視控制項。|  
|[CTreeCtrl::GetSelectedItem](../Topic/CTreeCtrl::GetSelectedItem.md)|擷取目前選取的樹狀檢視項目。|  
|[CTreeCtrl::GetTextColor](../Topic/CTreeCtrl::GetTextColor.md)|擷取目前控制項的文字色彩。|  
|[CTreeCtrl::GetToolTips](../Topic/CTreeCtrl::GetToolTips.md)|擷取控制代碼給樹狀檢視控制項的子控制項的工具提示。|  
|[CTreeCtrl::GetVisibleCount](../Topic/CTreeCtrl::GetVisibleCount.md)|擷取可見的樹狀目錄項目數目與樹狀檢視控制項。|  
|[CTreeCtrl::HitTest](../Topic/CTreeCtrl::HitTest.md)|傳回目前游標位置 `CTreeCtrl` 與物件產生關聯。|  
|[CTreeCtrl::InsertItem](../Topic/CTreeCtrl::InsertItem.md)|在樹狀檢視控制項在插入新的項目。|  
|[CTreeCtrl::ItemHasChildren](../Topic/CTreeCtrl::ItemHasChildren.md)|如果指定的項目具有子項目，則會傳回非零。|  
|[CTreeCtrl::MapAccIdToItem](../Topic/CTreeCtrl::MapAccIdToItem.md)|將指定的存取範圍識別項來處理對於目前樹狀檢視控制項的樹狀檢視項目。|  
|[CTreeCtrl::MapItemToAccID](../Topic/CTreeCtrl::MapItemToAccID.md)|將指定的控制代碼目前樹狀檢視控制項的樹狀檢視項目加入存取範圍識別項。|  
|[CTreeCtrl::Select](../Topic/CTreeCtrl::Select.md)|選取，捲動到檢視或重新繪製指定的樹狀檢視項目。|  
|[CTreeCtrl::SelectDropTarget](../Topic/CTreeCtrl::SelectDropTarget.md)|重繪樹狀目錄項目做為拖放作業的目標。|  
|[CTreeCtrl::SelectItem](../Topic/CTreeCtrl::SelectItem.md)|選取指定的樹狀檢視項目。|  
|[CTreeCtrl::SelectSetFirstVisible](../Topic/CTreeCtrl::SelectSetFirstVisible.md)|選取指定的樹狀檢視項目做為第一個可見的項目。|  
|[CTreeCtrl::SetAutoscrollInfo](../Topic/CTreeCtrl::SetAutoscrollInfo.md)|設定目前樹狀檢視控制項的 autoscroll 速率。|  
|[CTreeCtrl::SetBkColor](../Topic/CTreeCtrl::SetBkColor.md)|設定控制項的背景色彩。|  
|[CTreeCtrl::SetCheck](../Topic/CTreeCtrl::SetCheck.md)|設定樹狀目錄控制項項目的選取狀態。|  
|[CTreeCtrl::SetExtendedStyle](../Topic/CTreeCtrl::SetExtendedStyle.md)|設定目前樹狀檢視控制項的延伸樣式。|  
|[CTreeCtrl::SetImageList](../Topic/CTreeCtrl::SetImageList.md)|設定影像清單的控制代碼與樹狀檢視控制項。|  
|[CTreeCtrl::SetIndent](../Topic/CTreeCtrl::SetIndent.md)|設定位移 \(以像素為單位\) 從其父代 \(Parent\) 的樹狀檢視項目。|  
|[CTreeCtrl::SetInsertMark](../Topic/CTreeCtrl::SetInsertMark.md)|設定樹狀檢視控制項中的插入標記。|  
|[CTreeCtrl::SetInsertMarkColor](../Topic/CTreeCtrl::SetInsertMarkColor.md)|設定色彩來繪製樹狀檢視中插入標記。|  
|[CTreeCtrl::SetItem](../Topic/CTreeCtrl::SetItem.md)|設定所指定的樹狀檢視項目的屬性。|  
|[CTreeCtrl::SetItemData](../Topic/CTreeCtrl::SetItemData.md)|將 32 位元的應用程式專屬值與項目。|  
|[CTreeCtrl::SetItemExpandedImageIndex](../Topic/CTreeCtrl::SetItemExpandedImageIndex.md)|設定影像的索引顯示目前樹狀檢視控制項的指定項目時處於展開狀態。|  
|[CTreeCtrl::SetItemHeight](../Topic/CTreeCtrl::SetItemHeight.md)|將樹狀檢視項目的高度。|  
|[CTreeCtrl::SetItemImage](../Topic/CTreeCtrl::SetItemImage.md)|使影像與項目。|  
|[CTreeCtrl::SetItemState](../Topic/CTreeCtrl::SetItemState.md)|設定項目的狀態。|  
|[CTreeCtrl::SetItemStateEx](../Topic/CTreeCtrl::SetItemStateEx.md)|設定指定之項目的擴充的狀態儲存在目前樹狀檢視控制項的。|  
|[CTreeCtrl::SetItemText](../Topic/CTreeCtrl::SetItemText.md)|將項目的文字。|  
|[CTreeCtrl::SetLineColor](../Topic/CTreeCtrl::SetLineColor.md)|設定樹狀檢視控制項中的目前行色彩。|  
|[CTreeCtrl::SetScrollTime](../Topic/CTreeCtrl::SetScrollTime.md)|設定樹狀檢視控制項的最大捲動頁面。|  
|[CTreeCtrl::SetTextColor](../Topic/CTreeCtrl::SetTextColor.md)|設定控制項的文字色彩。|  
|[CTreeCtrl::SetToolTips](../Topic/CTreeCtrl::SetToolTips.md)|設定樹狀檢視控制項的子控制項的工具提示。|  
|[CTreeCtrl::ShowInfoTip](../Topic/CTreeCtrl::ShowInfoTip.md)|顯示指定之項目的資訊提示目前樹狀檢視控制項。|  
|[CTreeCtrl::SortChildren](../Topic/CTreeCtrl::SortChildren.md)|排序所父代項目的子系。|  
|[CTreeCtrl::SortChildrenCB](../Topic/CTreeCtrl::SortChildrenCB.md)|使用應用程式定義的函式排序，排序所父代項目的子系。|  
  
## 備註  
 「樹狀檢視控制項」是顯示項目的階層式清單，例如在文件的頁首、在索引中輸入或檔案和目錄磁碟上的視窗。  每個項目都包含標籤和選擇性點陣圖，影像，而且每個項目都可以有子項目\) 相關聯。  藉由按一下項目，使用者可以展開或摺疊子項目關聯的清單。  
  
 這個控制項 \(也 `CTreeCtrl` 類別\) 給在 Windows 98 和 Windows NT 4 版之下的程式才能使用 \(含\) 以後版本。  
  
 如需使用 `CTreeCtrl`的資訊，請參閱:  
  
-   [控制項](../../mfc/controls-mfc.md)  
  
-   [使用 CTreeCtrl](../../mfc/using-ctreectrl.md)  
  
-   在 [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的[樹狀檢視控制項參考](http://msdn.microsoft.com/library/windows/desktop/bb759988) 。  
  
-   知識庫文件 Q222905:HOWTO:顯示 CTreeCtrl 內容功能表。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CTreeCtrl`  
  
## 需求  
 **Header:** afxcmn.h  
  
## 請參閱  
 [MFC 範例 CMNCTRL1](../../top/visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CImageList Class](../../mfc/reference/cimagelist-class.md)