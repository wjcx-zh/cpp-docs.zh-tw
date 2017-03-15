---
title: "CTreeCtrl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CTreeCtrl
dev_langs:
- C++
helpviewer_keywords:
- directory lists
- tree view controls
- file lists [C++]
- CTreeCtrl class
ms.assetid: 96e20031-6161-4143-8c12-8d1816c66d90
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 5341367b44540e2d0991fd61e52611826bbdcda1
ms.lasthandoff: 02/24/2017

---
# <a name="ctreectrl-class"></a>CTreeCtrl Class
提供 Windows 通用樹狀檢閱控制項的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CTreeCtrl : public CWnd  
```  
  
## <a name="members"></a>Members  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|說明|  
|----------|-----------------|  
|[CTreeCtrl::CTreeCtrl](#ctreectrl)|建構 `CTreeCtrl` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CTreeCtrl::Create](#create)|建立樹狀檢視控制項並將它附加`CTreeCtrl`物件。|  
|[CTreeCtrl::CreateDragImage](#createdragimage)|建立指定的樹狀檢視項目產生拖曳點陣圖。|  
|[CTreeCtrl::CreateEx](#createex)|使用指定的 Windows 延伸樣式建立樹狀目錄控制項，並附加至該`CTreeCtrl`物件。|  
|[CTreeCtrl::DeleteAllItems](#deleteallitems)|刪除樹狀檢視控制項中的所有項目。|  
|[CTreeCtrl::DeleteItem](#deleteitem)|刪除樹狀檢視控制項中的新項目。|  
|[CTreeCtrl::EditLabel](#editlabel)|編輯指定的樹狀檢視項目就地。|  
|[CTreeCtrl::EndEditLabelNow](#endeditlabelnow)|取消目前的樹狀檢視控制項中的樹狀檢視項目的標籤上編輯作業。|  
|[CTreeCtrl::EnsureVisible](#ensurevisible)|可確保樹狀檢視項目會顯示在其樹狀檢視控制項。|  
|[CTreeCtrl::Expand](#expand)|擴充，或摺疊，指定的樹狀檢視項目的子項目。|  
|[CTreeCtrl::GetBkColor](#getbkcolor)|擷取目前的背景色彩的控制項。|  
|[CTreeCtrl::GetCheck](#getcheck)|擷取樹狀目錄控制項項目的核取狀態。|  
|[CTreeCtrl::GetChildItem](#getchilditem)|擷取指定的樹狀檢視項目的子系。|  
|[CTreeCtrl::GetCount](#getcount)|擷取樹狀檢視控制項相關聯的樹狀目錄項目數目。|  
|[CTreeCtrl::GetDropHilightItem](#getdrophilightitem)|擷取拖放作業的目標。|  
|[CTreeCtrl::GetEditControl](#geteditcontrol)|擷取用來編輯指定的樹狀檢視項目編輯控制項的控制代碼。|  
|[CTreeCtrl::GetExtendedStyle](#getextendedstyle)|擷取目前的樹狀檢視控制項使用的延伸的樣式。|  
|[CTreeCtrl::GetFirstVisibleItem](#getfirstvisibleitem)|擷取指定的樹狀檢視項目的第一個可見的項目。|  
|[CTreeCtrl::GetImageList](#getimagelist)|擷取樹狀檢視控制項相關聯的影像清單控制代碼。|  
|[CTreeCtrl::GetIndent](#getindent)|擷取的位移 （以像素為單位） 的樹狀檢視項目從其父代。|  
|[CTreeCtrl::GetInsertMarkColor](#getinsertmarkcolor)|擷取用來繪製的樹狀檢視的插入標記的色彩。|  
|[CTreeCtrl::GetItem](#getitem)|擷取指定的樹狀檢視項目的屬性。|  
|[CTreeCtrl::GetItemData](#getitemdata)|傳回項目相關聯的 32 位元應用程式特定值。|  
|[CTreeCtrl::GetItemExpandedImageIndex](#getitemexpandedimageindex)|擷取映像，以指定的項目目前的樹狀檢視控制項的展開狀態時所顯示的索引。|  
|[CTreeCtrl::GetItemHeight](#getitemheight)|擷取目前的樹狀檢視項目高度。|  
|[CTreeCtrl::GetItemImage](#getitemimage)|擷取項目相關聯的映像。|  
|[CTreeCtrl::GetItemPartRect](#getitempartrect)|擷取指定之組件中目前的樹狀檢視控制項的指定項目，這個周框。|  
|[CTreeCtrl::GetItemRect](#getitemrect)|擷取週框的樹狀檢視項目。|  
|[CTreeCtrl::GetItemState](#getitemstate)|傳回項目的狀態。|  
|[CTreeCtrl::GetItemStateEx](#getitemstateex)|擷取目前的樹狀檢視控制項中指定的項目延伸的狀態。|  
|[CTreeCtrl::GetItemText](#getitemtext)|傳回項目的文字。|  
|[CTreeCtrl::GetLastVisibleItem](#getlastvisibleitem)|擷取目前的樹狀檢視控制項中的最後一個擴充項目。|  
|[CTreeCtrl::GetLineColor](#getlinecolor)|擷取目前的樹狀檢視控制項的線條色彩。|  
|[CTreeCtrl::GetNextItem](#getnextitem)|擷取符合指定的關聯性的下一個樹狀結構檢視項目。|  
|[CTreeCtrl::GetNextSiblingItem](#getnextsiblingitem)|擷取指定的樹狀檢視項目的下一個同層級。|  
|[CTreeCtrl::GetNextVisibleItem](#getnextvisibleitem)|擷取指定的樹狀檢視項目的下一個可見的項目。|  
|[CTreeCtrl::GetParentItem](#getparentitem)|擷取指定的樹狀檢視項目的父代。|  
|[CTreeCtrl::GetPrevSiblingItem](#getprevsiblingitem)|擷取指定的樹狀檢視項目的前一個同層級。|  
|[CTreeCtrl::GetPrevVisibleItem](#getprevvisibleitem)|擷取指定的樹狀檢視項目的上一個可見的項目。|  
|[CTreeCtrl::GetRootItem](#getrootitem)|擷取指定的樹狀檢視項目的根目錄。|  
|[CTreeCtrl::GetScrollTime](#getscrolltime)|擷取樹狀檢視控制項的捲動的最大時間。|  
|[CTreeCtrl::GetSelectedCount](#getselectedcount)|擷取目前的樹狀檢視控制項中選取的項目數目。|  
|[CTreeCtrl::GetSelectedItem](#getselecteditem)|擷取目前選取的樹狀檢視項目。|  
|[CTreeCtrl::GetTextColor](#gettextcolor)|擷取控制項的目前文字色彩。|  
|[CTreeCtrl::GetToolTips](#gettooltips)|擷取子樹狀檢視控制項所使用的工具提示控制項的控制代碼。|  
|[CTreeCtrl::GetVisibleCount](#getvisiblecount)|擷取樹狀檢視控制項相關聯的可見的樹狀目錄項目數目。|  
|[CTreeCtrl::HitTest](#hittest)|傳回相關的資料指標的目前位置`CTreeCtrl`物件。|  
|[CTreeCtrl::InsertItem](#insertitem)|在樹狀檢視控制項中插入新項目。|  
|[CTreeCtrl::ItemHasChildren](#itemhaschildren)|傳回非零，如果指定的項目具有子項目。|  
|[CTreeCtrl::MapAccIdToItem](#mapaccidtoitem)|將指定的存取範圍識別項對應至樹狀檢視中的項目目前的樹狀檢視控制項的控制代碼。|  
|[CTreeCtrl::MapItemToAccID](#mapitemtoaccid)|將指定的控制代碼對應至樹狀檢視中的項目目前的樹狀檢視控制項，為協助工具的識別碼。|  
|[CTreeCtrl::Select](#select)|選取、 捲動到檢視，或重新繪製指定的樹狀檢視項目。|  
|[CTreeCtrl::SelectDropTarget](#selectdroptarget)|做為拖放作業的目標來重新繪製樹狀目錄項目。|  
|[CTreeCtrl::SelectItem](#selectitem)|選取指定的樹狀檢視項目。|  
|[CTreeCtrl::SelectSetFirstVisible](#selectsetfirstvisible)|選取指定的樹狀檢視項目做為第一個可見的項目。|  
|[CTreeCtrl::SetAutoscrollInfo](#setautoscrollinfo)|設定目前的樹狀檢視控制項的自動捲動速率。|  
|[CTreeCtrl::SetBkColor](#setbkcolor)|設定控制項的背景色彩。|  
|[CTreeCtrl::SetCheck](#setcheck)|設定樹狀目錄控制項目核取狀態。|  
|[CTreeCtrl::SetExtendedStyle](#setextendedstyle)|設定目前的樹狀檢視控制項的延伸的樣式。|  
|[CTreeCtrl::SetImageList](#setimagelist)|設定樹狀檢視控制項相關聯的影像清單控制代碼。|  
|[CTreeCtrl::SetIndent](#setindent)|設定從其父代的位移 （以像素為單位） 的樹狀檢視項目。|  
|[CTreeCtrl::SetInsertMark](#setinsertmark)|設定在樹狀檢視控制項的插入標記。|  
|[CTreeCtrl::SetInsertMarkColor](#setinsertmarkcolor)|設定用來繪製的樹狀檢視的插入標記的色彩。|  
|[CTreeCtrl::SetItem](#setitem)|設定指定的樹狀檢視項目的屬性。|  
|[CTreeCtrl::SetItemData](#setitemdata)|設定項目相關聯的 32 位元應用程式特定值。|  
|[CTreeCtrl::SetItemExpandedImageIndex](#setitemexpandedimageindex)|設定要展開的狀態指定的項目目前的樹狀檢視控制項時所顯示之影像的索引。|  
|[CTreeCtrl::SetItemHeight](#setitemheight)|檢視項目會設定樹狀結構的高度。|  
|[CTreeCtrl::SetItemImage](#setitemimage)|將映像與項目產生關聯。|  
|[CTreeCtrl::SetItemState](#setitemstate)|設定項目的狀態。|  
|[CTreeCtrl::SetItemStateEx](#setitemstateex)|將指定的項目擴充的狀態設定目前的樹狀檢視控制項中。|  
|[CTreeCtrl::SetItemText](#setitemtext)|設定項目的文字。|  
|[CTreeCtrl::SetLineColor](#setlinecolor)|設定樹狀檢視控制項的目前線條色彩。|  
|[CTreeCtrl::SetScrollTime](#setscrolltime)|設定樹狀檢視控制項的捲動的最大時間。|  
|[CTreeCtrl::SetTextColor](#settextcolor)|設定控制項的文字色彩。|  
|[CTreeCtrl::SetToolTips](#settooltips)|設定工具提示控制項的樹狀檢視控制項的子系。|  
|[CTreeCtrl::ShowInfoTip](#showinfotip)|在目前的樹狀檢視控制項中顯示指定的項目資訊提示。|  
|[CTreeCtrl::SortChildren](#sortchildren)|排序指定的父項目子的系。|  
|[CTreeCtrl::SortChildrenCB](#sortchildrencb)|排序使用的應用程式定義的排序函式指定的父項目子系。|  
  
## <a name="remarks"></a>備註  
 「 樹狀檢視控制項 」 是這個視窗會顯示在磁碟上的階層式清單的項目，例如標題在文件中的索引，或檔案和目錄中的項目。 每個項目都包含標籤和選擇性點陣圖影像，因此，每個項目都可以擁有與自己相關的子項目清單。 使用者可以按一下項目以展開和摺疊子項目的關聯清單。  
  
 這個控制項 (並因此`CTreeCtrl`類別) 僅適用於 Windows 98 和 Windows NT 第 4 版下執行的程式和更新版本。  
  
 如需有關使用`CTreeCtrl`，請參閱︰  
  
- [控制項](../../mfc/controls-mfc.md)  
  
- [使用 CTreeCtrl](../../mfc/using-ctreectrl.md)  
  
- [樹狀檢視控制項參考](http://msdn.microsoft.com/library/windows/desktop/bb759988)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
-   知識庫文件 Q222905︰ 如何︰ 為 CTreeCtrl 顯示內容功能表  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CTreeCtrl`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcmn.h  
  
