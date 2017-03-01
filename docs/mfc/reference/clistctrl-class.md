---
title: "CListCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CListCtrl
dev_langs:
- C++
helpviewer_keywords:
- CListCtrl class
- LVS_REPORT
- LVS_LIST
- LVS_ICON
- list view controls
- list view controls, CListCtrl class
- Windows common controls [C++], CListCtrl
- LVS_SMALLICON
ms.assetid: fe08a1ca-4b05-4ff7-a12a-ee4c765a2197
caps.latest.revision: 23
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: fb82dd194d59bff9e0a3fe8f047686a8bcc4d927
ms.lasthandoff: 02/24/2017

---
# <a name="clistctrl-class"></a>CListCtrl 類別
封裝「清單檢視控制項」的功能，顯示項目集合，其中每個項目是由圖示 (來自影像清單) 和標籤所組成的。  
  
## <a name="syntax"></a>語法  
  
```  
class CListCtrl : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CListCtrl::CListCtrl](#clistctrl)|建構 `CListCtrl` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CListCtrl::ApproximateViewRect](#approximateviewrect)|決定顯示清單檢視控制項的項目所需的高度與寬度。|  
|[CListCtrl::Arrange](#arrange)|對齊方格中的項目。|  
|[CListCtrl::CancelEditLabel](#canceleditlabel)|取消編輯作業的項目文字。|  
|[CListCtrl::Create](#create)|建立清單控制項，並將它附加`CListCtrl`物件。|  
|[CListCtrl::CreateDragImage](#createdragimage)|建立拖曳影像清單指定的項目。|  
|[CListCtrl::CreateEx](#createex)|建立具有指定的 Windows 延伸樣式清單控制項，並將其以附加`CListCtrl`物件。|  
|[CListCtrl::DeleteAllItems](#deleteallitems)|從控制項中刪除所有項目。|  
|[CListCtrl::DeleteColumn](#deletecolumn)|從清單檢視控制項中刪除資料行。|  
|[CListCtrl::DeleteItem](#deleteitem)|從控制項中刪除項目。|  
|[CListCtrl::DrawItem](#drawitem)|主控描繪控制項變更的視覺外觀時呼叫。|  
|[CListCtrl::EditLabel](#editlabel)|開始進行就地編輯項目的文字。|  
|[CListCtrl::EnableGroupView](#enablegroupview)|啟用或停用是否在清單檢視控制項中的項目顯示為群組。|  
|[CListCtrl::EnsureVisible](#ensurevisible)|請確定項目會出現。|  
|[CListCtrl::FindItem](#finditem)|搜尋具有指定特性的清單檢視項目。|  
|[CListCtrl::GetBkColor](#getbkcolor)|擷取清單檢視控制項的背景色彩。|  
|[CListCtrl::GetBkImage](#getbkimage)|擷取目前的清單檢視控制項的背景影像。|  
|[Clistctrl:: Getcallbackmask](#getcallbackmask)|擷取清單檢視控制項的回呼遮罩。|  
|[CListCtrl::GetCheck](#getcheck)|擷取目前的項目相關聯之狀態影像的顯示狀態。|  
|[CListCtrl::GetColumn](#getcolumn)|擷取控制項的資料行的屬性。|  
|[CListCtrl::GetColumnOrderArray](#getcolumnorderarray)|擷取清單檢視控制項的資料行順序 （由左到右）。|  
|[CListCtrl::GetColumnWidth](#getcolumnwidth)|擷取報表的檢視或清單檢視中的資料行的寬度。|  
|[CListCtrl::GetCountPerPage](#getcountperpage)|計算清單檢視控制項中以垂直方式可以符合的項目的數目。|  
|[CListCtrl::GetEditControl](#geteditcontrol)|擷取用來編輯項目的文字編輯控制項的控制代碼。|  
|[CListCtrl::GetEmptyText](#getemptytext)|擷取要顯示目前的清單檢視控制項為空字串。|  
|[CListCtrl::GetExtendedStyle](#getextendedstyle)|擷取清單檢視控制項的目前延伸的樣式。|  
|[CListCtrl::GetFirstSelectedItemPosition](#getfirstselecteditemposition)|擷取清單檢視控制項中的第一個選取的清單檢視項目的位置。|  
|[CListCtrl::GetFocusedGroup](#getfocusedgroup)|擷取目前的清單檢視控制項中具有鍵盤焦點的群組。|  
|[CListCtrl::GetGroupCount](#getgroupcount)|擷取目前的清單檢視控制項中的群組數目。|  
|[CListCtrl::GetGroupInfo](#getgroupinfo)|取得指定的群組清單檢視控制項的資訊。|  
|[CListCtrl::GetGroupInfoByIndex](#getgroupinfobyindex)|擷取目前的清單檢視控制項中的指定群組的相關資訊。|  
|[CListCtrl::GetGroupMetrics](#getgroupmetrics)|擷取群組的度量。|  
|[CListCtrl::GetGroupRect](#getgrouprect)|擷取目前的清單檢視控制項中指定之群組的周框。|  
|[CListCtrl::GetGroupState](#getgroupstate)|擷取目前的清單檢視控制項中指定之群組的狀態。|  
|[CListCtrl::GetHeaderCtrl](#getheaderctrl)|擷取清單檢視控制項的標題控制項。|  
|[CListCtrl::GetHotCursor](#gethotcursor)|擷取清單檢視控制項的熱追蹤啟用時，使用資料指標。|  
|[CListCtrl::GetHotItem](#gethotitem)|擷取目前游標下方的清單檢視項目。|  
|[CListCtrl::GetHoverTime](#gethovertime)|擷取清單檢視控制項的滑鼠停留時間。|  
|[CListCtrl::GetImageList](#getimagelist)|擷取用於繪圖的清單檢視項目的影像清單控制代碼。|  
|[CListCtrl::GetInsertMark](#getinsertmark)|擷取目前的插入標記的位置。|  
|[CListCtrl::GetInsertMarkColor](#getinsertmarkcolor)|擷取目前的插入標記的色彩。|  
|[CListCtrl::GetInsertMarkRect](#getinsertmarkrect)|擷取範圍的插入點的矩形。|  
|[Clistctrl:: Getitem](#getitem)|擷取清單檢視項目的屬性。|  
|[CListCtrl::GetItemCount](#getitemcount)|擷取清單檢視控制項中的項目數。|  
|[CListCtrl::GetItemData](#getitemdata)|擷取項目相關聯的應用程式特定值。|  
|[CListCtrl::GetItemIndexRect](#getitemindexrect)|擷取週框的全部或部分的目前清單檢視控制項中的子項目。|  
|[CListCtrl::GetItemPosition](#getitemposition)|擷取清單檢視項目的位置。|  
|[CListCtrl::GetItemRect](#getitemrect)|擷取項目的周框。|  
|[CListCtrl::GetItemSpacing](#getitemspacing)|計算目前的清單檢視控制項中的項目之間的間距。|  
|[CListCtrl::GetItemState](#getitemstate)|擷取清單檢視項目的狀態。|  
|[CListCtrl::GetItemText](#getitemtext)|擷取清單檢視項目或子項目的文字。|  
|[CListCtrl::GetNextItem](#getnextitem)|搜尋指定的屬性與指定的項目指定關聯性的清單檢視項目。|  
|[CListCtrl::GetNextItemIndex](#getnextitemindex)|擷取具有指定的屬性集的目前清單檢視控制項中項目的索引。|  
|[CListCtrl::GetNextSelectedItem](#getnextselecteditem)|擷取清單檢視項目的位置和位置的下一個選取的清單檢視項目來重複的索引。|  
|[CListCtrl::GetNumberOfWorkAreas](#getnumberofworkareas)|擷取清單檢視控制項的工作區的目前數目。|  
|[CListCtrl::GetOrigin](#getorigin)|擷取清單檢視控制項的目前檢視來源。|  
|[CListCtrl::GetOutlineColor](#getoutlinecolor)|擷取清單檢視控制項的框線的色彩。|  
|[CListCtrl::GetSelectedColumn](#getselectedcolumn)|擷取清單控制項中目前選取的資料行的索引。|  
|[CListCtrl::GetSelectedCount](#getselectedcount)|擷取清單檢視控制項中選取的項目數目。|  
|[CListCtrl::GetSelectionMark](#getselectionmark)|擷取清單檢視控制項的選取項目符號。|  
|[CListCtrl::GetStringWidth](#getstringwidth)|決定要顯示所有指定的字串所需的最小的資料行寬度。|  
|[CListCtrl::GetSubItemRect](#getsubitemrect)|擷取清單檢視控制項中的項目，這個周框。|  
|[CListCtrl::GetTextBkColor](#gettextbkcolor)|擷取清單檢視控制項的文字背景色彩。|  
|[CListCtrl::GetTextColor](#gettextcolor)|擷取清單檢視控制項的文字色彩。|  
|[CListCtrl::GetTileInfo](#gettileinfo)|擷取清單檢視控制項中並排顯示的相關資訊。|  
|[CListCtrl::GetTileViewInfo](#gettileviewinfo)|擷取清單檢視控制項中並排顯示檢視的相關資訊。|  
|[CListCtrl::GetToolTips](#gettooltips)|擷取清單檢視控制項用來顯示工具提示的工具提示控制項。|  
|[CListCtrl::GetTopIndex](#gettopindex)|擷取最上層的可見項目的索引。|  
|[CListCtrl::GetView](#getview)|取得清單檢視控制項的檢視。|  
|[CListCtrl::GetViewRect](#getviewrect)|擷取清單檢視控制項中的所有項目的周框。|  
|[CListCtrl::GetWorkAreas](#getworkareas)|擷取目前的工作區的清單檢視控制項。|  
|[CListCtrl::HasGroup](#hasgroup)|判斷清單檢視控制項是否具有指定的群組。|  
|[CListCtrl::HitTest](#hittest)|決定哪些清單檢視項目位於指定位置。|  
|[CListCtrl::InsertColumn](#insertcolumn)|在清單檢視控制項中插入新的資料行。|  
|[CListCtrl::InsertGroup](#insertgroup)|插入清單檢視控制項中的群組。|  
|[CListCtrl::InsertGroupSorted](#insertgroupsorted)|插入群組的已排序清單中指定的群組。|  
|[CListCtrl::InsertItem](#insertitem)|在清單檢視控制項中插入新項目。|  
|[CListCtrl::InsertMarkHitTest](#insertmarkhittest)|擷取最接近指定點的插入點。|  
|[CListCtrl::IsGroupViewEnabled](#isgroupviewenabled)|判斷是否啟用清單檢視控制項的群組檢視。|  
|[CListCtrl::IsItemVisible](#isitemvisible)|指出目前的清單檢視控制項中指定的項目是否可見。|  
|[CListCtrl::MapIDToIndex](#mapidtoindex)|將目前的清單檢視控制項中項目的唯一識別碼對應至索引。|  
|[CListCtrl::MapIndexToID](#mapindextoid)|將目前的清單檢視控制項中項目的索引對應至唯一的識別碼。|  
|[CListCtrl::MoveGroup](#movegroup)|將指定的群組移動。|  
|[CListCtrl::MoveItemToGroup](#moveitemtogroup)|移動指定群組，來指定零根據的索引的清單檢視控制項。|  
|[CListCtrl::RedrawItems](#redrawitems)|強制重新繪製的項目範圍的清單檢視控制項。|  
|[CListCtrl::RemoveAllGroups](#removeallgroups)|從清單檢視控制項中移除所有群組。|  
|[CListCtrl::RemoveGroup](#removegroup)|從清單檢視控制項中移除指定的群組。|  
|[CListCtrl::Scroll](#scroll)|捲動清單檢視控制項的內容。|  
|[CListCtrl::SetBkColor](#setbkcolor)|設定清單檢視控制項的背景色彩。|  
|[CListCtrl::SetBkImage](#setbkimage)|設定目前的清單檢視控制項的背景影像。|  
|[Clistctrl:: Setcallbackmask](#setcallbackmask)|設定清單檢視控制項的回呼遮罩。|  
|[CListCtrl::SetCheck](#setcheck)|設定目前顯示的項目相關聯之狀態影像的狀態。|  
|[CListCtrl::SetColumn](#setcolumn)|設定清單檢視資料行的屬性。|  
|[CListCtrl::SetColumnOrderArray](#setcolumnorderarray)|設定清單檢視控制項的資料行順序 （由左到右）。|  
|[CListCtrl::SetColumnWidth](#setcolumnwidth)|變更報表的檢視或清單檢視中的資料行的寬度。|  
|[CListCtrl::SetExtendedStyle](#setextendedstyle)|設定清單檢視控制項的目前延伸的樣式。|  
|[CListCtrl::SetGroupInfo](#setgroupinfo)|設定為指定的群組清單檢視控制項的資訊。|  
|[CListCtrl::SetGroupMetrics](#setgroupmetrics)|設定群組度量的清單檢視控制項。|  
|[CListCtrl::SetHotCursor](#sethotcursor)|設定已啟用熱追蹤，清單檢視控制項時所使用的游標。|  
|[CListCtrl::SetHotItem](#sethotitem)|將清單檢視控制項的目前作用的項目。|  
|[CListCtrl::SetHoverTime](#sethovertime)|設定清單檢視控制項的滑鼠停留時間。|  
|[CListCtrl::SetIconSpacing](#seticonspacing)|設定清單檢視控制項中的圖示之間的間距。|  
|[CListCtrl::SetImageList](#setimagelist)|將影像清單指派給清單檢視控制項。|  
|[CListCtrl::SetInfoTip](#setinfotip)|設定工具提示文字。|  
|[CListCtrl::SetInsertMark](#setinsertmark)|將插入點設定為定義的位置。|  
|[CListCtrl::SetInsertMarkColor](#setinsertmarkcolor)|設定插入點的色彩。|  
|[Clistctrl:: Setitem](#setitem)|設定部分或全部的清單檢視項目的屬性。|  
|[CListCtrl::SetItemCount](#setitemcount)|準備新增大量的項目清單檢視控制項。|  
|[CListCtrl::SetItemCountEx](#setitemcountex)|設定虛擬清單檢視控制項的項目計數。|  
|[CListCtrl::SetItemData](#setitemdata)|設定項目的應用程式特定值。|  
|[CListCtrl::SetItemIndexState](#setitemindexstate)|在目前的清單檢視控制項中設定項目的狀態。|  
|[CListCtrl::SetItemPosition](#setitemposition)|將項目移至清單檢視控制項中指定的位置。|  
|[CListCtrl::SetItemState](#setitemstate)|在清單檢視控制項中項目的狀態變更。|  
|[CListCtrl::SetItemText](#setitemtext)|變更清單檢視項目或子項目的的文字。|  
|[CListCtrl::SetOutlineColor](#setoutlinecolor)|設定清單檢視控制項的框線色彩。|  
|[CListCtrl::SetSelectedColumn](#setselectedcolumn)|設定選取的資料行的清單檢視控制項。|  
|[CListCtrl::SetSelectionMark](#setselectionmark)|設定清單檢視控制項的選取範圍標記。|  
|[CListCtrl::SetTextBkColor](#settextbkcolor)|在清單檢視控制項中設定文字的背景色彩。|  
|[CListCtrl::SetTextColor](#settextcolor)|將清單檢視控制項的文字色彩。|  
|[CListCtrl::SetTileInfo](#settileinfo)|設定清單檢視控制項的並排顯示的資訊。|  
|[CListCtrl::SetTileViewInfo](#settileviewinfo)|設定並排顯示檢視中使用清單檢視控制項的資訊。|  
|[CListCtrl::SetToolTips](#settooltips)|設定用來顯示工具提示的清單檢視控制項的工具提示控制項。|  
|[CListCtrl::SetView](#setview)|設定清單檢視控制項的檢視。|  
|[CListCtrl::SetWorkAreas](#setworkareas)|設定位置顯示圖示，在清單檢視控制項中的區域。|  
|[CListCtrl::SortGroups](#sortgroups)|排序的群組清單檢視控制項的使用者定義函式。|  
|[CListCtrl::SortItems](#sortitems)|使用應用程式定義的比較函式的清單檢視項目排序。|  
|[CListCtrl::SortItemsEx](#sortitemsex)|使用應用程式定義的比較函式的清單檢視項目排序。|  
|[CListCtrl::SubItemHitTest](#subitemhittest)|如果有任何項目，是位於指定位置，決定哪一個清單檢視項目。|  
|[CListCtrl::Update](#update)|強制重新繪製指定的項目控制項。|  
  
## <a name="remarks"></a>備註  
 除了圖示和標籤，每個項目可以擁有右邊的圖示和標籤資料行中顯示的資訊。 這個控制項 (並因此`CListCtrl`類別) 僅適用於執行 Windows 95/98 和 Windows NT 版本 3.51 下的程式和更新版本。  
  
 以下是將概略`CListCtrl`類別。 如需詳細的概念性的討論，請參閱[使用 CListCtrl](../../mfc/using-clistctrl.md)和[控制項](../../mfc/controls-mfc.md)。  
  
## <a name="views"></a>檢視  
 清單檢視控制項可以顯示其內容以四種不同的方式，稱為 「 檢視 」。  
  
-   圖示檢視  
  
     每個項目顯示成完整大小圖示 （32 x 32 像素為單位），其下的標籤。 使用者可以將項目拖曳到清單檢視 視窗中的任何位置。  
  
-   小圖示檢視  
  
     每個項目在右邊的標籤就會顯示為小圖示 （16 x 16 像素為單位）。 使用者可以將項目拖曳到清單檢視 視窗中的任何位置。  
  
-   清單檢視  
  
     每個項目會顯示為小圖示右邊的標籤。 項目會排列在資料行，並且無法拖曳至 [清單檢視] 視窗中的任何位置。  
  
-   報表檢視  
  
     每個項目會出現在其個別行中，排列在右邊的資料行中的其他資訊。 最左邊資料行包含的小圖示和標籤，而後續的資料行包含應用程式所指定的子項目。 為內嵌的標題控制項 (類別[CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)) 會實作這些資料行。 如需標題控制項和報表檢視中的資料行的詳細資訊，請參閱[使用 CListCtrl︰ 新增資料行加入至控制項 （報表檢視）](../../mfc/adding-columns-to-the-control-report-view.md)。  
  
 另請參閱：  
  
-   知識庫文件 Q250614︰ 如何︰ 在報表檢視 CListCtrl 中排序項目  
  
-   知識庫文件 Q200054: PRB: OnTimer() 是不呼叫重複清單控制項  
  
 目前清單檢視控制項的樣式會判斷目前的檢視。 如需有關這些樣式和其使用方式的詳細資訊，請參閱[使用 CListCtrl︰ 變更清單控制項樣式](../../mfc/changing-list-control-styles.md)。  
  
## <a name="extended-styles"></a>延伸的樣式  
 除了標準清單樣式類別`CListCtrl`支援一組大型的延伸樣式，提供豐富的功能。 這項功能的一些範例包括︰  
  
-   暫留選取範圍  
  
     啟用時，允許自動選取項目，當游標停留一段時間的項目。  
  
-   虛擬清單檢視  
  
     啟用時，允許最多支援控制項`DWORD`項目。 這可能是藉由放置管理應用程式上的項目資料的額外負荷。 除了項目選取範圍和焦點資訊，都必須由應用程式管理的所有項目資訊。 如需詳細資訊，請參閱[使用 CListCtrl︰ 虛擬清單控制項](../../mfc/virtual-list-controls.md)。  
  
-   一和二 – 按一下啟動  
  
     啟用時，可讓 （自動反白顯示的項目文字） 的熱追蹤並啟用一或兩個 – 按一下反白顯示的項目。  
  
-   將拖放資料行排序  
  
     啟用時，可讓拖放時重新排列清單檢視控制項中的資料行。 只有在報表檢視中。  
  
 如需有關使用這些新的延伸樣式，請參閱[使用 CListCtrl︰ 變更清單控制項樣式](../../mfc/changing-list-control-styles.md)。  
  
## <a name="items-and-subitems"></a>項目和子項目  
 在清單檢視控制項中的每個項目是由圖示 （來自影像清單）、 標籤、 目前的狀態和應用程式定義的值 （稱為 「 項目資料 」） 所組成。 至少有一個子項目也可以產生關聯與每個項目。 「 子項目 」 是一個字串，在報表檢視中，可以顯示在右邊的項目圖示和標籤資料行。 清單檢視控制項中的所有項目必須具有相同數目的子項目。  
  
 類別**CListCtrl**插入、 刪除、 尋找、 及修改這些項目提供數個函數。 如需詳細資訊，請參閱[clistctrl:: Getitem](#getitem)， [CListCtrl::InsertItem](#insertitem)，和[CListCtrl::FindItem](#finditem)，[將項目加入至控制項](../adding-items-to-the-control.md)，和[捲動、 排列、 排序和尋找清單控制項中的](../scrolling-arranging-sorting-and-finding-in-list-controls.md)。  
  
 根據預設，清單檢視控制項負責儲存項目的圖示和文字屬性。 不過，這些項目類型，除了類別`CListCtrl`支援 「 回呼項目 」。 「 回呼項目 」 是清單檢視項目，應用程式，而不是控制項 — 儲存文字、 圖示或兩者。 回呼遮罩用來指定應用程式所提供的項目屬性 （文字及/或圖示）。 如果應用程式會使用回呼項目，它必須能夠提供隨選的文字及/或圖示屬性。 當您的應用程式已經維護其中有些資訊很有幫助回呼項目。 如需詳細資訊，請參閱[使用 CListCtrl︰ 回呼項目和回呼遮罩](../callback-items-and-the-callback-mask.md)。  
  
## <a name="image-lists"></a>影像清單  
 圖示、 標頭項目影像和應用程式 – 定義狀態的清單檢視項目都包含數個映像清單中 (由類別實作[CImageList](cimagelist-class.md))，您建立並指派給清單檢視控制項。 每個清單檢視控制項可以有多達四個不同的影像清單︰  
  
-   大型圖示  
  
     圖示檢視中用於完整大小圖示。  
  
-   小圖示  
  
     在小圖示、 清單和報表檢視用於較小圖示檢視中使用的圖示版本。  
  
-   應用程式定義的狀態  
  
     包含狀態影像，以指出應用程式定義的狀態項目的圖示旁會顯示。  
  
-   標頭項目  
  
     在 [報表] 檢視用於每個標頭控制項項目中出現的小型影像。  
  
 根據預設，清單檢視控制項終結終結時，指派給它的影像清單不過，開發人員可以自訂此行為終結每個映像清單，不再使用時，應用程式所決定。 如需詳細資訊，請參閱[使用 CListCtrl︰ 清單項目和影像清單](../list-items-and-image-lists.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](cobject-class.md)  
  
 [CCmdTarget](ccmdtarget-class.md)  
  
 [CWnd](cwnd-class.md)  
  
 `CListCtrl`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcmn.h  
  
##  <a name="a-nameapproximateviewrecta--clistctrlapproximateviewrect"></a><a name="approximateviewrect"></a>CListCtrl::ApproximateViewRect  
 決定顯示清單檢視控制項的項目所需的高度與寬度。  
  
```  
CSize ApproximateViewRect(
    CSize sz = CSize(-1,  
 -1),  
    int iCount = -1) const;  
