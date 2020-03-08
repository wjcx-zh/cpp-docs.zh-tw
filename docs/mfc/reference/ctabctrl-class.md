---
title: CTabCtrl 類別
ms.date: 11/04/2016
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
ms.openlocfilehash: a0ca4cbad48c420250fe39e131de5504b1ae70f3
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78875862"
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
|[CTabCtrl：： CTabCtrl](#ctabctrl)|建構 `CTabCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CTabCtrl：： AdjustRect](#adjustrect)|指定視窗矩形來計算索引標籤控制項的顯示區域，或計算對應至特定顯示區域的視窗矩形。|
|[CTabCtrl：： Create](#create)|建立索引標籤控制項，並將它附加至 `CTabCtrl` 物件的實例。|
|[CTabCtrl：： CreateEx](#createex)|建立具有指定之 Windows 擴充樣式的索引標籤控制項，並將它附加至 `CTabCtrl` 物件的實例。|
|[CTabCtrl：:D eleteAllItems](#deleteallitems)|從索引標籤控制項移除所有專案。|
|[CTabCtrl：:D eleteItem](#deleteitem)|從索引標籤控制項移除專案。|
|[CTabCtrl：:D eselectAll](#deselectall)|重設索引標籤控制項中的專案，並清除任何已按下的。|
|[CTabCtrl：:D rawItem](#drawitem)|繪製索引標籤控制項的指定專案。|
|[CTabCtrl：： GetCurFocus](#getcurfocus)|使用索引標籤控制項的目前焦點來抓取索引標籤。|
|[CTabCtrl：： GetCurSel](#getcursel)|決定索引標籤控制項中目前選取的索引標籤。|
|[CTabCtrl：： GetExtendedStyle](#getextendedstyle)|抓取索引標籤控制項目前使用的延伸樣式。|
|[CTabCtrl：： GetImageList](#getimagelist)|抓取與索引標籤控制項相關聯的影像清單。|
|[CTabCtrl：： GetItem](#getitem)|抓取索引標籤控制項中索引標籤的相關資訊。|
|[CTabCtrl：： GetItemCount](#getitemcount)|抓取索引標籤控制項中的索引標籤數目。|
|[CTabCtrl：： GetItemRect](#getitemrect)|抓取索引標籤控制項中索引標籤的周框。|
|[CTabCtrl：： GetItemState](#getitemstate)|抓取指定之索引標籤控制項專案的狀態。|
|[CTabCtrl：： GetRowCount](#getrowcount)|抓取索引標籤控制項中索引標籤的目前資料列數目。|
|[CTabCtrl：： GetToolTips](#gettooltips)|抓取與索引標籤控制項相關聯的工具提示控制項的控制碼。|
|[CTabCtrl：： HighlightItem](#highlightitem)|設定索引標籤專案的反白顯示狀態。|
|[CTabCtrl：： HitTest](#hittest)|判斷哪個索引標籤（如果有的話）位於指定的螢幕位置。|
|[CTabCtrl：： InsertItem](#insertitem)|在索引標籤控制項中插入新的索引標籤。|
|[CTabCtrl：： RemoveImage](#removeimage)|從索引標籤控制項的影像清單中移除影像。|
|[CTabCtrl：： SetCurFocus](#setcurfocus)|將焦點設定為索引標籤控制項中的指定索引標籤。|
|[CTabCtrl：： SetCurSel](#setcursel)|選取索引標籤控制項中的索引標籤。|
|[CTabCtrl：： SetExtendedStyle](#setextendedstyle)|設定索引標籤控制項的延伸樣式。|
|[CTabCtrl：： SetImageList](#setimagelist)|將影像清單指派給索引標籤控制項。|
|[CTabCtrl：： SetItem](#setitem)|設定部分或所有索引標籤的屬性。|
|[CTabCtrl：： SetItemExtra](#setitemextra)|針對索引標籤控制項中的應用程式定義資料，設定每個索引標籤的位元組數目。|
|[CTabCtrl：： SetItemSize](#setitemsize)|設定專案的寬度和高度。|
|[CTabCtrl：： SetItemState](#setitemstate)|設定指定的索引標籤控制項專案的狀態。|
|[CTabCtrl：： SetMinTabWidth](#setmintabwidth)|設定索引標籤控制項中專案的最小寬度。|
|[CTabCtrl：： SetPadding](#setpadding)|設定索引標籤控制項中每個索引標籤的圖示和標籤的空間（填補）量。|
|[CTabCtrl：： SetToolTips](#settooltips)|將工具提示控制項指派給索引標籤控制項。|

## <a name="remarks"></a>備註

「索引標籤控制項」類似于筆記本中的分隔線或檔案櫃中的標籤。 藉由使用索引標籤控制項，應用程式可以定義視窗或對話方塊中同一個區域的多個頁面。 每個頁面都包含一組資訊或一群控制項，應用程式會在使用者選取對應的索引標籤時顯示。特殊的索引標籤控制項類型會顯示看起來像按鈕的索引標籤。 按一下按鈕應該會立即執行命令，而不是顯示頁面。

這個控制項（因此 `CTabCtrl` 類別）僅適用于在 Windows 95/98 和 Windows NT 3.51 版和更新版本下執行的程式。

如需使用 `CTabCtrl`的詳細資訊，請參閱[控制項](../../mfc/controls-mfc.md)和[使用 CTabCtrl](../../mfc/using-ctabctrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CTabCtrl`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

##  <a name="adjustrect"></a>CTabCtrl：： AdjustRect

指定視窗矩形來計算索引標籤控制項的顯示區域，或計算對應至特定顯示區域的視窗矩形。

```
void AdjustRect(BOOL bLarger,   LPRECT lpRect);
```

### <a name="parameters"></a>參數

*bLarger*<br/>
指出要執行的作業。 如果此參數為 TRUE， *lpRect*會指定一個顯示矩形，並接收對應的視窗矩形。 如果此參數為 FALSE，則*lpRect*會指定視窗矩形並接收對應的顯示矩形。

*lpRect*<br/>
[矩形](/previous-versions/dd162897\(v=vs.85\))結構的指標，指定給定的矩形並接收計算的矩形。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTabCtrl#1](../../mfc/reference/codesnippet/cpp/ctabctrl-class_1.cpp)]

##  <a name="create"></a>CTabCtrl：： Create

建立索引標籤控制項，並將它附加至 `CTabCtrl` 物件的實例。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定索引標籤控制項的樣式。 套用[索引標籤控制項樣式](/windows/win32/Controls/tab-control-styles)的任何組合，如 Windows SDK 中所述。 如需您也可以套用至控制項的視窗樣式清單，請參閱**備註**。

*各種*<br/>
指定索引標籤控制項的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](/previous-versions/dd162897\(v=vs.85\))結構。

*pParentWnd*<br/>
指定索引標籤控制項的父視窗，通常是 `CDialog`。 它不得為 NULL。

*nID*<br/>
指定索引標籤控制項的識別碼。

### <a name="return-value"></a>傳回值

如果物件的初始化成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

您可以使用兩個步驟來建立 `CTabCtrl` 物件。 首先，呼叫此函式，然後呼叫 `Create`，這會建立索引標籤控制項並將其附加至 `CTabCtrl` 物件。

除了索引標籤控制項樣式以外，您還可以將下列視窗樣式套用至索引標籤控制項：

- WS_CHILD 會建立表示索引標籤控制項的子視窗。 不能與 WS_POPUP 樣式一起使用。

- WS_VISIBLE 會建立一開始顯示的索引標籤控制項。

- WS_DISABLED 會建立一開始停用的視窗。

- WS_GROUP 指定控制項群組的第一個控制項，使用者可以在其中使用方向鍵從某個控制項移到下一個控制項。 在第一個控制項屬於相同群組之後，以 WS_GROUP 樣式定義的所有控制項。 下一個具有 WS_GROUP 樣式的控制項會結束樣式群組並啟動下一個群組（也就是一個群組結束于下一個開始的位置）。

- WS_TABSTOP 指定使用者可以使用 TAB 鍵移動的任意數目控制項之一。 TAB 鍵會將使用者移至 [WS_TABSTOP] 樣式所指定的下一個控制項。

若要建立具有延伸視窗樣式的索引標籤控制項，請呼叫[CTabCtrl：： CreateEx](#createex) ，而不是 `Create`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTabCtrl#2](../../mfc/reference/codesnippet/cpp/ctabctrl-class_2.cpp)]

##  <a name="createex"></a>CTabCtrl：： CreateEx

建立控制項（子視窗），並將它與 `CTabCtrl` 物件產生關聯。

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwExStyle*<br/>
指定所要建立之控制項的延伸樣式。 如需擴充 Windows 樣式的清單，請參閱 Windows SDK 中[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*參數。

*dwStyle*<br/>
指定索引標籤控制項的樣式。 套用[索引標籤控制項樣式](/windows/win32/Controls/tab-control-styles)的任何組合，如 Windows SDK 中所述。 如需您也可以套用至控制項的視窗樣式清單，請參閱[建立](#create)中的**備註**。

*各種*<br/>
[矩形](/previous-versions/dd162897\(v=vs.85\))結構的參考，描述要建立之視窗的大小和位置，以*pParentWnd*的用戶端座標表示。

*pParentWnd*<br/>
做為控制項父系之視窗的指標。

*nID*<br/>
控制項的子視窗識別碼。

### <a name="return-value"></a>傳回值

如果成功，則為非零，否則為0。

### <a name="remarks"></a>備註

使用 `CreateEx` 而非[Create](#create)來套用擴充的 windows 樣式（由 Windows 擴充樣式指定于**WS_EX_** 的前面）。

`CreateEx` 會使用*dwExStyle*所指定的擴充 Windows 樣式來建立控制項。 使用[SetExtendedStyle](#setextendedstyle)設定控制項特定的擴充樣式。 例如，使用 `CreateEx` 將這類樣式設定為 WS_EX_CONTEXTHELP，但使用 `SetExtendedStyle` 將這類樣式設定為 TCS_EX_FLATSEPARATORS。 如需詳細資訊，請參閱 Windows SDK 中的[索引標籤控制項擴充樣式](/windows/win32/Controls/tab-control-extended-styles)中所述的樣式。

##  <a name="ctabctrl"></a>CTabCtrl：： CTabCtrl

建構 `CTabCtrl` 物件。

```
CTabCtrl();
```

##  <a name="deleteallitems"></a>CTabCtrl：:D eleteAllItems

從索引標籤控制項移除所有專案。

```
BOOL DeleteAllItems();
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

##  <a name="deleteitem"></a>CTabCtrl：:D eleteItem

從索引標籤控制項中移除指定的專案。

```
BOOL DeleteItem(int nItem);
```

### <a name="parameters"></a>參數

*nItem*<br/>
要刪除的專案之以零為起始的值。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTabCtrl#3](../../mfc/reference/codesnippet/cpp/ctabctrl-class_3.cpp)]

##  <a name="deselectall"></a>CTabCtrl：:D eselectAll

重設索引標籤控制項中的專案，並清除任何已按下的。

```
void DeselectAll(BOOL fExcludeFocus);
```

### <a name="parameters"></a>參數

*fExcludeFocus*<br/>
指定專案 deselection 範圍的旗標。 如果此參數設定為 [FALSE]，則會重設所有的索引標籤按鈕。 如果設定為 TRUE，則會重設目前所選取的所有索引標籤專案（除外）。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 訊息的行為， [TCM_DESELECTALL](/windows/win32/Controls/tcm-deselectall)，如 Windows SDK 所述。

##  <a name="drawitem"></a>CTabCtrl：:D rawItem

當主控描繪索引標籤控制項的視覺外觀變更時由架構呼叫。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>參數

*lpDrawItemStruct*<br/>
[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)結構的指標，描述要繪製的專案。

### <a name="remarks"></a>備註

`DRAWITEMSTRUCT` 結構的 `itemAction` 成員會定義要執行的繪圖動作。

根據預設，此成員函式不會執行任何工作。 覆寫這個成員函式，以針對主控描繪 `CTabCtrl` 物件來執行繪製。

在此成員函式終止之前，應用程式應該還原為*lpDrawItemStruct*中提供的顯示內容所選取的所有圖形裝置介面（GDI）物件。

##  <a name="getcurfocus"></a>CTabCtrl：： GetCurFocus

抓取具有目前焦點的索引標籤。

```
int GetCurFocus() const;
```

### <a name="return-value"></a>傳回值

索引標籤之以零為起始的索引，其為目前的焦點。

##  <a name="getcursel"></a>CTabCtrl：： GetCurSel

抓取索引標籤控制項中目前選取的索引標籤。

```
int GetCurSel() const;
```

### <a name="return-value"></a>傳回值

如果成功，則為所選取索引標籤以零為起始的索引，如果未選取 tab 鍵，則為-1。

##  <a name="getextendedstyle"></a>CTabCtrl：： GetExtendedStyle

抓取索引標籤控制項目前使用的延伸樣式。

```
DWORD GetExtendedStyle();
```

### <a name="return-value"></a>傳回值

表示目前用於索引標籤控制項的延伸樣式。 這個值是[索引標籤控制項延伸樣式](/windows/win32/Controls/tab-control-extended-styles)的組合，如 Windows SDK 中所述。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 中的說明，實作用[TCM_GETEXTENDEDSTYLE](/windows/win32/Controls/tcm-getextendedstyle)Win32 訊息的行為。

##  <a name="getimagelist"></a>CTabCtrl：： GetImageList

擷取與索引標籤控制項關聯的影像清單。

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>傳回值

如果成功，則為指向索引標籤控制項影像清單的指標，否則為 NULL。

##  <a name="getitem"></a>CTabCtrl：： GetItem

抓取索引標籤控制項中索引標籤的相關資訊。

```
BOOL GetItem(int nItem,   TCITEM* pTabCtrlItem) const;
```

### <a name="parameters"></a>參數

*nItem*<br/>
索引標籤的以零為基底的索引。

*pTabCtrlItem*<br/>
[TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw)結構的指標，用來指定要取得的資訊。 也可用來接收索引標籤的相關資訊。這個結構會與 `InsertItem`、`GetItem`和 `SetItem` 成員函式搭配使用。

### <a name="return-value"></a>傳回值

如果成功，則傳回 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

當傳送訊息時，`mask` 成員會指定要傳回的屬性。 如果 `mask` 成員指定 TCIF_TEXT 值，則 `pszText` 成員必須包含接收專案文字的緩衝區位址，而且 `cchTextMax` 成員必須指定緩衝區的大小。

- `mask`

   值，指定要取得或設定的 `TCITEM` 結構成員。 這個成員可以是零或下列值的組合：

   - TCIF_TEXT `pszText` 成員有效。

   - TCIF_IMAGE `iImage` 成員有效。

   - TCIF_PARAM `lParam` 成員有效。

   - TCIF_RTLREADING 在希伯來文或阿拉伯文系統上使用由右至左的讀取順序來顯示 `pszText` 的文字。

   - TCIF_STATE `dwState` 成員有效。

- `pszText`

   以 null 終止的字串指標，如果結構包含索引標籤的相關資訊，則包含索引標籤文字。如果結構接收資訊，這個成員會指定接收索引標籤文字的緩衝區位址。

- `cchTextMax`

   `pszText`所指向的緩衝區大小。 如果結構未接收資訊，則會忽略這個成員。

- `iImage` 索引加入至索引標籤控制項的影像清單中，則為-1，如果索引標籤沒有影像，則為-1。

- `lParam`

   與索引標籤相關聯的應用程式定義資料。如果每個索引標籤的應用程式定義資料超過四個位元組，應用程式必須定義結構並使用它，而不是 `TCITEM` 結構。 應用程式定義結構的第一個成員必須是[TCITEMHEADER](/windows/win32/api/commctrl/ns-commctrl-tcitemheaderw)結構。 `TCITEMHEADER` 結構與 `TCITEM` 結構相同，但沒有 `lParam` 成員。 結構大小與 `TCITEMHEADER` 結構大小之間的差異應該等於每個索引標籤的額外位元組數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTabCtrl#4](../../mfc/reference/codesnippet/cpp/ctabctrl-class_4.cpp)]

##  <a name="getitemcount"></a>CTabCtrl：： GetItemCount

抓取索引標籤控制項中的索引標籤數目。

```
int GetItemCount() const;
```

### <a name="return-value"></a>傳回值

索引標籤控制項中的專案數。

### <a name="example"></a>範例

  請參閱[CPropertySheet：： GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)的範例。

##  <a name="getitemrect"></a>CTabCtrl：： GetItemRect

抓取索引標籤控制項中指定之索引標籤的周框。

```
BOOL GetItemRect(int nItem,   LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

*nItem*<br/>
索引標籤專案以零為基底的索引。

*lpRect*<br/>
[矩形](/previous-versions/dd162897\(v=vs.85\))的指標，該結構會接收索引標籤的周框。這些座標會使用此視口的目前對應模式。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

  請參閱[CPropertySheet：： GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)的範例。

##  <a name="getitemstate"></a>CTabCtrl：： GetItemState

抓取*nItem*所識別之索引標籤控制項專案的狀態。

```
DWORD GetItemState(
    int nItem,
    DWORD dwMask) const;
```

### <a name="parameters"></a>參數

*nItem*<br/>
要為其取得狀態資訊之專案的以零為起始的索引編號。

*dwMask*<br/>
遮罩，指定要傳回之專案的狀態旗標。 如需值清單，請參閱[TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw)結構的 mask 成員，如 Windows SDK 中所述。

### <a name="return-value"></a>傳回值

接收狀態資訊之 DWORD 值的參考。 可以是下列其中一個值：

|值|描述|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|已選取 [索引標籤控制項] 專案。|
|TCIS_HIGHLIGHTED|索引標籤控制項專案會反白顯示，而且索引標籤和文字會使用目前的醒目提示色彩繪製。 使用反白顯示色彩時，這會是真正的插補，而不是遞色。|

### <a name="remarks"></a>備註

專案的狀態是由 `TCITEM` 結構的 `dwState` 成員所指定。

##  <a name="getrowcount"></a>CTabCtrl：： GetRowCount

抓取索引標籤控制項中目前的資料列數目。

```
int GetRowCount() const;
```

### <a name="return-value"></a>傳回值

索引標籤控制項中索引標籤的資料列數目。

### <a name="remarks"></a>備註

只有具有 TCS_MULTILINE 樣式的索引標籤控制項可以有多個索引標籤的資料列。

##  <a name="gettooltips"></a>CTabCtrl：： GetToolTips

抓取與索引標籤控制項相關聯的工具提示控制項的控制碼。

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>傳回值

如果成功，則為工具提示控制項的控制碼;否則為 Null。

### <a name="remarks"></a>備註

如果索引標籤控制項具有 TCS_TOOLTIPS 樣式，則會建立工具提示控制項。 您也可以使用 `SetToolTips` 成員函式，將工具提示控制項指派給索引標籤控制項。

##  <a name="highlightitem"></a>CTabCtrl：： HighlightItem

設定索引標籤專案的反白顯示狀態。

```
BOOL HighlightItem(int idItem,   BOOL fHighlight = TRUE);
```

### <a name="parameters"></a>參數

*idItem*<br/>
索引標籤控制項專案以零為起始的索引。

*fHighlight*<br/>
值，指定要設定的反白顯示狀態。 如果此值為 TRUE，則會反白顯示索引標籤;如果為 FALSE，則索引標籤會設定為其預設狀態。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 中的說明，實作用[TCM_HIGHLIGHTITEM](/windows/win32/Controls/tcm-highlightitem)的 Win32 訊息。

##  <a name="hittest"></a>CTabCtrl：： HitTest

判斷哪個索引標籤（如果有的話）位於指定的螢幕位置。

```
int HitTest(TCHITTESTINFO* pHitTestInfo) const;
```

### <a name="parameters"></a>參數

*pHitTestInfo*<br/>
[TCHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-tchittestinfo)結構的指標，如 Windows SDK 中所述，指定要測試的螢幕位置。

### <a name="return-value"></a>傳回值

傳回索引標籤的以零為起始的索引，如果在指定的位置沒有 tab 鍵，則傳回-1。

##  <a name="insertitem"></a>CTabCtrl：： InsertItem

在現有的索引標籤控制項中插入新的索引標籤。

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

*nItem*<br/>
新索引標籤以零為基底的索引。

*pTabCtrlItem*<br/>
[TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw)結構的指標，指定索引標籤的屬性。

*lpszItem*<br/>
以 null 結束的字串的位址，其中包含索引標籤的文字。

*nImage*<br/>
要從影像清單插入的影像之以零為起始的索引。

*nMask*<br/>
指定要設定的 `TCITEM` 結構屬性。 可以是零或下列值的組合：

- TCIF_TEXT `pszText` 成員有效。

- TCIF_IMAGE `iImage` 成員有效。

- TCIF_PARAM *lParam*成員有效。

- TCIF_RTLREADING 在希伯來文或阿拉伯文系統上使用由右至左的讀取順序來顯示 `pszText` 的文字。

- TCIF_STATE *dwState*成員有效。

*lParam*<br/>
與索引標籤相關聯的應用程式定義資料。

*dwState*<br/>
指定專案狀態的值。 如需詳細資訊，請參閱 Windows SDK 中的[TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) 。

*dwStateMask*<br/>
指定要設定的狀態。 如需詳細資訊，請參閱 Windows SDK 中的[TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) 。

### <a name="return-value"></a>傳回值

如果成功，則為新索引標籤以零為基底的索引;否則為-1。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTabCtrl#5](../../mfc/reference/codesnippet/cpp/ctabctrl-class_5.cpp)]

##  <a name="removeimage"></a>CTabCtrl：： RemoveImage

從索引標籤控制項的影像清單中移除指定的影像。

```
void RemoveImage(int nImage);
```

### <a name="parameters"></a>參數

*nImage*<br/>
要移除之影像的以零為基底的索引。

### <a name="remarks"></a>備註

此索引標籤控制項會更新每個索引標籤的影像索引，讓每個索引標籤與相同的影像保持關聯。

##  <a name="setcurfocus"></a>CTabCtrl：： SetCurFocus

將焦點設定為索引標籤控制項中的指定索引標籤。

```
void SetCurFocus(int nItem);
```

### <a name="parameters"></a>參數

*nItem*<br/>
指定取得焦點的索引標籤。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 中的說明，實作用[TCM_SETCURFOCUS](/windows/win32/Controls/tcm-setcurfocus)Win32 訊息的行為。

##  <a name="setcursel"></a>CTabCtrl：： SetCurSel

選取索引標籤控制項中的索引標籤。

```
int SetCurSel(int nItem);
```

### <a name="parameters"></a>參數

*nItem*<br/>
要選取之專案的以零為起始的索引。

### <a name="return-value"></a>傳回值

如果成功，則為先前選取之索引標籤的以零為基底的索引，否則為-1。

### <a name="remarks"></a>備註

使用此函式選取索引標籤時，索引標籤控制項不會傳送 TCN_SELCHANGING 或 TCN_SELCHANGE 通知訊息。 這些通知會在使用者按一下或使用鍵盤來變更索引標籤時，使用 WM_NOTIFY 來傳送。

##  <a name="setextendedstyle"></a>CTabCtrl：： SetExtendedStyle

設定索引標籤控制項的延伸樣式。

```
DWORD SetExtendedStyle(DWORD dwNewStyle,   DWORD dwExMask = 0);
```

### <a name="parameters"></a>參數

*dwNewStyle*<br/>
值，指定索引標籤控制項延伸樣式的組合。

*dwExMask*<br/>
DWORD 值，指出要影響*dwNewStyle*中的哪一種樣式。 只有*dwExMask*中的擴充樣式才會變更。 所有其他樣式將會維持不變。 如果此參數為零，則*dwNewStyle*中的所有樣式都會受到影響。

### <a name="return-value"></a>傳回值

DWORD 值，其中包含先前的[索引標籤控制項擴充樣式](/windows/win32/Controls/tab-control-extended-styles)，如 Windows SDK 中所述。

### <a name="return-value"></a>傳回值

此成員函式會依照 Windows SDK 中的說明，實作用[TCM_SETEXTENDEDSTYLE](/windows/win32/Controls/tcm-setextendedstyle)Win32 訊息的行為。

##  <a name="setimagelist"></a>CTabCtrl：： SetImageList

將影像清單指派給索引標籤控制項。

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>參數

*pImageList*<br/>
要指派給索引標籤控制項之影像清單的指標。

### <a name="return-value"></a>傳回值

傳回上一個影像清單的指標，如果沒有上一個影像清單，則傳回 Null。

##  <a name="setitem"></a>CTabCtrl：： SetItem

設定部分或所有索引標籤的屬性。

```
BOOL SetItem(int nItem,   TCITEM* pTabCtrlItem);
```

### <a name="parameters"></a>參數

*nItem*<br/>
以零為基底的專案索引。

*pTabCtrlItem*<br/>
[TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw)結構的指標，其中包含新的專案屬性。 `mask` 成員會指定要設定的屬性。 如果 `mask` 成員指定 TCIF_TEXT 值，`pszText` 成員就是以 null 終止之字串的位址，而 `cchTextMax` 成員會被忽略。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

  請參閱[GetItem](#getitem)的範例。

##  <a name="setitemextra"></a>CTabCtrl：： SetItemExtra

針對索引標籤控制項中的應用程式定義資料，設定每個索引標籤的位元組數目。

```
BOOL SetItemExtra(int nBytes);
```

### <a name="parameters"></a>參數

*nBytes*<br/>
要設定的額外位元組數。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 中的說明，實作用[TCM_SETITEMEXTRA](/windows/win32/Controls/tcm-setitemextra)Win32 訊息的行為。

##  <a name="setitemsize"></a>CTabCtrl：： SetItemSize

設定索引標籤控制項項目的寬度和高度。

```
CSize SetItemSize(CSize size);
```

### <a name="parameters"></a>參數

*size*<br/>
索引標籤控制項項目的新寬度和高度 (以像素為單位)。

### <a name="return-value"></a>傳回值

傳回索引標籤控制項項目的舊寬度和高度。

##  <a name="setitemstate"></a>CTabCtrl：： SetItemState

設定*nItem*所識別之索引標籤控制項專案的狀態。

```
BOOL SetItemState(
    int nItem,
    DWORD dwMask,
    DWORD dwState);
```

### <a name="parameters"></a>參數

*nItem*<br/>
要設定其狀態資訊之專案的以零為起始的索引編號。

*dwMask*<br/>
遮罩，指定要設定之專案的狀態旗標。 如需值清單，請參閱[TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw)結構的 mask 成員，如 Windows SDK 中所述。

*dwState*<br/>
DWORD 值的參考，其中包含狀態資訊。 可以是下列其中一個值：

|值|描述|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|已選取 [索引標籤控制項] 專案。|
|TCIS_HIGHLIGHTED|索引標籤控制項專案會反白顯示，而且索引標籤和文字會使用目前的醒目提示色彩繪製。 使用反白顯示色彩時，這會是真正的插補，而不是遞色。|

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

##  <a name="setmintabwidth"></a>CTabCtrl：： SetMinTabWidth

設定索引標籤控制項中專案的最小寬度。

```
int SetMinTabWidth(int cx);
```

### <a name="parameters"></a>參數

*cx*<br/>
要為索引標籤控制項專案設定的最小寬度。 如果此參數設定為-1，控制項將會使用預設的定位鍵寬度。

### <a name="return-value"></a>傳回值

上一個最小的索引標籤寬度。

### <a name="return-value"></a>傳回值

此成員函式會依照 Windows SDK 中的說明，實作用[TCM_SETMINTABWIDTH](/windows/win32/Controls/tcm-setmintabwidth)Win32 訊息的行為。

##  <a name="setpadding"></a>CTabCtrl：： SetPadding

設定索引標籤控制項中每個索引標籤的圖示和標籤的空間（填補）量。

```
void SetPadding(CSize size);
```

### <a name="parameters"></a>參數

*size*<br/>
設定索引標籤控制項中每個索引標籤的圖示和標籤的空間（填補）量。

##  <a name="settooltips"></a>CTabCtrl：： SetToolTips

將工具提示控制項指派給索引標籤控制項。

```
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>參數

*pWndTip*<br/>
工具提示控制項的控制碼。

### <a name="remarks"></a>備註

呼叫 `GetToolTips`，即可取得與索引標籤控制項相關聯的工具提示控制項。

### <a name="example"></a>範例

  請參閱[CPropertySheet：： GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)的範例。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CHeaderCtrl 類別](../../mfc/reference/cheaderctrl-class.md)<br/>
[CListCtrl 類別](../../mfc/reference/clistctrl-class.md)