##  <a name="a-namecreatea--ctreectrlcreate"></a><a name="create"></a>CTreeCtrl::Create  
 如果您指定的樹狀目錄控制項在對話方塊範本，或如果您使用[CTreeView](../../mfc/reference/ctreeview-class.md)，建立對話方塊或檢視時自動建立樹狀目錄控制項。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,  
    const RECT& rect,  
    CWnd* pParentWnd,  
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 `dwStyle`  
 指定樹狀檢視控制項的樣式。 套用樣式 視窗中所述[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)，和任何組合[樹狀檢視控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760013)中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `rect`  
 指定樹狀檢視控制項的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構。  
  
 `pParentWnd`  
 指定樹狀檢視控制項的父視窗，通常`CDialog`。 它不得為**NULL**。  
  
 `nID`  
 指定樹狀檢視控制項的 id。  
  
### <a name="return-value"></a>傳回值  
 如果初始化成功則為非零否則為 0。  
  
### <a name="remarks"></a>備註  
 如果您想要建立做為某些其他視窗的子視窗的樹狀結構控制項中，使用**建立**成員函式。 如果您建立使用您建立的樹狀目錄控制項**建立**，您必須將它傳遞**WS_VISIBLE**，除了其他樹狀結構檢視樣式。  
  
 您建構`CTreeCtrl`兩個步驟。 第一次呼叫建構函式，然後呼叫**建立**，其建立樹狀檢視控制項，並將它附加`CTreeCtrl`物件。  
  
 若要建立具有延伸的視窗樣式的樹狀目錄控制項，呼叫[CreateEx](#createex)而不是**建立**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&1;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_1.cpp)]  
  
##  <a name="a-namecreateexa--ctreectrlcreateex"></a><a name="createex"></a>CTreeCtrl::CreateEx  
 呼叫此函式可建立的控制項 （子視窗），並將它與關聯`CTreeCtrl`物件。  
  
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
 指定正在建立的控制項的延伸的樣式。 如需延伸視窗樣式，請參閱`dwExStyle`參數[CreateWindowEx](http://msdn.microsoft.com/library/windows/desktop/ms632680)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `dwStyle`  
 指定樹狀檢視控制項的樣式。 套用樣式 視窗中所述[CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)，和任何組合[樹狀檢視控制項樣式](http://msdn.microsoft.com/library/windows/desktop/bb760013)中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `rect`  
 參考[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構描述的大小和位置來建立、 用戶端座標中的視窗的`pParentWnd`。  
  
 `pParentWnd`  
 是控制項的父視窗的指標。  
  
 `nID`  
 控制項的子視窗的 id。  
  
### <a name="return-value"></a>傳回值  
 如果成功的話，非零值為 0。  
  
### <a name="remarks"></a>備註  
 使用`CreateEx`而不是[建立](#create)套用延伸的視窗樣式，指定 Windows 延伸的樣式序言**WS_EX_**。  
  
##  <a name="a-namecreatedragimagea--ctreectrlcreatedragimage"></a><a name="createdragimage"></a>CTreeCtrl::CreateDragImage  
 呼叫此函式可在樹狀檢視控制項中建立特定的項目產生拖曳點陣圖、 建立點陣圖的影像清單以及加入點陣圖影像清單。  
  
```  
CImageList* CreateDragImage(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>參數  
 `hItem`  
 樹狀目錄項目拖曳至控制代碼。  
  
### <a name="return-value"></a>傳回值  
 指標影像清單拖曳點陣圖已加入其中，如果登錄成功。否則**NULL**。  
  
### <a name="remarks"></a>備註  
 應用程式使用的影像清單函式來顯示影像，當被拖曳的項目。  
  
 `CImageList`物件是永久的而且您必須刪除它完成。 例如:   
  
 [!code-cpp[NVC_MFC_CTreeCtrl #&2;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_2.cpp)]  
  
##  <a name="a-namectreectrla--ctreectrlctreectrl"></a><a name="ctreectrl"></a>CTreeCtrl::CTreeCtrl  
 建構 `CTreeCtrl` 物件。  
  
```  
CTreeCtrl();
```  
  
##  <a name="a-namedeleteallitemsa--ctreectrldeleteallitems"></a><a name="deleteallitems"></a>CTreeCtrl::DeleteAllItems  
 呼叫此函式可從樹狀檢視控制項中刪除所有項目。  
  
```  
BOOL DeleteAllItems();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&3;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_3.cpp)]  
  
##  <a name="a-namedeleteitema--ctreectrldeleteitem"></a><a name="deleteitem"></a>CTreeCtrl::DeleteItem  
 呼叫此函式可從樹狀檢視控制項中刪除項目。  
  
```  
BOOL DeleteItem(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>參數  
 `hItem`  
 要刪除的樹狀目錄項目的控制代碼。 如果*hitem*有**TVI_ROOT**值，從樹狀檢視控制項，會刪除所有的項目。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&4;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_4.cpp)]  
  
##  <a name="a-nameeditlabela--ctreectrleditlabel"></a><a name="editlabel"></a>CTreeCtrl::EditLabel  
 呼叫此函式可開始進行就地編輯的指定的項目的文字。  
  
```  
CEdit* EditLabel(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>參數  
 `hItem`  
 編輯樹狀目錄項目的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功，指標`CEdit`物件，用來編輯項目文字; 否則為**NULL**。  
  
### <a name="remarks"></a>備註  
 以單行編輯控制項包含的文字取代項目的文字來完成編輯。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&5;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_5.cpp)]  
  
##  <a name="a-nameendeditlabelnowa--ctreectrlendeditlabelnow"></a><a name="endeditlabelnow"></a>CTreeCtrl::EndEditLabelNow  
 最後一個標籤上的編輯作業的樹狀檢視中的項目目前的樹狀檢視控制項。  
  
```  
BOOL EndEditLabelNow(BOOL fCancelWithoutSave);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `fCancelWithoutSave`|`true`完成編輯作業之前捨棄變更樹狀檢視項目或`false`之前先儲存變更至樹狀檢視項目完成作業。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[TVM_ENDEDITLABELNOW](http://msdn.microsoft.com/library/windows/desktop/bb773564)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameensurevisiblea--ctreectrlensurevisible"></a><a name="ensurevisible"></a>CTreeCtrl::EnsureVisible  
 呼叫此函式可確保樹狀檢視項目，會顯示。  
  
```  
BOOL EnsureVisible(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>參數  
 `hItem`  
 可見的樹狀目錄項目的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 傳回**TRUE**系統如果捲動以確保指定的項目是可見的樹狀檢視控制項中的項目。 否則，傳回的值是**FALSE**。  
  
### <a name="remarks"></a>備註  
 必要時，函式展開父項目，或捲動樹狀檢視控制項，使項目為可見。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&6;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_6.cpp)]  
  
##  <a name="a-nameexpanda--ctreectrlexpand"></a><a name="expand"></a>CTreeCtrl::Expand  
 如果任何項目，與指定的父項目相關聯，請呼叫此函式來展開或摺疊子項目的清單。  
  
```  
BOOL Expand(
    HTREEITEM hItem,  
    UINT nCode);
```  
  
### <a name="parameters"></a>參數  
 `hItem`  
 展開樹狀目錄項目的控制代碼。  
  
 `nCode`  
 旗標，指出所要採取的動作類型。 這個旗標可以有下列值之一︰  
  
- `TVE_COLLAPSE`摺疊清單。  
  
- `TVE_COLLAPSERESET`摺疊清單，並移除子項目。 **TVIS_EXPANDEDONCE**狀態旗標會重設。 這個旗標必須搭配`TVE_COLLAPSE`旗標。  
  
- `TVE_EXPAND`展開清單。  
  
- `TVE_TOGGLE`如果目前已擴充，或將它擴充，如果目前摺疊，摺疊清單。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="example"></a>範例  
  請參閱範例[CTreeCtrl::EnsureVisible](#ensurevisible)。  
  
##  <a name="a-namegetbkcolora--ctreectrlgetbkcolor"></a><a name="getbkcolor"></a>CTreeCtrl::GetBkColor  
 此成員函式實作的 Win32 訊息的行為[TVM_GETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773570)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
COLORREF GetBkColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A **COLORREF**值，表示控制項的目前視窗背景色彩。 如果此值為-1，控制項就使用系統視窗色彩。 在此情況下，您可以使用`::GetSysColor(COLOR_WINDOW)`取得控制項使用的目前系統色彩。  
  
### <a name="example"></a>範例  
  請參閱範例[CTreeCtrl::SetTextColor](#settextcolor)。  
  
##  <a name="a-namegetchecka--ctreectrlgetcheck"></a><a name="getcheck"></a>CTreeCtrl::GetCheck  
 呼叫此成員函式擷取項目的核取狀態。  
  
```  
BOOL GetCheck(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>參數  
 `hItem`  
 **HTREEITEM**要接收的狀態資訊。  
  
### <a name="return-value"></a>傳回值  
 非零，如果選取的樹狀目錄控制項目;否則為 0。  
  
### <a name="example"></a>範例  
  請參閱範例[CTreeCtrl::SetCheck](#setcheck)。  
  
##  <a name="a-namegetchilditema--ctreectrlgetchilditem"></a><a name="getchilditem"></a>CTreeCtrl::GetChildItem  
 呼叫此函式可擷取的樹狀目錄檢視項目，是所指定的項目子系`hItem`。  
  
```  
HTREEITEM GetChildItem(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>參數  
 `hItem`  
 樹狀目錄項目的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功，子項目的控制代碼否則**NULL**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&7;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_7.cpp)]  
  
##  <a name="a-namegetcounta--ctreectrlgetcount"></a><a name="getcount"></a>CTreeCtrl::GetCount  
 呼叫此函式可擷取的樹狀檢視控制項中的項目計數。  
  
```  
UINT GetCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在樹狀檢視控制項中的項目數目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&8;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_8.cpp)]  
  
##  <a name="a-namegetdrophilightitema--ctreectrlgetdrophilightitem"></a><a name="getdrophilightitem"></a>CTreeCtrl::GetDropHilightItem  
 呼叫此函式可擷取項目是拖放作業的目標。  
  
```  
HTREEITEM GetDropHilightItem() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，卸除的項目控點否則**NULL**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&9;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_9.cpp)]  
  