```  
  
### <a name="parameters"></a>參數  
 `sz`  
 像素為單位指定控制項的提議的維度。 如果不指定維度，架構會使用控制項的目前寬度或高度值。  
  
 `iCount`  
 若要在控制項中顯示的項目數目。 如果這個參數是-1，架構會使用項目的總數目前在控制項中。  
  
### <a name="return-value"></a>傳回值  
 A`CSize`物件，其中包含的大約寬度和高度所需的項目，顯示像素為單位。  
  
### <a name="remarks"></a>備註  
 此成員函式實作 Win32 巨集的行為[ListView_ApproximateViewRect](http://msdn.microsoft.com/library/windows/desktop/bb761231)所述，在[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namearrangea--clistctrlarrange"></a><a name="arrange"></a>CListCtrl::Arrange  
 重新放置圖示檢視中的項目，使它們對齊格線。  
  
```  
BOOL Arrange(UINT nCode);
```  
  
### <a name="parameters"></a>參數  
 `nCode`  
 指定對齊樣式的項目。 它可以是下列值之一︰  
  
- `LVA_ALIGNLEFT`對齊視窗的左邊緣的項目。  
  
- `LVA_ALIGNTOP`對齊視窗的上邊緣處的項目。  
  
- `LVA_DEFAULT`對齊項目，根據目前對齊樣式清單檢視 （預設值）。  
  
- `LVA_SNAPTOGRID`所有圖示貼都齊最近的格線位置。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 `nCode`參數指定對齊樣式。  
  
### <a name="example"></a>範例    
```cpp  
    // Align all of the list view control items along the top
    // of the window (the list view control must be in icon or
    // small icon mode).
    m_myListCtrl.Arrange(LVA_ALIGNTOP);
```

  
##  <a name="a-namecanceleditlabela--clistctrlcanceleditlabel"></a><a name="canceleditlabel"></a>CListCtrl::CancelEditLabel  
 取消編輯作業的項目文字。  
  
```  
void CancelEditLabel();
```  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LVM_CANCELEDITLABEL](http://msdn.microsoft.com/library/windows/desktop/bb774886)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-nameclistctrla--clistctrlclistctrl"></a><a name="clistctrl"></a>CListCtrl::CListCtrl  
 建構 `CListCtrl` 物件。  
  
```  
CListCtrl();
```  
  
##  <a name="a-namecreatea--clistctrlcreate"></a><a name="create"></a>CListCtrl::Create  
 建立清單控制項，並將它附加`CListCtrl`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `dwStyle`  
 指定清單控制項的樣式。 套用至控制項的清單控制項樣式的任何組合。 請參閱[清單檢視的視窗樣式](http://msdn.microsoft.com/library/windows/desktop/bb774739)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]的一種樣式的完整清單。 設定擴充特定控制項使用的樣式[SetExtendedStyle](#setextendedstyle)。  
  
 `rect`  
 指定清單控制項的大小和位置。 它可以是`CRect`物件或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構。  
  
 `pParentWnd`  
 指定清單控制項的父視窗，通常`CDialog`。 它不得為**NULL**。  
  
 `nID`  
 指定清單控制項的 id。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 您建構`CListCtrl`兩個步驟。 首先，呼叫建構函式，接著呼叫**建立**，其建立清單檢視控制項，並將它附加`CListCtrl`物件。  
  
 若要將延伸的視窗樣式套用至清單控制項物件，呼叫[CreateEx](#createex)而不是**建立**。  
  
### <a name="example"></a>範例  

```cpp  
    m_myListCtrl.Create(
        WS_CHILD|WS_VISIBLE|WS_BORDER|LVS_REPORT|LVS_EDITLABELS,
        CRect(10,10,400,200), pParentWnd, IDD_MYLISTCTRL);   
```

  
##  <a name="a-namecreateexa--clistctrlcreateex"></a><a name="createex"></a>CListCtrl::CreateEx  
 建立控制項 （子視窗），並將它與相關聯`CListCtrl`物件。  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,  
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `dwExStyle`  
 指定正在建立的控制項的延伸的樣式。 如需延伸視窗樣式，請參閱`dwExStyle`參數[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
 `dwStyle`  
 指定清單控制項的樣式。 套用至控制項的清單控制項樣式的任何組合。 一種樣式的完整清單，請參閱[清單檢視的視窗樣式](http://msdn.microsoft.com/library/windows/desktop/bb774739)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
 `rect`  
 參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構描述的大小和位置來建立、 用戶端座標中的視窗的`pParentWnd`。  
  
 `pParentWnd`  
 是控制項的父視窗的指標。  
  
 `nID`  
 控制項的子視窗的 id。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 使用`CreateEx`而不是[建立](#create)套用延伸的視窗樣式，指定 Windows 延伸的樣式序言**WS_EX_**。  
  
 `CreateEx`建立具有所指定的延伸視窗樣式控制項`dwExStyle`。 若要設定特定延伸的樣式至控制項，呼叫[SetExtendedStyle](#setextendedstyle)。 例如，使用`CreateEx`設為這類樣式**WS_EX_CONTEXTHELP**，但使用`SetExtendedStyle`設為這類樣式**LVS_EX_FULLROWSELECT**。 如需詳細資訊，請參閱本主題中所述的樣式[擴充清單檢視樣式](http://msdn.microsoft.com/library/windows/desktop/bb774732)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namecreatedragimagea--clistctrlcreatedragimage"></a><a name="createdragimage"></a>CListCtrl::CreateDragImage  
 建立拖曳影像清單所指定的項目`nItem`。  
  
```  
CImageList* CreateDragImage(
    int nItem,  
    LPPOINT lpPoint);
```  
  
### <a name="parameters"></a>參數  
 `nItem`  
 若要建立的拖曳影像清單的項目索引。  
  
 `lpPoint`  
 位址[點](http://msdn.microsoft.com/library/windows/desktop/dd162805)接收影像的左上角的初始位置的結構檢視中進行協調。  
  
### <a name="return-value"></a>傳回值  
 如果成功，拖曳影像清單的指標否則**NULL**。  
  
### <a name="remarks"></a>備註  
 `CImageList`物件是永久的而且您必須刪除它完成。 例如：  
  

```cpp  
        CImageList* pImageList = m_myListCtrl.CreateDragImage(nItem, &point);

        // do something

        delete pImageList;
```

  
##  <a name="a-namedeleteallitemsa--clistctrldeleteallitems"></a><a name="deleteallitems"></a>CListCtrl::DeleteAllItems  
 刪除清單檢視控制項中的所有項目。  
  
```  
BOOL DeleteAllItems();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="example"></a>範例  

```cpp  
    // Delete all of the items from the list view control.
    m_myListCtrl.DeleteAllItems();
    ASSERT(m_myListCtrl.GetItemCount() == 0);
```

  
##  <a name="a-namedeletecolumna--clistctrldeletecolumn"></a><a name="deletecolumn"></a>CListCtrl::DeleteColumn  
 從清單檢視控制項中刪除資料行。  
  
```  
BOOL DeleteColumn(int nCol);
```  
  
### <a name="parameters"></a>參數  
 `nCol`  
 要刪除的資料行索引。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="example"></a>範例  

```cpp  
        int nColumnCount = m_myListCtrl.GetHeaderCtrl()->GetItemCount();

        // Delete all of the columns.
        for (int i=0; i < nColumnCount; i++)
        {
            m_myListCtrl.DeleteColumn(0);
        }
```

  
##  <a name="a-namedeleteitema--clistctrldeleteitem"></a><a name="deleteitem"></a>CListCtrl::DeleteItem  
 從清單檢視控制項中刪除項目。  
  
```  
BOOL DeleteItem(int nItem);
```  
  
### <a name="parameters"></a>參數  
 `nItem`  
 指定要刪除之項目的索引。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="example"></a>範例  
```cpp  
        int nCount = m_myListCtrl.GetItemCount();

        // Delete all of the items from the list view control.
        for (int i=0; i < nCount; i++)
        {
            m_myListCtrl.DeleteItem(0);
        }
```

  
##  <a name="a-namedrawitema--clistctrldrawitem"></a><a name="drawitem"></a>CListCtrl::DrawItem  
 當主控描繪清單檢視控制項變更的視覺外觀的架構所呼叫。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>參數  
 `lpDrawItemStruct`  
 長指標`DRAWITEMSTRUCT`結構，其中包含所需的繪圖的類型資訊。  
  
