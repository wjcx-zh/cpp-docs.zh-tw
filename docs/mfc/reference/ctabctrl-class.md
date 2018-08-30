---
title: CTabCtrl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CTabCtrl
- AFXCMN/CTabCtrl
- AFXCMN/CTabCtrl::CTabCtrl
- AFXCMN/CTabCtrl::AdjustRect
- AFXCMN/CTabCtrl::Create
- AFXCMN/CTabCtrl::CreateEx
- AFXCMN/CTabCtrl::DeleteAllItems
- AFXCMN/CTabCtrl::DeleteItem
- AFXCMN/CTabCtrl::DeselectAll
- AFXCMN/CTabCtrl::DrawItem
- AFXCMN/CTabCtrl::GetCurFocus
- AFXCMN/CTabCtrl::GetCurSel
- AFXCMN/CTabCtrl::GetExtendedStyle
- AFXCMN/CTabCtrl::GetImageList
- AFXCMN/CTabCtrl::GetItem
- AFXCMN/CTabCtrl::GetItemCount
- AFXCMN/CTabCtrl::GetItemRect
- AFXCMN/CTabCtrl::GetItemState
- AFXCMN/CTabCtrl::GetRowCount
- AFXCMN/CTabCtrl::GetToolTips
- AFXCMN/CTabCtrl::HighlightItem
- AFXCMN/CTabCtrl::HitTest
- AFXCMN/CTabCtrl::InsertItem
- AFXCMN/CTabCtrl::RemoveImage
- AFXCMN/CTabCtrl::SetCurFocus
- AFXCMN/CTabCtrl::SetCurSel
- AFXCMN/CTabCtrl::SetExtendedStyle
- AFXCMN/CTabCtrl::SetImageList
- AFXCMN/CTabCtrl::SetItem
- AFXCMN/CTabCtrl::SetItemExtra
- AFXCMN/CTabCtrl::SetItemSize
- AFXCMN/CTabCtrl::SetItemState
- AFXCMN/CTabCtrl::SetMinTabWidth
- AFXCMN/CTabCtrl::SetPadding
- AFXCMN/CTabCtrl::SetToolTips
dev_langs:
- C++
helpviewer_keywords:
- CTabCtrl [MFC], CTabCtrl
- CTabCtrl [MFC], AdjustRect
- CTabCtrl [MFC], Create
- CTabCtrl [MFC], CreateEx
- CTabCtrl [MFC], DeleteAllItems
- CTabCtrl [MFC], DeleteItem
- CTabCtrl [MFC], DeselectAll
- CTabCtrl [MFC], DrawItem
- CTabCtrl [MFC], GetCurFocus
- CTabCtrl [MFC], GetCurSel
- CTabCtrl [MFC], GetExtendedStyle
- CTabCtrl [MFC], GetImageList
- CTabCtrl [MFC], GetItem
- CTabCtrl [MFC], GetItemCount
- CTabCtrl [MFC], GetItemRect
- CTabCtrl [MFC], GetItemState
- CTabCtrl [MFC], GetRowCount
- CTabCtrl [MFC], GetToolTips
- CTabCtrl [MFC], HighlightItem
- CTabCtrl [MFC], HitTest
- CTabCtrl [MFC], InsertItem
- CTabCtrl [MFC], RemoveImage
- CTabCtrl [MFC], SetCurFocus
- CTabCtrl [MFC], SetCurSel
- CTabCtrl [MFC], SetExtendedStyle
- CTabCtrl [MFC], SetImageList
- CTabCtrl [MFC], SetItem
- CTabCtrl [MFC], SetItemExtra
- CTabCtrl [MFC], SetItemSize
- CTabCtrl [MFC], SetItemState
- CTabCtrl [MFC], SetMinTabWidth
- CTabCtrl [MFC], SetPadding
- CTabCtrl [MFC], SetToolTips
ms.assetid: 42e4aff6-46ae-4b2c-beaa-d1dce8d82138
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5c9ea52115cf5921aab4cc7f6cefb939f3e6e461
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43207176"
---
# <a name="ctabctrl-class"></a>CTabCtrl 類別
提供 Windows 通用索引標籤控制項的功能。  
  
## <a name="syntax"></a>語法  
  