##  <a name="a-namegeteditcontrola--ctreectrlgeteditcontrol"></a><a name="geteditcontrol"></a>CTreeCtrl::GetEditControl  
 呼叫此函式可擷取用來編輯樹狀檢視項目的文字編輯控制項的控制代碼。  
  
```  
CEdit* GetEditControl() const;  
```  
  
### <a name="return-value"></a>傳回值  
 用來編輯項目文字，如果成功，編輯控制項的指標否則**NULL**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&10;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_10.cpp)]  
  
##  <a name="a-namegetextendedstylea--ctreectrlgetextendedstyle"></a><a name="getextendedstyle"></a>CTreeCtrl::GetExtendedStyle  
 擷取目前的樹狀檢視控制項使用的延伸的樣式。  
  
```  
DWORD GetExtendedStyle() const;  
```  
  
### <a name="return-value"></a>傳回值  
 值，其中包含的位元組合 (OR) 目前的樹狀檢視控制項的延伸樣式。 如需詳細資訊，請參閱[樹狀檢視控制項擴充樣式](http://msdn.microsoft.com/library/windows/desktop/bb759981)。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[TVM_GETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb773580)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetfirstvisibleitema--ctreectrlgetfirstvisibleitem"></a><a name="getfirstvisibleitem"></a>CTreeCtrl::GetFirstVisibleItem  
 呼叫此函式可擷取樹狀檢視控制項的第一個可見項目。  
  
```  
HTREEITEM GetFirstVisibleItem() const;  
```  
  
### <a name="return-value"></a>傳回值  
 控制代碼的第一個可見的項目。否則**NULL**。  
  
### <a name="example"></a>範例  
  請參閱範例[CTreeCtrl::SetCheck](#setcheck)。  
  
##  <a name="a-namegetimagelista--ctreectrlgetimagelist"></a><a name="getimagelist"></a>CTreeCtrl::GetImageList  
 呼叫此函式可擷取一般的控制代碼或狀態影像清單與樹狀檢視控制項相關聯。  
  
```  
CImageList* GetImageList(UINT nImageList) const;  
```  
  
### <a name="parameters"></a>參數  
 `nImageList`  
 若要擷取的影像清單的型別。 影像清單可以是下列值之一︰  
  
- `TVSIL_NORMAL`擷取標準映像清單，其中包含樹狀檢視項目選取及未選取映像。  
  
- `TVSIL_STATE`擷取狀態影像清單，其中包含使用者定義狀態的樹狀目錄檢視項目的影像。  
  
### <a name="return-value"></a>傳回值  
 如果成功，控制項的影像清單的指標否則**NULL**。  
  
### <a name="remarks"></a>備註  
 在樹狀檢視控制項中的每個項目可以有一組與其相關聯的點陣圖影像。 選取項目，並另顯示當未選取此項目時，會顯示一個映像。 例如，項目可能會顯示開啟的資料夾，選取時，關閉的資料夾時未選取。  
  
 如需有關影像清單的詳細資訊，請參閱[CImageList](../../mfc/reference/cimagelist-class.md)類別。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&11;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_11.cpp)]  
  
##  <a name="a-namegetindenta--ctreectrlgetindent"></a><a name="getindent"></a>CTreeCtrl::GetIndent  
 呼叫此函式可擷取量，單位為像素，相對於其父項目的縮排項目子系。  
  
```  
UINT GetIndent() const;  
```  
  
### <a name="return-value"></a>傳回值  
 像素計算的縮排距離。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&12;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_12.cpp)]  
  
##  <a name="a-namegetinsertmarkcolora--ctreectrlgetinsertmarkcolor"></a><a name="getinsertmarkcolor"></a>CTreeCtrl::GetInsertMarkColor  
 此成員函式實作的 Win32 訊息的行為[TVM_GETINSERTMARKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773590)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
COLORREF GetInsertMarkColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A **COLORREF**值，其中包含目前的插入標記色彩。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&13;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_13.cpp)]  
  
##  <a name="a-namegetitema--ctreectrlgetitem"></a><a name="getitem"></a>CTreeCtrl::GetItem  
 呼叫此函式來擷取指定的樹狀檢視項目的屬性。  
  
```  
BOOL GetItem(TVITEM* pItem) const;  
```  
  