### <a name="remarks"></a>備註  
 **ItemAction**成員[DRAWITEMSTRUCT](http://msdn.microsoft.com/library/windows/desktop/bb775802)結構會定義要執行的繪圖動作。  
  
 根據預設，此成員函式沒有作用。 覆寫此成員函式實作繪圖的主控描繪`CListCtrl`物件。  
  
 應用程式應該還原選取的顯示內容中提供所有的圖形裝置介面 (GDI) 物件`lpDrawItemStruct`之前此成員函式會結束。  
  
##  <a name="a-nameeditlabela--clistctrleditlabel"></a><a name="editlabel"></a>CListCtrl::EditLabel  
 開始進行就地編輯項目的文字。  
  
```  
CEdit* EditLabel(int nItem);
```  
  
### <a name="parameters"></a>參數  
 `nItem`  
 要編輯的清單檢視項目的索引。  
  
### <a name="return-value"></a>傳回值  
 如果成功，指標`CEdit`物件，用來編輯項目文字; 否則為**NULL**。  
  
### <a name="remarks"></a>備註  
 清單檢視控制項具有`LVS_EDITLABELS`視窗樣式可讓使用者編輯項目標籤位置。 使用者開始編輯按一下具有焦點之項目的標籤。  
  
 使用此函式開始進行就地編輯指定的清單檢視項目的文字。  
  
### <a name="example"></a>範例  
```cpp  
        // Make sure the focus is set to the list view control.
        m_myListCtrl.SetFocus();

        // Show the edit control on the label of the first
        // item in the list view control.
        CEdit* pmyEdit = m_myListCtrl.EditLabel(1);
        ASSERT(pmyEdit != NULL);
```

  
##  <a name="a-nameenablegroupviewa--clistctrlenablegroupview"></a><a name="enablegroupview"></a>CListCtrl::EnableGroupView  
 啟用或停用是否在清單檢視控制項中的項目顯示為群組。  
  
```  
LRESULT EnableGroupView(BOOL fEnable);
```  
  
### <a name="parameters"></a>參數  
 `fEnable`  
 指出是否啟用 listview 控制項來群組顯示項目。 **TRUE**若要啟用群組;**FALSE**停用它。  
  
### <a name="return-value"></a>傳回值  
 會傳回下列值之一︰  
  
- **0**能夠顯示清單檢視項目，因為已啟用或停用群組。  
  
- **1**已成功變更控制項的狀態。  
  
- **-1**作業失敗。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LVM_ENABLEGROUPVIEW](http://msdn.microsoft.com/library/windows/desktop/bb774900)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-nameensurevisiblea--clistctrlensurevisible"></a><a name="ensurevisible"></a>CListCtrl::EnsureVisible  
 確保至少部分顯示清單檢視項目。  
  
```  
BOOL EnsureVisible(
    int nItem,  
    BOOL bPartialOK);
```  
  
### <a name="parameters"></a>參數  
 `nItem`  
 要顯示的清單檢視項目的索引。  
  
 `bPartialOK`  
 指定是否可以接受部分的可見性。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 必要時捲動清單檢視控制項。 如果`bPartialOK`參數為非零，則不捲動發生於項目是否有部分顯示。  
  
### <a name="example"></a>範例  
```cpp  
        // Ensure that the last item is visible.
        int nCount = m_myListCtrl.GetItemCount();
        if (nCount > 0)
            m_myListCtrl.EnsureVisible(nCount-1, FALSE);
```

  
##  <a name="a-namefinditema--clistctrlfinditem"></a><a name="finditem"></a>CListCtrl::FindItem  
 搜尋具有指定特性的清單檢視項目。  
  
```  
int FindItem(
    LVFINDINFO* pFindInfo,  
    int nStart = -1) const;  
```  
  
### <a name="parameters"></a>參數  
 `pFindInfo`  
 指標[LVFINDINFO](http://msdn.microsoft.com/library/windows/desktop/bb774745)結構，其中包含要搜尋項目的相關資訊。  
  
 `nStart`  
 若要開始，搜尋項目或是-1，從頭開始的索引。 在項目`nStart`如果排除搜尋`nStart`不等於-1。  
  
### <a name="return-value"></a>傳回值  
 如果成功的項目則為-1 則索引。  
  
### <a name="remarks"></a>備註  
 `pFindInfo`參數指向**LVFINDINFO**結構，其中包含用來搜尋清單檢視項目的資訊。  
  
### <a name="example"></a>範例  

```cpp  
        LVFINDINFO info;
        int nIndex;

        info.flags = LVFI_PARTIAL|LVFI_STRING;
        info.psz = _T("item");

        // Delete all of the items that begin with the string.
        while ((nIndex = m_myListCtrl.FindItem(&info)) != -1)
        {
            m_myListCtrl.DeleteItem(nIndex);
        }
```

  
##  <a name="a-namegetbkcolora--clistctrlgetbkcolor"></a><a name="getbkcolor"></a>CListCtrl::GetBkColor  
 擷取清單檢視控制項的背景色彩。  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 32 位元值，用來指定 RGB 色彩。  
  
### <a name="example"></a>範例  
  請參閱範例[CListCtrl::SetBkColor](#setbkcolor)。  
  
##  <a name="a-namegetbkimagea--clistctrlgetbkimage"></a><a name="getbkimage"></a>CListCtrl::GetBkImage  
 擷取目前的清單檢視控制項的背景影像。  
  
```  
BOOL GetBkImage(LVBKIMAGE* plvbkImage) const;  
```  
  
### <a name="parameters"></a>參數  
 `plvbkImage`  
 指標**LVBKIMAGE**結構，其中包含目前的背景影像的清單檢視。  
  
### <a name="return-value"></a>傳回值  
 傳回非零，如果成功或為零。  
  
### <a name="remarks"></a>備註  
 這個方法會實作 Win32 巨集的行為[ListView_GetBkImage](http://msdn.microsoft.com/library/windows/desktop/bb761246)所述，在[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  

```cpp  
        LVBKIMAGE bki;

        // If no background image is set for the list view control use
        // the Microsoft homepage image as the background image.
        if (m_myListCtrl.GetBkImage(&bki) && (bki.ulFlags == LVBKIF_SOURCE_NONE))
        {
            m_myListCtrl.SetBkImage(
                _T("http://www.microsoft.com/library/images/gifs/homepage/microsoft.gif"),
                TRUE);
        }
```

  
##  <a name="a-namegetcallbackmaska--clistctrlgetcallbackmask"></a><a name="getcallbackmask"></a>Clistctrl:: Getcallbackmask  
 擷取清單檢視控制項的回呼遮罩。  
  
```  
UINT GetCallbackMask() const;  
```  
  
### <a name="return-value"></a>傳回值  
 清單檢視控制項的回呼遮罩。  
  
### <a name="remarks"></a>備註  
 「 回呼項目 」 是清單檢視項目，應用程式，而不是控制項 — 儲存文字、 圖示或兩者。 雖然清單檢視控制項可以讓您儲存這些屬性，但是您可能想要使用回呼項目，如果您的應用程式已在維護其中有些資訊。 回呼遮罩可讓您指定的項目狀態位元會維護應用程式，並將其套用至整個控制項，而不是特定的項目。 回呼遮罩預設為零，表示控制項正在追蹤所有項目的狀態。 如果應用程式會使用回呼項目，或指定非零的回呼遮罩，它必須能夠提供隨選清單檢視項目屬性。  
  
### <a name="example"></a>範例  
  請參閱範例[clistctrl:: Setcallbackmask](#setcallbackmask)。  
  
##  <a name="a-namegetchecka--clistctrlgetcheck"></a><a name="getcheck"></a>CListCtrl::GetCheck  
 擷取目前的項目相關聯之狀態影像的顯示狀態。  
  
```  
BOOL GetCheck(int nItem) const;  
```  
  
### <a name="parameters"></a>參數  
 `nItem`  
 清單控制項項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 非零，如果已選取項目，否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式實作 Win32 巨集的行為[ListView_GetCheckState](http://msdn.microsoft.com/library/windows/desktop/bb761250)所述，在[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CListCtrl::SetCheck](#setcheck)。  
  
##  <a name="a-namegetcolumna--clistctrlgetcolumn"></a><a name="getcolumn"></a>CListCtrl::GetColumn  
 擷取清單檢視控制項的資料行的屬性。  
  
```  
BOOL GetColumn(
    int nCol,  
    LVCOLUMN* pColumn) const;  
```  
  
### <a name="parameters"></a>參數  
 `nCol`  
 要擷取其屬性的資料行的索引。  
  
 `pColumn`  
 位址[LVCOLUMN](http://msdn.microsoft.com/library/windows/desktop/bb774743)結構，指定要擷取資訊或接收的資料行資訊。 **遮罩**成員會指定哪個資料行屬性來擷取。 如果**遮罩**成員指定`LVCF_TEXT`值**pszText**成員必須包含接收項目文字的緩衝區的位址和**cchTextMax**成員必須指定緩衝區的大小。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 **LVCOLUMN**結構包含在報表檢視資料行的相關資訊。  
  
### <a name="example"></a>範例  

```cpp  
        LVCOLUMN col;

        col.mask = LVCF_WIDTH;

        // Double the column width of the first column.
        if (m_myListCtrl.GetColumn(0, &col))
        {
            col.cx *= 2;
            m_myListCtrl.SetColumn(0, &col);
        }
```

  
##  <a name="a-namegetcolumnorderarraya--clistctrlgetcolumnorderarray"></a><a name="getcolumnorderarray"></a>CListCtrl::GetColumnOrderArray  
 擷取清單檢視控制項的資料行順序 （由左到右）。  
  
```  
BOOL GetColumnOrderArray(
    LPINT piArray,  
    int iCount = -1);
```  
  
### <a name="parameters"></a>參數  
 `piArray`  
 將包含清單檢視控制項中的資料行的索引值的緩衝區指標。 緩衝區必須夠大，無法包含在清單檢視控制項中的資料行總數。  
  
 `iCount`  
 在清單檢視控制項中的資料行數目。 如果這個參數是-1，架構會自動擷取的資料行數目。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 此成員函式實作 Win32 巨集的行為[ListView_GetColumnOrderArray](http://msdn.microsoft.com/library/windows/desktop/bb761254)所述，在[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  

```cpp  
        // Reverse the order of the columns in the list view control
        // (i.e. make the first column the last, the last column
        // the first, and so on...).
        CHeaderCtrl* pHeaderCtrl = m_myListCtrl.GetHeaderCtrl();

        if (pHeaderCtrl != NULL)
        {
            int  nColumnCount = pHeaderCtrl->GetItemCount();
            LPINT pnOrder = (LPINT) malloc(nColumnCount*sizeof(int));
            ASSERT(pnOrder != NULL);
m_myListCtrl.GetColumnOrderArray(pnOrder, nColumnCount);

            int i, j, nTemp;
            for (i = 0, j = nColumnCount-1; i < j; i++, j--)
            {
                nTemp = pnOrder[i];
                pnOrder[i] = pnOrder[j];
                pnOrder[j] = nTemp;
            }

            m_myListCtrl.SetColumnOrderArray(nColumnCount, pnOrder);
            free(pnOrder);
        }
```

  
##  <a name="a-namegetcolumnwidtha--clistctrlgetcolumnwidth"></a><a name="getcolumnwidth"></a>CListCtrl::GetColumnWidth  
 擷取報表的檢視或清單檢視中的資料行的寬度。  
  
```  
int GetColumnWidth(int nCol) const;  
```  
  
### <a name="parameters"></a>參數  
 `nCol`  
 指定資料行寬度是要擷取的索引。  
  
### <a name="return-value"></a>傳回值  
 像素為單位指定的資料行的寬度， `nCol`。  
  
### <a name="example"></a>範例  

```cpp  
        // Increase the column width of the second column by 20.
        int nWidth = m_myListCtrl.GetColumnWidth(1);
        m_myListCtrl.SetColumnWidth(1, 20 + nWidth);
```

  
##  <a name="a-namegetcountperpagea--clistctrlgetcountperpage"></a><a name="getcountperpage"></a>CListCtrl::GetCountPerPage  
 計算可容納垂直的清單檢視控制項的可見區域，在清單檢視或報表檢視中的項目數目。  
  
```  
int GetCountPerPage() const;  
```  
  
### <a name="return-value"></a>傳回值  
 可以納入垂直清單檢視控制項的可見區域，在 [清單] 檢視或報表檢視中的項目數目。  
  
### <a name="example"></a>範例  
  請參閱範例[CListCtrl::GetTopIndex](#gettopindex)。  
  
##  <a name="a-namegeteditcontrola--clistctrlgeteditcontrol"></a><a name="geteditcontrol"></a>CListCtrl::GetEditControl  
 擷取用來編輯清單檢視項目的文字編輯控制項的控制代碼。  
  
```  
CEdit* GetEditControl() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，指標[CEdit](cedit-class.md)物件，用來編輯項目文字; 否則為**NULL**。  
  
### <a name="example"></a>範例  

```cpp  
        // The string replacing the text in the edit control.
        LPCTSTR lpszmyString = _T("custom label!");

        // If possible, replace the text in the label edit control.
        CEdit* pEdit = m_myListCtrl.GetEditControl();

        if (pEdit != NULL)
        {
            pEdit->SetWindowText(lpszmyString);
        }
```

  
##  <a name="a-namegetemptytexta--clistctrlgetemptytext"></a><a name="getemptytext"></a>CListCtrl::GetEmptyText  
 擷取要顯示目前的清單檢視控制項為空字串。  
  
```  
CString GetEmptyText() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A [CString](../../atl-mfc-shared/reference/cstringt-class.md) ，其中包含要顯示如果控制項是空的文字。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[LVM_GETEMPTYTEXT](http://msdn.microsoft.com/library/windows/desktop/bb774921)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namegetextendedstylea--clistctrlgetextendedstyle"></a><a name="getextendedstyle"></a>CListCtrl::GetExtendedStyle  
 擷取清單檢視控制項的目前延伸的樣式。  
  
```  
DWORD GetExtendedStyle();
```  
  
### <a name="return-value"></a>傳回值  
 目前使用的清單中的延伸樣式的組合檢視控制項。 描述一種延伸樣式清單，請參閱[延伸清單檢視樣式](http://msdn.microsoft.com/library/windows/desktop/bb774732)中的主題[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="remarks"></a>備註  
 此成員函式實作 Win32 巨集的行為[ListView_GetExtendedListViewStyle](http://msdn.microsoft.com/library/windows/desktop/bb761264)所述，在[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CListCtrl::SetExtendedStyle](#setextendedstyle)。  
  
##  <a name="a-namegetfirstselecteditempositiona--clistctrlgetfirstselecteditemposition"></a><a name="getfirstselecteditemposition"></a>CListCtrl::GetFirstSelectedItemPosition  
 取得清單檢視控制項中的第一個選取的項目位置。  
  
```  
POSITION GetFirstSelectedItemPosition() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A**位置**值，可用於反覆項目或物件指標擷取。**NULL**如果未不選取任何項目。  
  
### <a name="example"></a>範例  
 下列程式碼範例示範此函式的用法。  
  

```cpp  
        POSITION pos = m_myListCtrl.GetFirstSelectedItemPosition();
        if (pos == NULL)
        {
            TRACE(_T("No items were selected!\n"));
        }
        else
        {
            while (pos)
            {
                int nItem = m_myListCtrl.GetNextSelectedItem(pos);
                TRACE(_T("Item %d was selected!\n"), nItem);
                // you could do your own processing on nItem here
            }
        }
```

  
##  <a name="a-namegetfocusedgroupa--clistctrlgetfocusedgroup"></a><a name="getfocusedgroup"></a>CListCtrl::GetFocusedGroup  
 擷取目前的清單檢視控制項中具有鍵盤焦點的群組。  
  
```  
int GetFocusedGroup() const;  
```  
  
### <a name="return-value"></a>傳回值  
 狀態是的群組的索引`LVGS_FOCUSED`，如果沒有這類群組，則為-1。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[LVM_GETFOCUSEDGROUP](http://msdn.microsoft.com/library/windows/desktop/bb774925)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。 如需詳細資訊，請參閱`LVGS_FOCUSED`值`state`成員[LVGROUP](http://msdn.microsoft.com/library/windows/desktop/bb774769)結構。  
  
##  <a name="a-namegetgroupcounta--clistctrlgetgroupcount"></a><a name="getgroupcount"></a>CListCtrl::GetGroupCount  
 擷取目前的清單檢視控制項中的群組數目。  
  
```  
int GetGroupCount()const;  
```  
  
### <a name="return-value"></a>傳回值  
 在清單檢視控制項中的群組數目。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[LVM_GETGROUPCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb774931)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]-->。  
  
##  <a name="a-namegetgroupinfoa--clistctrlgetgroupinfo"></a><a name="getgroupinfo"></a>CListCtrl::GetGroupInfo  
 取得指定的群組清單檢視控制項的資訊。  
  
```  
int GetGroupInfo(
    int iGroupId,  
    PLVGROUP pgrp) const;  
```  
  
### <a name="parameters"></a>參數  
 `iGroupId`  
 要擷取其資訊之群組的識別碼。  
  
 `pgrp`  
 指標[LVGROUP](http://msdn.microsoft.com/library/windows/desktop/bb774769)包含指定之群組的詳細資訊。  
  
### <a name="return-value"></a>傳回值  
 否則會傳回群組中，如果成功，則為-1 的識別碼。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LVM_GETGROUPINFO](http://msdn.microsoft.com/library/windows/desktop/bb774932)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namegetgroupinfobyindexa--clistctrlgetgroupinfobyindex"></a><a name="getgroupinfobyindex"></a>CListCtrl::GetGroupInfoByIndex  
 擷取目前的清單檢視控制項中的指定群組的相關資訊。  
  
```  
BOOL GetGroupInfoByIndex(
    int iIndex,   
    PLVGROUP pGroup) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `iIndex`|群組的以零為起始的索引。|  
|[輸出] `pGroup`|指標[LVGROUP](http://msdn.microsoft.com/library/windows/desktop/bb774769)接收所指定之群組的相關資訊的結構`iIndex`參數。<br /><br /> 呼叫端會負責初始化的成員[LVGROUP](http://msdn.microsoft.com/library/windows/desktop/bb774769)結構。 設定`cbSize`成員的結構大小的旗標`mask`成員來指定要擷取之資訊。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[LVM_GETGROUPINFOBYINDEX](http://msdn.microsoft.com/library/windows/desktop/bb774933)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]-->。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數， `m_listCtrl`，也就是用來存取目前的清單檢視控制項。 下一個範例中會使用此變數。  

```cpp  
public:
    // Variable used to access the list control.
    CListCtrl m_listCtrl; 
```

  
### <a name="example"></a>範例  
 下列程式碼範例示範`GetGroupInfoByIndex`方法。 在先前章節中的這段程式碼範例我們建立的清單檢視控制項，會顯示兩個資料行標題為"ClientID"和 「 成績 」，在報表檢視。 如果存在這類群組，下列程式碼範例會擷取其索引為 0，群組的相關資訊。    
```cpp  
    // GetGroupInfoByIndex
    const int GROUP_HEADER_BUFFER_SIZE = 40;

// Initialize the structure 
    LVGROUP gInfo = {0};
    gInfo.cbSize = sizeof(LVGROUP);
    wchar_t wstrHeadGet[GROUP_HEADER_BUFFER_SIZE] = {0};
    gInfo.cchHeader = GROUP_HEADER_BUFFER_SIZE;
    gInfo.pszHeader = wstrHeadGet;
    gInfo.mask = (LVGF_ALIGN | LVGF_STATE | LVGF_HEADER | LVGF_GROUPID);
    gInfo.state = LVGS_NORMAL;
    gInfo.uAlign  = LVGA_HEADER_LEFT;

    BOOL bRet = m_listCtrl.GetGroupInfoByIndex( 0, &gInfo );
    if (bRet == TRUE) {
        CString strHeader = CString( gInfo.pszHeader );
        CString str;
        str.Format(_T("Header: '%s'"), strHeader);
        AfxMessageBox(str, MB_ICONINFORMATION);
    }
    else
    {
        AfxMessageBox(_T("No group information was retrieved."));
    }
```

  
##  <a name="a-namegetgroupmetricsa--clistctrlgetgroupmetrics"></a><a name="getgroupmetrics"></a>CListCtrl::GetGroupMetrics  
 擷取群組的度量。  
  
```  
void GetGroupMetrics(PLVGROUPMETRICS pGroupMetrics) const;  
```  
  
### <a name="parameters"></a>參數  
 `pGroupMetrics`  
 指標[LVGROUPMETRICS](http://msdn.microsoft.com/library/windows/desktop/bb774752)包含群組度量資訊。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LVM_GETGROUPMETRICS](http://msdn.microsoft.com/library/windows/desktop/bb774934)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namegetgrouprecta--clistctrlgetgrouprect"></a><a name="getgrouprect"></a>CListCtrl::GetGroupRect  
 擷取目前的清單檢視控制項中指定之群組的周框。  
  
```  
BOOL GetGroupRect(
    int iGroupId,   
    LPRECT lpRect,   
    int iCoords = LVGGR_GROUP) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `iGroupId`|指定群組。|  
|[in、out] `lpRect`|指標[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構。 如果此方法成功，結構會接收群組所指定的矩形座標`iGroupId`。|  
|[in] `iCoords`|指定要擷取的矩形座標。 使用下列值之一︰<br /><br /> - `LVGGR_GROUP`-整個展開群組的 （預設值） 座標。<br />- `LVGGR_HEADER`-只有標頭 （摺疊群組） 的座標。<br />- `LVGGR_SUBSETLINK`座標只子集連結 （標記子集）。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 呼叫端會負責配置[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)指向結構`pRect`參數。  
  
 這個方法會傳送[LVM_GETGROUPRECT](http://msdn.microsoft.com/library/windows/desktop/bb774935)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數， `m_listCtrl`，也就是用來存取目前的清單檢視控制項。 下一個範例中會使用此變數。    
```cpp  
public:
    // Variable used to access the list control.
    CListCtrl m_listCtrl; 
```

  
### <a name="example"></a>範例  
 下列程式碼範例示範`GetGroupRect`方法。 在先前章節中的這個程式碼範例，我們會建立顯示標題為"ClientID"和 「 成績 」，在報表檢視中的兩個資料行的清單檢視控制項。 下列程式碼範例 3D 周圍繪製矩形的群組，其索引為 0，如果存在這類群組。    
  
```cpp  
    // GetGroupRect

    // Get the graphics rectangle that surrounds group 0.
    CRect rect;
    BOOL bRet = m_listCtrl.GetGroupRect( 0, &rect, LVGGR_GROUP); 
    // Draw a blue rectangle around group 0.
    if (bRet == TRUE) {
        m_listCtrl.GetDC()->Draw3dRect( &rect, RGB(0, 0, 255), RGB(0, 0, 255));
    }
    else {
        AfxMessageBox(_T("No group information was retrieved."), MB_ICONINFORMATION);
    }
```

  
##  <a name="a-namegetgroupstatea--clistctrlgetgroupstate"></a><a name="getgroupstate"></a>CListCtrl::GetGroupState  
 擷取目前的清單檢視控制項中指定之群組的狀態。  
  
```  
UINT GetGroupState(
    int iGroupId,   
    DWORD dwMask) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `iGroupId`|群組的以零為起始的索引。|  
|[in] `dwMask`|遮罩，指定狀態来擷取的值為指定的群組。 如需詳細資訊，請參閱`mask`成員[LVGROUP](http://msdn.microsoft.com/library/windows/desktop/bb774769)結構。|  
  
### <a name="return-value"></a>傳回值  
 指定的群組，或 0，如果找不到群組要求的狀態。  
  
### <a name="remarks"></a>備註  
 傳回值是位元的 AND 運算的結果上`dwMask`參數和值的`state`成員[LVGROUP](http://msdn.microsoft.com/library/windows/desktop/bb774769)結構，表示目前的清單檢視控制項。  
  
 這個方法會傳送[LVM_GETGROUPSTATE](http://msdn.microsoft.com/library/windows/desktop/bb774936)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。 如需詳細資訊，請參閱[ListView_GetGroupState](http://msdn.microsoft.com/library/windows/desktop/bb761288)巨集。  
  
##  <a name="a-namegetheaderctrla--clistctrlgetheaderctrl"></a><a name="getheaderctrl"></a>CListCtrl::GetHeaderCtrl  
 擷取清單檢視控制項的標題控制項。  
  
```  
CHeaderCtrl* GetHeaderCtrl();
```  
  
### <a name="return-value"></a>傳回值  
 使用清單檢視控制項之標頭控制項的指標。  
  
### <a name="remarks"></a>備註  
 此成員函式實作 Win32 巨集的行為[ListView_GetHeader](http://msdn.microsoft.com/library/windows/desktop/bb761290)所述，在[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CListCtrl::GetColumnOrderArray](#getcolumnorderarray)。  
  
##  <a name="a-namegethotcursora--clistctrlgethotcursor"></a><a name="gethotcursor"></a>CListCtrl::GetHotCursor  
 擷取清單檢視控制項的熱追蹤啟用時，使用資料指標。  
  
```  
HCURSOR GetHotCursor();
```  
  
### <a name="return-value"></a>傳回值  
 正在使用清單檢視控制項的目前最忙碌的游標資源控制代碼。  
  
### <a name="remarks"></a>備註  
 此成員函式實作 Win32 巨集的行為[ListView_GetHotCursor](http://msdn.microsoft.com/library/windows/desktop/bb761292)所述，在[!INCLUDE[winSDK](./includes/winsdk_md.md)]。 游標通過任何清單檢視項目時，會出現 熱游標，啟用動態顯示選取範圍時，才可見。 藉由設定啟用暫留選取**LVS_EX_TRACKSELECT**延伸樣式。  
  
### <a name="example"></a>範例    
  
```cpp  
        // Set the hot cursor to be the system app starting cursor.
        HCURSOR hCursor = ::LoadCursor(NULL, IDC_APPSTARTING);
        m_myListCtrl.SetHotCursor(hCursor);
        ASSERT(m_myListCtrl.GetHotCursor() == hCursor);
```

  
##  <a name="a-namegethotitema--clistctrlgethotitem"></a><a name="gethotitem"></a>CListCtrl::GetHotItem  
 擷取目前游標下方的清單檢視項目。  
  
```  
int GetHotItem();
```  
  
### <a name="return-value"></a>傳回值  
 清單檢視控制項的目前作用的項目索引。  
  
### <a name="remarks"></a>備註  
 此成員函式實作 Win32 巨集的行為[ListView_GetHotItem](http://msdn.microsoft.com/library/windows/desktop/bb761294)所述，在[!INCLUDE[winSDK](./includes/winsdk_md.md)]。 熱門項目定義為已啟用目前選取的項目時熱追蹤 （和浮動選取）。  
  
 如果使用者停留在清單檢視項目時，已啟用熱追蹤，項目標籤會自動反白顯示而不使用滑鼠按鈕。  
  
### <a name="example"></a>範例    
  
```cpp  
    // Set the hot item to the first item only if no other item is 
    // highlighted.
    if (m_myListCtrl.GetHotItem() == -1)
        m_myListCtrl.SetHotItem(0);
```

  
##  <a name="a-namegethovertimea--clistctrlgethovertime"></a><a name="gethovertime"></a>CListCtrl::GetHoverTime  
 擷取清單檢視控制項的滑鼠停留時間。  
  
```  
DWORD GetHoverTime() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回延遲，以毫秒為單位，將滑鼠游標必須停留的項目之前加以選取。 如果傳回值為-1，暫留時間是預設的滑鼠停留時間。  
  
### <a name="remarks"></a>備註  
 此成員函式實作 Win32 巨集的行為[ListView_GetHoverTime](http://msdn.microsoft.com/library/windows/desktop/bb761296)所述，在[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例    
  
```cpp  
        // If the hover time is the default set to 1 sec.
        DWORD dwTime = m_myListCtrl.GetHoverTime();
        if (dwTime == -1)
            m_myListCtrl.SetHoverTime(1000);
```

  
##  <a name="a-namegetimagelista--clistctrlgetimagelist"></a><a name="getimagelist"></a>CListCtrl::GetImageList  
 擷取用於繪圖的清單檢視項目的影像清單控制代碼。  
  
```  
CImageList* GetImageList(int nImageList) const;  
```  
  
### <a name="parameters"></a>參數  
 `nImageList`  
 值，指定要擷取的映像清單。 它可以是下列值之一︰  
  
- `LVSIL_NORMAL`大圖示的影像清單。  
  
- `LVSIL_SMALL`小圖示的影像清單。  
  
- `LVSIL_STATE`狀態影像的影像清單。  
  
### <a name="return-value"></a>傳回值  
 用於繪製清單檢視項目影像清單的指標。  
  
### <a name="example"></a>範例    
  
```cpp  
        ASSERT(m_myListCtrl.GetImageList(LVSIL_NORMAL) == NULL);
m_myListCtrl.SetImageList(&m_lcImageList, LVSIL_NORMAL);
        ASSERT(m_myListCtrl.GetImageList(LVSIL_NORMAL) == &m_lcImageList);
```

  
##  <a name="a-namegetinsertmarka--clistctrlgetinsertmark"></a><a name="getinsertmark"></a>CListCtrl::GetInsertMark  
 擷取目前的插入標記的位置。  
  
```  
BOOL GetInsertMark(LPLVINSERTMARK lvim) const;  
```  
  
### <a name="parameters"></a>參數  
 `lvim`  
 指標[LVINSERTMARK](http://msdn.microsoft.com/library/windows/desktop/bb774758)結構，其中包含插入標記的資訊。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**如果成功，或**FALSE**否則。 **FALSE**如果傳回的大小以`cbSize`成員**LVINSERTMARK**結構不等於結構的實際大小。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LVM_GETINSERTMARK](http://msdn.microsoft.com/library/windows/desktop/bb774945)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namegetinsertmarkcolora--clistctrlgetinsertmarkcolor"></a><a name="getinsertmarkcolor"></a>CListCtrl::GetInsertMarkColor  
 擷取目前的插入標記的色彩。  
  
```  
COLORREF GetInsertMarkColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)結構，其中包含插入點的色彩。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LVM_GETINSERTMARKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb774947)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namegetinsertmarkrecta--clistctrlgetinsertmarkrect"></a><a name="getinsertmarkrect"></a>CListCtrl::GetInsertMarkRect  
 擷取範圍的插入點的矩形。  
  
```  
int GetInsertMarkRect(LPRECT pRect) const;  
```  
  
### <a name="parameters"></a>參數  
 `pRect`  
 指標`RECT`結構，其中包含限定的插入點的矩形的座標。  
  
### <a name="return-value"></a>傳回值  
 會傳回下列值之一︰  
  
- **0**找不到插入點。  
  
- **1**找到的插入點。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LVM_GETINSERTMARKRECT](http://msdn.microsoft.com/library/windows/desktop/bb774949)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namegetitema--clistctrlgetitem"></a><a name="getitem"></a>Clistctrl:: Getitem  
 擷取部分或所有的清單檢視項目的屬性。  
  
```  
BOOL GetItem(LVITEM* pItem) const;  
```  
  
### <a name="parameters"></a>參數  
 `pItem`  
 指標[LVITEM](http://msdn.microsoft.com/library/windows/desktop/bb774760)收到的項目屬性的結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 **LVITEM**結構會指定或接收的清單檢視項目屬性。  
  
##  <a name="a-namegetitemcounta--clistctrlgetitemcount"></a><a name="getitemcount"></a>CListCtrl::GetItemCount  
 擷取清單檢視控制項中的項目數。  
  
```  
int GetItemCount() const; 
```  
  
### <a name="return-value"></a>傳回值  
 在清單檢視控制項中的項目數目。  
  
### <a name="example"></a>範例  
  請參閱範例[CListCtrl::DeleteItem](#deleteitem)。  
  
##  <a name="a-namegetitemdataa--clistctrlgetitemdata"></a><a name="getitemdata"></a>CListCtrl::GetItemData  
 擷取所指定的項目相關聯的 32 位元應用程式特定值`nItem`。  
  
```  
DWORD_PTR GetItemData(int nItem) const; 
```  
  
### <a name="parameters"></a>參數  
 `nItem`  
 資料都要擷取之清單項目的索引。  
  
### <a name="return-value"></a>傳回值  
 32 位元應用程式特定值，指定的項目相關聯。  
  
### <a name="remarks"></a>備註  
 這個值是**lParam**成員[LVITEM](http://msdn.microsoft.com/library/windows/desktop/bb774760)結構中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]  
  
### <a name="example"></a>範例  

```cpp  
    // If any item's data is equal to zero then reset it to -1.
    for (int i=0; i < m_myListCtrl.GetItemCount(); i++)
    {
        if (m_myListCtrl.GetItemData(i) == 0)
        {
            m_myListCtrl.SetItemData(i, (DWORD) -1);
        }
    }
```

  
##  <a name="a-namegetitemindexrecta--clistctrlgetitemindexrect"></a><a name="getitemindexrect"></a>CListCtrl::GetItemIndexRect  
 擷取週框的全部或部分的目前清單檢視控制項中的子項目。  
  
```  
BOOL GetItemIndexRect(
    PLVITEMINDEX pItemIndex,   
    int iColumn,   
    int rectType,   
    LPRECT pRect) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `pItemIndex`|指標[LVITEMINDEX](http://msdn.microsoft.com/library/windows/desktop/bb774762)子項目的父項目的結構。<br /><br /> 呼叫端會負責配置和設定的成員[LVITEMINDEX](http://msdn.microsoft.com/library/windows/desktop/bb774762)結構。 此參數不得為`NULL`。|  
|[in] `iColumn`|在控制項中的資料行的以零為起始的索引。|  
|[in] `rectType`|這擷取週框的清單檢視子項目部分。 指定下列其中一個值：<br /><br /> `LVIR_BOUNDS`-傳回整個子項目，包括圖示和標籤的周框矩形。<br /><br /> `LVIR_ICON`-傳回，這個周框的圖示或小圖示的子項目。<br /><br /> `LVIR_LABEL`-傳回子項目文字的週框。|  
|[輸出] `pRect`|指標[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)接收子項目的周框矩形的相關資訊的結構。<br /><br /> 呼叫端會負責配置[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構。 此參數不得為`NULL`。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[LVM_GETITEMINDEXRECT](http://msdn.microsoft.com/library/windows/desktop/bb761046)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。 如需詳細資訊，請參閱[ListView_GetItemIndexRect 巨集](http://msdn.microsoft.com/library/windows/desktop/bb774959)。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數， `m_listCtrl`，也就是用來存取目前的清單檢視控制項。 下一個範例中會使用此變數。    
  
```cpp  
public:
    // Variable used to access the list control.
    CListCtrl m_listCtrl; 
```

  
### <a name="example"></a>範例  
 下列程式碼範例示範`GetGroupRect`方法。 之前輸入這個程式碼範例我們建立的清單檢視控制項，會顯示兩個資料行標題為"ClientID"和 「 成績 」，在報表檢視。 下列程式碼範例 3D 周圍繪製矩形的第二個的子項目這兩個資料行中。    
  
```cpp  
    // GetItemIndexRect
    // Get the rectangle that bounds the second item in the first group.
    LVITEMINDEX lvItemIndex;
    lvItemIndex.iGroup = 0;
    lvItemIndex.iItem = 1;
    CRect rect;
    BOOL bRet = m_listCtrl.GetItemIndexRect(
        &lvItemIndex, 0, LVIR_BOUNDS, &rect);

    // Draw a red rectangle around the item.
    m_listCtrl.GetDC()->Draw3dRect( &rect, RGB(255, 0, 0), RGB(255, 0, 0) );
```

  
##  <a name="a-namegetitempositiona--clistctrlgetitemposition"></a><a name="getitemposition"></a>CListCtrl::GetItemPosition  
 擷取清單檢視項目的位置。  
  
```  
BOOL GetItemPosition(
    int nItem,  
    LPPOINT lpPoint) const;  
```  
  
### <a name="parameters"></a>參數  
 `nItem`  
 要擷取其位置的項目索引。  
  
 `lpPoint`  
 位址[點](http://msdn.microsoft.com/library/windows/desktop/dd162805)接收位置的項目左上角的結構檢視中協調。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="example"></a>範例    
  
```cpp  
        POINT pt;

        // Move all items in the list control 100 pixels to the right.
        UINT i, nCount = m_myListCtrl.GetItemCount();

        for (i=0; i < nCount; i++)
        {
            m_myListCtrl.GetItemPosition(i, &pt);
            pt.x += 100;
            m_myListCtrl.SetItemPosition(i, pt);
        }   
```

  
##  <a name="a-namegetitemrecta--clistctrlgetitemrect"></a><a name="getitemrect"></a>CListCtrl::GetItemRect  
 擷取週框的全部或部份目前檢視中的項目。  
  
```  
BOOL GetItemRect(
    int nItem,  
    LPRECT lpRect,  
    UINT nCode) const;  
```  
  
### <a name="parameters"></a>參數  
 `nItem`  
 要擷取其位置的項目索引。  
  
 `lpRect`  
 位址[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)接收，這個周框的結構。  
  
 `nCode`  
 清單檢視項目，為其擷取週框的部分。 它可以是下列值之一︰  
  
- `LVIR_BOUNDS`傳回整個項目，包括圖示和標籤的周框矩形。  
  
- `LVIR_ICON`傳回圖示或小圖示的周框矩形。  
  
- `LVIR_LABEL`傳回項目文字的週框。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="example"></a>範例    
  
```cpp  
// OnClick is the handler for the NM_CLICK notification
void CListCtrlDlg::OnClick(NMHDR* pNMHDR, LRESULT* pResult)
{
    UNREFERENCED_PARAMETER(pResult);
LPNMITEMACTIVATE pia = (LPNMITEMACTIVATE)pNMHDR;

    // Get the current mouse location and convert it to client
    // coordinates.
    CPoint pos( ::GetMessagePos() ); 
    ScreenToClient(&pos);

    // Get indexes of the first and last visible items in 
    // the listview control.
    int index = m_myListCtrl.GetTopIndex();
    int last_visible_index = index + m_myListCtrl.GetCountPerPage();
    if (last_visible_index > m_myListCtrl.GetItemCount())
        last_visible_index = m_myListCtrl.GetItemCount();

    // Loop until number visible items has been reached.
    while (index <= last_visible_index)
    {
        // Get the bounding rectangle of an item. If the mouse
        // location is within the bounding rectangle of the item,
        // you know you have found the item that was being clicked.
        CRect r;
        m_myListCtrl.GetItemRect(index, &r, LVIR_BOUNDS);
        if (r.PtInRect(pia->ptAction))
        {
            UINT flag = LVIS_SELECTED | LVIS_FOCUSED;
            m_myListCtrl.SetItemState(index, flag, flag);
            break;
        }

        // Get the next item in listview control.
        index++;
    }
}
```

  
##  <a name="a-namegetitemspacinga--clistctrlgetitemspacing"></a><a name="getitemspacing"></a>CListCtrl::GetItemSpacing  
 計算目前的清單檢視控制項中的項目之間的間距。  
  
```  
BOOL GetItemSpacing(
    BOOL fSmall,   
    int* pnHorzSpacing,   
    int* pnVertSpacing) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `fSmall`|要擷取的項目間距的檢視。 指定`true`小圖示檢視或`false`圖示檢視。|  
|[輸出] `pnHorzSpacing`|包含項目之間的水平間距。|  
|[輸出] `pnVertSpacing`|包含項目之間的垂直間距。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[LVM_GETITEMSPACING](http://msdn.microsoft.com/library/windows/desktop/bb761051)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namegetitemstatea--clistctrlgetitemstate"></a><a name="getitemstate"></a>CListCtrl::GetItemState  
 擷取清單檢視項目的狀態。  
  
```  
UINT GetItemState(
    int nItem,  
    UINT nMask) const;  
```  
  
### <a name="parameters"></a>參數  
 `nItem`  
 要擷取其狀態的項目索引。  
  
 `nMask`  
 指定要傳回哪一個項目的狀態旗標的遮罩。  
  
### <a name="return-value"></a>傳回值  
 狀態旗標，指定之清單檢視項目。  
  
### <a name="remarks"></a>備註  
 所指定項目的狀態**狀態**成員[LVITEM](http://msdn.microsoft.com/library/windows/desktop/bb774760)結構中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。 當您指定或變更項目的狀態**stateMask**成員會指定您想要變更的狀態位元。  
  
### <a name="example"></a>範例  
  請參閱範例[CListCtrl::GetTopIndex](#gettopindex)。  
  
##  <a name="a-namegetitemtexta--clistctrlgetitemtext"></a><a name="getitemtext"></a>CListCtrl::GetItemText  
 擷取清單檢視項目或子項目的文字。  
  
```  
int GetItemText(
    int nItem,  
    int nSubItem,  
    LPTSTR lpszText,  
    int nLen) const; 
 
CString GetItemText(
    int nItem,  
    int nSubItem) const;  
```  
  
### <a name="parameters"></a>參數  
 `nItem`  
 要擷取其文字的項目索引。  
  
 `nSubItem`  
 指定的文字是要擷取子項目。  
  
 `lpszText`  
 要接收的項目文字的字串指標。  
  
 `nLen`  
 所指向的緩衝區長度`lpszText`。  
  
### <a name="return-value"></a>傳回值  
 傳回的版本`int`傳回擷取字串長度。  
  
 傳回的版本`CString`傳回項目文字。  
  
### <a name="remarks"></a>備註  
 如果`nSubItem`為零，此函式會擷取項目標籤; 如果`nSubItem`為非零值，它會擷取子項目的文字。 如需子項目的引數的詳細資訊，請參閱討論[LVITEM](http://msdn.microsoft.com/library/windows/desktop/bb774760)結構[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namegetnextitema--clistctrlgetnextitem"></a><a name="getnextitem"></a>CListCtrl::GetNextItem  
 搜尋清單檢視項目具有指定的屬性，而且，與指定的項目之指定關聯性。  
  
```  
int GetNextItem(
    int nItem,  
    int nFlags) const;  
```  
  
### <a name="parameters"></a>參數  
 `nItem`  
 若要開始使用，搜尋項目或-1，若要尋找符合指定的旗標的第一個項目索引。 在搜尋中排除指定的項目本身。  
  
 `nFlags`  
 幾何關聯至指定的項目，以及所要求項目的狀態要求的項目。 幾何關聯可以是下列值之一︰  
  
- `LVNI_ABOVE`搜尋指定的項目上方的項目。  
  
- `LVNI_ALL`搜尋索引 （預設值） 的後續項目。  
  
- `LVNI_BELOW`搜尋指定的項目底下的項目。  
  
- `LVNI_TOLEFT`搜尋指定的項目左邊的項目。  
  
- `LVNI_TORIGHT`搜尋指定的項目右邊的項目。  
  
 這個狀態可以是零，或者它可以是下列其中一個或多個這些值︰  
  
- `LVNI_DROPHILITED`項目有`LVIS_DROPHILITED`狀態設定旗標。  
  
- `LVNI_FOCUSED`項目有`LVIS_FOCUSED`狀態設定旗標。  
  
- `LVNI_SELECTED`項目有`LVIS_SELECTED`狀態設定旗標。  
  
 如果項目未包含所有指定的狀態旗標設定，搜尋會繼續執行下一個項目。  
  
### <a name="return-value"></a>傳回值  
 下一個項目，如果成功，否則為-1 的索引。  
  
##  <a name="a-namegetnextitemindexa--clistctrlgetnextitemindex"></a><a name="getnextitemindex"></a>CListCtrl::GetNextItemIndex  
 擷取具有指定的屬性集的目前清單檢視控制項中項目的索引。  
  
```  
BOOL GetNextItemIndex(
    PLVITEMINDEX pItemIndex,   
    int nFlags) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in、out] `pItemIndex`|指標[LVITEMINDEX](http://msdn.microsoft.com/library/windows/desktop/bb774762)該結構描述項目開始搜尋，或是-1，尋找符合中的旗標的第一個項目`nFlags`參數。<br /><br /> 如果此方法成功，`LVITEMINDEX`結構描述搜尋找到的項目。|  
|[in] `nFlags`|位元組合 (OR) 旗標，指定如何執行搜尋。<br /><br /> 搜尋可能取決於索引、 狀態或外觀的目標項目，或以指定目標項目的實體位置，相對於項目`pItemIndex`參數。 如需詳細資訊，請參閱`flags`中的參數[LVM_GETNEXTITEMINDEX](http://msdn.microsoft.com/library/windows/desktop/bb761059)訊息。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 呼叫端會負責配置和設定的成員`LVITEMINDEX`指向結構`pItemIndex`參數。  
  
 這個方法會傳送[LVM_GETNEXTITEMINDEX](http://msdn.microsoft.com/library/windows/desktop/bb761059)訊息，說明 Windows SDK 中。  
  
##  <a name="a-namegetnextselecteditema--clistctrlgetnextselecteditem"></a><a name="getnextselecteditem"></a>CListCtrl::GetNextSelectedItem  
 取得索引所識別之清單項目的`pos`，然後設定*pos*至**位置**值。  
  
```  
int GetNextSelectedItem(POSITION& pos) const;  
```  
  
### <a name="parameters"></a>參數  
 `pos`  
 參考**位置**先前呼叫所傳回的值`GetNextSelectedItem`或`GetFirstSelectedItemPosition`。 這個呼叫是下一個位置來更新此值。  
  
### <a name="return-value"></a>傳回值  
 清單項目所識別的索引`pos`。  
  
### <a name="remarks"></a>備註  
 您可以使用`GetNextSelectedItem`向前反覆項目迴圈，如果您建立的初始位置，藉由呼叫`GetFirstSelectedItemPosition`。  
  
 您必須確定您**位置**值無效。 如果它是無效的 Mfc 程式庫的偵錯版本會判斷提示。  
  
### <a name="example"></a>範例  
 下列程式碼範例示範此函式的用法。    
  
```cpp  
        POSITION pos = m_myListCtrl.GetFirstSelectedItemPosition();
        if (pos == NULL)
        {
            TRACE(_T("No items were selected!\n"));
        }
        else
        {
            while (pos)
            {
                int nItem = m_myListCtrl.GetNextSelectedItem(pos);
                TRACE(_T("Item %d was selected!\n"), nItem);
                // you could do your own processing on nItem here
            }
        }
```

  
##  <a name="a-namegetnumberofworkareasa--clistctrlgetnumberofworkareas"></a><a name="getnumberofworkareas"></a>CListCtrl::GetNumberOfWorkAreas  
 擷取清單檢視控制項的工作區的目前數目。  
  
```  
UINT GetNumberOfWorkAreas() const;  
```  
  
### <a name="return-value"></a>傳回值  
 不使用這一次。  
  
### <a name="remarks"></a>備註  
 此成員函式實作 Win32 巨集的行為[ListView_GetNumberOfWorkAreas](http://msdn.microsoft.com/library/windows/desktop/bb774988)所述，在[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例    
  
```cpp  
        UINT i, uCount = m_myListCtrl.GetNumberOfWorkAreas();
        LPRECT lpRects = (LPRECT) malloc(uCount*sizeof(RECT));

        if (lpRects != NULL)
        {
            // Dump all of the work area dimensions.
            m_myListCtrl.GetWorkAreas(uCount, lpRects);

            for (i=0; i < uCount; i++)
            {
                TRACE(_T("Work area %d; left = %d, top = %d, right = %d, ")
                    _T("bottom = %d\r\n"),
                    i, lpRects[i].left, lpRects[i].top, lpRects[i].right, 
                    lpRects[i].bottom);
            }

            free(lpRects);
        }
        else
        {
            TRACE(_T("Couldn't allocate enough memory!"));   
        }

```

  
##  <a name="a-namegetoutlinecolora--clistctrlgetoutlinecolor"></a><a name="getoutlinecolor"></a>CListCtrl::GetOutlineColor  
 擷取清單檢視控制項的框線的色彩。  
  
```  
COLORREF GetOutlineColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)結構，其中包含外框色彩。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LVM_GETOUTLINECOLOR](http://msdn.microsoft.com/library/windows/desktop/bb761065)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namegetorigina--clistctrlgetorigin"></a><a name="getorigin"></a>CListCtrl::GetOrigin  
 擷取清單檢視控制項的目前檢視來源。  
  
```  
BOOL GetOrigin(LPPOINT lpPoint) const;  
```  
  
### <a name="parameters"></a>參數  
 `lpPoint`  
 位址[點](http://msdn.microsoft.com/library/windows/desktop/dd162805)接收檢視原始的結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。 不過，如果控制項是在報表檢視中，傳回值永遠是零。  
  
##  <a name="a-namegetselectedcolumna--clistctrlgetselectedcolumn"></a><a name="getselectedcolumn"></a>CListCtrl::GetSelectedColumn  
 擷取清單控制項中目前選取的資料行的索引。  
  
```  
UINT GetSelectedColumn() const;  
```  
  
### <a name="return-value"></a>傳回值  
 選取的資料行的索引。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LVM_GETSELECTEDCOLUMN](http://msdn.microsoft.com/library/windows/desktop/bb761067)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namegetselectedcounta--clistctrlgetselectedcount"></a><a name="getselectedcount"></a>CListCtrl::GetSelectedCount  
 擷取清單檢視控制項中選取的項目數目。  
  
```  
UINT GetSelectedCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在清單檢視控制項中選取的項目數目。  
  
### <a name="example"></a>範例    
  
```cpp  
        UINT i, uSelectedCount = m_myListCtrl.GetSelectedCount();
        int  nItem = -1;

        // Update all of the selected items.
        if (uSelectedCount > 0)
        {
            for (i=0; i < uSelectedCount; i++)
            {
                nItem = m_myListCtrl.GetNextItem(nItem, LVNI_SELECTED);
                ASSERT(nItem != -1);
                m_myListCtrl.Update(nItem); 
            }
        }
```

  
##  <a name="a-namegetselectionmarka--clistctrlgetselectionmark"></a><a name="getselectionmark"></a>CListCtrl::GetSelectionMark  
 擷取清單檢視控制項的選取項目符號。  
  
```  
int GetSelectionMark();
```  
  
### <a name="return-value"></a>傳回值  
 以零為起始的選取範圍標記中或如果沒有選取範圍標記為-1。  
  
### <a name="remarks"></a>備註  
 此成員函式實作 Win32 巨集的行為[ListView_GetSelectionMark](http://msdn.microsoft.com/library/windows/desktop/bb774998)所述，在[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  

```cpp  
    // Set the selection mark to the first item only if no other item is 
    // selected.
    if (m_myListCtrl.GetSelectionMark() == -1)
        m_myListCtrl.SetSelectionMark(0);
```

  
##  <a name="a-namegetstringwidtha--clistctrlgetstringwidth"></a><a name="getstringwidth"></a>CListCtrl::GetStringWidth  
 決定要顯示所有指定的字串所需的最小的資料行寬度。  
  
```  
int GetStringWidth(LPCTSTR lpsz) const;  
```  
  
### <a name="parameters"></a>參數  
 `lpsz`  
 寬度是要判斷 null 結尾的字串的位址。  
  
### <a name="return-value"></a>傳回值  
 寬度，單位為像素所指向的字串`lpsz`。  
  
### <a name="remarks"></a>備註  
 傳回的寬度會考慮控制項的目前字型和資料行邊界，但不是小圖示的寬度。  
  
### <a name="example"></a>範例  

```cpp  
        CString strColumn;
        int nWidth;

        // Insert six columns in the list view control. Make the width of
        // the column be the width of the column header plus 50%.
        for (int i = 0; i < 6; i++)
        {
            strColumn.Format(_T("column %d"), i);
            nWidth = 3*m_myListCtrl.GetStringWidth(strColumn)/2;
            m_myListCtrl.InsertColumn(i, strColumn, LVCFMT_LEFT, nWidth);
        }
```

  
##  <a name="a-namegetsubitemrecta--clistctrlgetsubitemrect"></a><a name="getsubitemrect"></a>CListCtrl::GetSubItemRect  
 擷取清單檢視控制項中的項目，這個周框。  
  
```  
BOOL GetSubItemRect(
    int iItem,  
    int iSubItem,  
    int nArea,  
    CRect& ref);
```  
  
### <a name="parameters"></a>參數  
 *iItem*  
 子項目的父項目的索引。  
  
 *iSubItem*  
 以一為子項目的索引。  
  
 *nArea*  
 要擷取決定週框 （清單檢視子項目） 的部分。 週框的部分 （圖示、 標籤或兩者） 會指定將位元 OR 運算子套用至一或多個下列值︰  
  
- `LVIR_BOUNDS`傳回整個項目，包括圖示和標籤的周框矩形。  
  
- `LVIR_ICON`傳回圖示或小圖示的周框矩形。  
  
- `LVIR_LABEL`傳回整個項目，包括圖示和標籤的周框矩形。 這等同於`LVIR_BOUNDS`。  
  
 `ref`  
 若要參考[CRect](../../atl-mfc-shared/reference/crect-class.md)物件，其中包含子項目的座標的週框。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 此成員函式實作 Win32 巨集的行為[ListView_GetSubItemRect](http://msdn.microsoft.com/library/windows/desktop/bb775004)所述，在[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namegettextbkcolora--clistctrlgettextbkcolor"></a><a name="gettextbkcolor"></a>CListCtrl::GetTextBkColor  
 擷取清單檢視控制項的文字背景色彩。  
  
```  
COLORREF GetTextBkColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 32 位元值，用來指定 RGB 色彩。  
  
### <a name="example"></a>範例  
  請參閱範例[CListCtrl::SetTextBkColor](#settextbkcolor)。  
  
##  <a name="a-namegettextcolora--clistctrlgettextcolor"></a><a name="gettextcolor"></a>CListCtrl::GetTextColor  
 擷取清單檢視控制項的文字色彩。  
  
```  
COLORREF GetTextColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 32 位元值，用來指定 RGB 色彩。  
  
### <a name="example"></a>範例  
  請參閱範例[CListCtrl::SetTextColor](#settextcolor)。  
  
##  <a name="a-namegettileinfoa--clistctrlgettileinfo"></a><a name="gettileinfo"></a>CListCtrl::GetTileInfo  
 擷取清單檢視控制項中並排顯示的相關資訊。  
  
```  
BOOL GetTileInfo(PLVTILEINFO pti) const;  
```  
  
### <a name="parameters"></a>參數  
 *pti*  
 指標[LVTILEINFO](http://msdn.microsoft.com/library/windows/desktop/bb774766)接收並排顯示資訊的結構。  
  
### <a name="return-value"></a>傳回值  
 不使用傳回的值。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LVM_GETTILEINFO](http://msdn.microsoft.com/library/windows/desktop/bb761081)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namegettileviewinfoa--clistctrlgettileviewinfo"></a><a name="gettileviewinfo"></a>CListCtrl::GetTileViewInfo  
 擷取清單檢視控制項中並排顯示檢視的相關資訊。  
  
```  
BOOL GetTileViewInfo(PLVTILEVIEWINFO ptvi) const;  
```  
  
### <a name="parameters"></a>參數  
 `ptvi`  
 指標[LVTILEVIEWINFO](http://msdn.microsoft.com/library/windows/desktop/bb774768)接收已擷取之資訊的結構。  
  
### <a name="return-value"></a>傳回值  
 不使用傳回的值。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LVM_GETTILEVIEWINFO](http://msdn.microsoft.com/library/windows/desktop/bb761083)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namegettooltipsa--clistctrlgettooltips"></a><a name="gettooltips"></a>CListCtrl::GetToolTips  
 擷取清單檢視控制項用來顯示工具提示的工具提示控制項。  
  
```  
CToolTipCtrl* GetToolTips() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CToolTipCtrl](ctooltipctrl-class.md)清單控制項所使用的物件。 如果[建立](#create)成員函式會使用樣式**LVS_NOTOOLTIPS**，使用任何工具提示，以及**NULL**傳回。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[LVM_GETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb761085)所述，在[!INCLUDE[winSDK](./includes/winsdk_md.md)]。 實作 MFC`GetToolTips`傳回`CToolTipCtrl`物件，它會使用清單控制項，而不是工具提示控制項的控制代碼。  
  
### <a name="example"></a>範例  

```cpp  
        CToolTipCtrl* pTip = m_myListCtrl.GetToolTips();
        if (NULL != pTip)
        {
            pTip->UpdateTipText(_T("I'm a list view!"), &m_myListCtrl,
                IDD_MYLISTCTRL);
        }
```

  
##  <a name="a-namegettopindexa--clistctrlgettopindex"></a><a name="gettopindex"></a>CListCtrl::GetTopIndex  
 在 [清單] 檢視或報表檢視中擷取最上層的可見項目的索引。  
  
```  
int GetTopIndex() const;  
```  
  
### <a name="return-value"></a>傳回值  
 最上層的可見項目的索引。  
  
### <a name="example"></a>範例  

 
```cpp  
        // Make sure the focus is set to the list view control.
        m_myListCtrl.SetFocus();

        // Select all of the items that are completely visible.
        int n = m_myListCtrl.GetTopIndex();
        int nLast = n + m_myListCtrl.GetCountPerPage();

        for (; n < nLast; n++)
        {
            m_myListCtrl.SetItemState(n, LVIS_SELECTED, LVIS_SELECTED);
            ASSERT(m_myListCtrl.GetItemState(n, LVIS_SELECTED) == LVIS_SELECTED); 
        }
```

  
##  <a name="a-namegetviewa--clistctrlgetview"></a><a name="getview"></a>CListCtrl::GetView  
 取得清單檢視控制項的檢視。  
  
```  
DWORD GetView() const;  
```  
  
### <a name="return-value"></a>傳回值  
 清單檢視控制項目前的檢視。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LVM_GETVIEW](http://msdn.microsoft.com/library/windows/desktop/bb761091)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namegetviewrecta--clistctrlgetviewrect"></a><a name="getviewrect"></a>CListCtrl::GetViewRect  
 擷取清單檢視控制項中的所有項目的周框。  
  
```  
BOOL GetViewRect(LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>參數  
 `lpRect`  
 位址[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 清單檢視中必須是檢視圖示或小圖示檢視中。  
  
##  <a name="a-namegetworkareasa--clistctrlgetworkareas"></a><a name="getworkareas"></a>CListCtrl::GetWorkAreas  
 擷取目前的工作區的清單檢視控制項。  
  
```  
void GetWorkAreas(
    int nWorkAreas,  
    LPRECT prc) const;  
```  
  
### <a name="parameters"></a>參數  
 `nWorkAreas`  
 數目`RECT`中所包含的結構*prc*陣列。  
  
 `prc`  
 陣列的指標`RECT`結構 (或[CRect](../../atl-mfc-shared/reference/crect-class.md)物件)，接收的清單檢視控制項的工作區域。 這些結構中的值是在工作區座標。  
  
### <a name="remarks"></a>備註  
 此成員函式實作 Win32 巨集的行為[ListView_GetWorkAreas](http://msdn.microsoft.com/library/windows/desktop/bb775024)所述，在[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CListCtrl::GetNumberOfWorkAreas](#getnumberofworkareas)。  
  
##  <a name="a-namehasgroupa--clistctrlhasgroup"></a><a name="hasgroup"></a>CListCtrl::HasGroup  
 判斷清單檢視控制項是否具有指定的群組。  
  
```  
BOOL HasGroup(int iGroupId) const;  
```  
  
### <a name="parameters"></a>參數  
 `iGroupId`  
 所要求之群組的識別碼。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LVM_HASGROUP](http://msdn.microsoft.com/library/windows/desktop/bb761097)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namehittesta--clistctrlhittest"></a><a name="hittest"></a>CListCtrl::HitTest  
 判斷哪一個清單檢視項目，任何項目，位於指定位置。  
  
```  
int HitTest(LVHITTESTINFO* pHitTestInfo) const;  
  
int HitTest(
    CPoint pt,  
    UINT* pFlags = NULL) const;  
```  
  
### <a name="parameters"></a>參數  
 `pHitTestInfo`  
 位址**LVHITTESTINFO**結構，其中包含要進行點擊測試，位置接收的點擊測試結果的相關資訊。  
  
 `pt`  
 要測試的點。  
  
 `pFlags`  
 接收測試結果的相關資訊的整數指標。 請參閱說明**旗標**成員[LVHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb774754)結構[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>傳回值  
 所指定的位置處的項目索引`pHitTestInfo`，若有的話，否則為-1。  
  
### <a name="remarks"></a>備註  
 您可以使用`LVHT_ABOVE`， `LVHT_BELOW`， `LVHT_TOLEFT`，和`LVHT_TORIGHT`值的結構**旗標**成員來決定是否要捲動清單檢視控制項的內容。 兩個這類旗標可以結合，例如，如果您的上面和工作區左邊的位置。  
  
 您可以測試**LVHT_ONITEM**值的結構**旗標**成員來決定是否在清單檢視項目指定的位置。 這個值是上的位元 OR 運算`LVHT_ONITEMICON`， `LVHT_ONITEMLABEL`，和`LVHT_ONITEMSTATEICON`值的結構**旗標**成員。  
  
### <a name="example"></a>範例  

```cpp  
void CListCtrlDlg::OnRClick(NMHDR* pNMHDR, LRESULT* pResult)
{
    LPNMITEMACTIVATE pia = (LPNMITEMACTIVATE)pNMHDR;
    CPoint point(pia->ptAction);

    // Select the item the user clicked on.
    UINT uFlags;
    int nItem = m_myListCtrl.HitTest(point, &uFlags);

    if (uFlags & LVHT_ONITEMLABEL)
    {
        m_myListCtrl.SetItem(nItem, 0, LVIF_STATE, NULL, 0, LVIS_SELECTED, 
            LVIS_SELECTED, 0);
    }

    *pResult = 0;
}
```

  
##  <a name="a-nameinsertcolumna--clistctrlinsertcolumn"></a><a name="insertcolumn"></a>CListCtrl::InsertColumn  
 在清單檢視控制項中插入新的資料行。  
  
```  
int InsertColumn(
    int nCol,  
    const LVCOLUMN* pColumn);

 
int InsertColumn(
    int nCol,  
    LPCTSTR lpszColumnHeading,  
    int nFormat = LVCFMT_LEFT,  
    int nWidth = -1,  
    int nSubItem = -1);
```  
  
### <a name="parameters"></a>參數  
 `nCol`  
 新的資料行的索引。  
  
 `pColumn`  
 位址**LVCOLUMN**結構，其中包含新的資料行的屬性。  
  
 *lpszColumnHeading*  
 字串，包含資料行標題的位址。  
  
 `nFormat`  
 指定資料行的對齊方式的整數。 它可以是下列值之一︰ **LVCFMT_LEFT**， **LVCFMT_RIGHT**，或**LVCFMT_CENTER**。  
  
 `nWidth`  
 資料行，單位為像素寬度。 如果這個參數是-1，未設定資料行寬度。  
  
 `nSubItem`  
 索引資料行相關聯的子項目。 這個參數是-1，如果沒有子項目是資料行相關聯。  
  
### <a name="return-value"></a>傳回值  
 新的資料行，如果成功則為-1 的其他索引。  
  
### <a name="remarks"></a>備註  
 清單檢視控制項中的最左邊資料行必須是靠左對齊。  
  
 [LVCOLUMN](http://msdn.microsoft.com/library/windows/desktop/bb774743)結構包含在報表檢視中的資料行的屬性。 它也用來接收資料行的相關資訊。 此結構描述中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-nameinsertgroupa--clistctrlinsertgroup"></a><a name="insertgroup"></a>CListCtrl::InsertGroup  
 插入清單檢視控制項中的群組。  
  
```  
LRESULT InsertGroup(
    int index,  
    PLVGROUP pgrp);
```  
  
### <a name="parameters"></a>參數  
 *索引*  
 群組是要插入之項目的索引。  
  
 `pgrp`  
 指標[LVGROUP](http://msdn.microsoft.com/library/windows/desktop/bb774769)結構，其中包含要加入的群組。  
  
### <a name="return-value"></a>傳回值  
 傳回群組已加入的項目則為-1 的索引; 如果作業失敗。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LVM_INSERTGROUP](http://msdn.microsoft.com/library/windows/desktop/bb761103)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-nameinsertgroupsorteda--clistctrlinsertgroupsorted"></a><a name="insertgroupsorted"></a>CListCtrl::InsertGroupSorted  
 插入群組的已排序清單中指定的群組。  
  
```  
LRESULT InsertGroupSorted(PLVINSERTGROUPSORTED pStructInsert);
```  
  
### <a name="parameters"></a>參數  
 *pStructInsert*  
 指標[LVINSERTGROUPSORTED](http://msdn.microsoft.com/library/windows/desktop/bb774756)結構，其中包含要插入的群組。  
  
### <a name="return-value"></a>傳回值  
 不使用傳回的值。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LVM_INSERTGROUPSORTED](http://msdn.microsoft.com/library/windows/desktop/bb761105)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-nameinsertitema--clistctrlinsertitem"></a><a name="insertitem"></a>CListCtrl::InsertItem  
 將項目插入清單檢視控制項。  
  
```  
int InsertItem(const LVITEM* pItem);

 
int InsertItem(
    int nItem,  
    LPCTSTR lpszItem);

 
int InsertItem(
    int nItem,  
    LPCTSTR lpszItem,  
    int nImage);

 
int InsertItem(
    UINT nMask,  
    int nItem,  
    LPCTSTR lpszItem,  
    UINT nState,  
    UINT nStateMask,  
    int nImage,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>參數  
 `pItem`  
 指標[LVITEM](http://msdn.microsoft.com/library/windows/desktop/bb774760)結構，指定的項目屬性中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
 `nItem`  
 要插入之項目的索引。  
  
 `lpszItem`  
 字串，其中包含的項目標籤的位址或`LPSTR_TEXTCALLBACK`該項目是否為回呼項目。 回呼項目上的資訊，請參閱[clistctrl:: Getcallbackmask](#getcallbackmask)。  
  
 `nImage`  
 項目的影像的索引或`I_IMAGECALLBACK`該項目是否為回呼項目。 回呼項目上的資訊，請參閱[clistctrl:: Getcallbackmask](#getcallbackmask)。  
  
 `nMask`  
 `nMask`參數會指定哪一個項目做為參數傳遞的屬性的有效值。 它可以是其中一個或多個遮罩值中所述[LVITEM 結構](http://msdn.microsoft.com/library/windows/desktop/bb774760)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。 有效的值可以與位元 OR 運算子結合。  
  
 `nState`  
 表示項目的狀態、 狀態影像和覆疊影像。 請參閱[!INCLUDE[winSDK](./includes/winsdk_md.md)]主題[LVITEM 結構](http://msdn.microsoft.com/library/windows/desktop/bb774760)如需詳細資訊和[清單檢視項目狀態](http://msdn.microsoft.com/library/windows/desktop/bb774733)有效旗標的清單。  
  
 `nStateMask`  
 表示要擷取或修改的位元之狀態的成員。 請參閱[LVITEM 結構](http://msdn.microsoft.com/library/windows/desktop/bb774760)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]如需詳細資訊。  
  
 `lParam`  
 與項目相關聯的 32 位元應用程式特定值。 如果指定此參數，您必須設定`nMask`屬性`LVIF_PARAM`。  
  
### <a name="return-value"></a>傳回值  
 新的項目，如果成功則為-1 的其他索引。  
  
### <a name="remarks"></a>備註  
 呼叫這個方法可能會造成**LVM_INSERTITEM**傳送到您的控制項視窗的訊息。 控制項的相關聯的訊息處理常式可能無法設定項目文字，在某些情況下的 (例如使用的視窗樣式，例如**LVS_OWNERDRAW**)。 如需有關這些條件的詳細資訊，請參閱[LVM_INSERTITEM](http://msdn.microsoft.com/library/windows/desktop/bb761107)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  

```cpp  
        CString strText;
        int nColumnCount = m_myListCtrl.GetHeaderCtrl()->GetItemCount();

        // Insert 10 items in the list view control.
        for (int i = 0; i < 10; i++)
        {
            strText.Format(TEXT("item %d"), i);

            // Insert the item, select every other item.
            m_myListCtrl.InsertItem(LVIF_TEXT | LVIF_STATE, i, strText, 
                (i % 2) == 0 ? LVIS_SELECTED : 0, LVIS_SELECTED, 0, 0);

            // Initialize the text of the subitems.
            for (int j = 1; j < nColumnCount; j++)
            {
                strText.Format(TEXT("sub-item %d %d"), i, j);
                m_myListCtrl.SetItemText(i, j, strText);
            }
        }
```

  
##  <a name="a-nameinsertmarkhittesta--clistctrlinsertmarkhittest"></a><a name="insertmarkhittest"></a>CListCtrl::InsertMarkHitTest  
 擷取最接近指定點的插入點。  
  
```  
int InsertMarkHitTest(
    LPPOINT pPoint,  
    LPLVINSERTMARK lvim) const;  
```  
  
### <a name="parameters"></a>參數  
 `pPoint`  
 指標[點](http://msdn.microsoft.com/library/windows/desktop/dd162805)結構，包含點擊的測試的座標，相對於清單控制項的用戶端區域。  
  
 `lvim`  
 指標[LVINSERTMARK](http://msdn.microsoft.com/library/windows/desktop/bb774758)結構，指定最接近的座標點參數所定義的插入點。  
  
### <a name="return-value"></a>傳回值  
 插入點最接近指定點。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LVM_INSERTMARKHITTEST](http://msdn.microsoft.com/library/windows/desktop/bb761131)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-nameisgroupviewenableda--clistctrlisgroupviewenabled"></a><a name="isgroupviewenabled"></a>CListCtrl::IsGroupViewEnabled  
 判斷是否啟用清單檢視控制項的群組檢視。  
  
```  
BOOL IsGroupViewEnabled() const;  
```  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**如果已啟用群組檢視，或**FALSE**否則。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LVM_ISGROUPVIEWENABLED](http://msdn.microsoft.com/library/windows/desktop/bb761133)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-nameisitemvisiblea--clistctrlisitemvisible"></a><a name="isitemvisible"></a>CListCtrl::IsItemVisible  
 指出目前的清單檢視控制項中指定的項目是否可見。  
  
```  
BOOL IsItemVisible(int index) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `index`|目前的清單檢視控制項中項目的以零為起始的索引。|  
  
### <a name="return-value"></a>傳回值  
 `true`如果指定的項目為可見，否則`false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[LVM_ISITEMVISIBLE](http://msdn.microsoft.com/library/windows/desktop/bb761135)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namemapidtoindexa--clistctrlmapidtoindex"></a><a name="mapidtoindex"></a>CListCtrl::MapIDToIndex  
 將目前的清單檢視控制項中項目的唯一識別碼對應至索引。  
  
```  
UINT MapIDToIndex(UINT id) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `id`|項目的唯一識別碼。|  
  
### <a name="return-value"></a>傳回值  
 目前的索引，做為指定的識別碼。  
  
### <a name="remarks"></a>備註  
 清單檢視控制項在內部會追蹤索引的項目。 由於索引可以變更控制項的存留期間，可能會造成問題。 清單檢視控制項時建立項目，您可以使用這個識別碼，以保證唯一性的清單檢視控制項的存留期間，可以標記識別碼的項目。  
  
 請注意，在多執行緒環境中索引保證只裝載不會在背景執行緒上的清單檢視控制項的執行緒上。  
  
 這個方法會傳送[LVM_MAPIDTOINDEX](http://msdn.microsoft.com/library/windows/desktop/bb761137)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namemapindextoida--clistctrlmapindextoid"></a><a name="mapindextoid"></a>CListCtrl::MapIndexToID  
 將目前的清單檢視控制項中項目的索引對應至唯一的識別碼。  
  
```  
UINT MapIndexToID(UINT index) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `index`|項目的以零為起始的索引。|  
  
### <a name="return-value"></a>傳回值  
 指定項目的唯一 ID。  
  
### <a name="remarks"></a>備註  
 清單檢視控制項在內部會追蹤索引的項目。 由於索引可以變更控制項的存留期間，可能會造成問題。 建立項目時，清單檢視控制項可以標記項目識別碼。 您可以使用此識別碼的清單檢視控制項的存留期存取的特定項目。  
  
 請注意，在多執行緒環境中索引保證只裝載不會在背景執行緒上的清單檢視控制項的執行緒上。  
  
 這個方法會傳送[LVM_MAPINDEXTOID](http://msdn.microsoft.com/library/windows/desktop/bb761139)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數， `m_listCtrl`，也就是用來存取目前的清單檢視控制項。 下一個範例中會使用此變數。    
  
```cpp  
public:
    // Variable used to access the list control.
    CListCtrl m_listCtrl; 
```

  
### <a name="example"></a>範例  
 下列程式碼範例示範`MapIndexToID`方法。 在先前章節中的這個程式碼範例，我們會建立顯示標題為"ClientID"和 「 成績 」，在報表檢視中的兩個資料行的清單檢視控制項。 下列範例會將每個清單檢視項目的索引對應到身分證號碼，並接著會擷取每個識別碼的索引。 最後，範例會報告是否已擷取原始的索引。    
  
```cpp  
    // MapIndexToID
    int iCount = m_listCtrl.GetItemCount();
    UINT nId = 0;
    UINT nIndex = 0;
    for (int iIndexOriginal = 0; iIndexOriginal < iCount; iIndexOriginal++)
    {
        // Map index to ID.
        nId = m_listCtrl.MapIndexToID((UINT)iIndexOriginal);

        // Map ID to index.
        nIndex = m_listCtrl.MapIDToIndex(nId);

        if (nIndex != (UINT)(iIndexOriginal))
        {
            CString str;
            str.Format(_T("Mapped index (%d) is not equal to original index (%d)"),
                nIndex, (UINT)(iIndexOriginal));
            AfxMessageBox(str);
            return;
        }
    }
    AfxMessageBox(_T("The mapped indexes and original indexes are equal."), 
        MB_ICONINFORMATION);
```

  
##  <a name="a-namemovegroupa--clistctrlmovegroup"></a><a name="movegroup"></a>CListCtrl::MoveGroup  
 移動指定群組，來指定零根據的索引的清單檢視控制項。  
  
```  
LRESULT MoveGroup(
    int iGroupId,  
    int toIndex);
```  
  
### <a name="parameters"></a>參數  
 `iGroupId`  
 要移動之群組的識別碼。  
  
 `toIndex`  
 要移動這些群組的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 不使用傳回的值。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LVM_MOVEGROUP](http://msdn.microsoft.com/library/windows/desktop/bb761141)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namemoveitemtogroupa--clistctrlmoveitemtogroup"></a><a name="moveitemtogroup"></a>CListCtrl::MoveItemToGroup  
 將指定的項目移到指定的群組。  
  
```  
void MoveItemToGroup(
    int idItemFrom,  
    int idGroupTo);
```  
  
### <a name="parameters"></a>參數  
 [in] `idItemFrom`  
 要移動之項目的索引。  
  
 [in] `idGroupTo`  
 群組識別碼的項目將會移至。  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  這個方法目前未實作。  
  
 這個方法會模擬的功能[LVM_MOVEITEMTOGROUP](http://msdn.microsoft.com/library/windows/desktop/bb761143)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-nameredrawitemsa--clistctrlredrawitems"></a><a name="redrawitems"></a>CListCtrl::RedrawItems  
 強制重新繪製的項目範圍的清單檢視控制項。  
  
```  
BOOL RedrawItems(
    int nFirst,  
    int nLast);
```  
  
### <a name="parameters"></a>參數  
 `nFirst`  
 重新繪製的第一個項目索引。  
  
 `nLast`  
 重新繪製的最後一個項目的索引。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 指定的項目都會不實際重新繪製之前，清單檢視視窗會收到`WM_PAINT`訊息。 若要立即重繪，呼叫 Windows [UpdateWindow](http://msdn.microsoft.com/library/windows/desktop/dd145167)之後使用這個函式的函式。  
  
##  <a name="a-nameremoveallgroupsa--clistctrlremoveallgroups"></a><a name="removeallgroups"></a>CListCtrl::RemoveAllGroups  
 從清單檢視控制項中移除所有群組。  
  
```  
void RemoveAllGroups();
```  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LVM_REMOVEALLGROUPS](http://msdn.microsoft.com/library/windows/desktop/bb761147)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-nameremovegroupa--clistctrlremovegroup"></a><a name="removegroup"></a>CListCtrl::RemoveGroup  
 從清單檢視控制項中移除指定的群組。  
  
```  
LRESULT RemoveGroup(int iGroupId);
```  
  
### <a name="parameters"></a>參數  
 `iGroupId`  
 要移除群組的識別碼。  
  
### <a name="return-value"></a>傳回值  
 否則會傳回群組中，如果成功，則為-1 的索引。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LVM_REMOVEGROUP](http://msdn.microsoft.com/library/windows/desktop/bb761149)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namescrolla--clistctrlscroll"></a><a name="scroll"></a>CListCtrl::Scroll  
 捲動清單檢視控制項的內容。  
  
```  
BOOL Scroll(CSize size);
```  
  
### <a name="parameters"></a>參數  
 `size`  
 A`CSize`物件，指定水平和垂直捲動，像素為單位的數量。 **y**成員`size`除以高度，單位為像素的清單檢視控制項的列，並捲動所產生的行數。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
##  <a name="a-namesetbkcolora--clistctrlsetbkcolor"></a><a name="setbkcolor"></a>CListCtrl::SetBkColor  
 設定清單檢視控制項的背景色彩。  
  
```  
BOOL SetBkColor(COLORREF cr);
```  
  
### <a name="parameters"></a>參數  
 `cr`  
 背景色彩設定，或`CLR_NONE`沒有背景色彩的值。 使用背景色彩的清單檢視控制項重繪其本身明顯較不含背景色彩。 如需資訊，請參閱[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="example"></a>範例  

 
```cpp  
        // Use the 3D button face color for the background.
        COLORREF crBkColor = ::GetSysColor(COLOR_3DFACE);
        m_myListCtrl.SetBkColor(crBkColor);
        ASSERT(m_myListCtrl.GetBkColor() == crBkColor);
```

  
##  <a name="a-namesetbkimagea--clistctrlsetbkimage"></a><a name="setbkimage"></a>CListCtrl::SetBkImage  
 設定清單檢視控制項的背景的影像。  
  
```  
BOOL SetBkImage(LVBKIMAGE* plvbkImage);
 
BOOL SetBkImage(
    HBITMAP hbm,  
    BOOL fTile = TRUE,  
    int xOffsetPercent = 0,  
    int yOffsetPercent = 0);
 
BOOL SetBkImage(
    LPTSTR pszUrl,  
    BOOL fTile = TRUE,  
    int xOffsetPercent = 0,  
    int yOffsetPercent = 0);
```  
  
### <a name="parameters"></a>參數  
 `plvbkImage`  
 位址**LVBKIMAGE**結構，包含新的背景影像資訊。  
  
 `hbm`  
 點陣圖的控制代碼。  
  
 `pszUrl`  
 A **NULL**-結尾的字串，其中包含背景影像的 URL。  
  
 *fTile*  
 並排顯示在清單檢視控制項，背景影像時，非零值。否則為 0。  
  
 *xOffsetPercent*  
 單位為像素影像的左邊緣，從清單檢視控制項的原點位移。  
  
 *yOffsetPercent*  
 單位為像素影像的上邊緣，從清單檢視控制項的原點位移。  
  
### <a name="return-value"></a>傳回值  
 傳回非零，如果成功或為零。  
  
### <a name="remarks"></a>備註  
  
> [!NOTE]
>  因為`CListCtrl::SetBkImage`使用 OLE COM 功能，必須先初始化 OLE 程式庫使用`SetBkImage`。 最好初始化應用程式時初始化 COM 程式庫和應用程式終止時，解除初始化程式庫。 這是自動在 MFC 應用程式，讓使用 ActiveX 技術、 OLE Automation、 OLE 連結/內嵌，或 ODBC/DAO 的作業。  
  
### <a name="example"></a>範例  
  請參閱範例[CListCtrl::GetBkImage](#getbkimage)。  
  
##  <a name="a-namesetcallbackmaska--clistctrlsetcallbackmask"></a><a name="setcallbackmask"></a>Clistctrl:: Setcallbackmask  
 設定清單檢視控制項的回呼遮罩。  
  
```  
BOOL SetCallbackMask(UINT nMask);
```  
  
### <a name="parameters"></a>參數  
 `nMask`  
 回呼遮罩的新值。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="example"></a>範例  

 
```cpp  
    // Set the callback mask so that only the selected and focused states
    // are stored for each item.
    m_myListCtrl.SetCallbackMask(LVIS_SELECTED|LVIS_FOCUSED);
    ASSERT(m_myListCtrl.GetCallbackMask() == 
        (LVIS_SELECTED|LVIS_FOCUSED));
```


##  <a name="a-namesetchecka--clistctrlsetcheck"></a><a name="setcheck"></a>CListCtrl::SetCheck  
 判斷清單控制項項目的狀態影像是否可見。  
  
```  
BOOL SetCheck(
    int nItem,  
    BOOL fCheck = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `nItem`  
 清單控制項項目以零為起始的索引。  
  
 `fCheck`  
 指定是否狀態影像的項目是否應該顯示。 根據預設， *fCheck*是**TRUE**和狀態影像會顯示。 如果`fCheck`是**FALSE**，看不到。  
  
### <a name="return-value"></a>傳回值  
 非零，如果已勾選的項目，否則為 0。  
  
### <a name="example"></a>範例  

 
```cpp  
        int nCount = m_myListCtrl.GetItemCount();
        BOOL fCheck = FALSE;

        // Set the check state of every other item to TRUE and 
        // all others to FALSE.
        for (int i = 0; i < nCount; i++)
        {
            m_myListCtrl.SetCheck(i, fCheck);
            ASSERT((m_myListCtrl.GetCheck(i) && fCheck) || 
                (!m_myListCtrl.GetCheck(i) && !fCheck));
            fCheck = !fCheck;
        }
```

  
##  <a name="a-namesetcolumna--clistctrlsetcolumn"></a><a name="setcolumn"></a>CListCtrl::SetColumn  
 設定清單檢視資料行的屬性。  
  
```  
BOOL SetColumn(
    int nCol,  
    const LVCOLUMN* pColumn);
```  
  
### <a name="parameters"></a>參數  
 `nCol`  
 若要設定其屬性的資料行的索引。  
  
 `pColumn`  
 位址[LVCOLUMN](http://msdn.microsoft.com/library/windows/desktop/bb774743)結構，其中包含新的資料行屬性中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。 結構的**遮罩**成員會指定哪個資料行屬性來設定。 如果**遮罩**成員指定`LVCF_TEXT`值，此結構**pszText**成員是以 null 結束的字串和結構的位址**cchTextMax**成員會被忽略。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="example"></a>範例  
  請參閱範例[CListCtrl::GetColumn](#getcolumn)。  
  
##  <a name="a-namesetcolumnorderarraya--clistctrlsetcolumnorderarray"></a><a name="setcolumnorderarray"></a>CListCtrl::SetColumnOrderArray  
 設定清單檢視控制項的資料行順序 （由左到右）。  
  
```  
BOOL SetColumnOrderArray(
    int iCount,  
    LPINT piArray);
```  
  
### <a name="parameters"></a>參數  
 `piArray`  
 包含索引值 （從左到右） 的清單檢視控制項中的資料行緩衝區的指標。 緩衝區必須夠大，無法包含在清單檢視控制項中的資料行總數。  
  
 `iCount`  
 在清單檢視控制項中的資料行數目。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 此成員函式實作 Win32 巨集的行為[ListView_SetColumnOrderArray](http://msdn.microsoft.com/library/windows/desktop/bb775072)所述，在[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CListCtrl::GetColumnOrderArray](#getcolumnorderarray)。  
  
##  <a name="a-namesetcolumnwidtha--clistctrlsetcolumnwidth"></a><a name="setcolumnwidth"></a>CListCtrl::SetColumnWidth  
 變更報表的檢視或清單檢視中的資料行的寬度。  
  
```  
BOOL SetColumnWidth(
    int nCol,  
    int cx);
```  
  
### <a name="parameters"></a>參數  
 `nCol`  
 設定寬度的資料行索引。 在清單檢視中，這個參數必須是 0。  
  
 `cx`  
 新的資料行的寬度。 可以是**LVSCW_AUTOSIZE**或**LVSCW_AUTOSIZE_USEHEADER**所述，在[LVM_SETCOLUMNWIDTH](http://msdn.microsoft.com/library/windows/desktop/bb761163)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
##  <a name="a-namesetextendedstylea--clistctrlsetextendedstyle"></a><a name="setextendedstyle"></a>CListCtrl::SetExtendedStyle  
 設定清單檢視控制項的目前延伸的樣式。  
  
```  
DWORD SetExtendedStyle(DWORD dwNewStyle);
```  
  
### <a name="parameters"></a>參數  
 `dwNewStyle`  
 清單檢視控制項所使用的延伸樣式的組合。 描述一種樣式清單，請參閱[擴充清單檢視樣式](http://msdn.microsoft.com/library/windows/desktop/bb774732)中的主題[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>傳回值  
 使用清單檢視控制項的上一個延伸樣式的組合。  
  
### <a name="remarks"></a>備註  
 此成員函式實作 Win32 巨集的行為[ListView_SetExtendedListViewStyle](http://msdn.microsoft.com/library/windows/desktop/bb775076)所述，在[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  

 
```cpp  
    // Allow the header controls item to be movable by the user.
    m_myListCtrl.SetExtendedStyle
        (m_myListCtrl.GetExtendedStyle()|LVS_EX_HEADERDRAGDROP);
```

  
##  <a name="a-namesetgroupinfoa--clistctrlsetgroupinfo"></a><a name="setgroupinfo"></a>CListCtrl::SetGroupInfo  
 設定描述指定的群組的目前清單檢視控制項的資訊。  
  
```  
int SetGroupInfo(
    int iGroupId,  
    PLVGROUP pgrp);
```  
  
### <a name="parameters"></a>參數  
 `iGroupId`  
 設定其資訊之群組的識別碼。  
  
 `pgrp`  
 指標[LVGROUP](http://msdn.microsoft.com/library/windows/desktop/bb774769)結構，其中包含要設定的資訊。 呼叫端會負責配置這個結構，並設定其成員項目。  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，群組的識別碼反之則為-1。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[LVM_SETGROUPINFO](http://msdn.microsoft.com/library/windows/desktop/bb761167)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namesetgroupmetricsa--clistctrlsetgroupmetrics"></a><a name="setgroupmetrics"></a>CListCtrl::SetGroupMetrics  
 設定群組度量的清單檢視控制項。  
  
```  
void SetGroupMetrics(PLVGROUPMETRICS pGroupMetrics);
```  
  
### <a name="parameters"></a>參數  
 `pGroupMetrics`  
 指標[LVGROUPMETRICS](http://msdn.microsoft.com/library/windows/desktop/bb774752)結構，其中包含要設定的群組度量資訊。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LVM_SETGROUPMETRICS](http://msdn.microsoft.com/library/windows/desktop/bb761168)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namesethotcursora--clistctrlsethotcursor"></a><a name="sethotcursor"></a>CListCtrl::SetHotCursor  
 設定已啟用熱追蹤，清單檢視控制項時所使用的游標。  
  
```  
HCURSOR SetHotCursor(HCURSOR hc);
```  
  
### <a name="parameters"></a>參數  
 *代表*  
 游標資源，用來表示熱資料指標控制代碼。  
  
### <a name="return-value"></a>傳回值  
 正在使用清單檢視控制項的上一個作用的游標資源控制代碼。  
  
### <a name="remarks"></a>備註  
 此成員函式實作 Win32 巨集的行為[ListView_SetHotCursor](http://msdn.microsoft.com/library/windows/desktop/bb775082)所述，在[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
 熱游標，只顯示啟用動態顯示選取範圍時，會出現游標通過任何清單檢視項目。 藉由設定啟用暫留選取**LVS_EX_TRACKSELECT**延伸樣式。  
  
### <a name="example"></a>範例  
  請參閱範例[CListCtrl::GetHotCursor](#gethotcursor)。  
  
##  <a name="a-namesethotitema--clistctrlsethotitem"></a><a name="sethotitem"></a>CListCtrl::SetHotItem  
 將清單檢視控制項的目前作用的項目。  
  
```  
int SetHotItem(int iIndex);
```  
  
### <a name="parameters"></a>參數  
 `iIndex`  
 要設定為熱門項目之項目的以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 先前熱門項目以零為起始的索引。  
  
### <a name="remarks"></a>備註  
 此成員函式實作 Win32 巨集的行為[ListView_SetHotItem](http://msdn.microsoft.com/library/windows/desktop/bb775083)所述，在[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CListCtrl::GetHotItem](#gethotitem)。  
  
##  <a name="a-namesethovertimea--clistctrlsethovertime"></a><a name="sethovertime"></a>CListCtrl::SetHoverTime  
 設定清單檢視控制項的滑鼠停留時間。  
  
```  
DWORD SetHoverTime(DWORD dwHoverTime = (DWORD)-1);
```  
  
### <a name="parameters"></a>參數  
 *dwHoverTime*  
 新的延遲，以毫秒為單位，將滑鼠游標必須停留的項目之前加以選取。 如果傳遞的預設值，時間是設定為預設暫留時間。  
  
### <a name="return-value"></a>傳回值  
 上一個滑鼠停留的時間，以毫秒為單位。  
  
### <a name="remarks"></a>備註  
 此成員函式實作 Win32 巨集的行為[ListView_SetHoverTime](http://msdn.microsoft.com/library/windows/desktop/bb775084)所述，在[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CListCtrl::GetHoverTime](#gethovertime)。  
  
##  <a name="a-nameseticonspacinga--clistctrlseticonspacing"></a><a name="seticonspacing"></a>CListCtrl::SetIconSpacing  
 設定清單檢視控制項中的圖示之間的間距。  
  
```  
CSize SetIconSpacing(
    int cx,  
    int cy);  
  
CSize SetIconSpacing(CSize size);
```  
  
### <a name="parameters"></a>參數  
 `cx`  
 在 x 軸上的圖示之間的距離 （以像素為單位）。  
  
 `cy`  
 Y 軸上的圖示之間的距離 （以像素為單位）。  
  
 `size`  
 A`CSize`物件，指定圖示，在 x 軸和 y 軸之間的距離 （以像素為單位）。  
  
### <a name="return-value"></a>傳回值  
 A [CSize](../../atl-mfc-shared/reference/csize-class.md)物件，其中包含圖示間距的上一個值。  
  
### <a name="remarks"></a>備註  
 此成員函式實作 Win32 巨集的行為[ListView_SetIconSpacing](http://msdn.microsoft.com/library/windows/desktop/bb775085)所述，在[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  

 
```cpp  
    // Leave lots of space between icons.
    m_myListCtrl.SetIconSpacing(CSize(100, 100));
```

  
##  <a name="a-namesetimagelista--clistctrlsetimagelist"></a><a name="setimagelist"></a>CListCtrl::SetImageList  
 將影像清單指派給清單檢視控制項。  
  
```  
CImageList* SetImageList(
    CImageList* pImageList,  
    int nImageListType);
```  
  
### <a name="parameters"></a>參數  
 `pImageList`  
 若要指派的影像清單的指標。  
  
 `nImageListType`  
 影像清單的型別。 它可以是下列值之一︰  
  
- `LVSIL_NORMAL`大圖示的影像清單。  
  
- `LVSIL_SMALL`小圖示的影像清單。  
  
- `LVSIL_STATE`狀態影像的影像清單。  
  
### <a name="return-value"></a>傳回值  
 先前的影像清單的指標。  
  
### <a name="example"></a>範例  
  請參閱範例[CListCtrl::GetImageList](#getimagelist)。  
  
##  <a name="a-namesetinfotipa--clistctrlsetinfotip"></a><a name="setinfotip"></a>CListCtrl::SetInfoTip  
 設定工具提示文字。  
  
```  
BOOL SetInfoTip(PLVSETINFOTIP plvInfoTip);
```  
  
### <a name="parameters"></a>參數  
 *plvInfoTip*  
 指標[LVFSETINFOTIP](http://msdn.microsoft.com/library/windows/desktop/bb774764)結構，其中包含要設定的資訊。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LVM_SETINFOTIP](http://msdn.microsoft.com/library/windows/desktop/bb761180)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namesetinsertmarka--clistctrlsetinsertmark"></a><a name="setinsertmark"></a>CListCtrl::SetInsertMark  
 將插入點設定為定義的位置。  
  
```  
BOOL SetInsertMark(LPLVINSERTMARK lvim);
```  
  
### <a name="parameters"></a>參數  
 `lvim`  
 指標[LVINSERTMARK](http://msdn.microsoft.com/library/windows/desktop/bb774758)結構，指定要設定插入點的位置。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**如果成功，或**FALSE**否則。 **FALSE**如果傳回的大小以`cbSize`成員**LVINSERTMARK**結構不等於結構的實際大小，或當插入點不會套用在目前的檢視。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LVM_SETINSERTMARK](http://msdn.microsoft.com/library/windows/desktop/bb761182)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namesetinsertmarkcolora--clistctrlsetinsertmarkcolor"></a><a name="setinsertmarkcolor"></a>CListCtrl::SetInsertMarkColor  
 設定插入點的色彩。  
  
```  
COLORREF SetInsertMarkColor(COLORREF color);
```  
  
### <a name="parameters"></a>參數  
 `color`  
 A [COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)結構，指定要設定插入點的色彩。  
  
### <a name="return-value"></a>傳回值  
 傳回**COLORREF**結構，其中包含上一個色彩。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LVM_SETINSERTMARKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb761184)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namesetitema--clistctrlsetitem"></a><a name="setitem"></a>Clistctrl:: Setitem  
 設定部分或全部的清單檢視項目的屬性。  
  
```  
BOOL SetItem(const LVITEM* pItem);

 
BOOL SetItem(
    int nItem,  
    int nSubItem,  
    UINT nMask,  
    LPCTSTR lpszItem,  
    int nImage,  
    UINT nState,  
    UINT nStateMask,  
    LPARAM lParam);

 
BOOL SetItem(
    int nItem,  
    int nSubItem,  
    UINT nMask,  
    LPCTSTR lpszItem,  
    int nImage,  
    UINT nState,  
    UINT nStateMask,  
    LPARAM lParam,  
    int nIndent);
```  
  
### <a name="parameters"></a>參數  
 `pItem`  
 位址[LVITEM](http://msdn.microsoft.com/library/windows/desktop/bb774760)結構，其中包含新的項目屬性中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。 結構的**iItem**和**iSubItem**成員識別項目或子項目，以及結構**遮罩**成員指定要設定屬性。 如需有關**遮罩**成員，請參閱**註解**。  
  
 `nItem`  
 重新設定其屬性的項目索引。  
  
 `nSubItem`  
 屬性會設定子項目的索引。  
  
 `nMask`  
 指出哪些屬性的設定 （請參閱 < 備註 >）。  
  
 `lpszItem`  
 指定項目的標籤的 null 結尾字串的位址。  
  
 `nImage`  
 影像清單內的項目影像的索引。  
  
 `nState`  
 指定狀態變更 （請參閱 < 備註 >） 的值。  
  
 `nStateMask`  
 指定何種狀態變更 （請參閱 < 備註 >）。  
  
 `lParam`  
 要與項目相關聯的 32 位元應用程式特定值。  
  
 `nIndent`  
 縮排的像素為單位的寬度。 如果`nIndent`小於超過系統定義最小寬度，新的寬度設定為系統定義的最小值  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 **IItem**和**iSubItem**成員**LVITEM**結構和`nItem`和`nSubItem`參數會識別此項目和其屬性所設定的子項目。  
  
 **遮罩**成員**LVITEM**結構和`nMask`參數來指定哪一個項目屬性會設定︰  
  
- `LVIF_TEXT`**PszText**成員或`lpszItem`參數是以 null 終止字串的位址; **cchTextMax**成員會被忽略。  
  
- `LVIF_STATE`**StateMask**成員或`nStateMask`參數會指定哪一個項目狀態變更和**狀態**成員或`nState`參數會包含這些狀態的值。  
  
### <a name="example"></a>範例  
  請參閱範例[CListCtrl::HitTest](#hittest)。  
  
##  <a name="a-namesetitemcounta--clistctrlsetitemcount"></a><a name="setitemcount"></a>CListCtrl::SetItemCount  
 準備新增大量的項目清單檢視控制項。  
  
```  
void SetItemCount(int nItems);
```  
  
### <a name="parameters"></a>參數  
 `nItems`  
 最後會包含控制項的項目數目。  
  
### <a name="remarks"></a>備註  
 若要設定的虛擬清單檢視控制項的項目計數，請參閱[CListCtrl::SetItemCountEx](#setitemcountex)。  
  
### <a name="remarks"></a>備註  
 此成員函式實作 Win32 巨集的行為[ListView_SetItemCount](http://msdn.microsoft.com/library/windows/desktop/bb775093)所述，在[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  

 
```cpp  
        CString str;

        // Add 1024 items to the list view control.
        m_myListCtrl.SetItemCount(1024);

        for (int i = 0; i < 1024; i++)
        {
            str.Format(TEXT("item %d"), i);
            m_myListCtrl.InsertItem(i, str);
        }
```

  
##  <a name="a-namesetitemcountexa--clistctrlsetitemcountex"></a><a name="setitemcountex"></a>CListCtrl::SetItemCountEx  
 設定虛擬清單檢視控制項的項目計數。  
  
```  
BOOL SetItemCountEx(
    int iCount,  
    DWORD dwFlags = LVSICF_NOINVALIDATEALL);
```  
  
### <a name="parameters"></a>參數  
 `iCount`  
 最後會包含控制項的項目數目。  
  
 `dwFlags`  
 重設項目計數之後指定清單檢視控制項的行為。 這個值可以是以下的組合︰  
  
- **LVSICF_NOINVALIDATEALL**清單檢視控制項將會重新繪製除非檢視目前正在受影響的項目。 此為預設值。  
  
- **LVSICF_NOSCROLL**項目計數的變更時，清單檢視控制項不會變更捲軸的位置。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 此成員函式實作 Win32 巨集的行為[ListView_SetItemCountEx](http://msdn.microsoft.com/library/windows/desktop/bb775095)所述，在[!INCLUDE[winSDK](./includes/winsdk_md.md)]，只應虛擬清單檢視的呼叫。  
  
### <a name="example"></a>範例  

 
```cpp  
        CString str;

        // Add 1024 items to the list view control.

        // Force my virtual list view control to allocate 
        // enough memory for my 1024 items.
        m_myVirtualListCtrl.SetItemCountEx(1024, LVSICF_NOSCROLL|
            LVSICF_NOINVALIDATEALL);

        for (int i = 0; i < 1024; i++)
        {
            str.Format(TEXT("item %d"), i);
            m_myVirtualListCtrl.InsertItem(i, str);
        }
```

  
##  <a name="a-namesetitemdataa--clistctrlsetitemdata"></a><a name="setitemdata"></a>CListCtrl::SetItemData  
 設定所指定的項目相關聯的 32 位元應用程式特定值`nItem`。  
  
```  
BOOL SetItemData(int nItem, DWORD_PTR dwData);
```  
  
### <a name="parameters"></a>參數  
 `nItem`  
 資料都要設定的清單項目的索引。  
  
 `dwData`  
 要與項目相關聯的 32 位元值。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 這個值是**lParam**成員[LVITEM](http://msdn.microsoft.com/library/windows/desktop/bb774760)結構中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  

 
```cpp  
    // Set the data of each item to be equal to its index.
    for (int i = 0; i < m_myListCtrl.GetItemCount(); i++)
    {
        m_myListCtrl.SetItemData(i, i);
    }
```

  
##  <a name="a-namesetitemindexstatea--clistctrlsetitemindexstate"></a><a name="setitemindexstate"></a>CListCtrl::SetItemIndexState  
 在目前的清單檢視控制項中設定項目的狀態。  
  
```  
BOOL SetItemIndexState(
    PLVITEMINDEX pItemIndex,   
    DWORD dwState,   
    DWORD dwMask) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `pItemIndex`|指標[LVITEMINDEX](http://msdn.microsoft.com/library/windows/desktop/bb774762)該結構描述項目。 呼叫端會負責配置這個結構，並設定其成員項目。|  
|[in] `dwState`|設定項目狀態的位元組合即[清單檢視項目狀態](http://msdn.microsoft.com/library/windows/desktop/bb774733)。 指定&0; 時可重設，或其中一個狀態設定。|  
|[in] `dwMask`|所指定的狀態的有效位元遮罩`dwState`參數。 指定的位元組合 (OR)[清單檢視項目狀態](http://msdn.microsoft.com/library/windows/desktop/bb774733)。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊`dwState`參數，請參閱[清單檢視項目狀態](http://msdn.microsoft.com/library/windows/desktop/bb774733)。  
  
 如需詳細資訊`dwMask`參數，請參閱`stateMask`成員[LVITEM](http://msdn.microsoft.com/library/windows/desktop/bb774760)結構。  
  
 這個方法會傳送[LVM_SETITEMINDEXSTATE](http://msdn.microsoft.com/library/windows/desktop/bb761190)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namesetitempositiona--clistctrlsetitemposition"></a><a name="setitemposition"></a>CListCtrl::SetItemPosition  
 將項目移至清單檢視控制項中指定的位置。  
  
```  
BOOL SetItemPosition(
    int nItem,  
    POINT pt);
```  
  
### <a name="parameters"></a>參數  
 `nItem`  
 若要設定其位置的項目索引。  
  
 `pt`  
 A[點](http://msdn.microsoft.com/library/windows/desktop/dd162805)結構，指定檢視中的新位置座標，項目的左上角。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 控制項必須是圖示或小圖示檢視中。  
  
 如果清單檢視控制項有`LVS_AUTOARRANGE`樣式，清單檢視中排列集中設定之項目的位置。  
  
### <a name="example"></a>範例  
  請參閱範例[CListCtrl::GetItemPosition](#getitemposition)。  
  
##  <a name="a-namesetitemstatea--clistctrlsetitemstate"></a><a name="setitemstate"></a>CListCtrl::SetItemState  
 在清單檢視控制項中項目的狀態變更。  
  
```  
BOOL SetItemState(
    int nItem,  
    LVITEM* pItem);

 
BOOL SetItemState(
    int nItem,  
    UINT nState,  
    UINT nMask);
```  
  
### <a name="parameters"></a>參數  
 `nItem`  
 若要設定其狀態的項目索引。  
  
 `pItem`  
 位址[LVITEM](http://msdn.microsoft.com/library/windows/desktop/bb774760)結構中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。 結構的**stateMask**成員會指定要變更與該結構的哪些狀態位元**狀態**成員包含那些位元的新值。 其他成員會被忽略。  
  
 `nState`  
 狀態位元的新值。 如需可能的值，請參閱[CListCtrl::GetNextItem](#getnextitem)和[LVITEM](http://msdn.microsoft.com/library/windows/desktop/bb774760)狀態成員。  
  
 `nMask`  
 指定要變更哪些狀態位元遮罩。 這個值對應至的 stateMask 成員[LVITEM](http://msdn.microsoft.com/library/windows/desktop/bb774760)結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 項目的 「 狀態 」 是一個值，指定項目的可用性，指出使用者動作或否則反映出項目的狀態。 清單檢視控制項變更狀態位元，例如當使用者選取項目。 應用程式可能會變更以停用或隱藏項目，或指定重疊影像或狀態影像的其他狀態位元。  
  
### <a name="example"></a>範例  
  請參閱範例[CListCtrl::GetTopIndex](#gettopindex)。  
  
##  <a name="a-namesetitemtexta--clistctrlsetitemtext"></a><a name="setitemtext"></a>CListCtrl::SetItemText  
 變更清單檢視項目或子項目的的文字。  
  
```  
BOOL SetItemText(
    int nItem,  
    int nSubItem,  
    LPCTSTR lpszText);
```  
  
### <a name="parameters"></a>參數  
 `nItem`  
 若要設定其文字的項目索引。  
  
 `nSubItem`  
 若要設定項目標籤子項目，則為零的索引。  
  
 `lpszText`  
 包含新的項目文字的字串指標。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 這個方法不會適用於包含 LVS_OWNERDATA 視窗樣式的控制項 （事實上，這會導致判斷提示在偵錯組建）。 如需此清單控制項樣式的詳細資訊，請參閱[清單檢視控制項概觀](http://msdn.microsoft.com/library/windows/desktop/bb774735)。  
  
### <a name="example"></a>範例  
  請參閱範例[CListCtrl::InsertItem](#insertitem)。  
  
##  <a name="a-namesetoutlinecolora--clistctrlsetoutlinecolor"></a><a name="setoutlinecolor"></a>CListCtrl::SetOutlineColor  
 如果設定的清單檢視控制項的框線色彩[LVS_EX_BORDERSELECT](http://msdn.microsoft.com/library/windows/desktop/bb774739)延伸的視窗樣式設定。  
  
```  
COLORREF SetOutlineColor(COLORREF color);
```  
  
### <a name="parameters"></a>參數  
 `color`  
 新[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)結構，其中包含外框色彩。  
  
### <a name="return-value"></a>傳回值  
 先前**COLORREF**結構，其中包含外框色彩  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LVM_SETOUTLINECOLOR](http://msdn.microsoft.com/library/windows/desktop/bb761200)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namesetselectedcolumna--clistctrlsetselectedcolumn"></a><a name="setselectedcolumn"></a>CListCtrl::SetSelectedColumn  
 設定選取的資料行的清單檢視控制項。  
  
```  
LRESULT SetSelectedColumn(int iCol);
```  
  
### <a name="parameters"></a>參數  
 *iCol*  
 若要選取資料行的索引。  
  
### <a name="return-value"></a>傳回值  
 不使用傳回的值。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LVM_SETSELECTEDCOLUMN](http://msdn.microsoft.com/library/windows/desktop/bb761202)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namesetselectionmarka--clistctrlsetselectionmark"></a><a name="setselectionmark"></a>CListCtrl::SetSelectionMark  
 設定清單檢視控制項的選取範圍標記。  
  
```  
int SetSelectionMark(int iIndex);
```  
  
### <a name="parameters"></a>參數  
 `iIndex`  
 多個選取範圍中第一個項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 先前的選取範圍標記或如果沒有選取範圍標記為-1。  
  
### <a name="remarks"></a>備註  
 此成員函式實作 Win32 巨集的行為[ListView_SetSelectionMark](http://msdn.microsoft.com/library/windows/desktop/bb775112)所述，在[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
  請參閱範例[CListCtrl::GetSelectionMark](#getselectionmark)。  
  
##  <a name="a-namesettextbkcolora--clistctrlsettextbkcolor"></a><a name="settextbkcolor"></a>CListCtrl::SetTextBkColor  
 在清單檢視控制項中設定文字的背景色彩。  
  
```  
BOOL SetTextBkColor(COLORREF cr);
```  
  
### <a name="parameters"></a>參數  
 `cr`  
 A **COLORREF**指定新文字的背景色彩。 如需資訊，請參閱[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="example"></a>範例  

 
```cpp  
        // Use the 3D button face color for the background.
        COLORREF crBkColor = ::GetSysColor(COLOR_3DFACE);
        m_myListCtrl.SetTextBkColor(crBkColor);
        ASSERT(m_myListCtrl.GetTextBkColor() == crBkColor);
```

  
##  <a name="a-namesettextcolora--clistctrlsettextcolor"></a><a name="settextcolor"></a>CListCtrl::SetTextColor  
 將清單檢視控制項的文字色彩。  
  
```  
BOOL SetTextColor(COLORREF cr);
```  
  
### <a name="parameters"></a>參數  
 `cr`  
 A **COLORREF**指定新的文字色彩。 如需資訊，請參閱[COLORREF](http://msdn.microsoft.com/library/windows/desktop/dd183449)中[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="example"></a>範例  

 
```cpp  
    // Use the window text color for
    // the item text of the list view control.
    COLORREF crTextColor = ::GetSysColor(COLOR_WINDOWTEXT);
    m_myListCtrl.SetTextColor(crTextColor);
    ASSERT(m_myListCtrl.GetTextColor() == crTextColor);
```

  
##  <a name="a-namesettileinfoa--clistctrlsettileinfo"></a><a name="settileinfo"></a>CListCtrl::SetTileInfo  
 設定清單檢視控制項的並排顯示的資訊。  
  
```  
BOOL SetTileInfo(PLVTILEINFO pti);
```  
  
### <a name="parameters"></a>參數  
 *pti*  
 指標[LVTILEINFO](http://msdn.microsoft.com/library/windows/desktop/bb774766)結構，其中包含要設定的資訊。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LVM_SETTILEINFO](http://msdn.microsoft.com/library/windows/desktop/bb761210)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namesettileviewinfoa--clistctrlsettileviewinfo"></a><a name="settileviewinfo"></a>CListCtrl::SetTileViewInfo  
 設定並排顯示檢視中使用清單檢視控制項的資訊。  
  
```  
BOOL SetTileViewInfo(PLVTILEVIEWINFO ptvi);
```  
  
### <a name="parameters"></a>參數  
 `ptvi`  
 指標[LVTILEVIEWINFO](http://msdn.microsoft.com/library/windows/desktop/bb774768)結構，其中包含要設定的資訊。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**成功時， **FALSE**失敗。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LVM_SETTILEVIEWINFO](http://msdn.microsoft.com/library/windows/desktop/bb761212)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namesettooltipsa--clistctrlsettooltips"></a><a name="settooltips"></a>CListCtrl::SetToolTips  
 設定用來顯示工具提示的清單檢視控制項的工具提示控制項。  
  
```  
CToolTipCtrl* SetToolTips(CToolTipCtrl* pWndTip);
```  
  
### <a name="parameters"></a>參數  
 `pWndTip`  
 指標`CToolTipCtrl`將使用清單控制項的物件。  
  
### <a name="return-value"></a>傳回值  
 指標[CToolTipCtrl](ctooltipctrl-class.md)物件，其中包含的控制項，先前使用的工具提示或`NULL`如果先前不用任何工具提示。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[LVM_SETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb761216)所述，在[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
 若要不使用工具提示，指出`LVS_NOTOOLTIPS`樣式，當您建立`CListCtrl`物件。  
  
##  <a name="a-namesetviewa--clistctrlsetview"></a><a name="setview"></a>CListCtrl::SetView  
 設定清單檢視控制項的檢視。  
  
```  
DWORD SetView(int iView);
```  
  
### <a name="parameters"></a>參數  
 *iView*  
 要選取的檢視。  
  
### <a name="return-value"></a>傳回值  
 否則會傳回 1，表示成功，則為-1。 例如，如果檢視是無效，則傳回-1。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LVM_SETVIEW](http://msdn.microsoft.com/library/windows/desktop/bb761220)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namesetworkareasa--clistctrlsetworkareas"></a><a name="setworkareas"></a>CListCtrl::SetWorkAreas  
 設定位置顯示圖示，在清單檢視控制項中的區域。  
  
```  
void SetWorkAreas(
    int nWorkAreas,  
    LPRECT lpRect);
```  
  
### <a name="parameters"></a>參數  
 `nWorkAreas`  
 數目`RECT`結構 (或[CRect](../../atl-mfc-shared/reference/crect-class.md)物件) 中所指陣列`lpRect`。  
  
 `lpRect`  
 陣列中的位址`RECT`結構 (或`CRect`物件)，指定新的工作區的清單檢視控制項。 必須在用戶端座標中指定這些區域。 如果這個參數是**NULL**，工作區將會設定為控制項的用戶端區域。  
  
### <a name="remarks"></a>備註  
 此成員函式實作 Win32 巨集的行為[ListView_SetWorkAreas](http://msdn.microsoft.com/library/windows/desktop/bb775128)所述，在[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  

 
```cpp  
    // Remove all working areas.
    m_myListCtrl.SetWorkAreas(0, NULL);
```

  
##  <a name="a-namesortgroupsa--clistctrlsortgroups"></a><a name="sortgroups"></a>CListCtrl::SortGroups  
 排序清單檢視控制項中的群組識別碼是使用應用程式定義的比較函式。  
  
```  
BOOL SortGroups(
    PFNLVGROUPCOMPARE _pfnGroupCompare,  
    LPVOID _plv);
```  
  
### <a name="parameters"></a>參數  
 `_pfnGroupCompare`  
 群組比較函式的指標。  
  
 `_plv`  
 Void 指標。  
  
### <a name="return-value"></a>傳回值  
 成功時傳回 `true`，失敗時則傳回 `false`。  
  
### <a name="remarks"></a>備註  
 此成員函式模擬的功能[LVM_SORTGROUPS](http://msdn.microsoft.com/library/windows/desktop/bb761225)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
##  <a name="a-namesortitemsa--clistctrlsortitems"></a><a name="sortitems"></a>CListCtrl::SortItems  
 使用應用程式定義的比較函式，以排序清單檢視項目。  
  
```  
BOOL SortItems(
    PFNLVCOMPARE pfnCompare,  
    DWORD_PTR dwData);
```  
  
### <a name="parameters"></a>參數  
 [in] `pfnCompare`  
 應用程式定義的比較函式的位址。  
  
 排序作業呼叫的比較函式每次需要判斷兩個清單項目的相對順序。 比較函式必須是靜態成員的類別，或是獨立的函式不是任何類別的成員。  
  
 [in] `dwData`  
 應用程式定義的值傳遞至比較函式。  
  
### <a name="return-value"></a>傳回值  
 `true`如果方法成功。否則`false`。  
  
### <a name="remarks"></a>備註  
 這個方法會變更以反映新的順序的每個項目的索引。  
  
 比較函式， `pfnCompare`，具有下列格式︰  
  
```  
int CALLBACK CompareFunc(LPARAM lParam1,
    LPARAM lParam2,
    LPARAM lParamSort);
```  
如果第一個項目之前，應該還有第二個比較函式必須傳回負數值，為正整數值，如果第一個項目應該遵循第二個或如果兩個項目相等。  
  
 `lParam1`參數是比較時，第一個項目相關聯的 32 位元值和`lParam2`參數是第二個項目相關聯的值。 這種值中所指定的`lParam`成員的項目[LVITEM](http://msdn.microsoft.com/library/windows/desktop/bb774760)結構時插入到清單。 `lParamSort`參數等同於`dwData`值。  
  
 這個方法會傳送[LVM_SORTITEMS](http://msdn.microsoft.com/library/windows/desktop/bb761227)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 以下是簡單的比較函式會導致正在排序的項目及其`lParam`值。  
  
```cpp  
// Sort items by associated lParam
int CALLBACK CListCtrlDlg::MyCompareProc(LPARAM lParam1, LPARAM lParam2, 
    LPARAM lParamSort)
{
    UNREFERENCED_PARAMETER(lParamSort);
return (int)(lParam1 - lParam2);
}
```
  
```cpp  
// Sort the items by passing in the comparison function.
void CListCtrlDlg::Sort()
{
    m_myListCtrl.SortItems(&CListCtrlDlg::MyCompareProc, 0);
}
```
  
##  <a name="a-namesortitemsexa--clistctrlsortitemsex"></a><a name="sortitemsex"></a>CListCtrl::SortItemsEx  
 依目前的清單檢視控制項的項目使用的應用程式定義的比較函式。  
  
```  
BOOL SortItemsEx(
    PFNLVCOMPARE pfnCompare,   
    DWORD_PTR dwData);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `pfnCompare`|應用程式定義的比較函式的位址。<br /><br /> 排序作業呼叫的比較函式每次需要判斷兩個清單項目的相對順序。 比較函式必須是靜態成員的類別，或是獨立的函式不是任何類別的成員。|  
|[in] `dwData`|應用程式定義的值傳遞至比較函式。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會變更以反映新的順序的每個項目的索引。  
  
 比較函式， `pfnCompare`，具有下列格式︰  
  
```  
int CALLBACK CompareFunc(LPARAM lParam1,
    LPARAM lParam2,
    LPARAM lParamSort);
```  
此訊息就像[LVM_SORTITEMS](http://msdn.microsoft.com/library/windows/desktop/bb761227)，除了類型的資訊傳遞到比較函式。 在[LVM_SORTITEMS](http://msdn.microsoft.com/library/windows/desktop/bb761227)，`lParam1`和`lParam2`是要比較之項目的值。 在[LVM_SORTITEMSEX](http://msdn.microsoft.com/library/windows/desktop/bb761228)，`lParam1`是要比較的第一個項目目前的索引和`lParam2`是目前的第二個項目索引。 您可以傳送[LVM_GETITEMTEXT](http://msdn.microsoft.com/library/windows/desktop/bb761055)訊息，以擷取項目的詳細資訊。  
  
 如果第一個項目之前，應該還有第二個比較函式必須傳回負數值，為正整數值，如果第一個項目應該遵循第二個或如果兩個項目相等。  
  
> [!NOTE]
>  在排序過程中，清單檢視內容是不穩定。 如果回呼函式會傳送任何訊息至 list view 控制項以外的其他[LVM_GETITEM](http://msdn.microsoft.com/library/windows/desktop/bb774953)，是無法預期的結果。  
  
 這個方法會傳送[LVM_SORTITEMSEX](http://msdn.microsoft.com/library/windows/desktop/bb761228)訊息中所述[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數， `m_listCtrl`，也就是用來存取目前的清單檢視控制項。 下一個範例中會使用此變數。  
  
```cpp  
public:
    // Variable used to access the list control.
    CListCtrl m_listCtrl; 
```

  
### <a name="example"></a>範例  
 下列程式碼範例示範`SortItemEx`方法。 在先前章節中的這個程式碼範例，我們會建立顯示標題為"ClientID"和 「 成績 」，在報表檢視中的兩個資料行的清單檢視控制項。 下列程式碼範例會依資料表使用中 「 成績 」 資料行的值。  
  

```cpp  
// The ListCompareFunc() method is a global function used by SortItemEx().
int CALLBACK ListCompareFunc(
                             LPARAM lParam1, 
                             LPARAM lParam2, 
                             LPARAM lParamSort)
{
    CListCtrl* pListCtrl = (CListCtrl*) lParamSort;
    CString    strItem1 = pListCtrl->GetItemText(static_cast<int>(lParam1), 1);
    CString    strItem2 = pListCtrl->GetItemText(static_cast<int>(lParam2), 1)
    int x1 = _tstoi(strItem1.GetBuffer());
    int x2 = _tstoi(strItem2.GetBuffer());
    int result = 0;
    if ((x1 - x2) < 0)
        result = -1;
    else if ((x1 - x2) == 0)
        result = 0;
    else
        result = 1;

    return result;
}

void CCListCtrl_s2Dlg::OnBnClickedButton1()
{
    // SortItemsEx
    m_listCtrl.SortItemsEx( ListCompareFunc, (LPARAM)&m_listCtrl );
}
```

  
##  <a name="a-namesubitemhittesta--clistctrlsubitemhittest"></a><a name="subitemhittest"></a>CListCtrl::SubItemHitTest  
 如果有任何項目，是位於指定位置，決定哪一個清單檢視項目。  
  
```  
int SubItemHitTest(LPLVHITTESTINFO pInfo);
```  
  
### <a name="parameters"></a>參數  
 `pInfo`  
 指標[LVHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb774754)結構。  
  
### <a name="return-value"></a>傳回值  
 以一為索引的項目，或子項目、 進行測試 （如果有的話），否則為-1。  
  
### <a name="remarks"></a>備註  
 此成員函式實作 Win32 巨集的行為[ListView_SubItemHitTest](http://msdn.microsoft.com/library/windows/desktop/bb775135)所述，在[!INCLUDE[winSDK](./includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  

```cpp  
void CListCtrlDlg::OnDblClk(NMHDR* pNMHDR, LRESULT* pResult)
{
    UNREFERENCED_PARAMETER(pResult);
LPNMITEMACTIVATE pia = (LPNMITEMACTIVATE)pNMHDR;
    LVHITTESTINFO lvhti;

    // Clear the subitem text the user clicked on.
    lvhti.pt = pia->ptAction;
    m_myListCtrl.SubItemHitTest(&lvhti);

    if (lvhti.flags & LVHT_ONITEMLABEL)
    {
        m_myListCtrl.SetItemText(lvhti.iItem, lvhti.iSubItem, NULL);
    }
}
```

  
##  <a name="a-nameupdatea--clistctrlupdate"></a><a name="update"></a>CListCtrl::Update  
 強制重新繪製所指定的項目在清單檢視控制項`nItem`。  
  
```  
BOOL Update(int nItem);
```  
  
### <a name="parameters"></a>參數  
 `nItem`  
 要更新之項目的索引。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為&0;。  
  
### <a name="remarks"></a>備註  
 此函式也會排列清單檢視控制項，如果有`LVS_AUTOARRANGE`樣式。  
  
### <a name="example"></a>範例  
  請參閱範例[CListCtrl::GetSelectedCount](#getselectedcount)。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 ROWLIST](../../visual-cpp-samples.md)   
 [CWnd 類別](cwnd-class.md)   
 [階層架構圖表](../hierarchy-chart.md)   
 [CImageList 類別](cimagelist-class.md)