```  
class CTabCtrl : public CWnd  
```  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[CTabCtrl::CTabCtrl](#ctabctrl)|建構 `CTabCtrl` 物件。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CTabCtrl::AdjustRect](#adjustrect)|計算索引標籤控制項的顯示區域，指定視窗的矩形中，或計算視窗矩形，就會對應至指定的顯示區域。|  
|[CTabCtrl::Create](#create)|建立索引標籤控制項，並將它附加至執行個體的`CTabCtrl`物件。|  
|[CTabCtrl::CreateEx](#createex)|使用指定的 Windows 延伸樣式建立的索引標籤控制項，並將它附加至執行個體的`CTabCtrl`物件。|  
|[CTabCtrl::DeleteAllItems](#deleteallitems)|移除索引標籤控制項中的所有項目。|  
|[CTabCtrl::DeleteItem](#deleteitem)|移除索引標籤控制項中的項目。|  
|[CTabCtrl::DeselectAll](#deselectall)|重設在索引標籤控制項中，清除任何已按下的項目。|  
|[CTabCtrl::DrawItem](#drawitem)|繪製索引標籤控制項的指定項目。|  
|[CTabCtrl::GetCurFocus](#getcurfocus)|擷取具有目前焦點所在的索引標籤控制項的索引標籤。|  
|[CTabCtrl::GetCurSel](#getcursel)|判斷索引標籤控制項中目前選取的索引標籤。|  
|[CTabCtrl::GetExtendedStyle](#getextendedstyle)|擷取目前正在使用的索引標籤控制項中的延伸的樣式。|  
|[CTabCtrl::GetImageList](#getimagelist)|擷取索引標籤控制項相關聯的映像清單。|  
|[CTabCtrl::GetItem](#getitem)|擷取索引標籤控制項中的索引標籤的相關資訊。|  
|[CTabCtrl::GetItemCount](#getitemcount)|擷取索引標籤控制項中的索引標籤數目。|  
|[CTabCtrl::GetItemRect](#getitemrect)|擷取指定的索引標籤控制項中的索引標籤的週框。|  
|[CTabCtrl::GetItemState](#getitemstate)|擷取指定的索引標籤控制項項目的狀態。|  
|[CTabCtrl::GetRowCount](#getrowcount)|擷取目前的索引標籤控制項中的索引標籤的資料列數目。|  
|[CTabCtrl::GetToolTips](#gettooltips)|擷取索引標籤控制項相關聯的工具提示控制項的控制代碼。|  
|[CTabCtrl::HighlightItem](#highlightitem)|設定反白顯示項目的狀態 索引標籤。|  
|[CTabCtrl::HitTest](#hittest)|判斷哪一個索引標籤上，如果有的話，位於指定的螢幕位置。|  
|[Ctabctrl:: Insertitem](#insertitem)|在索引標籤控制項中插入新的索引標籤。|  
|[CTabCtrl::RemoveImage](#removeimage)|移除映像 索引標籤控制項的影像清單中。|  
|[CTabCtrl::SetCurFocus](#setcurfocus)|將焦點設在索引標籤控制項中指定的索引標籤。|  
|[CTabCtrl::SetCurSel](#setcursel)|選取索引標籤控制項中的索引標籤。|  
|[CTabCtrl::SetExtendedStyle](#setextendedstyle)|設定索引標籤控制項的延伸的樣式。|  
|[CTabCtrl::SetImageList](#setimagelist)|指派至索引標籤控制項的影像清單。|  
|[CTabCtrl::SetItem](#setitem)|設定下列部分或所有索引標籤的屬性。|  
|[CTabCtrl::SetItemExtra](#setitemextra)|設定每個索引標籤索引標籤控制項中的應用程式定義的資料保留的位元組數目。|  
|[CTabCtrl::SetItemSize](#setitemsize)|設定寬度和高度的項目。|  
|[CTabCtrl::SetItemState](#setitemstate)|設定指定的索引標籤控制項項目的狀態。|  
|[CTabCtrl::SetMinTabWidth](#setmintabwidth)|設定項目的最小寬度 索引標籤控制項中。|  
|[CTabCtrl::SetPadding](#setpadding)|設定 （填補） 每個索引標籤的圖示和標籤中的索引標籤控制項周圍的空間數量。|  
|[CTabCtrl::SetToolTips](#settooltips)|指派至索引標籤控制項的工具提示控制項。|  
  
## <a name="remarks"></a>備註  
 「 索引標籤控制項 」 是類似於筆記本的插頁或檔案櫃中的標籤。 藉由使用索引標籤控制項，應用程式可以定義視窗或對話方塊中同一個區域的多個頁面。 每一頁是由一組資訊或一群應用程式會顯示當使用者選取 [對應] 索引標籤的控制項所組成。一種特殊的索引標籤控制項顯示看起來像按鈕的索引標籤。 按一下按鈕，應該立即執行的命令，而不是顯示頁面。  
  
 這個控制項 (並因此`CTabCtrl`類別) 僅適用於 Windows 95/98 和 Windows NT 版 3.51 下執行的程式和更新版本。  
  
 如需有關使用`CTabCtrl`，請參閱 <<c2> [ 控制項](../../mfc/controls-mfc.md)並[使用 CTabCtrl](../../mfc/using-ctabctrl.md)。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CTabCtrl`  
  
## <a name="requirements"></a>需求  
 **標頭：** afxcmn.h  
  
##  <a name="adjustrect"></a>  CTabCtrl::AdjustRect  
 計算索引標籤控制項的顯示區域，指定視窗的矩形中，或計算視窗矩形，就會對應至指定的顯示區域。  
  
```  
void AdjustRect(BOOL bLarger,   LPRECT lpRect);
```  
  
### <a name="parameters"></a>參數  
 *bLarger*  
 表示要執行哪些作業。 如果此參數為 TRUE， *lpRect*指定的顯示矩形，並接收對應的視窗矩形。 如果此參數為 FALSE 時， *lpRect*指定視窗矩形，並接收對應的顯示矩形。  
  
 *lpRect*  
 指標[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構，指定指定的矩形，並且接收計算出的矩形。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTabCtrl#1](../../mfc/reference/codesnippet/cpp/ctabctrl-class_1.cpp)]  
  
##  <a name="create"></a>  CTabCtrl::Create  
 建立索引標籤控制項，並將它附加至執行個體的`CTabCtrl`物件。  
  
```  
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 *cheaderctrl:: Create*  
 指定的索引標籤控制項的樣式。 套用的任何組合[索引標籤控制項的樣式](/windows/desktop/Controls/tab-control-styles)、 Windows SDK 中所述。 請參閱**備註**取得一份您也可以套用至控制項的視窗樣式。  
  
 *rect*  
 指定的索引標籤控制項的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構。  
  
 *pParentWnd*  
 指定的索引標籤控制項的父視窗，通常`CDialog`。 它必須不是 NULL。  
  
 *nID*  
 指定的索引標籤控制項的識別碼。  
  
### <a name="return-value"></a>傳回值  
 如果物件的初始化是否成功，則為 TRUE否則為 FALSE。  
  
### <a name="remarks"></a>備註  
 您建構`CTabCtrl`兩個步驟中的物件。 首先，呼叫建構函式，並接著呼叫`Create`，這會建立索引標籤控制項，並將它附加至`CTabCtrl`物件。  
  
 除了索引標籤控制項的樣式，您可以套用下列的視窗樣式標籤控制項：  
  
- WS_CHILD 建立子視窗，表示索引標籤控制項。 無法搭配 WS_POPUP 樣式。  
  
- WS_VISIBLE 會建立一開始即可見的索引標籤控制項。  
  
- WS_DISABLED 會建立一開始會停用的視窗。  
  
- WS_GROUP 指定的控制項所在使用者可以前往從一個控制項下一步 箭號索引鍵群組的第一個控制項。 之後的第一個控制項屬於相同的群組，以 WS_GROUP 樣式定義的所有控制項。 WS_GROUP 樣式的下一個控制項結束 樣式 群組，並開始下一步 群組 （也就是一個群組結束下一步 開始的位置）。  
  
- WS_TABSTOP 指定任意數目的其中一個控制項，讓使用者可以使用 TAB 鍵移動。 TAB 鍵會將使用者移至下一個 WS_TABSTOP 樣式所指定的控制項。  
  
 若要建立延伸的視窗樣式索引標籤控制項，呼叫[CTabCtrl::CreateEx](#createex)而不是`Create`。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTabCtrl#2](../../mfc/reference/codesnippet/cpp/ctabctrl-class_2.cpp)]  
  
##  <a name="createex"></a>  CTabCtrl::CreateEx  
 建立控制項 （子視窗），並將它與關聯`CTabCtrl`物件。  
  
```  
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```  
  
### <a name="parameters"></a>參數  
 *dwExStyle*  
 指定正在建立之控制項的延伸的樣式。 如需延伸的 Windows 樣式的清單，請參閱 < *dwExStyle*參數[CreateWindowEx](https://msdn.microsoft.com/library/windows/desktop/ms632680) Windows SDK 中。  
  
 *cheaderctrl:: Create*  
 指定的索引標籤控制項的樣式。 套用的任何組合[索引標籤控制項的樣式](/windows/desktop/Controls/tab-control-styles)、 Windows SDK 中所述。 請參閱**備註**中[建立](#create)取得一份您也可以套用至控制項的視窗樣式。  
  
 *rect*  
 參考[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構描述的大小和位置，在中建立工作區座標中的視窗*pParentWnd*。  
  
 *pParentWnd*  
 是控制項的父視窗的指標。  
  
 *nID*  
 控制項的子視窗識別碼。  
  
### <a name="return-value"></a>傳回值  
 非零值，如果成功則為 0。  
  
### <a name="remarks"></a>備註  
 使用`CreateEx`而非[建立](#create)套用延伸的 Windows 樣式，由 Windows 延伸的樣式前置詞**WS_EX_**。  
  
 `CreateEx` 建立具有所指定的擴充 Windows 樣式的控制項*dwExStyle*。 設定擴充特定控制項使用的樣式[SetExtendedStyle](#setextendedstyle)。 例如，使用`CreateEx`將這類樣式設定為 WS_EX_CONTEXTHELP，但使用`SetExtendedStyle`將這類樣式設定為 TCS_EX_FLATSEPARATORS。 如需詳細資訊，請參閱中所述的樣式[ 索引標籤控制項擴充樣式](/windows/desktop/Controls/tab-control-extended-styles)Windows SDK 中。  
  
##  <a name="ctabctrl"></a>  CTabCtrl::CTabCtrl  
 建構 `CTabCtrl` 物件。  
  
```  
CTabCtrl();
```  
  
##  <a name="deleteallitems"></a>  CTabCtrl::DeleteAllItems  
 移除索引標籤控制項中的所有項目。  
  
```  
BOOL DeleteAllItems();
```  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
##  <a name="deleteitem"></a>  CTabCtrl::DeleteItem  
 從索引標籤控制項中移除指定的項目。  
  
```  
BOOL DeleteItem(int nItem);
```  
  
### <a name="parameters"></a>參數  
 *nItem*  
 要刪除之項目的以零為起始的值。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTabCtrl#3](../../mfc/reference/codesnippet/cpp/ctabctrl-class_3.cpp)]  
  
##  <a name="deselectall"></a>  CTabCtrl::DeselectAll  
 重設在索引標籤控制項中，清除任何已按下的項目。  
  
```  
void DeselectAll(BOOL fExcludeFocus);
```  
  
### <a name="parameters"></a>參數  
 *fExcludeFocus*  
 指定的項目取消選取範圍的旗標。 如果此參數設定為 FALSE 時，就會重設所有的索引標籤按鈕。 如果它設定為 TRUE，則所有索引標籤除了目前選取的項目會重設。  
  
### <a name="remarks"></a>備註  
 此成員函式實作 Win32 訊息的行為[TCM_DESELECTALL](/windows/desktop/Controls/tcm-deselectall)、 Windows SDK 中所述。  
  
##  <a name="drawitem"></a>  CTabCtrl::DrawItem  
 由架構的視覺外觀的主控描繪索引標籤控制項變更時呼叫。  
  
```  
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```  
  
### <a name="parameters"></a>參數  
 *lpDrawItemStruct*  
 指標[DRAWITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct)結構，描述要繪製的項目。  
  
### <a name="remarks"></a>備註  
 `itemAction`隸屬`DRAWITEMSTRUCT`結構會定義要執行的繪圖動作。  
  
 根據預設，此成員函式沒有任何作用。 覆寫此成員函式，來實作活動，抽獎獲得主控描繪`CTabCtrl`物件。  
  
 應用程式應該還原選取的顯示內容中提供所有的圖形裝置介面 (GDI) 物件*lpDrawItemStruct*之前此成員函式會結束。  
  
##  <a name="getcurfocus"></a>  CTabCtrl::GetCurFocus  
 擷取具有目前焦點所在的索引標籤的索引。  
  
```  
int GetCurFocus() const;  
```  
  
### <a name="return-value"></a>傳回值  
 具有目前焦點所在的索引標籤的以零為起始的索引。  
  
##  <a name="getcursel"></a>  CTabCtrl::GetCurSel  
 擷取索引標籤控制項中目前選取的索引標籤。  
  
```  
int GetCurSel() const;  
```  
  
### <a name="return-value"></a>傳回值  
 選取的索引標籤，如果成功或-1，表示已不選取任何索引標籤的以零為起始的索引。  
  
##  <a name="getextendedstyle"></a>  CTabCtrl::GetExtendedStyle  
 擷取目前正在使用的索引標籤控制項中的延伸的樣式。  
  
```  
DWORD GetExtendedStyle();
```  
  
### <a name="return-value"></a>傳回值  
 表示目前的索引標籤控制項的使用中的延伸的樣式。 這個值是組成[索引標籤控制項擴充樣式](/windows/desktop/Controls/tab-control-extended-styles)、 Windows SDK 中所述。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TCM_GETEXTENDEDSTYLE](/windows/desktop/Controls/tcm-getextendedstyle)、 Windows SDK 中所述。  
  
##  <a name="getimagelist"></a>  CTabCtrl::GetImageList  
 擷取與索引標籤控制項關聯的影像清單。  
  
```  
CImageList* GetImageList() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功，便會控制索引標籤的映像清單的指標;否則為 NULL。  
  
##  <a name="getitem"></a>  CTabCtrl::GetItem  
 擷取索引標籤控制項中的索引標籤的相關資訊。  
  
```  
BOOL GetItem(int nItem,   TCITEM* pTabCtrlItem) const;  
```  
  
### <a name="parameters"></a>參數  
 *nItem*  
 索引標籤的以零為起始的索引。  
  
 *pTabCtrlItem*  
 指標[TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema)用來指定要擷取之資訊的結構。 也用來接收 [] 索引標籤的相關資訊。此結構會搭配`InsertItem`， `GetItem`，和`SetItem`成員函式。  
  
### <a name="return-value"></a>傳回值  
 如果成功則傳回 TRUEFALSE 否則。  
  
### <a name="remarks"></a>備註  
 在傳送訊息時`mask`成員指定要傳回的屬性。 如果`mask`成員指定 TCIF_TEXT 值`pszText`成員必須包含接收項目文字的緩衝區的位址和`cchTextMax`成員必須指定緩衝區的大小。  
  
 `mask`  
 值，指定其`TCITEM`結構擷取或設定成員。 這個成員可以是零個或以下值的組合：  
  
- TCIF_TEXT`pszText`成員是否有效。  
  
- TCIF_IMAGE`iImage`成員是否有效。  
  
- TCIF_PARAM`lParam`成員是否有效。  
  
- TCIF_RTLREADING 文字的`pszText`希伯來文或阿拉伯文系統上使用由右至左讀取順序顯示。  
  
- TCIF_STATE`dwState`成員是否有效。  
  
 `pszText`  
 以 null 終止的字串，包含在索引標籤文字，如果結構包含一個索引標籤的相關資訊的指標。如果此結構會接收資訊，這個成員會指定接收在索引標籤文字的緩衝區的位址。  
  
 `cchTextMax`  
 所指向的緩衝區大小`pszText`。 如果結構不能接收資訊，則會忽略這個成員。  
  
 `iImage`  
 如果沒有任何索引標籤的影像，索引索引標籤控制項影像清單，或-1。  
  
 lParam  
 [] 索引標籤相關聯應用程式定義的資料。如果有四個位元組以上的應用程式定義的資料，每個索引標籤，應用程式必須定義的結構，並使用它，而不要`TCITEM`結構。 應用程式定義的結構的第一個成員必須是[TCITEMHEADER](/windows/desktop/api/commctrl/ns-commctrl-tagtcitemheadera)結構。 `TCITEMHEADER`結構完全相同`TCITEM`結構，但不含`lParam`成員。 您的結構大小和大小之間的差異`TCITEMHEADER`結構應該等於每個索引標籤的額外位元組數目。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTabCtrl#4](../../mfc/reference/codesnippet/cpp/ctabctrl-class_4.cpp)]  
  
##  <a name="getitemcount"></a>  CTabCtrl::GetItemCount  
 擷取索引標籤控制項中的索引標籤數目。  
  
```  
int GetItemCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 索引標籤控制項中的項目數目。  
  
### <a name="example"></a>範例  
  範例，請參閱[CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)。  
  
##  <a name="getitemrect"></a>  CTabCtrl::GetItemRect  
 擷取指定的索引標籤，在索引標籤控制項中指定的週框。  
  
```  
BOOL GetItemRect(int nItem,   LPRECT lpRect) const;  
```  
  
### <a name="parameters"></a>參數  
 *nItem*  
 以零為起始的索引標籤項目索引。  
  
 *lpRect*  
 指標[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)接收 [] 索引標籤的週框矩形的結構。這些座標使用檢視區的目前對應模式。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="example"></a>範例  
  範例，請參閱[CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)。  
  
##  <a name="getitemstate"></a>  CTabCtrl::GetItemState  
 擷取所識別的索引標籤控制項項目的狀態*nItem*。  
  
```  
DWORD GetItemState(
    int nItem,  
    DWORD dwMask) const;  
```  
  
### <a name="parameters"></a>參數  
 *nItem*  
 要擷取狀態資訊項目的以零為起始的索引編號。  
  
 *dwMask*  
 指定要傳回其中一個項目的狀態旗標的遮罩。 如需值的清單，請參閱遮罩隸屬[TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema)結構，在 Windows SDK 中所述。  
  
### <a name="return-value"></a>傳回值  
 接收的狀態資訊的 DWORD 值參考。 可為下列其中一個值：  
  
|值|描述|  
|-----------|-----------------|  
|TCIS_BUTTONPRESSED|選取索引標籤控制項項目。|  
|TCIS_HIGHLIGHTED|索引標籤控制項項目會反白顯示，以及索引標籤和文字則會使用目前的反白顯示色彩繪製。 當使用反白顯示色彩，這會是的則為 true 的插補，非遞色色彩。|  
  
### <a name="remarks"></a>備註  
 所指定項目的狀態`dwState`隸屬`TCITEM`結構。  
  
##  <a name="getrowcount"></a>  CTabCtrl::GetRowCount  
 擷取目前的索引標籤控制項中的資料列數目。  
  
```  
int GetRowCount() const;  
```  
  
### <a name="return-value"></a>傳回值  
 索引標籤控制項中的索引標籤的資料列數目。  
  
### <a name="remarks"></a>備註  
 具有 TCS_MULTILINE 樣式的索引標籤控制項可以有多個資料列的索引標籤。  
  
##  <a name="gettooltips"></a>  CTabCtrl::GetToolTips  
 擷取索引標籤控制項相關聯的工具提示控制項的控制代碼。  
  
```  
CToolTipCtrl* GetToolTips() const;  
```  
  
### <a name="return-value"></a>傳回值  
 如果成功; 時，工具提示控制項的控制代碼否則為 NULL。  
  
### <a name="remarks"></a>備註  
 如果它有 TCS_TOOLTIPS 樣式，索引標籤控制項就會建立工具提示控制項。 您也可以指派至 索引標籤控制項工具提示控制項，使用`SetToolTips`成員函式。  
  
##  <a name="highlightitem"></a>  CTabCtrl::HighlightItem  
 設定反白顯示項目的狀態 索引標籤。  
  
```  
BOOL HighlightItem(int idItem,   BOOL fHighlight = TRUE);
```  
  
### <a name="parameters"></a>參數  
 *idItem*  
 以零為起始的索引標籤控制項項目索引。  
  
 *fHighlight*  
 值，指定要設定的反白顯示狀態。 如果此值為 TRUE，則 [] 索引標籤會反白顯示;如果為 FALSE，[] 索引標籤設為其預設狀態。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息[TCM_HIGHLIGHTITEM](/windows/desktop/Controls/tcm-highlightitem)、 Windows SDK 中所述。  
  
##  <a name="hittest"></a>  CTabCtrl::HitTest  
 判斷哪一個索引標籤上，如果有的話，位於指定的螢幕位置。  
  
```  
int HitTest(TCHITTESTINFO* pHitTestInfo) const;  
```  
  
### <a name="parameters"></a>參數  
 *pHitTestInfo*  
 指標[TCHITTESTINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtchittestinfo)結構，在 Windows SDK 中，指定要測試螢幕位置所述。  
  
### <a name="return-value"></a>傳回值  
 如果沒有索引標籤位於指定的位置，則傳回 [] 索引標籤或-1 為起始的索引。  
  
##  <a name="insertitem"></a>  Ctabctrl:: Insertitem  
 將新的索引標籤插入現有的索引標籤控制項。  
  
```  
LONG InsertItem(
    int nItem,
    TCITEM* pTabCtrlItem);

 
LONG InsertItem(
    int nItem,
    LPCTSTR lpszItem);

 
LONG InsertItem(
    int nItem,
    LPCTSTR lpszItem,
    int nImage);

 
LONG InsertItem(
    UINT nMask,
    int nItem,
    LPCTSTR lpszItem,
    int nImage,
    LPARAM lParam);

 
LONG InsertItem(
    UINT nMask,  
    int nItem,  
    LPCTSTR lpszItem,  
    int nImage,  
    LPARAM lParam,  
    DWORD dwState,  
    DWORD dwStateMask);
```  
  
### <a name="parameters"></a>參數  
 *nItem*  
 新的索引標籤的以零為起始的索引。  
  
 *pTabCtrlItem*  
 指標[TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema)結構，指定索引標籤的屬性。  
  
 *lpszItem*  
 包含文字的索引標籤的 null 終止字串的位址。  
  
 *n*  
 要插入的影像清單中的影像以零為起始的索引。  
  
 *nMask*  
 指定哪些`TCITEM`結構設定的屬性。 可以是零或下列值的組合：  
  
- TCIF_TEXT`pszText`成員是否有效。  
  
- TCIF_IMAGE`iImage`成員是否有效。  
  
- TCIF_PARAM *lParam*成員是否有效。  
  
- TCIF_RTLREADING 文字的`pszText`希伯來文或阿拉伯文系統上使用由右至左讀取順序顯示。  
  
- TCIF_STATE *dwState*成員是否有效。  
  
 *lParam*  
 [] 索引標籤相關聯應用程式定義的資料。  
  
 *dwState*  
 指定的項目狀態的值。 如需詳細資訊，請參閱 < [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) Windows SDK 中。  
  
 *dwStateMask*  
 指定要設定哪些狀態。 如需詳細資訊，請參閱 < [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) Windows SDK 中。  
  
### <a name="return-value"></a>傳回值  
 新的索引標籤，如果成功則為起始的索引否則為-1。  
  
### <a name="example"></a>範例  
 [!code-cpp[NVC_MFC_CTabCtrl#5](../../mfc/reference/codesnippet/cpp/ctabctrl-class_5.cpp)]  
  
##  <a name="removeimage"></a>  CTabCtrl::RemoveImage  
 索引標籤控制項的影像清單中移除指定的映像。  
  
```  
void RemoveImage(int nImage);
```  
  
### <a name="parameters"></a>參數  
 *n*  
 要移除之影像的以零為起始的索引。  
  
### <a name="remarks"></a>備註  
 索引標籤控制項可用來更新每個索引標籤的影像索引，讓每個索引標籤會保持相同的映像相關聯。  
  
##  <a name="setcurfocus"></a>  CTabCtrl::SetCurFocus  
 將焦點設在索引標籤控制項中指定的索引標籤。  
  
```  
void SetCurFocus(int nItem);
```  
  
### <a name="parameters"></a>參數  
 *nItem*  
 指定的索引標籤，取得焦點的索引。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TCM_SETCURFOCUS](/windows/desktop/Controls/tcm-setcurfocus)、 Windows SDK 中所述。  
  
##  <a name="setcursel"></a>  CTabCtrl::SetCurSel  
 選取索引標籤控制項中的索引標籤。  
  
```  
int SetCurSel(int nItem);
```  
  
### <a name="parameters"></a>參數  
 *nItem*  
 要選取的項目以零為起始的索引。  
  
### <a name="return-value"></a>傳回值  
 以零為起始的索引，先前選取的索引標籤，如果成功，否則為-1。  
  
### <a name="remarks"></a>備註  
 索引標籤控制項不會傳送 TCN_SELCHANGING 或 TCN_SELCHANGE 通知訊息時使用此函式來選取索引標籤。 使用 WM_NOTIFY，當使用者按一下，或使用鍵盤來變更索引標籤，會傳送這些通知。  
  
##  <a name="setextendedstyle"></a>  CTabCtrl::SetExtendedStyle  
 設定索引標籤控制項的延伸的樣式。  
  
```  
DWORD SetExtendedStyle(DWORD dwNewStyle,   DWORD dwExMask = 0);
```  
  
### <a name="parameters"></a>參數  
 *dwNewStyle*  
 值，指定的索引標籤組合來控制延伸的樣式。  
  
 *dwExMask*  
 DWORD 值，指出在哪些樣式*dwNewStyle*會受到影響。 只有在延伸的樣式*dwExMask*將會變更。 因為，仍會維護所有其他樣式。 如果此參數為零，則所有的樣式*dwNewStyle*會受到影響。  
  
### <a name="return-value"></a>傳回值  
 DWORD 值，包含先前[索引標籤控制項擴充樣式](/windows/desktop/Controls/tab-control-extended-styles)、 Windows SDK 中所述。  
  
### <a name="return-value"></a>傳回值  
 此成員函式實作的 Win32 訊息的行為[TCM_SETEXTENDEDSTYLE](/windows/desktop/Controls/tcm-setextendedstyle)、 Windows SDK 中所述。  
  
##  <a name="setimagelist"></a>  CTabCtrl::SetImageList  
 指派至索引標籤控制項的影像清單。  
  
```  
CImageList* SetImageList(CImageList* pImageList);
```  
  
### <a name="parameters"></a>參數  
 *pImageList*  
 要指派給 索引標籤控制項之影像清單的指標。  
  
### <a name="return-value"></a>傳回值  
 如果沒有任何先前的映像清單，請到前一個映像清單或 NULL 傳回的指標。  
  
##  <a name="setitem"></a>  CTabCtrl::SetItem  
 設定下列部分或所有索引標籤的屬性。  
  
```  
BOOL SetItem(int nItem,   TCITEM* pTabCtrlItem);
```  
  
### <a name="parameters"></a>參數  
 *nItem*  
 項目的以零為起始的索引。  
  
 *pTabCtrlItem*  
 指標[TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema)結構，其中包含新的項目屬性。 `mask`成員指定要設定的屬性。 如果`mask`成員指定 TCIF_TEXT 值`pszText`成員是以 null 結束的字串的位址和`cchTextMax`成員會被忽略。  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
### <a name="example"></a>範例  
  範例，請參閱[GetItem](#getitem)。  
  
##  <a name="setitemextra"></a>  CTabCtrl::SetItemExtra  
 設定每個索引標籤索引標籤控制項中的應用程式定義的資料保留的位元組數目。  
  
```  
BOOL SetItemExtra(int nBytes);
```  
  
### <a name="parameters"></a>參數  
 *nBytes*  
 若要設定額外的位元組數目。  
  
### <a name="return-value"></a>傳回值  
 如果成功則不為零，否則為 0。  
  
### <a name="remarks"></a>備註  
 此成員函式實作的 Win32 訊息的行為[TCM_SETITEMEXTRA](/windows/desktop/Controls/tcm-setitemextra)、 Windows SDK 中所述。  
  
##  <a name="setitemsize"></a>  CTabCtrl::SetItemSize  
 設定索引標籤控制項項目的寬度和高度。  
  
```  
CSize SetItemSize(CSize size);
```  
  
### <a name="parameters"></a>參數  
 *size*  
 索引標籤控制項項目的新寬度和高度 (以像素為單位)。  
  
### <a name="return-value"></a>傳回值  
 傳回索引標籤控制項項目的舊寬度和高度。  
  
##  <a name="setitemstate"></a>  CTabCtrl::SetItemState  
 設定索引標籤控制項項目所識別的狀態*nItem*。  
  
```  
BOOL SetItemState(
    int nItem,
    DWORD dwMask,
    DWORD dwState);
```  
  
### <a name="parameters"></a>參數  
 *nItem*  
 要設定的狀態資訊項目的以零為起始的索引編號。  
  
 *dwMask*  
 指定其中一個項目的狀態設定旗標的遮罩。 如需值的清單，請參閱遮罩隸屬[TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema)結構，在 Windows SDK 中所述。  
  
 *dwState*  
 包含狀態資訊的 DWORD 值參考。 可為下列其中一個值：  
  
|值|描述|  
|-----------|-----------------|  
|TCIS_BUTTONPRESSED|選取索引標籤控制項項目。|  
|TCIS_HIGHLIGHTED|索引標籤控制項項目會反白顯示，以及索引標籤和文字則會使用目前的反白顯示色彩繪製。 當使用反白顯示色彩，這會是的則為 true 的插補，非遞色色彩。|  
  
### <a name="return-value"></a>傳回值  
 如果成功則為非零；否則為 0。  
  
##  <a name="setmintabwidth"></a>  CTabCtrl::SetMinTabWidth  
 設定項目的最小寬度 索引標籤控制項中。  
  
```  
int SetMinTabWidth(int cx);
```  
  
### <a name="parameters"></a>參數  
 *cx*  
 索引標籤控制項項目設定的最小寬度。 如果此參數設定為-1 時，控制項就會使用預設索引標籤寬度。  
  
### <a name="return-value"></a>傳回值  
 先前的最小的索引標籤寬度。  
  
### <a name="return-value"></a>傳回值  
 此成員函式實作的 Win32 訊息的行為[TCM_SETMINTABWIDTH](/windows/desktop/Controls/tcm-setmintabwidth)、 Windows SDK 中所述。  
  
##  <a name="setpadding"></a>  CTabCtrl::SetPadding  
 設定 （填補） 每個索引標籤的圖示和標籤中的索引標籤控制項周圍的空間數量。  
  
```  
void SetPadding(CSize size);
```  
  
### <a name="parameters"></a>參數  
 *size*  
 設定 （填補） 每個索引標籤的圖示和標籤中的索引標籤控制項周圍的空間數量。  
  
##  <a name="settooltips"></a>  CTabCtrl::SetToolTips  
 指派至索引標籤控制項的工具提示控制項。  
  
```  
void SetToolTips(CToolTipCtrl* pWndTip);
```  
  
### <a name="parameters"></a>參數  
 *pWndTip*  
 工具提示控制項的控制代碼。  
  
### <a name="remarks"></a>備註  
 您可以取得工具提示控制項，藉由呼叫相關聯的索引標籤控制項`GetToolTips`。  
  
### <a name="example"></a>範例  
  範例，請參閱[CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)。  
  
## <a name="see-also"></a>另請參閱  
 [CWnd 類別](../../mfc/reference/cwnd-class.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [CHeaderCtrl 類別](../../mfc/reference/cheaderctrl-class.md)   
 [CListCtrl 類別](../../mfc/reference/clistctrl-class.md)