### <a name="parameters"></a>參數  
 `pItem`  
 指標[TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456)結構中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="example"></a>範例  
  請參閱範例[CTreeCtrl::DeleteItem](#deleteitem)。  
  
##  <a name="a-namegetitemdataa--ctreectrlgetitemdata"></a><a name="getitemdata"></a>CTreeCtrl::GetItemData  
 呼叫此函式可擷取與指定的項目相關聯的 32 位元應用程式特定值。  
  
```  
DWORD_PTR GetItemData(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>參數  
 `hItem`  
 要擷取其資料的項目控制代碼。  
  
### <a name="return-value"></a>傳回值  
 與所指定的項目相關聯的 32 位元應用程式特定值`hItem`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&14;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_14.cpp)]  
  
##  <a name="a-namegetitemexpandedimageindexa--ctreectrlgetitemexpandedimageindex"></a><a name="getitemexpandedimageindex"></a>CTreeCtrl::GetItemExpandedImageIndex  
 擷取映像，以指定的項目目前的樹狀檢視控制項的展開狀態時所顯示的索引。  
  
```  
int GetItemExpandedImageIndex(HTREEITEM hItem)const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `hItem`|控制代碼的樹狀檢視控制項項目。|  
  
### <a name="return-value"></a>傳回值  
 若要展開的狀態指定的項目時所顯示影像的索引。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[TVM_GETITEM](http://msdn.microsoft.com/library/windows/desktop/bb773596)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 訊息傳回[TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459)結構描述樹狀檢視控制項項目，這個方法會擷取`iExpandedImage`根據該結構的成員。  
  
##  <a name="a-namegetitemheighta--ctreectrlgetitemheight"></a><a name="getitemheight"></a>CTreeCtrl::GetItemHeight  
 此成員函式實作的 Win32 訊息的行為[TVM_GETITEMHEIGHT](http://msdn.microsoft.com/library/windows/desktop/bb773599)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
SHORT GetItemHeight() const;  
```  
  
### <a name="return-value"></a>傳回值  
 項目，像素為單位的高度。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&15;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_15.cpp)]  
  
##  <a name="a-namegetitemimagea--ctreectrlgetitemimage"></a><a name="getitemimage"></a>CTreeCtrl::GetItemImage  
 在樹狀檢視控制項中的每個項目可以有一組與其相關聯的點陣圖影像。  
  
```  
BOOL GetItemImage(
    HTREEITEM hItem,  
    int& nImage,  
    int& nSelectedImage) const;  
```  
  
### <a name="parameters"></a>參數  
 `hItem`  
 要擷取其映像的項目控制代碼。  
  
 `nImage`  
 整數，接收樹狀檢視控制項影像清單內的項目影像的索引。  
  
 `nSelectedImage`  
 整數，接收項目的樹狀檢視控制項影像清單中選取映像的索引。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 項目的標籤左邊顯示的影像。 選取項目，並另顯示當未選取此項目時，會顯示一個映像。 例如，項目可能會顯示開啟的資料夾，選取時，關閉的資料夾時未選取。  
  
 呼叫此函式可擷取的索引項目的影像和其樹狀檢視控制項影像清單中選取的映像。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&16;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_16.cpp)]  
  
##  <a name="a-namegetitempartrecta--ctreectrlgetitempartrect"></a><a name="getitempartrect"></a>CTreeCtrl::GetItemPartRect  
 擷取指定之組件中目前的樹狀檢視控制項的指定項目，這個周框。  
  
```  
BOOL GetItemPartRect(
    HTREEITEM hItem,   
    int nPart,   
    LPRECT lpRect)const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `hItem`|控制代碼的樹狀檢視控制項項目。|  
|[in] `nPart`|組件的識別碼。 必須設定為`TVGIPR_BUTTON`。|  
|[輸出] `lpRect`|指標[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)結構。 如果此方法成功，結構會接收部分所指定的矩形座標`hItem`和`nPart`。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 每個樹狀目錄控制項目限於圖形矩形。 只要按一下該矩形中的某個點時，項目即為*叫用*。 當矩形中的點按下時，所識別的項目，這個方法會傳回最大矩形`hItem`叫用參數。  
  
 這個方法會傳送`TVM_GETITEMPARTRECT`訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 如需詳細資訊，請參閱[TreeView_GetItemPartRect](http://msdn.microsoft.com/library/windows/desktop/bb773847)巨集。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數， `m_treeCtrl`，也就是用來存取目前樹狀檢視控制項。 程式碼範例也會定義一個不帶正負號的整數和 HTREEITEM 的數個變數。 下一個範例中使用這些變數。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會使用存取範圍識別項和[CTreeCtrl::MapAccIdToItem](#mapaccidtoitem)方法來擷取控制代碼的根樹狀檢視項目。 然後此範例會使用控制代碼和[CTreeCtrl::GetItemPartRect](#getitempartrect)方法，以 3D 周圍繪製矩形該項目。 在先前章節中的程式碼範例中，不會顯示，我們會建立包含根國家/地區為美國節點，賓州和美國華盛頓州的狀態的子節點，而這些狀態的城市的樹狀目錄項目樹狀檢視。 我們使用[CTreeCtrl::MapItemToAccID](#mapitemtoaccid)根樹狀檢視項目產生關聯的存取範圍識別項的方法。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&5;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_18.cpp)]  
  
##  <a name="a-namegetitemrecta--ctreectrlgetitemrect"></a><a name="getitemrect"></a>CTreeCtrl::GetItemRect  
 呼叫此函式來擷取週框`hItem`，並判斷它是否可見。  
  
```  
BOOL GetItemRect(
    HTREEITEM hItem,  
    LPRECT lpRect,  
    BOOL bTextOnly) const;  
```  
  
### <a name="parameters"></a>參數  
 `hItem`  
 樹狀檢視控制項項目的控制代碼。  
  
 `lpRect`  
 指標[RECT](http://msdn.microsoft.com/library/windows/desktop/dd162897)接收，這個周框的結構。 座標是相對於樹狀檢視控制項的左上角。  
  
 *bTextOnly*  
 如果這個參數不是零，這個周框包含項目的文字。 否則它會在樹狀檢視控制項中包含項目所佔的整行。  
  
### <a name="return-value"></a>傳回值  
 週框矩形中包含的項目是可見的如果為非零`lpRect`。 否則為 0 與`lpRect`未初始化。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&17;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_19.cpp)]  
  
##  <a name="a-namegetitemstatea--ctreectrlgetitemstate"></a><a name="getitemstate"></a>CTreeCtrl::GetItemState  
 傳回指定之項目的狀態`hItem`。  
  
```  
UINT GetItemState(
    HTREEITEM hItem,  
    UINT nStateMask) const;  
```  
  
### <a name="parameters"></a>參數  
 `hItem`  
 要擷取其狀態的項目控制代碼。  
  
 `nStateMask`  
 遮罩，指示要擷取的一或多個狀態。 如需有關可能的值為`nStateMask`，查看討論**狀態**和**stateMask**成員[TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456)結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>傳回值  
 A **UINT**保存 nStateMask 所指定之值的位元 OR。 如需可能的值，請參閱[CTreeCtrl::GetItem](#getitem)。 若要尋找特定狀態的值，執行位元的 AND 運算的狀態值和傳回值，如下列範例所示。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&18;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_20.cpp)]  
  
##  <a name="a-namegetitemstateexa--ctreectrlgetitemstateex"></a><a name="getitemstateex"></a>CTreeCtrl::GetItemStateEx  
 擷取目前的樹狀檢視控制項中指定的項目延伸的狀態。  
  
```  
UINT GetItemStateEx(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `hItem`|控制代碼的樹狀檢視控制項項目。|  
  
### <a name="return-value"></a>傳回值  
 擴充項目的狀態。 如需詳細資訊，請參閱`uStateEx`成員[TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459)結構。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[TVM_GETITEM](http://msdn.microsoft.com/library/windows/desktop/bb773596)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 訊息傳回[TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459)該結構描述樹狀檢視控制項項目，而且這個方法會擷取`uStateEx`根據該結構的成員。  
  
##  <a name="a-namegetitemtexta--ctreectrlgetitemtext"></a><a name="getitemtext"></a>CTreeCtrl::GetItemText  
 傳回指定之項目的文字`hItem`。  
  
```  
CString GetItemText(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>參數  
 `hItem`  
 要擷取其文字的項目控制代碼。  
  
### <a name="return-value"></a>傳回值  
 A`CString`物件，其中包含項目的文字。  
  
### <a name="example"></a>範例  
  請參閱範例[CTreeCtrl::GetNextItem](#getnextitem)。  
  
##  <a name="a-namegetlastvisibleitema--ctreectrlgetlastvisibleitem"></a><a name="getlastvisibleitem"></a>CTreeCtrl::GetLastVisibleItem  
 擷取目前的樹狀檢視控制項中的最後一個未展開的節點項目。  
  
```  
HTREEITEM GetLastVisibleItem() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果方法成功，將最後一個未展開的節點項控制代碼否則， `NULL`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[TVM_GETNEXTITEM](http://msdn.microsoft.com/library/windows/desktop/bb773622)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 如需詳細資訊，請參閱`TVGN_LASTVISIBLE`加上旗標`flag`該訊息的參數。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數， `m_treeCtrl`，也就是用來存取目前樹狀檢視控制項。 程式碼範例也會定義一個不帶正負號的整數和 HTREEITEM 的數個變數。 一或多個這些變數會用於下一個範例。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例擷取的最後一個未展開的樹狀檢視節點項目，控制代碼，然後繪製 3D 矩形以圍繞該項目。 在先前章節中的程式碼範例中，不會顯示，我們會建立包含根國家/地區為美國節點，賓州和美國華盛頓州的狀態的子節點，而這些狀態的城市的樹狀目錄項目樹狀檢視。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&6;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_21.cpp)]  
  
##  <a name="a-namegetlinecolora--ctreectrlgetlinecolor"></a><a name="getlinecolor"></a>CTreeCtrl::GetLineColor  
 此成員函式實作的 win32 訊息的行為[TVM_GETLINECOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773619)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
COLORREF GetLineColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 目前的線條色彩。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&19;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_22.cpp)]  
  
##  <a name="a-namegetnextitema--ctreectrlgetnextitem"></a><a name="getnextitem"></a>CTreeCtrl::GetNextItem  
 呼叫此函式可擷取的樹狀目錄檢視項目，具有指定的關聯性，並由`nCode`參數至`hItem`。  
  
```  
HTREEITEM GetNextItem(
    HTREEITEM hItem,  
    UINT nCode) const;  
```  
  
### <a name="parameters"></a>參數  
 `hItem`  
 樹狀目錄項目的控制代碼。  
  
 `nCode`  
 旗標，表示要關聯型別`hItem`。 這個旗標可以是下列值之一︰  
  
- `TVGN_CARET`擷取目前選取的項目。  
  
- `TVGN_CHILD`擷取第一個子項目所指定的項目`hItem`參數。  
  
- `TVGN_DROPHILITE`擷取拖放作業的目標項目。  
  
- `TVGN_FIRSTVISIBLE`擷取的第一個可見項目。  
  
- `TVGN_LASTVISIBLE`擷取樹狀目錄中的最後一個擴充項目。 這不會擷取最後一個項目顯示在樹狀檢視 視窗中。  
  
- `TVGN_NEXT`擷取下一個同層級項目。  
  
- `TVGN_NEXTVISIBLE`擷取指定的項目會遵循的下一個可見項目。  
  
- `TVGN_PARENT`擷取指定項目的父代。  
  
- `TVGN_PREVIOUS`擷取上一個同層級項目。  
  
- `TVGN_PREVIOUSVISIBLE`擷取位於指定的項目的第一個可見項目。  
  
- `TVGN_ROOT`擷取第一個子系項目，其中指定的項目是組件的根項目。  
  
### <a name="return-value"></a>傳回值  
 如果成功下, 一個項目的控制代碼否則**NULL**。  
  
### <a name="remarks"></a>備註  
 此函式會傳回**NULL**如果擷取的項目樹狀結構的根節點。 例如，如果您使用此郵件並`TVGN_PARENT`旗標的樹狀檢視的根節點，第一層子系上不會傳回訊息**NULL**。  
  
### <a name="example"></a>範例  
 如需使用`GetNextItem`在迴圈中，請參閱[CTreeCtrl::DeleteItem](#deleteitem)。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl #&20;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_23.cpp)]  
  
##  <a name="a-namegetnextsiblingitema--ctreectrlgetnextsiblingitem"></a><a name="getnextsiblingitem"></a>CTreeCtrl::GetNextSiblingItem  
 呼叫此函式可擷取下一個同層級`hItem`。  
  
```  
HTREEITEM GetNextSiblingItem(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>參數  
 `hItem`  
 樹狀目錄項目的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 控制代碼的下一個同層級項目中。否則**NULL**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&21;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_24.cpp)]  
  
##  <a name="a-namegetnextvisibleitema--ctreectrlgetnextvisibleitem"></a><a name="getnextvisibleitem"></a>CTreeCtrl::GetNextVisibleItem  
 呼叫此函式可擷取的下一個可見的項目`hItem`。  
  
```  
HTREEITEM GetNextVisibleItem(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>參數  
 `hItem`  
 樹狀目錄項目的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 控制代碼的下一個可見項目。否則**NULL**。  
  
### <a name="example"></a>範例  
  請參閱範例[CTreeCtrl::SetCheck](#setcheck)。  
  
##  <a name="a-namegetparentitema--ctreectrlgetparentitem"></a><a name="getparentitem"></a>CTreeCtrl::GetParentItem  
 呼叫此函式可擷取的父代`hItem`。  
  
```  
HTREEITEM GetParentItem(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>參數  
 `hItem`  
 樹狀目錄項目的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 與父項目，控制代碼否則**NULL**。  
  
### <a name="remarks"></a>備註  
 此函式會傳回**NULL**如果所指定項目的父代是樹狀結構的根節點。  
  
### <a name="example"></a>範例  
  請參閱範例[CTreeCtrl::EnsureVisible](#ensurevisible)。  
  
##  <a name="a-namegetprevsiblingitema--ctreectrlgetprevsiblingitem"></a><a name="getprevsiblingitem"></a>CTreeCtrl::GetPrevSiblingItem  
 呼叫此函式可擷取的前一個同層級`hItem`。  
  
```  
HTREEITEM GetPrevSiblingItem(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>參數  
 `hItem`  
 樹狀目錄項目的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 控制代碼的之前同層級。否則**NULL**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&22;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_25.cpp)]  
  
##  <a name="a-namegetprevvisibleitema--ctreectrlgetprevvisibleitem"></a><a name="getprevvisibleitem"></a>CTreeCtrl::GetPrevVisibleItem  
 呼叫此函式可擷取的上一個可見的項目`hItem`。  
  
```  
HTREEITEM GetPrevVisibleItem(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>參數  
 `hItem`  
 樹狀目錄項目的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 控制代碼的上一個可見項目。否則**NULL**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&23;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_26.cpp)]  
  
##  <a name="a-namegetrootitema--ctreectrlgetrootitem"></a><a name="getrootitem"></a>CTreeCtrl::GetRootItem  
 呼叫此函式可擷取樹狀檢視控制項的根項目。  
  
```  
HTREEITEM GetRootItem() const;  
```  
  
### <a name="return-value"></a>傳回值  
 控制代碼的根項目。否則**NULL**。  
  
### <a name="example"></a>範例  
  請參閱範例[CTreeCtrl::EditLabel](#editlabel)。  
  
##  <a name="a-namegetscrolltimea--ctreectrlgetscrolltime"></a><a name="getscrolltime"></a>CTreeCtrl::GetScrollTime  
 呼叫此成員函式擷取樹狀檢視控制項的捲動的最大時間。  
  
```  
UINT GetScrollTime() const;  
```  
  
### <a name="return-value"></a>傳回值  
 最大的捲軸的時間，以毫秒為單位。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 win32 訊息的行為[TVM_GETSCROLLTIME](http://msdn.microsoft.com/library/windows/desktop/bb773625)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetselectedcounta--ctreectrlgetselectedcount"></a><a name="getselectedcount"></a>CTreeCtrl::GetSelectedCount  
 擷取目前的樹狀檢視控制項中選取的項目數目。  
  
```  
UINT GetSelectedCount();
```  
  
### <a name="return-value"></a>傳回值  
 選取的項目數目。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[TVM_GETSELECTEDCOUNT](http://msdn.microsoft.com/library/windows/desktop/bb773629)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetselecteditema--ctreectrlgetselecteditem"></a><a name="getselecteditem"></a>CTreeCtrl::GetSelectedItem  
 呼叫此函式可擷取樹狀檢視控制項的目前選取的項目。  
  
```  
HTREEITEM GetSelectedItem() const;  
```  
  
### <a name="return-value"></a>傳回值  
 選取的項目，控制代碼否則**NULL**。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&24;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_27.cpp)]  
  
##  <a name="a-namegettextcolora--ctreectrlgettextcolor"></a><a name="gettextcolor"></a>CTreeCtrl::GetTextColor  
 此成員函式實作的 Win32 訊息的行為[TVM_GETTEXTCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773633)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
COLORREF GetTextColor() const;  
```  
  
### <a name="return-value"></a>傳回值  
 A **COLORREF**值，表示目前的文字色彩。 如果此值為-1，控制項使用系統色彩的文字色彩。  
  
### <a name="example"></a>範例  
  請參閱範例[CTreeCtrl::SetTextColor](#settextcolor)。  
  
##  <a name="a-namegettooltipsa--ctreectrlgettooltips"></a><a name="gettooltips"></a>CTreeCtrl::GetToolTips  
 此成員函式實作的 Win32 訊息的行為[TVM_GETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb773729)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
CToolTipCtrl* GetToolTips() const;  
```  
  
### <a name="return-value"></a>傳回值  
 指標[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)樹狀結構控制項中所使用的物件。 如果[建立](#create)成員函式會使用樣式**TVS_NOTOOLTIPS**，使用任何工具提示，以及**NULL**傳回。  
  
### <a name="remarks"></a>備註  
 實作 MFC`GetToolTips`傳回`CToolTipCtrl`物件，可由樹狀目錄控制項，而不是工具提示控制項的控制代碼。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&25;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_28.cpp)]  
  
##  <a name="a-namegetvisiblecounta--ctreectrlgetvisiblecount"></a><a name="getvisiblecount"></a>CTreeCtrl::GetVisibleCount  
 呼叫此函式可擷取的樹狀檢視控制項中可見的項目計數。  
  
```  
UINT GetVisibleCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 在樹狀檢視控制項中，可見的項目數目否則為-1。  
  
### <a name="example"></a>範例  
  請參閱範例[CTreeCtrl::SetCheck](#setcheck)。  
  
##  <a name="a-namehittesta--ctreectrlhittest"></a><a name="hittest"></a>CTreeCtrl::HitTest  
 呼叫此函式可判斷樹狀檢視控制項的指定相對於用戶端區域點的位置。  
  
```  
HTREEITEM HitTest(
    CPoint pt,  
    UINT* pFlags = NULL) const;  
  
HTREEITEM HitTest(TVHITTESTINFO* pHitTestInfo) const;  
```  
  
### <a name="parameters"></a>參數  
 `pt`  
 用戶端座標點的測試。  
  
 `pFlags`  
 接收的點擊測試結果的相關資訊的整數指標。 它可以是其中一個或多個值底下列出**旗標**< 備註 > 一節中的成員。  
  
 `pHitTestInfo`  
 位址[TVHITTESTINFO](http://msdn.microsoft.com/library/windows/desktop/bb773448)結構，其中包含要進行點擊測試，位置接收的點擊測試結果的相關資訊。  
  
### <a name="return-value"></a>傳回值  
 佔用指定的點的樹狀檢視項目控制代碼或**NULL**如果任何項目所不佔的點。  
  
### <a name="remarks"></a>備註  
 呼叫此函式時，`pt`參數會指定要測試的點的座標。 此函數會傳回指定的點處的項目控制代碼或**NULL**如果任何項目所不佔的點。 此外，`pFlags`參數會包含值，指出指定點的位置。 可能的值為：  
  
|||  
|-|-|  
|值|意義|  
|TVHT_ABOVE|用戶端區域上方。|  
|TVHT_BELOW|以下的用戶端區域。|  
|TVHT_NOWHERE|在工作區中，但最後一個項目下方。|  
|TVHT_ONITEM|上的點陣圖或項目相關聯的標籤。|  
|TVHT_ONITEMBUTTON|上一個項目相關聯的按鈕。|  
|TVHT_ONITEMICON|上一個項目相關聯的點陣圖。|  
|TVHT_ONITEMINDENT|在項目相關聯的縮排。|  
|TVHT_ONITEMLABEL|上一個項目相關聯的標籤 （字串）。|  
|TVHT_ONITEMRIGHT|在右邊的項目區域中。|  
|TVHT_ONITEMSTATEICON|狀態的圖示，以在使用者定義狀態的樹狀檢視項目。|  
|TVHT_TOLEFT|工作區的左邊。|  
|TVHT_TORIGHT|工作區的右邊。|  
|||  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&26;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_29.cpp)]  
  
##  <a name="a-nameinsertitema--ctreectrlinsertitem"></a><a name="insertitem"></a>CTreeCtrl::InsertItem  
 呼叫此函式可在樹狀檢視控制項中插入新項目。  
  
```  
HTREEITEM InsertItem(LPTVINSERTSTRUCT lpInsertStruct);

 
HTREEITEM InsertItem(
    UINT nMask,  
    LPCTSTR lpszItem,  
    int nImage,  
    int nSelectedImage,  
    UINT nState,  
    UINT nStateMask,  
    LPARAM lParam,  
    HTREEITEM hParent,  
    HTREEITEM hInsertAfter);

 
HTREEITEM InsertItem(
    LPCTSTR lpszItem,  
    HTREEITEM hParent = TVI_ROOT,  
    HTREEITEM hInsertAfter = TVI_LAST);

 
HTREEITEM InsertItem(
    LPCTSTR lpszItem,  
    int nImage,  
    int nSelectedImage,  
    HTREEITEM hParent = TVI_ROOT,  
    HTREEITEM hInsertAfter = TVI_LAST);
```  
  
### <a name="parameters"></a>參數  
 *lpInsertStruct*  
 指標`TVINSERTSTRUCT`，指定要插入樹狀結構檢視項目的屬性。  
  
 `nMask`  
 指定要設定屬性的整數。 請參閱`TVITEM`結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `lpszItem`  
 字串，包含的項目文字的位址。  
  
 `nImage`  
 在樹狀檢視控制項影像清單中的項目影像的索引。  
  
 `nSelectedImage`  
 項目的樹狀檢視控制項影像清單中選取映像的索引。  
  
 `nState`  
 指定的項目狀態的值。 請參閱樹狀檢視控制項目狀態中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]的適當狀態的清單。  
  
 `nStateMask`  
 指定要設定哪些狀態。 請參閱`TVITEM`結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `lParam`  
 與項目相關聯的 32 位元應用程式特定值。  
  
 `hParent`  
 插入的項目的父代的控制代碼。  
  
 *hInsertAfter*  
 要插入新項目後之項目的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功，將新項目的控制代碼否則**NULL**。  
  
### <a name="remarks"></a>備註  
 此範例示範您可能的想来插入的樹狀目錄控制項項目時，使用每個版本的函式。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&27;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_30.cpp)]  
  
##  <a name="a-nameitemhaschildrena--ctreectrlitemhaschildren"></a><a name="itemhaschildren"></a>CTreeCtrl::ItemHasChildren  
 使用此函數來判斷是否樹狀目錄項目指定`hItem`有子項目。  
  
```  
BOOL ItemHasChildren(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>參數  
 `hItem`  
 樹狀目錄項目的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 如果樹狀目錄項目指定為非零`hItem`有子系的項目; 如果不為 0。  
  
### <a name="remarks"></a>備註  
 因此，您可以使用如果[CTreeCtrl::GetChildItem](#getchilditem)來擷取這些子項目。  
  
### <a name="example"></a>範例  
  請參閱範例[CTreeCtrl::GetSelectedItem](#getselecteditem)。  
  
##  <a name="a-namemapaccidtoitema--ctreectrlmapaccidtoitem"></a><a name="mapaccidtoitem"></a>CTreeCtrl::MapAccIdToItem  
 將指定的存取範圍識別項對應至樹狀檢視中的項目目前的樹狀檢視控制項的控制代碼。  
  
```  
HTREEITEM MapAccIdToItem(UINT uAccId) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `uAccId`|在樹狀檢視項目中的項目可存取性識別項。|  
  
### <a name="return-value"></a>傳回值  
 樹狀檢視項目之控制代碼 ( `HTREEITEM`) 對應至`uAccId`參數。 如需詳細資訊，請參閱`hItem`成員[TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459)結構。  
  
### <a name="remarks"></a>備註  
 協助工具是應用程式，可以協助殘障人士使用電腦。 存取範圍識別項由`IAccessible`介面，以唯一地指定在視窗中的項目。 如需有關存取範圍識別項的詳細資訊，請搜尋 「 有關 Active Accessibility 支援 」 主題，網址[Microsoft Developer Network](http://go.microsoft.com/fwlink/linkid=56322)。  
  
 這個方法會傳送[TVM_MAPACCIDTOHTREEITEM](http://msdn.microsoft.com/library/windows/desktop/bb773734)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數， `m_treeCtrl`，也就是用來存取目前樹狀檢視控制項。 程式碼範例也會定義一個不帶正負號的整數和 HTREEITEM 的數個變數。 下一個範例中使用這些變數。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會使用存取範圍識別項和[CTreeCtrl::MapAccIdToItem](#mapaccidtoitem)方法來擷取控制代碼的根樹狀檢視項目。 此範例會使用控制代碼和[CTreeCtrl::GetItemPartRect](#getitempartrect)方法，以 3D 周圍繪製矩形該項目。 在先前章節中的程式碼範例中，不會顯示，我們會建立包含根國家/地區為美國節點，賓州和美國華盛頓州的狀態的子節點，而這些狀態的城市的樹狀目錄項目樹狀檢視。 我們使用[CTreeCtrl::MapItemToAccID](#mapitemtoaccid)根樹狀檢視項目產生關聯的存取範圍識別項的方法。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&5;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_18.cpp)]  
  
##  <a name="a-namemapitemtoaccida--ctreectrlmapitemtoaccid"></a><a name="mapitemtoaccid"></a>CTreeCtrl::MapItemToAccID  
 將指定的控制代碼的樹狀檢視中的項目目前的樹狀檢視控制項對應至可存取性識別項。  
  
```  
UINT MapItemToAccID(HTREEITEM hItem) const;  
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `hItem`|樹狀檢視中的項目控制項的控制代碼。 如需詳細資訊，請參閱`hItem`成員[TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459)結構。|  
  
### <a name="return-value"></a>傳回值  
 存取範圍識別項對應至`hItem`參數。  
  
### <a name="remarks"></a>備註  
 協助工具是應用程式，可以協助殘障人士使用電腦。 存取範圍識別項由`IAccessible`介面，以唯一地指定在視窗中的項目。 如需有關存取範圍識別項的詳細資訊，請搜尋 「 有關 Active Accessibility 支援 」 主題，網址[Microsoft Developer Network](http://go.microsoft.com/fwlink/linkid=56322)。  
  
 這個方法會傳送[TVM_MAPHTREEITEMTOACCID](http://msdn.microsoft.com/library/windows/desktop/bb773735)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數， `m_treeCtrl`，也就是用來存取目前樹狀檢視控制項。 程式碼範例也會定義一個不帶正負號的整數和 HTREEITEM 的數個變數。 下一個範例中使用這些變數。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會取得樹狀檢視控制項目的識別碼。 在先前章節中的程式碼範例中，不會顯示，我們會建立包含根國家/地區為美國節點，賓州和美國華盛頓州的狀態的子節點，而這些狀態的城市的樹狀目錄項目樹狀檢視。 這個程式碼範例會取得國家/地區根節點的唯一識別碼。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&2;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_31.cpp)]  
  
##  <a name="a-nameselecta--ctreectrlselect"></a><a name="select"></a>CTreeCtrl::Select  
 呼叫此函式來選取指定的樹狀檢視項目，項目捲動到檢視，或重新繪製用來表示拖放作業的目標的樣式項目。  
  
```  
BOOL Select(
    HTREEITEM hItem,  
    UINT nCode);
```  
  
### <a name="parameters"></a>參數  
 `hItem`  
 樹狀目錄項目的控制代碼。  
  
 `nCode`  
 要執行的動作類型。 這個參數可以是下列值之一︰  
  
- `TVGN_CARET`將選取項目設定為指定的項目。  
  
- `TVGN_DROPHILITE`在樣式中用來表示拖放作業的目標來重新繪製指定的項目。  
  
- `TVGN_FIRSTVISIBLE`垂直捲動樹狀檢視，使指定的項目是第一個可見的項目。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 如果`nCode`包含值`TVGN_CARET`，父視窗會收到**TVN_SELCHANGING**和**TVN_SELCHANGED**通知訊息。 此外，如果指定的項目是摺疊之父項目的子系，子項目的父代的清單會展開以顯示指定的項目。 在此情況下，父視窗會收到**TVN_ITEMEXPANDING**和**TVN_ITEMEXPANDED**通知訊息。  
  
### <a name="example"></a>範例  
  請參閱範例[CTreeCtrl::HitTest](#hittest)。  
  
##  <a name="a-nameselectdroptargeta--ctreectrlselectdroptarget"></a><a name="selectdroptarget"></a>CTreeCtrl::SelectDropTarget  
 呼叫此函式來重繪項目，用來表示拖放作業的目標的樣式。  
  
```  
BOOL SelectDropTarget(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>參數  
 `hItem`  
 樹狀目錄項目的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&9;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_9.cpp)]  
  
##  <a name="a-nameselectitema--ctreectrlselectitem"></a><a name="selectitem"></a>CTreeCtrl::SelectItem  
 呼叫此函式來選取指定的樹狀檢視項目。  
  
```  
BOOL SelectItem(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>參數  
 `hItem`  
 樹狀目錄項目的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 如果`hItem`是**NULL**，則此函式會不選取任何項目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&26;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_29.cpp)]  
  
##  <a name="a-nameselectsetfirstvisiblea--ctreectrlselectsetfirstvisible"></a><a name="selectsetfirstvisible"></a>CTreeCtrl::SelectSetFirstVisible  
 呼叫此函式可垂直捲動樹狀檢視，使指定的項目是第一個可見的項目。  
  
```  
BOOL SelectSetFirstVisible(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>參數  
 `hItem`  
 要設定為第一個可見項目的樹狀目錄項目的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 函式 視窗中，以將訊息傳送`TVM_SELECTITEM`和`TVGN_FIRSTVISIBLE`訊息參數。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&28;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_32.cpp)]  
  
##  <a name="a-namesetautoscrollinfoa--ctreectrlsetautoscrollinfo"></a><a name="setautoscrollinfo"></a>CTreeCtrl::SetAutoscrollInfo  
 設定目前的樹狀檢視控制項的自動捲動速率。  
  
```  
BOOL SetAutoscrollInfo(
    UINT uPixelsPerSec,   
    UINT uUpdateTime);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `uPixelsPerSec`|每秒来捲動的像素數目。|  
|[in] `uUpdateTime`|更新控制項的時間間隔。|  
  
### <a name="return-value"></a>傳回值  
 一律傳回 `true`。  
  
### <a name="remarks"></a>備註  
 自動捲動參數用來捲動到檢視看不到目前的項目。 樹狀檢視控制項必須要有`TVS_EX_AUTOHSCROLL`延伸樣式中所述[樹狀檢視控制項的延伸樣式](http://msdn.microsoft.com/library/windows/desktop/bb759981)。  
  
 這個方法會傳送[TVM_SETAUTOSCROLLINFO](http://msdn.microsoft.com/library/windows/desktop/bb773738)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數， `m_treeCtrl`，也就是用來存取目前樹狀檢視控制項。 程式碼範例也會定義一個不帶正負號的整數和 HTREEITEM 的數個變數。 下一個範例中使用這些變數。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會設定目前的樹狀檢視控制項的自動捲動行為。 在先前章節中的程式碼範例中，不會顯示，我們會建立包含根國家/地區為美國節點，賓州和美國華盛頓州的狀態的子節點，而這些狀態的城市的樹狀目錄項目樹狀檢視。 我們刻意進行樹狀檢視控制項窄，它必須自動捲動以顯示具有焦點的樹狀目錄項目。 程式碼範例會設定樹狀檢視控制項自動捲動，30 秒每隔 5 秒，直到項目樹狀結構檢視中的像素。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&4;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_33.cpp)]  
  
##  <a name="a-namesetbkcolora--ctreectrlsetbkcolor"></a><a name="setbkcolor"></a>CTreeCtrl::SetBkColor  
 此成員函式實作的 Win32 訊息的行為[TVM_SETBKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773741)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
COLORREF SetBkColor(COLORREF clr);
```  
  
### <a name="parameters"></a>參數  
 `clr`  
 A **COLORREF**值，其中包含新的背景色彩。 此值為-1，控制項將會回復為使用系統色彩的背景色彩。  
  
### <a name="return-value"></a>傳回值  
 A **COLORREF**值，表示目前的文字色彩。 如果此值為-1，控制項使用系統色彩的文字色彩。  
  
### <a name="example"></a>範例  
  請參閱範例[CTreeCtrl::SetTextColor](#settextcolor)。  
  
##  <a name="a-namesetchecka--ctreectrlsetcheck"></a><a name="setcheck"></a>CTreeCtrl::SetCheck  
 呼叫此成員函式設定樹狀目錄控制項項目的核取狀態。  
  
```  
BOOL SetCheck(
    HTREEITEM hItem,  
    BOOL fCheck = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `hItem`  
 **HTREEITEM**接收核取狀態變更。  
  
 `fCheck`  
 指出是否要選取或取消選取樹狀目錄控制項目。 根據預設，`SetCheck`設定要檢查的項目。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 何時會檢查樹狀目錄控制項目 (`fCheck`設為**TRUE**)，項目出現與相鄰的核取記號。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&29;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_34.cpp)]  
  
### <a name="example"></a>範例  
 若要使用核取方塊，設定 TVS_CHECKBOXES 之前填入樹狀目錄控制項。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl #&30;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_35.cpp)]  
  
##  <a name="a-namesetextendedstylea--ctreectrlsetextendedstyle"></a><a name="setextendedstyle"></a>CTreeCtrl::SetExtendedStyle  
 設定目前的樹狀檢視控制項的延伸的樣式。  
  
```  
DWORD SetExtendedStyle(
    DWORD dwExMask,   
    DWORD dwExStyles);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `dwExMask`|位元遮罩，指出這個方法會影響目前的樹狀檢視控制項中的樣式。 如果此參數為零，則會忽略的值和`dwExStyles`參數指派給樹狀檢視控制項。<br /><br /> 指定零或位元組合 (OR) 中所述的樣式[樹狀檢視控制項擴充樣式](http://msdn.microsoft.com/library/windows/desktop/bb759981)。|  
|[in] `dwExStyles`|位元遮罩，指定目前的樹狀檢視中的樣式，來控制對設定或清除。<br /><br /> 若要設定樣式的組合，指定的位元組合 (OR) 中所述的樣式[樹狀檢視控制項擴充樣式](http://msdn.microsoft.com/library/windows/desktop/bb759981)。 若要清除一組的樣式，指定零。|  
  
### <a name="return-value"></a>傳回值  
 包含先前擴充控制項樣式的值。  
  
### <a name="remarks"></a>備註  
 這個方法會清除在指定的樣式`dwExMask`參數，然後設定中指定的樣式`dwExStyles`參數。 只有對應的位元的延伸的樣式`dwExMask`變更。  
  
 這個方法會傳送[TVM_SETEXTENDEDSTYLE](http://msdn.microsoft.com/library/windows/desktop/bb773744)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數， `m_treeCtrl`，也就是用來存取目前樹狀檢視控制項。 程式碼範例也會定義一個不帶正負號的整數和 HTREEITEM 的數個變數。 下一個範例中使用這些變數。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例會將`TVS_EX_AUTOHSCROLL`延伸至目前的樹狀檢視控制項的樣式。 在先前章節中的程式碼範例中，不會顯示，我們會建立包含根國家/地區為美國節點，賓州和美國華盛頓州的狀態的子節點，而這些狀態的城市的樹狀目錄項目樹狀檢視。 我們刻意進行樹狀檢視控制項窄，它必須自動捲動以顯示具有焦點的樹狀目錄項目。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&3;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_36.cpp)]  
  
##  <a name="a-namesetimagelista--ctreectrlsetimagelist"></a><a name="setimagelist"></a>CTreeCtrl::SetImageList  
 呼叫此函式來設定標準或樹狀結構的狀態影像清單檢視控制項，並且重繪其使用新的映像的控制項。  
  
```  
CImageList* SetImageList(
    CImageList* pImageList,  
    int nImageListType);
```  
  
### <a name="parameters"></a>參數  
 `pImageList`  
 若要指派的影像清單的指標。 如果`pImageList`是**NULL**，從樹狀檢視控制項移除所有映像。  
  
 `nImageListType`  
 若要設定的影像清單的型別。 影像清單可以是下列值之一︰  
  
- `TVSIL_NORMAL`設定一般的映像清單，其中包含樹狀檢視項目選取及未選取映像。 您必須使用此狀態的重疊影像。  
  
- `TVSIL_STATE`設定狀態影像清單，其中包含使用者定義狀態的樹狀目錄檢視項目的影像。  
  
### <a name="return-value"></a>傳回值  
 指標上述映像清單中，如果有的話。否則**NULL**。  
  
### <a name="example"></a>範例  
  請參閱範例[CTreeCtrl::GetImageList](#getimagelist)。  
  
##  <a name="a-namesetindenta--ctreectrlsetindent"></a><a name="setindent"></a>CTreeCtrl::SetIndent  
 呼叫此函式來設定縮排的樹狀檢視控制項的寬度，並且重繪的控制項，以反映新的寬度。  
  
```  
void SetIndent(UINT nIndent);
```  
  
### <a name="parameters"></a>參數  
 `nIndent`  
 縮排的像素為單位的寬度。 如果`nIndent`小於超過系統定義最小寬度，新的寬度設定為系統定義的最小值。  
  
### <a name="example"></a>範例  
  請參閱範例[CTreeCtrl::GetIndent](#getindent)。  
  
##  <a name="a-namesetinsertmarka--ctreectrlsetinsertmark"></a><a name="setinsertmark"></a>CTreeCtrl::SetInsertMark  
 此成員函式實作的 Win32 訊息的行為[TVM_SETINSERTMARK](http://msdn.microsoft.com/library/windows/desktop/bb773753)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
BOOL SetInsertMark(
    HTREEITEM hItem,  
    BOOL fAfter = TRUE);
```  
  
### <a name="parameters"></a>參數  
 `hItem`  
 **HTREEITEM**指定插入標記將會放在哪一個項目。 如果這個引數是**NULL**，插入標記會移除。  
  
 *fAfter*  
 **BOOL**值，指定是否插入標記就會變成之前或之後指定的項目。 如果這個引數為非零，插入標記就會放在項目之後。 如果這個引數為零，插入標記會放在項目之前。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&31;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_37.cpp)]  
  
##  <a name="a-namesetinsertmarkcolora--ctreectrlsetinsertmarkcolor"></a><a name="setinsertmarkcolor"></a>CTreeCtrl::SetInsertMarkColor  
 此成員函式實作的 Win32 訊息的行為[TVM_SETINSERTMARKCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773755)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
COLORREF SetInsertMarkColor(COLORREF clrNew);
```  
  
### <a name="parameters"></a>參數  
 `clrNew`  
 A **COLORREF**值，其中包含新的插入標記色彩。  
  
### <a name="return-value"></a>傳回值  
 A **COLORREF**包含前一個插入標記色彩值。  
  
### <a name="example"></a>範例  
  請參閱範例[CTreeCtrl::GetInsertMarkColor](#getinsertmarkcolor)。  
  
##  <a name="a-namesetitema--ctreectrlsetitem"></a><a name="setitem"></a>CTreeCtrl::SetItem  
 呼叫此函式可設定的屬性指定的樹狀檢視項目。  
  
```  
BOOL SetItem(TVITEM* pItem);

 
BOOL SetItem(
    HTREEITEM hItem,  
    UINT nMask,  
    LPCTSTR lpszItem,  
    int nImage,  
    int nSelectedImage,  
    UINT nState,  
    UINT nStateMask,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>參數  
 `pItem`  
 指標[TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456)結構，其中包含新的項目屬性中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `hItem`  
 重新設定其屬性的項目控制代碼。 請參閱**hItem**成員`TVITEM`結構[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
 `nMask`  
 指定要設定屬性的整數。 請參閱**遮罩**成員`TVITEM`結構。  
  
 `lpszItem`  
 字串，包含的項目文字的位址。  
  
 `nImage`  
 在樹狀檢視控制項影像清單中的項目影像的索引。 請參閱`iImage`成員`TVITEM`結構。  
  
 `nSelectedImage`  
 項目的樹狀檢視控制項影像清單中選取映像的索引。 請參閱**iSelectedImage**成員`TVITEM`結構。  
  
 `nState`  
 指定的項目狀態的值。 請參閱**狀態**成員`TVITEM`結構。  
  
 `nStateMask`  
 指定要設定哪些狀態。 請參閱**stateMask**成員`TVITEM`結構。  
  
 `lParam`  
 與項目相關聯的 32 位元應用程式特定值。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 在`TVITEM`結構**hItem**成員會識別項目，而**遮罩**成員指定要設定屬性。  
  
 如果**遮罩**成員或`nMask`參數會指定`TVIF_TEXT`值**pszText**成員或`lpszItem`是以 null 終止字串的位址和**cchTextMax**成員會被忽略。 如果**遮罩**(或`nMask`) 指定`TVIF_STATE`值**stateMask**成員或`nStateMask`參數會指定哪一個項目狀態變更和**狀態**成員或`nState`參數會包含這些狀態的值。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&32;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_38.cpp)]  
  
##  <a name="a-namesetitemdataa--ctreectrlsetitemdata"></a><a name="setitemdata"></a>CTreeCtrl::SetItemData  
 呼叫此函式可設定與指定的項目相關聯的 32 位元應用程式特定值。  
  
```  
BOOL SetItemData(
    HTREEITEM hItem,  
    DWORD_PTR dwData);
```  
  
### <a name="parameters"></a>參數  
 `hItem`  
 要擷取其資料的項目控制代碼。  
  
 `dwData`  
 與所指定的項目相關聯的 32 位元應用程式特定值`hItem`。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&33;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_39.cpp)]  
  
##  <a name="a-namesetitemexpandedimageindexa--ctreectrlsetitemexpandedimageindex"></a><a name="setitemexpandedimageindex"></a>CTreeCtrl::SetItemExpandedImageIndex  
 設定要展開的狀態指定的項目目前的樹狀檢視控制項時所顯示之影像的索引。  
  
```  
BOOL SetItemExpandedImageIndex(
    HTREEITEM hItem,   
    int iExpandedImage);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `hItem`|控制代碼的樹狀檢視控制項項目。|  
|[in] `iExpandedImage`|若要展開的狀態指定的項目時所顯示影像的索引。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[TVM_SETITEM](http://msdn.microsoft.com/library/windows/desktop/bb773758)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 這個方法會指派`iExpandedImage`參數`iExpandedImage`成員[TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459)結構，然後使用該結構中的訊息。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數， `m_treeCtrl`，也就是用來存取目前樹狀檢視控制項。 程式碼範例也會定義一個不帶正負號的整數和 HTREEITEM 的數個變數。 下一個範例中使用這些變數。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例是簡單的測試，來判斷是否[CTreeCtrl::GetItemExpandedImageIndex](#getitemexpandedimageindex)方法會傳回所設定的值[CTreeCtrl::SetItemExpandedImageIndex](#setitemexpandedimageindex)方法。 在先前章節中的程式碼範例中，不會顯示，我們會建立包含根國家/地區為美國節點，賓州和美國華盛頓州的狀態的子節點，而這些狀態的城市的樹狀目錄項目樹狀檢視。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&8;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_40.cpp)]  
  
##  <a name="a-namesetitemheighta--ctreectrlsetitemheight"></a><a name="setitemheight"></a>CTreeCtrl::SetItemHeight  
 此成員函式實作的 Win32 訊息的行為[TVM_SETITEMHEIGHT](http://msdn.microsoft.com/library/windows/desktop/bb773761)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
SHORT SetItemHeight(SHORT cyHeight);
```  
  
### <a name="parameters"></a>參數  
 `cyHeight`  
 在樹狀結構檢視中，像素為單位指定每個項目的新的高度。 如果這個引數小於影像的高度，則它會設為影像的高度。 如果這個引數不是即使，會四捨五入至最接近甚至值。 這個引數為-1，控制項將會回復為使用其預設值的項目高度。  
  
### <a name="return-value"></a>傳回值  
 先前的項目，像素為單位的高度。  
  
### <a name="example"></a>範例  
  請參閱範例[CTreeCtrl::GetItemHeight](#getitemheight)。  
  
##  <a name="a-namesetitemimagea--ctreectrlsetitemimage"></a><a name="setitemimage"></a>CTreeCtrl::SetItemImage  
 將映像與項目產生關聯。  
  
```  
BOOL SetItemImage(
    HTREEITEM hItem,  
    int nImage,  
    int nSelectedImage);
```  
  
### <a name="parameters"></a>參數  
 `hItem`  
 若要設定其映像的項目控制代碼。  
  
 `nImage`  
 在樹狀檢視控制項影像清單中的項目影像的索引。  
  
 `nSelectedImage`  
 項目的樹狀檢視控制項影像清單中選取映像的索引。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 在樹狀檢視控制項中的每個項目可以有一組與其相關聯的點陣圖影像。 項目的標籤左邊顯示的影像。 選取項目，並另顯示當未選取此項目時，會顯示一個映像。 例如，項目可能會顯示開啟的資料夾，選取時，關閉的資料夾時未選取。  
  
 呼叫此函式可設定的索引項目的影像和其樹狀檢視控制項影像清單中選取的映像。  
  
 如需有關映像的詳細資訊，請參閱[CImageList](../../mfc/reference/cimagelist-class.md)。  
  
### <a name="example"></a>範例  
  請參閱範例[CTreeCtrl::GetItemImage](#getitemimage)。  
  
##  <a name="a-namesetitemstatea--ctreectrlsetitemstate"></a><a name="setitemstate"></a>CTreeCtrl::SetItemState  
 設定指定之項目的狀態`hItem`。  
  
```  
BOOL SetItemState(
    HTREEITEM hItem,  
    UINT nState,  
    UINT nStateMask);
```  
  
### <a name="parameters"></a>參數  
 `hItem`  
 若要設定其狀態的項目控制代碼。  
  
 `nState`  
 指定項目的新狀態。  
  
 `nStateMask`  
 指定要變更何種狀態。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 狀態資訊，請參閱[CTreeCtrl::GetItem](#getitem)。  
  
### <a name="example"></a>範例  
  請參閱範例[CTreeCtrl::GetItemState](#getitemstate)。  
  
##  <a name="a-namesetitemstateexa--ctreectrlsetitemstateex"></a><a name="setitemstateex"></a>CTreeCtrl::SetItemStateEx  
 將指定的項目擴充的狀態設定目前的樹狀檢視控制項中。  
  
```  
BOOL SetItemStateEx(
    HTREEITEM hItem,   
    UINT uStateEx);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `hItem`|控制代碼的樹狀檢視控制項項目。|  
|[in] `uStateEx`|擴充項目的狀態。 如需詳細資訊，請參閱`uStateEx`成員[TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459)結構。|  
  
### <a name="return-value"></a>傳回值  
 如果此方法成功為 `true`；否則為 `false`。  
  
### <a name="remarks"></a>備註  
 這個方法會傳送[TVM_SETITEM](http://msdn.microsoft.com/library/windows/desktop/bb773758)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。 這個方法會指派`uStateEx`參數`uStateEx`成員[TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459)結構，然後使用該結構中的訊息。  
  
### <a name="example"></a>範例  
 下列程式碼範例會定義變數， `m_treeCtrl`，也就是用來存取目前樹狀檢視控制項。 程式碼範例也會定義一個不帶正負號的整數和 HTREEITEM 的數個變數。 下一個範例中使用這些變數。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&1;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_17.h)]  
  
### <a name="example"></a>範例  
 下列程式碼範例將設定樹狀檢視項目已停用狀態。 在先前章節中的程式碼範例中，不會顯示，我們會建立包含根國家/地區為美國節點，賓州和美國華盛頓州的狀態的子節點，而這些狀態的城市的樹狀目錄項目樹狀檢視。 這個程式碼範例將賓州節點設定已停用狀態。  
  
 [!code-cpp[NVC_MFC_CTreeCtrl_s&#1;&7;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_41.cpp)]  
  
##  <a name="a-namesetitemtexta--ctreectrlsetitemtext"></a><a name="setitemtext"></a>CTreeCtrl::SetItemText  
 設定指定之項目的文字`hItem`。  
  
```  
BOOL SetItemText(
    HTREEITEM hItem,  
    LPCTSTR lpszItem);
```  
  
### <a name="parameters"></a>參數  
 `hItem`  
 若要設定其文字的項目控制代碼。  
  
 `lpszItem`  
 字串，包含項目的新文字的位址  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&34;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_42.cpp)]  
  
##  <a name="a-namesetlinecolora--ctreectrlsetlinecolor"></a><a name="setlinecolor"></a>CTreeCtrl::SetLineColor  
 呼叫此成員函式設定樹狀檢視控制項的目前線條色彩。  
  
```  
COLORREF SetLineColor(COLORREF clrNew = CLR_DEFAULT);
```  
  
### <a name="parameters"></a>參數  
 `clrNew`  
 新的線條色彩。  
  
### <a name="return-value"></a>傳回值  
 先前的線條色彩。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 win32 訊息的行為[TVM_SETLINECOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773764)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&35;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_43.cpp)]  
  
##  <a name="a-namesetscrolltimea--ctreectrlsetscrolltime"></a><a name="setscrolltime"></a>CTreeCtrl::SetScrollTime  
 呼叫此成員函式可設定樹狀檢視控制項的最大的捲軸的時間。  
  
```  
UINT SetScrollTime(UINT uScrollTime);
```  
  
### <a name="parameters"></a>參數  
 *uScrollTime*  
 新最大的捲軸的時間，以毫秒為單位。 如果此值為小於 100，就會四捨五入到 100。  
  
### <a name="return-value"></a>傳回值  
 上一個最大的捲軸的時間，以毫秒為單位。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 win32 訊息的行為[TVM_SETSCROLLTIME](http://msdn.microsoft.com/library/windows/desktop/bb773767)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesettextcolora--ctreectrlsettextcolor"></a><a name="settextcolor"></a>CTreeCtrl::SetTextColor  
 此成員函式實作的 Win32 訊息的行為[TVM_SETTEXTCOLOR](http://msdn.microsoft.com/library/windows/desktop/bb773769)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
COLORREF SetTextColor(COLORREF clr);
```  
  
### <a name="parameters"></a>參數  
 `clr`  
 A **COLORREF**值，其中包含新的文字色彩。 這個引數為-1，控制項將會回復為使用系統色彩的文字色彩。  
  
### <a name="return-value"></a>傳回值  
 A **COLORREF**值，表示先前的文字色彩。 如果此值為-1，控制項使用系統色彩的文字色彩。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&36;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_44.cpp)]  
  
##  <a name="a-namesettooltipsa--ctreectrlsettooltips"></a><a name="settooltips"></a>CTreeCtrl::SetToolTips  
 此成員函式實作的 Win32 訊息的行為[TVM_SETTOOLTIPS](http://msdn.microsoft.com/library/windows/desktop/bb773772)所述，在[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
```  
CToolTipCtrl* SetToolTips(CToolTipCtrl* pWndTip);
```  
  
### <a name="parameters"></a>參數  
 `pWndTip`  
 指標[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)樹狀目錄控制項將會使用的物件。  
  
### <a name="return-value"></a>傳回值  
 指標[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)物件，其中包含的控制項，先前使用的工具提示或**NULL**如果先前不用任何工具提示。  
  
### <a name="remarks"></a>備註  
 若要使用的工具提示，指示**TVS_NOTOOLTIPS**樣式，當您建立`CTreeCtrl`物件。  
  
### <a name="example"></a>範例  
  請參閱範例[CTreeCtrl::GetToolTips](#gettooltips)。  
  
##  <a name="a-nameshowinfotipa--ctreectrlshowinfotip"></a><a name="showinfotip"></a>CTreeCtrl::ShowInfoTip  
 在目前的樹狀檢視控制項中顯示指定的項目資訊提示。  
  
```  
void ShowInfoTip(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>參數  
  
|參數|描述|  
|---------------|-----------------|  
|[in] `hItem`|樹狀檢視中的項目控制項的控制代碼。 如需詳細資訊，請參閱`hItem`成員[TVITEMEX](http://msdn.microsoft.com/library/windows/desktop/bb773459)結構。|  
  
### <a name="remarks"></a>備註  
 如需有關工具提示和資訊提示之間的差異的詳細資訊，請搜尋 「 工具提示和資訊提示 」 主題，網址[Microsoft Developer Network](http://go.microsoft.com/fwlink/linkid=56322)。  
  
 這個方法會傳送[TVM_SHOWINFOTIP](http://msdn.microsoft.com/library/windows/desktop/bb773779)訊息中所述[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesortchildrena--ctreectrlsortchildren"></a><a name="sortchildren"></a>CTreeCtrl::SortChildren  
 呼叫此函式可依字母順序排序樹狀檢視控制項中指定的父項目的子項目。  
  
```  
BOOL SortChildren(HTREEITEM hItem);
```  
  
### <a name="parameters"></a>參數  
 `hItem`  
 父項目，其中的子系項目是要排序的控制代碼。 如果`hItem`是**NULL**，排序會繼續從樹狀結構的根目錄。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 `SortChildren`將遞迴樹狀目錄中。只有的直接子系`hItem`將排序。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&37;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_45.cpp)]  
  
##  <a name="a-namesortchildrencba--ctreectrlsortchildrencb"></a><a name="sortchildrencb"></a>CTreeCtrl::SortChildrenCB  
 呼叫此函式來使用應用程式定義的回呼函式來比較項目樹狀結構檢視項目排序。  
  
```  
BOOL SortChildrenCB(LPTVSORTCB pSort);
```  
  
### <a name="parameters"></a>參數  
 *pSort*  
 指標[TVSORTCB](http://msdn.microsoft.com/library/windows/desktop/bb773462)結構。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="remarks"></a>備註  
 結構的比較函式， **lpfnCompare**，必須傳回負值正如果第一個項目應該在第二個值，如果第一個項目應該遵循第二個，或如果兩個項目相等。  
  
 `lParam1`和`lParam2`參數會對應至**lParam**成員[TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456)結構的兩個項目進行比較。 `lParamSort`參數相當於**lParam**成員`TV_SORTCB`結構。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTreeCtrl #&38;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_46.cpp)]  
  
 [!code-cpp[NVC_MFC_CTreeCtrl #&39;](../../mfc/reference/codesnippet/cpp/ctreectrl-class_47.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [MFC 範例 CMNCTRL1](../../visual-cpp-samples.md)   
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CImageList 類別](../../mfc/reference/cimagelist-class.md)

