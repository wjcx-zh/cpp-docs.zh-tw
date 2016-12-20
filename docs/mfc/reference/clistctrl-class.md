---
title: "CListCtrl Class | Microsoft Docs"
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
  - "CListCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CListCtrl 類別"
  - "list view controls"
  - "list view controls, CListCtrl 類別"
  - "LVS_ICON"
  - "LVS_LIST"
  - "LVS_REPORT"
  - "LVS_SMALLICON"
  - "Windows common controls [C++], CListCtrl"
ms.assetid: fe08a1ca-4b05-4ff7-a12a-ee4c765a2197
caps.latest.revision: 23
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CListCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

封裝「清單檢視控制項的功能，」顯示項目的集合包含圖示 \(從影像清單中\) 和標籤的每個。  
  
## 語法  
  
```  
class CListCtrl : public CWnd  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CListCtrl::CListCtrl](../Topic/CListCtrl::CListCtrl.md)|建構 `CListCtrl` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CListCtrl::ApproximateViewRect](../Topic/CListCtrl::ApproximateViewRect.md)|判斷要求的寬度和高度顯示清單檢視控制項中的項目。|  
|[CListCtrl::Arrange](../Topic/CListCtrl::Arrange.md)|對齊格線項目。|  
|[CListCtrl::CancelEditLabel](../Topic/CListCtrl::CancelEditLabel.md)|取消編輯作業的項目文字。|  
|[CListCtrl::Create](../Topic/CListCtrl::Create.md)|建立清單控制項並將其附加至 `CListCtrl` 物件。|  
|[CListCtrl::CreateDragImage](../Topic/CListCtrl::CreateDragImage.md)|建立指定之項目的一個拖曳影像清單。|  
|[CListCtrl::CreateEx](../Topic/CListCtrl::CreateEx.md)|建立擁有指定之視窗的延伸樣式的清單控制項並將其附加至 `CListCtrl` 物件。|  
|[CListCtrl::DeleteAllItems](../Topic/CListCtrl::DeleteAllItems.md)|刪除控制項中的所有項目。|  
|[CListCtrl::DeleteColumn](../Topic/CListCtrl::DeleteColumn.md)|刪除清單檢視控制項中的資料行。|  
|[CListCtrl::DeleteItem](../Topic/CListCtrl::DeleteItem.md)|刪除控制項中的項目。|  
|[CListCtrl::DrawItem](../Topic/CListCtrl::DrawItem.md)|呼叫，以主控描繪控制項變更的視覺外觀。|  
|[CListCtrl::EditLabel](../Topic/CListCtrl::EditLabel.md)|啟動就地編輯項目的文字。|  
|[CListCtrl::EnableGroupView](../Topic/CListCtrl::EnableGroupView.md)|啟用或停用  清單中的項目是否要檢視控制項顯示為群組。|  
|[CListCtrl::EnsureVisible](../Topic/CListCtrl::EnsureVisible.md)|確定此項目為可見的。|  
|[CListCtrl::FindItem](../Topic/CListCtrl::FindItem.md)|搜尋指定特性的清單檢視項目。|  
|[CListCtrl::GetBkColor](../Topic/CListCtrl::GetBkColor.md)|擷取清單檢視控制項的背景色彩。|  
|[CListCtrl::GetBkImage](../Topic/CListCtrl::GetBkImage.md)|擷取清單檢視控制項的目前背景影像。|  
|[CListCtrl::GetCallbackMask](../Topic/CListCtrl::GetCallbackMask.md)|擷取清單檢視控制項的回呼遮罩。|  
|[CListCtrl::GetCheck](../Topic/CListCtrl::GetCheck.md)|擷取狀態影像上目前的顯示狀態相關聯的項目。|  
|[CListCtrl::GetColumn](../Topic/CListCtrl::GetColumn.md)|擷取控制項的屬性。|  
|[CListCtrl::GetColumnOrderArray](../Topic/CListCtrl::GetColumnOrderArray.md)|擷取資料行順序 \(由左至右\) 清單檢視控制項。|  
|[CListCtrl::GetColumnWidth](../Topic/CListCtrl::GetColumnWidth.md)|擷取一個資料行的寬度 \(以報告檢視或清單檢視的。|  
|[CListCtrl::GetCountPerPage](../Topic/CListCtrl::GetCountPerPage.md)|計算能夠容納垂直清單檢視控制項中的項目數目。|  
|[CListCtrl::GetEditControl](../Topic/CListCtrl::GetEditControl.md)|擷取用來編輯控制項的控制代碼所編輯項目的文字。|  
|[CListCtrl::GetEmptyText](../Topic/CListCtrl::GetEmptyText.md)|如果目前的清單檢視控制項是空的，以擷取要顯示的字串。|  
|[CListCtrl::GetExtendedStyle](../Topic/CListCtrl::GetExtendedStyle.md)|擷取清單檢視控制項中目前的延伸樣式。|  
|[CListCtrl::GetFirstSelectedItemPosition](../Topic/CListCtrl::GetFirstSelectedItemPosition.md)|擷取第一個選取的清單檢視項目在清單檢視控制項。|  
|[CListCtrl::GetFocusedGroup](../Topic/CListCtrl::GetFocusedGroup.md)|擷取具有鍵盤焦點在目前清單檢視控制項群組。|  
|[CListCtrl::GetGroupCount](../Topic/CListCtrl::GetGroupCount.md)|擷取群組的數目目前清單檢視控制項的。|  
|[CListCtrl::GetGroupInfo](../Topic/CListCtrl::GetGroupInfo.md)|取得清單檢視控制項的指定之群組的資訊。|  
|[CListCtrl::GetGroupInfoByIndex](../Topic/CListCtrl::GetGroupInfoByIndex.md)|擷取所指定之群組的資訊會儲存在目前清單檢視控制項。|  
|[CListCtrl::GetGroupMetrics](../Topic/CListCtrl::GetGroupMetrics.md)|擷取群組的度量資訊。|  
|[CListCtrl::GetGroupRect](../Topic/CListCtrl::GetGroupRect.md)|擷取指定之群組的週框 \(Bounding Rectangle\) 目前的清單檢視控制項。|  
|[CListCtrl::GetGroupState](../Topic/CListCtrl::GetGroupState.md)|擷取指定之群組的狀態在目前清單檢視控制項。|  
|[CListCtrl::GetHeaderCtrl](../Topic/CListCtrl::GetHeaderCtrl.md)|擷取清單檢視控制項的標題控制項。|  
|[CListCtrl::GetHotCursor](../Topic/CListCtrl::GetHotCursor.md)|當熱追蹤針對清單檢視控制項啟用時，擷取使用的游標。|  
|[CListCtrl::GetHotItem](../Topic/CListCtrl::GetHotItem.md)|目前擷取的清單檢視項目游標下方。|  
|[CListCtrl::GetHoverTime](../Topic/CListCtrl::GetHoverTime.md)|擷取清單檢視控制項的目前停留時間。|  
|[CListCtrl::GetImageList](../Topic/CListCtrl::GetImageList.md)|擷取用來繪製清單檢視項目的影像清單的控制代碼。|  
|[CListCtrl::GetInsertMark](../Topic/CListCtrl::GetInsertMark.md)|擷取插入標記的位置。|  
|[CListCtrl::GetInsertMarkColor](../Topic/CListCtrl::GetInsertMarkColor.md)|擷取插入標記的目前色彩。|  
|[CListCtrl::GetInsertMarkRect](../Topic/CListCtrl::GetInsertMarkRect.md)|擷取週框的插入點的矩形。|  
|[CListCtrl::GetItem](../Topic/CListCtrl::GetItem.md)|擷取清單檢視項目的屬性。|  
|[CListCtrl::GetItemCount](../Topic/CListCtrl::GetItemCount.md)|擷取集合中的項目數目清單檢視控制項。|  
|[CListCtrl::GetItemData](../Topic/CListCtrl::GetItemData.md)|擷取專屬的值與項目。|  
|[CListCtrl::GetItemIndexRect](../Topic/CListCtrl::GetItemIndexRect.md)|擷取子項目的全部或部分的週框 \(Bounding Rectangle\) 目前的清單檢視控制項的。|  
|[CListCtrl::GetItemPosition](../Topic/CListCtrl::GetItemPosition.md)|擷取清單檢視項目的位置。|  
|[CListCtrl::GetItemRect](../Topic/CListCtrl::GetItemRect.md)|擷取項目的週框。|  
|[CListCtrl::GetItemSpacing](../Topic/CListCtrl::GetItemSpacing.md)|計算在項目之間的間距目前清單檢視控制項。|  
|[CListCtrl::GetItemState](../Topic/CListCtrl::GetItemState.md)|擷取清單檢視項目的狀態。|  
|[CListCtrl::GetItemText](../Topic/CListCtrl::GetItemText.md)|擷取清單檢視項目或子項目的文字。|  
|[CListCtrl::GetNextItem](../Topic/CListCtrl::GetNextItem.md)|搜尋的清單檢視項目具有指定的屬性和與某一特定項目所指定的關聯性。|  
|[CListCtrl::GetNextItemIndex](../Topic/CListCtrl::GetNextItemIndex.md)|擷取項目的索引會指定屬性集的目前清單檢視控制項的。|  
|[CListCtrl::GetNextSelectedItem](../Topic/CListCtrl::GetNextSelectedItem.md)|擷取清單檢視項目位置的索引和秒已選取清單檢視項目的位置中逐一查看的。|  
|[CListCtrl::GetNumberOfWorkAreas](../Topic/CListCtrl::GetNumberOfWorkAreas.md)|擷取工作區域的目前編號清單檢視控制項。|  
|[CListCtrl::GetOrigin](../Topic/CListCtrl::GetOrigin.md)|擷取清單檢視控制項的目前檢視的原點。|  
|[CListCtrl::GetOutlineColor](../Topic/CListCtrl::GetOutlineColor.md)|擷取清單檢視控制項的框線色彩。|  
|[CListCtrl::GetSelectedColumn](../Topic/CListCtrl::GetSelectedColumn.md)|擷取目前選取的資料行索引在清單控制項中。|  
|[CListCtrl::GetSelectedCount](../Topic/CListCtrl::GetSelectedCount.md)|擷取選取的項目數目清單檢視控制項。|  
|[CListCtrl::GetSelectionMark](../Topic/CListCtrl::GetSelectionMark.md)|擷取清單檢視控制項選取的標記。|  
|[CListCtrl::GetStringWidth](../Topic/CListCtrl::GetStringWidth.md)|判斷所需要的最少的資料行寬度顯示所有指定的字串。|  
|[CListCtrl::GetSubItemRect](../Topic/CListCtrl::GetSubItemRect.md)|擷取一個項目的週框 \(Bounding Rectangle\) 清單檢視控制項。|  
|[CListCtrl::GetTextBkColor](../Topic/CListCtrl::GetTextBkColor.md)|擷取清單檢視控制項文字的背景色彩。|  
|[CListCtrl::GetTextColor](../Topic/CListCtrl::GetTextColor.md)|擷取清單檢視控制項的文字色彩。|  
|[CListCtrl::GetTileInfo](../Topic/CListCtrl::GetTileInfo.md)|擷取關於並排顯示的資訊在清單檢視控制項。|  
|[CListCtrl::GetTileViewInfo](../Topic/CListCtrl::GetTileViewInfo.md)|擷取有關清單檢視控制項的資訊在並排顯示。|  
|[CListCtrl::GetToolTips](../Topic/CListCtrl::GetToolTips.md)|擷取清單檢視控制項使用以顯示工具提示的工具提示控制項。|  
|[CListCtrl::GetTopIndex](../Topic/CListCtrl::GetTopIndex.md)|擷取最頂端可見項目的索引。|  
|[CListCtrl::GetView](../Topic/CListCtrl::GetView.md)|取得清單檢視控制項的檢視。|  
|[CListCtrl::GetViewRect](../Topic/CListCtrl::GetViewRect.md)|擷取所有項目的週框 \(Bounding Rectangle\) 清單檢視控制項。|  
|[CListCtrl::GetWorkAreas](../Topic/CListCtrl::GetWorkAreas.md)|擷取清單檢視控制項的目前工作區域。|  
|[CListCtrl::HasGroup](../Topic/CListCtrl::HasGroup.md)|判斷清單檢視控制項是否有指定的群組。|  
|[CListCtrl::HitTest](../Topic/CListCtrl::HitTest.md)|判斷清單檢視項目在指定的位置。|  
|[CListCtrl::InsertColumn](../Topic/CListCtrl::InsertColumn.md)|在清單檢視控制項插入新的資料行。|  
|[CListCtrl::InsertGroup](../Topic/CListCtrl::InsertGroup.md)|插入群組在清單檢視控制項。|  
|[CListCtrl::InsertGroupSorted](../Topic/CListCtrl::InsertGroupSorted.md)|要插入指定之群組的群組的排序清單。|  
|[CListCtrl::InsertItem](../Topic/CListCtrl::InsertItem.md)|在清單檢視控制項在插入新的項目。|  
|[CListCtrl::InsertMarkHitTest](../Topic/CListCtrl::InsertMarkHitTest.md)|擷取插入點最接近指定點的點。|  
|[CListCtrl::IsGroupViewEnabled](../Topic/CListCtrl::IsGroupViewEnabled.md)|判斷群組檢視是否為清單檢視控制項啟用。|  
|[CListCtrl::IsItemVisible](../Topic/CListCtrl::IsItemVisible.md)|表示目前在清單檢視控制項中指定的項目是否為可見的。|  
|[CListCtrl::MapIDToIndex](../Topic/CListCtrl::MapIDToIndex.md)|將某個項目的唯一 ID 在目前清單檢視控制項的索引。|  
|[CListCtrl::MapIndexToID](../Topic/CListCtrl::MapIndexToID.md)|將某個項目的索引目前清單檢視控制項的唯一 ID.|  
|[CListCtrl::MoveGroup](../Topic/CListCtrl::MoveGroup.md)|移動指定的群組。|  
|[CListCtrl::MoveItemToGroup](../Topic/CListCtrl::MoveItemToGroup.md)|移動指定的群組移至清單檢視控制項中指定的以零起始索引。|  
|[CListCtrl::RedrawItems](../Topic/CListCtrl::RedrawItems.md)|強制清單檢視控制項重新繪製項目的範圍。|  
|[CListCtrl::RemoveAllGroups](../Topic/CListCtrl::RemoveAllGroups.md)|從清單檢視控制項中移除所有群組。|  
|[CListCtrl::RemoveGroup](../Topic/CListCtrl::RemoveGroup.md)|從清單檢視控制項中移除指定的群組。|  
|[CListCtrl::Scroll](../Topic/CListCtrl::Scroll.md)|移動清單檢視控制項的內容。|  
|[CListCtrl::SetBkColor](../Topic/CListCtrl::SetBkColor.md)|設定清單檢視控制項的背景色彩。|  
|[CListCtrl::SetBkImage](../Topic/CListCtrl::SetBkImage.md)|設定清單檢視控制項的目前背景影像。|  
|[CListCtrl::SetCallbackMask](../Topic/CListCtrl::SetCallbackMask.md)|設定清單檢視控制項的回呼遮罩。|  
|[CListCtrl::SetCheck](../Topic/CListCtrl::SetCheck.md)|設定狀態影像上目前的顯示狀態相關聯的項目。|  
|[CListCtrl::SetColumn](../Topic/CListCtrl::SetColumn.md)|設定清單檢視資料行的屬性。|  
|[CListCtrl::SetColumnOrderArray](../Topic/CListCtrl::SetColumnOrderArray.md)|設定資料行順序 \(由左至右\) 清單檢視控制項。|  
|[CListCtrl::SetColumnWidth](../Topic/CListCtrl::SetColumnWidth.md)|變更一個資料行的寬度 \(以報告檢視或清單檢視的。|  
|[CListCtrl::SetExtendedStyle](../Topic/CListCtrl::SetExtendedStyle.md)|設定清單檢視控制項中目前的延伸樣式。|  
|[CListCtrl::SetGroupInfo](../Topic/CListCtrl::SetGroupInfo.md)|設定清單檢視控制項的指定之群組的資訊。|  
|[CListCtrl::SetGroupMetrics](../Topic/CListCtrl::SetGroupMetrics.md)|設定清單檢視控制項群組的度量資訊。|  
|[CListCtrl::SetHotCursor](../Topic/CListCtrl::SetHotCursor.md)|當熱追蹤針對清單檢視控制項時，啟用設定使用的游標。|  
|[CListCtrl::SetHotItem](../Topic/CListCtrl::SetHotItem.md)|設定清單檢視控制項的目前作用中的項目。|  
|[CListCtrl::SetHoverTime](../Topic/CListCtrl::SetHoverTime.md)|設定清單檢視控制項的目前停留時間。|  
|[CListCtrl::SetIconSpacing](../Topic/CListCtrl::SetIconSpacing.md)|將圖示之間的間距清單檢視控制項。|  
|[CListCtrl::SetImageList](../Topic/CListCtrl::SetImageList.md)|指定影像清單中的清單檢視控制項。|  
|[CListCtrl::SetInfoTip](../Topic/CListCtrl::SetInfoTip.md)|設定工具提示文字。|  
|[CListCtrl::SetInsertMark](../Topic/CListCtrl::SetInsertMark.md)|將設定為這個物件中的插入點。|  
|[CListCtrl::SetInsertMarkColor](../Topic/CListCtrl::SetInsertMarkColor.md)|將插入點的色彩。|  
|[CListCtrl::SetItem](../Topic/CListCtrl::SetItem.md)|設定部分或所有的清單檢視項目的屬性。|  
|[CListCtrl::SetItemCount](../Topic/CListCtrl::SetItemCount.md)|清單檢視控制項提供加入大量項目的準備工作。|  
|[CListCtrl::SetItemCountEx](../Topic/CListCtrl::SetItemCountEx.md)|設定虛擬清單檢視控制項中的項目計數。|  
|[CListCtrl::SetItemData](../Topic/CListCtrl::SetItemData.md)|設定項目的應用程式特定的值。|  
|[CListCtrl::SetItemIndexState](../Topic/CListCtrl::SetItemIndexState.md)|將某個項目的狀態在目前清單檢視控制項的。|  
|[CListCtrl::SetItemPosition](../Topic/CListCtrl::SetItemPosition.md)|將項目移至在清單檢視控制項中指定的位置。|  
|[CListCtrl::SetItemState](../Topic/CListCtrl::SetItemState.md)|將某個項目的狀態在清單檢視控制項。|  
|[CListCtrl::SetItemText](../Topic/CListCtrl::SetItemText.md)|變更清單檢視項目或子項目的文字。|  
|[CListCtrl::SetOutlineColor](../Topic/CListCtrl::SetOutlineColor.md)|設定清單檢視控制項的框線色彩。|  
|[CListCtrl::SetSelectedColumn](../Topic/CListCtrl::SetSelectedColumn.md)|設定清單檢視控制項中選取的資料行。|  
|[CListCtrl::SetSelectionMark](../Topic/CListCtrl::SetSelectionMark.md)|設定清單檢視控制項選取的標記。|  
|[CListCtrl::SetTextBkColor](../Topic/CListCtrl::SetTextBkColor.md)|設定文字的背景色彩在清單檢視控制項。|  
|[CListCtrl::SetTextColor](../Topic/CListCtrl::SetTextColor.md)|設定清單檢視控制項的文字色彩。|  
|[CListCtrl::SetTileInfo](../Topic/CListCtrl::SetTileInfo.md)|設定清單檢視控制項的並排顯示的資訊。|  
|[CListCtrl::SetTileViewInfo](../Topic/CListCtrl::SetTileViewInfo.md)|設定清單檢視控制項在並排顯示中所使用的資訊。|  
|[CListCtrl::SetToolTips](../Topic/CListCtrl::SetToolTips.md)|設定清單檢視控制項用於顯示工具提示的工具提示控制項。|  
|[CListCtrl::SetView](../Topic/CListCtrl::SetView.md)|設定清單檢視控制項的檢視。|  
|[CListCtrl::SetWorkAreas](../Topic/CListCtrl::SetWorkAreas.md)|設定要顯示在清單檢視控制項中顯示的區域。|  
|[CListCtrl::SortGroups](../Topic/CListCtrl::SortGroups.md)|排序清單檢視控制項的群組具有使用者定義的函式。|  
|[CListCtrl::SortItems](../Topic/CListCtrl::SortItems.md)|排序清單時所使用的應用程式定義的比較檢視項目的函式。|  
|[CListCtrl::SortItemsEx](../Topic/CListCtrl::SortItemsEx.md)|排序清單時所使用的應用程式定義的比較檢視項目的函式。|  
|[CListCtrl::SubItemHitTest](../Topic/CListCtrl::SubItemHitTest.md)|判斷清單檢視項目\)，如果有的話，在指定的位置。|  
|[CListCtrl::Update](../Topic/CListCtrl::Update.md)|強制控制項重新繪製指定的項目。|  
  
## 備註  
 除了圖示和標籤 \(Label\) 外，每個項目都可以在資料行中顯示的資訊在圖示和標籤右邊。  這個控制項 \(也 `CListCtrl` 類別\) 給在 Windows 95 \/98 和 Windows NT 3.51 版之下的程式才能使用 \(含\) 以後版本。  
  
 以下是 `CListCtrl` 類別的簡短概觀。  如需深入的概念，討論，請參閱 [使用 CListCtrl](../../mfc/using-clistctrl.md) 和 [控制項](../../mfc/controls-mfc.md)。  
  
## 檢視  
 清單檢視控制項可以顯示其內容使用四種不同的方法，稱為「檢視」。  
  
-   圖示。  
  
     每個項目顯示為一個大型圖示 \(32 x 32 像素\) 與標籤底下。  使用者可以將項目加入清單檢視視窗中的任何位置。  
  
-   小圖示檢視  
  
     每個項目都會顯示為小型圖示 \(16 x 16 像素\) 與標籤在圖示右邊。  使用者可以將項目加入清單檢視視窗中的任何位置。  
  
-   清單檢視  
  
     每個項目都會顯示為標籤的小圖示顯示在圖示右邊。  項目在資料行中排列，無法拖曳至清單檢視視窗中的任何位置。  
  
-   報告檢視  
  
     每一個項目在資料行中顯示在自己的程式碼行，而其他資訊來排列靠右對齊。  最左邊的資料行包含小圖示和標籤 \(Label\)，然後，後續的欄包含子項目所指定的應用程式。  內嵌標題控制項 \(類別\) [CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)實作這些資料行。  如需標題控制項和資料行的詳細資訊在 \[報表檢視，請參閱 [使用 CListCtrl:將資料行加入至控制項 \(報告檢視\)](../../mfc/adding-columns-to-the-control-report-view.md)。  
  
 請參閱:  
  
-   知識庫文件 Q250614:HOWTO:在 CListCtrl 的排序項目在報表檢視  
  
-   知識庫文件 Q200054:\<PRB:OnTimer \(\) 不會針對清單控制項重複呼叫  
  
 控制項的目前清單檢視的樣式來判斷目前的檢視。  如需這些模式及其用法的詳細資訊，請參閱 [使用 CListCtrl:變更的清單控制項模式](../../mfc/changing-list-control-styles.md)。  
  
## 延伸樣式  
 除了標準清單樣式之外，將 `CListCtrl` 支援大量延伸樣式，提供了豐富的功能。  這項功能的範例包括:  
  
-   停留於選取範圍  
  
     當已啟用，讓項目的自動選取，當游標停留在某個項目的時間。  
  
-   虛擬清單檢視  
  
     當已啟用，讓控制項支援 `DWORD` 項目。  這是將額外負荷可能會處理項目資料在應用程式。  除了項目選取範圍和焦點 \(Focus\) 資訊，必須由應用程式處理所有項目的資訊。  如需詳細資訊，請參閱 [使用 CListCtrl:虛擬清單控制項](../../mfc/virtual-list-controls.md)。  
  
-   一個和兩個按一下啟動。  
  
     當已啟用，讓熱追蹤 \(自動反白顯示項目文字\) 和反白顯示之項目的一個或兩個按一下啟動。  
  
-   拖放資料行順序  
  
     啟用時，允許拖放重新排列在清單檢視控制項中的資料行。  只適用於 \[報表檢視。  
  
 如需使用這些新的延伸樣式的詳細資訊，請參閱 [使用 CListCtrl:變更的清單控制項模式](../../mfc/changing-list-control-styles.md)。  
  
## 項目和子項目  
 在清單檢視控制項的每個項目都包含圖示 \(從影像清單\)，標籤、狀態和應用程式定義的值 \(稱為「項目資料」\)。  一個或多個子項目也與每一個項目。  「子項目」，將報告檢視中，在資料行中顯示該項目的圖示和標籤右邊的字串。  在清單檢視控制項中的所有項目都必須有子項目的數目。  
  
 類別 **CListCtrl** 外掛程式，刪除，尋找和修改這些項目提供數個函式。  如需詳細資訊，請參閱 [CListCtrl::GetItem](../Topic/CListCtrl::GetItem.md)、 [CListCtrl::InsertItem](../Topic/CListCtrl::InsertItem.md)和 [CListCtrl::FindItem](../Topic/CListCtrl::FindItem.md)、 [使用 CListCtrl:將項目加入至控制項](../../mfc/adding-items-to-the-control.md)和 [使用 CListCtrl:移動，排列，排序和尋找在清單控制項](../../mfc/scrolling-arranging-sorting-and-finding-in-list-controls.md)。  
  
 根據預設，清單檢視控制項中項目的圖示和文字屬性管理。  不過，刪除這些項目之外，類別， `CListCtrl` 支援回呼「項目」。回呼「項目」是應用程式的清單檢視項目 \(而不是控制項—文字存放區，圖示或兩者。  回呼遮罩是用來指定哪些項目屬性 \(文字和圖示\) 提供應用程式。  如果應用程式使用回呼項目，必須能夠提供文字和圖示的屬性是在要求時。  當您的應用程式已經維護一些資訊時，回呼項目很有用。  如需詳細資訊，請參閱 [使用 CListCtrl:回呼項目和回呼遮罩](../../mfc/callback-items-and-the-callback-mask.md)。  
  
## 影像清單  
 圖示、標題項目影像和應用程式定義狀態清單檢視項目的數個影像清單包含 \(由類別實作 [CImageList](../../mfc/reference/cimagelist-class.md)\)，您將建立和指派到清單檢視控制項。  每個清單檢視控制項可能已經有影像清單的四種不同:  
  
-   大型圖示  
  
     使用在 \[圖示\] 檢視提供大型圖示。  
  
-   小圖示。  
  
     使用以小圖示、清單和報告檢視可用來圖示檢視中圖示的較小的版本。  
  
-   應用程式定義狀態。  
  
     包含狀態影像，在項目圖示旁邊顯示表示應用程式定義的狀態。  
  
-   Header item  
  
     使用在報表檢視會出現在每個標題控制項項目的小型影像。  
  
 根據預設，，終結時，清單檢視控制項終結影像清單中指定給它，不過，藉由終結每個影像清單的自訂這個行為，並在不使用時，由應用程式所依賴的開發人員。  如需詳細資訊，請參閱 [使用 CListCtrl:清單項目和影像清單](../../mfc/list-items-and-image-lists.md)。  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CListCtrl`  
  
## 需求  
 **Header:** afxcmn.h  
  
## 請參閱  
 [MFC 範例 ROWLIST](../../top/visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CImageList Class](../../mfc/reference/cimagelist-class.md)