---
title: CHeaderCtrl 類別
ms.date: 11/04/2016
f1_keywords:
- CHeaderCtrl
- AFXCMN/CHeaderCtrl
- AFXCMN/CHeaderCtrl::CHeaderCtrl
- AFXCMN/CHeaderCtrl::ClearAllFilters
- AFXCMN/CHeaderCtrl::ClearFilter
- AFXCMN/CHeaderCtrl::Create
- AFXCMN/CHeaderCtrl::CreateDragImage
- AFXCMN/CHeaderCtrl::CreateEx
- AFXCMN/CHeaderCtrl::DeleteItem
- AFXCMN/CHeaderCtrl::DrawItem
- AFXCMN/CHeaderCtrl::EditFilter
- AFXCMN/CHeaderCtrl::GetBitmapMargin
- AFXCMN/CHeaderCtrl::GetFocusedItem
- AFXCMN/CHeaderCtrl::GetImageList
- AFXCMN/CHeaderCtrl::GetItem
- AFXCMN/CHeaderCtrl::GetItemCount
- AFXCMN/CHeaderCtrl::GetItemDropDownRect
- AFXCMN/CHeaderCtrl::GetItemRect
- AFXCMN/CHeaderCtrl::GetOrderArray
- AFXCMN/CHeaderCtrl::GetOverflowRect
- AFXCMN/CHeaderCtrl::HitTest
- AFXCMN/CHeaderCtrl::InsertItem
- AFXCMN/CHeaderCtrl::Layout
- AFXCMN/CHeaderCtrl::OrderToIndex
- AFXCMN/CHeaderCtrl::SetBitmapMargin
- AFXCMN/CHeaderCtrl::SetFilterChangeTimeout
- AFXCMN/CHeaderCtrl::SetFocusedItem
- AFXCMN/CHeaderCtrl::SetHotDivider
- AFXCMN/CHeaderCtrl::SetImageList
- AFXCMN/CHeaderCtrl::SetItem
- AFXCMN/CHeaderCtrl::SetOrderArray
helpviewer_keywords:
- CHeaderCtrl [MFC], CHeaderCtrl
- CHeaderCtrl [MFC], ClearAllFilters
- CHeaderCtrl [MFC], ClearFilter
- CHeaderCtrl [MFC], Create
- CHeaderCtrl [MFC], CreateDragImage
- CHeaderCtrl [MFC], CreateEx
- CHeaderCtrl [MFC], DeleteItem
- CHeaderCtrl [MFC], DrawItem
- CHeaderCtrl [MFC], EditFilter
- CHeaderCtrl [MFC], GetBitmapMargin
- CHeaderCtrl [MFC], GetFocusedItem
- CHeaderCtrl [MFC], GetImageList
- CHeaderCtrl [MFC], GetItem
- CHeaderCtrl [MFC], GetItemCount
- CHeaderCtrl [MFC], GetItemDropDownRect
- CHeaderCtrl [MFC], GetItemRect
- CHeaderCtrl [MFC], GetOrderArray
- CHeaderCtrl [MFC], GetOverflowRect
- CHeaderCtrl [MFC], HitTest
- CHeaderCtrl [MFC], InsertItem
- CHeaderCtrl [MFC], Layout
- CHeaderCtrl [MFC], OrderToIndex
- CHeaderCtrl [MFC], SetBitmapMargin
- CHeaderCtrl [MFC], SetFilterChangeTimeout
- CHeaderCtrl [MFC], SetFocusedItem
- CHeaderCtrl [MFC], SetHotDivider
- CHeaderCtrl [MFC], SetImageList
- CHeaderCtrl [MFC], SetItem
- CHeaderCtrl [MFC], SetOrderArray
ms.assetid: b847ac90-5fae-4a87-88e0-ca45f77b8b3b
ms.openlocfilehash: f225d406ab1560b4308a468ebd71b3dfd88cfa2a
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562168"
---
# <a name="cheaderctrl-class"></a>CHeaderCtrl 類別

提供 Windows 通用標頭控制項的功能。

## <a name="syntax"></a>語法

```
class CHeaderCtrl : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CHeaderCtrl：： CHeaderCtrl](#cheaderctrl)|建構 `CHeaderCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CHeaderCtrl：： ClearAllFilters](#clearallfilters)|清除標題控制項的所有篩選準則。|
|[CHeaderCtrl：： ClearFilter](#clearfilter)|清除標題控制項的篩選。|
|[CHeaderCtrl：： Create](#create)|建立標題控制項並將其附加至 `CHeaderCtrl` 物件。|
|[CHeaderCtrl：： CreateDragImage](#createdragimage)|在標題控制項內建立專案影像的透明版本。|
|[CHeaderCtrl：： CreateEx](#createex)|建立具有指定之 Windows 擴充樣式的標題控制項，並將其附加至 `CListCtrl` 物件。|
|[CHeaderCtrl：:D eleteItem](#deleteitem)|從標題控制項刪除專案。|
|[CHeaderCtrl：:D rawItem](#drawitem)|繪製指定的標題控制項專案。|
|[CHeaderCtrl：： EditFilter](#editfilter)|開始編輯指定的標題控制項篩選。|
|[CHeaderCtrl：： GetBitmapMargin](#getbitmapmargin)|抓取頁首控制項中點陣圖邊界的寬度。|
|[CHeaderCtrl：： GetFocusedItem](#getfocuseditem)|取得具有焦點之目前標題控制項中的專案識別碼。|
|[CHeaderCtrl：： GetImageList](#getimagelist)|抓取用來在標題控制項中繪製標題專案的影像清單控制碼。|
|[CHeaderCtrl：： GetItem](#getitem)|抓取標題控制項中的專案相關資訊。|
|[CHeaderCtrl：： GetItemCount](#getitemcount)|捕獲標題控制項中的專案計數。|
|[CHeaderCtrl：： GetItemDropDownRect](#getitemdropdownrect)|取得標題控制項中所指定下拉式按鈕的周框資訊。|
|[CHeaderCtrl：： GetItemRect](#getitemrect)|抓取標題控制項中指定專案的周框。|
|[CHeaderCtrl：： GetOrderArray](#getorderarray)|抓取標題控制項中專案的由左至右的順序。|
|[CHeaderCtrl：： GetOverflowRect](#getoverflowrect)|取得目前標題控制項之溢位按鈕的周框。|
|[CHeaderCtrl：： System.windows.media.visualtreehelper.hittest](#hittest)|判斷哪個標頭專案（如果有的話）位於指定的點。|
|[CHeaderCtrl：： InsertItem](#insertitem)|將新的專案插入至標題控制項。|
|[CHeaderCtrl：： Layout](#layout)|抓取指定矩形內的標題控制項大小和位置。|
|[CHeaderCtrl：： OrderToIndex](#ordertoindex)|根據標題控制項中的順序，抓取專案的索引值。|
|[CHeaderCtrl：： SetBitmapMargin](#setbitmapmargin)|設定標題控制項中點陣圖邊界的寬度。|
|[CHeaderCtrl：： SetFilterChangeTimeout](#setfilterchangetimeout)|設定篩選屬性與張貼通知的變更時間之間的逾時間隔 `HDN_FILTERCHANGE` 。|
|[CHeaderCtrl：： SetFocusedItem](#setfocuseditem)|將焦點設定為目前標題控制項中的指定標頭專案。|
|[CHeaderCtrl：： SetHotDivider](#sethotdivider)|變更標題專案之間的分隔線，以表示手動拖放標頭專案。|
|[CHeaderCtrl：： SetImageList](#setimagelist)|將影像清單指派給標題控制項。|
|[CHeaderCtrl：： SetItem](#setitem)|在標題控制項中設定指定專案的屬性。|
|[CHeaderCtrl：： SetOrderArray](#setorderarray)|設定標題控制項中專案的由左到右的順序。|

## <a name="remarks"></a>備註

標題控制項是一種視窗，通常位於一組文字或數位的資料行上方。 它包含每個資料行的標題，而且可以分成幾個部分。 使用者可以拖曳分隔各個部分的分隔線，以設定每個資料行的寬度。 如需標題控制項的圖例，請參閱 [標題控制項](/windows/win32/Controls/header-controls)。

此控制項 (，因此 `CHeaderCtrl` 類別) 僅適用于在 Windows 95/98 和 Windows NT 3.51 版和更新版本下執行的程式。

針對 Windows 95/Internet Explorer 4.0 的一般控制項新增的功能包括下列各項：

- 標頭專案自訂順序。

- 拖放的標頭專案，用於重新排列標題專案的順序。 當您建立物件時，請使用 HDS_DRAGDROP 的樣式 `CHeaderCtrl` 。

- 資料行調整大小時，持續可見的標題列文字。 當您建立物件時，請使用 HDS_FULLDRAG 的樣式 `CHeaderCtrl` 。

- 標頭熱追蹤，當指標停留在標題專案上方時，便會將其反白顯示。 當您建立物件時，請使用 HDS_HOTTRACK 的樣式 `CHeaderCtrl` 。

- 影像清單支援。 標頭專案可以包含儲存在 `CImageList` 物件或文字中的影像。

如需使用的詳細資訊 `CHeaderCtrl` ，請參閱 [控制項](../../mfc/controls-mfc.md) 和 [使用 CHeaderCtrl](../../mfc/using-cheaderctrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHeaderCtrl`

## <a name="requirements"></a>規格需求

**標頭：** afxcmn.h

## <a name="cheaderctrlcheaderctrl"></a><a name="cheaderctrl"></a> CHeaderCtrl：： CHeaderCtrl

建構 `CHeaderCtrl` 物件。

```
CHeaderCtrl();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_1.cpp)]

## <a name="cheaderctrlclearallfilters"></a><a name="clearallfilters"></a> CHeaderCtrl：： ClearAllFilters

清除標題控制項的所有篩選準則。

```
BOOL ClearAllFilters();
```

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會以-1 的資料行值來執行 Win32 訊息 [HDM_CLEARFILTER](/windows/win32/Controls/hdm-clearfilter) 的行為，如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_2.cpp)]

## <a name="cheaderctrlclearfilter"></a><a name="clearfilter"></a> CHeaderCtrl：： ClearFilter

清除標題控制項的篩選。

```
BOOL ClearFilter(int nColumn);
```

### <a name="parameters"></a>參數

*nColumn*<br/>
指出要清除之篩選準則的資料行值。

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會執行 Win32 訊息 [HDM_CLEARFILTER](/windows/win32/Controls/hdm-clearfilter)的行為，如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_3.cpp)]

## <a name="cheaderctrlcreate"></a><a name="create"></a> CHeaderCtrl：： Create

建立標題控制項並將其附加至 `CHeaderCtrl` 物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定標題控制項的樣式。 如需標題控制項樣式的描述，請參閱 Windows SDK 中的 [標題控制項樣式](/windows/win32/Controls/header-control-styles) 。

*矩形*<br/>
指定標題控制項的大小和位置。 它可以是 [CRect](../../atl-mfc-shared/reference/crect-class.md) 物件或 [RECT](/windows/win32/api/windef/ns-windef-rect) 結構。

*pParentWnd*<br/>
指定標題控制項的父視窗，通常是 `CDialog` 。 它不得為 NULL。

*nID*<br/>
指定標題控制項的識別碼。

### <a name="return-value"></a>傳回值

如果初始化成功，則為非零;否則為零。

### <a name="remarks"></a>備註

您可以使用 `CHeaderCtrl` 兩個步驟來建立物件。 首先，呼叫此函式，然後呼叫 `Create` ，它會建立標題控制項並將其附加至 `CHeaderCtrl` 物件。

除了標題控制項樣式之外，您還可以使用下列通用控制項樣式來決定頁首控制項的位置和大小， (查看) 詳細資訊的 [通用控制項樣式](/windows/win32/Controls/common-control-styles) ：

- CCS_BOTTOM 會讓控制項將本身定位在父視窗的工作區底部，然後將寬度設定為與父視窗寬度相同。

- CCS_NODIVIDER 防止在控制項頂端繪製兩個圖元的醒目提示。

- CCS_NOMOVEY 會讓控制項調整大小，並以水準方式移動，但不會垂直移動以回應 WM_SIZE 訊息。 如果使用 CCS_NORESIZE 樣式，則不適用這個樣式。 標題控制項預設具有此樣式。

- CCS_NOPARENTALIGN 防止控制項自動移至父視窗的頂端或底部。 相反地，即使父視窗的大小有所變更，控制項仍會在父視窗內保存其位置。 如果也使用了 CCS_TOP 或 CCS_BOTTOM 樣式，則高度會調整為預設值，但位置和寬度會維持不變。

- CCS_NORESIZE 在設定其初始大小或新的大小時，防止控制項使用預設的寬度和高度。 相反地，控制項會使用要求中所指定的寬度和高度來建立或調整大小。

- CCS_TOP 會讓控制項將本身定位在父視窗的工作區頂端，並將寬度設定為與父視窗寬度相同。

您也可以將下列視窗樣式套用至標題控制項 (如需詳細資訊，請參閱 [視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)) ：

- WS_CHILD 建立子視窗。 無法搭配 WS_POPUP 樣式使用。

- WS_VISIBLE 建立一開始可見的視窗。

- WS_DISABLED 會建立一開始停用的視窗。

- WS_GROUP 指定一組控制項的第一個控制項，讓使用者可以使用方向鍵從某個控制項移到下一個控制項。 在第一個控制項屬於相同群組之後，以 WS_GROUP 樣式定義的所有控制項。 下一個具有 WS_GROUP 樣式的控制項會結束樣式群組，並啟動下一個群組 (亦即，一個群組會在下一個開始) 的位置結束。

- WS_TABSTOP 指定任意數目的控制項之一，使用者可以使用 TAB 鍵來移動這些控制項。 TAB 鍵會將使用者移至 WS_TABSTOP 樣式所指定的下一個控制項。

如果您想要將擴充的 windows 樣式用於控制項，請呼叫 [CreateEx](#createex) ，而不是 `Create` 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_4.cpp)]

## <a name="cheaderctrlcreateex"></a><a name="createex"></a> CHeaderCtrl：： CreateEx

 (子視窗) 建立控制項，並將它與物件產生關聯 `CHeaderCtrl` 。

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
指定要建立之控制項的延伸樣式。 如需擴充 Windows 樣式的清單，請參閱 Windows SDK 中[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*參數。

*dwStyle*<br/>
標題控制項的樣式。 如需標題控制項樣式的描述，請參閱 Windows SDK 中的 [標題控制項樣式](/windows/win32/Controls/header-control-styles) 。 如需其他樣式的清單，請參閱 [建立](#create) 。

*矩形*<br/>
[矩形](/windows/win32/api/windef/ns-windef-rect)結構的參考，描述要建立之視窗的大小和位置（以*pParentWnd*的用戶端座標表示）。

*pParentWnd*<br/>
視窗的指標，該視窗為控制項的父代。

*nID*<br/>
控制項的子視窗識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

使用 `CreateEx` 而不是套用 `Create` 延伸的 windows 樣式（由 windows 擴充樣式指定的，在 **WS_EX_** 前面。

## <a name="cheaderctrlcreatedragimage"></a><a name="createdragimage"></a> CHeaderCtrl：： CreateDragImage

在標題控制項內建立專案影像的透明版本。

```
CImageList* CreateDragImage(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
標題控制項中專案的以零為基底的索引。 指派給此專案的影像是透明影像的基礎。

### <a name="return-value"></a>傳回值

如果成功，則為 [CImageList](../../mfc/reference/cimagelist-class.md) 物件的指標;否則為 Null。 傳回的清單中只包含一個影像。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [HDM_CREATEDRAGIMAGE](/windows/win32/Controls/hdm-createdragimage)的行為。 它是提供來支援標頭專案拖放。

`CImageList`傳回的指標指向的物件是暫存物件，並且會在下一次閒置時間處理時刪除。

## <a name="cheaderctrldeleteitem"></a><a name="deleteitem"></a> CHeaderCtrl：:D eleteItem

從標題控制項刪除專案。

```
BOOL DeleteItem(int nPos);
```

### <a name="parameters"></a>參數

*nPos*<br/>
指定要刪除之專案的以零為基底的索引。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#5](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_5.cpp)]

## <a name="cheaderctrldrawitem"></a><a name="drawitem"></a> CHeaderCtrl：:D rawItem

當主控描繪標題控制項的視覺外觀變更時，由架構呼叫。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>參數

*lpDrawItemStruct*<br/>
[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)結構的指標，描述要繪製的專案。

### <a name="remarks"></a>備註

`itemAction`結構的成員 `DRAWITEMSTRUCT` 會定義要執行的繪圖動作。

依預設，此成員函式不會執行任何動作。 覆寫這個成員函式，以針對主控描繪物件來執行繪圖 `CHeaderCtrl` 。

應用程式應該在此成員函式終止之前，還原為 *lpDrawItemStruct* 中提供的顯示內容選取的所有圖形裝置介面 (GDI) 物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_6.cpp)]

## <a name="cheaderctrleditfilter"></a><a name="editfilter"></a> CHeaderCtrl：： EditFilter

開始編輯指定的標題控制項篩選。

```
BOOL EditFilter(
    int nColumn,
    BOOL bDiscardChanges);
```

### <a name="parameters"></a>參數

*nColumn*<br/>
要編輯的資料行。

*bDiscardChanges*<br/>
值，指定在傳送 [HDM_EDITFILTER](/windows/win32/Controls/hdm-editfilter) 訊息時，如果使用者正在編輯篩選，如何處理使用者的編輯變更。

指定 TRUE 以捨棄使用者所做的變更，或指定 FALSE 以接受使用者所做的變更。

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會執行 Win32 訊息 [HDM_EDITFILTER](/windows/win32/Controls/hdm-editfilter)的行為，如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#7](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_7.cpp)]

## <a name="cheaderctrlgetbitmapmargin"></a><a name="getbitmapmargin"></a> CHeaderCtrl：： GetBitmapMargin

抓取頁首控制項中點陣圖邊界的寬度。

```
int GetBitmapMargin() const;
```

### <a name="return-value"></a>傳回值

點陣圖邊界的寬度（以圖元為單位）。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [HDM_GETBITMAPMARGIN](/windows/win32/Controls/hdm-getbitmapmargin)的行為。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#8](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_8.cpp)]

## <a name="cheaderctrlgetfocuseditem"></a><a name="getfocuseditem"></a> CHeaderCtrl：： GetFocusedItem

取得在目前的標題控制項中具有焦點之專案的索引。

```
int GetFocusedItem() const;
```

### <a name="return-value"></a>傳回值

具有焦點之標頭專案的以零為基底的索引。

### <a name="remarks"></a>備註

這個方法會傳送 [HDM_GETFOCUSEDITEM](/windows/win32/Controls/hdm-getfocuseditem) 的訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例 `m_headerCtrl` 會定義用來存取目前標題控制項的變數。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>範例

下列程式碼範例示範 `SetFocusedItem` 和 `GetFocusedItem` 方法。 在程式碼的先前章節中，我們建立了具有五個數據行的標題控制項。 不過，您可以拖曳資料行分隔字元，這樣就不會顯示資料行。 下列範例會設定並確認最後一個資料行標頭為焦點專案。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

## <a name="cheaderctrlgetimagelist"></a><a name="getimagelist"></a> CHeaderCtrl：： GetImageList

抓取用來在標題控制項中繪製標題專案的影像清單控制碼。

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>傳回值

[CImageList](../../mfc/reference/cimagelist-class.md)物件的指標。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [HDM_GETIMAGELIST](/windows/win32/Controls/hdm-getimagelist)的行為。 `CImageList`傳回的指標指向的物件是暫存物件，並且會在下一次閒置時間處理時刪除。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#9](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_11.cpp)]

## <a name="cheaderctrlgetitem"></a><a name="getitem"></a> CHeaderCtrl：： GetItem

抓取標題控制項專案的相關資訊。

```
BOOL GetItem(
    int nPos,
    HDITEM* pHeaderItem) const;
```

### <a name="parameters"></a>參數

*nPos*<br/>
指定要抓取之專案的以零為基底的索引。

*pHeaderItem*<br/>
接收新專案之 [HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) 結構的指標。 此結構會搭配和成員函式使用 `InsertItem` `SetItem` 。 在專案中設定的任何旗標 `mask` ，可確保在傳回時適當地填入對應元素中的值。 如果專案 `mask` 設定為零，則其他結構元素中的值會沒有意義。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#10](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_12.cpp)]

## <a name="cheaderctrlgetitemcount"></a><a name="getitemcount"></a> CHeaderCtrl：： GetItemCount

捕獲標題控制項中的專案計數。

```
int GetItemCount() const;
```

### <a name="return-value"></a>傳回值

如果成功，則為標題控制項專案的數目;否則為-1。

### <a name="example"></a>範例

  請參閱 CHeaderCtrl 的範例 [：:D eleteitem](#deleteitem)。

## <a name="cheaderctrlgetitemdropdownrect"></a><a name="getitemdropdownrect"></a> CHeaderCtrl：： GetItemDropDownRect

取得目前標題控制項中的標題專案之下拉式按鈕的周框。

```
BOOL GetItemDropDownRect(
    int iItem,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

*iItem*\
在以零為基底的索引，其樣式為 HDF_SPLITBUTTON 的標頭專案。 如需詳細資訊，請參閱 `fmt` [HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) 結構的成員。

*lpRect*\
擴展 [矩形](/windows/win32/api/windef/ns-windef-rect) 結構的指標，用來接收周框的資訊。

### <a name="return-value"></a>傳回值

如果此函式成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送 [HDM_GETITEMDROPDOWNRECT](/windows/win32/Controls/hdm-getitemdropdownrect) 的訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例 `m_headerCtrl` 會定義用來存取目前標題控制項的變數。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>範例

下列程式碼範例會示範 `GetItemDropDownRect` 方法。 在程式碼的先前章節中，我們建立了具有五個數據行的標題控制項。 下列程式碼範例會在保留給標頭下拉式按鈕的第一個資料行的位置周圍繪製3D 矩形。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_13.cpp)]

## <a name="cheaderctrlgetitemrect"></a><a name="getitemrect"></a> CHeaderCtrl：： GetItemRect

抓取標題控制項中指定專案的周框。

```
BOOL GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
標題控制項專案之以零為起始的索引。

*lpRect*<br/>
[矩形](/windows/win32/api/windef/ns-windef-rect)位址的指標，此結構會接收周框的矩形資訊。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

這個方法會執行 Win32 訊息 [HDM_GETITEMRECT](/windows/win32/Controls/hdm-getitemrect)的行為，如 Windows SDK 中所述。

## <a name="cheaderctrlgetorderarray"></a><a name="getorderarray"></a> CHeaderCtrl：： GetOrderArray

抓取標題控制項中專案的由左至右的順序。

```
BOOL GetOrderArray(
    LPINT piArray,
    int iCount);
```

### <a name="parameters"></a>參數

*piArray*<br/>
緩衝區位址的指標，此緩衝區會接收標題控制項中專案的索引值，順序是由左至右的順序。

*iCount*<br/>
標題控制項專案的數目。 必須為非負數。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [HDM_GETORDERARRAY](/windows/win32/Controls/hdm-getorderarray)的行為。 它是提供來支援標頭專案順序。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#11](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_14.cpp)]

## <a name="cheaderctrlgetoverflowrect"></a><a name="getoverflowrect"></a> CHeaderCtrl：： GetOverflowRect

取得目前標題控制項之溢位按鈕的周框。

```
BOOL GetOverflowRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

*lpRect*\
擴展 [矩形](/windows/win32/api/windef/ns-windef-rect) 結構的指標，此結構會接收周框的資訊。

### <a name="return-value"></a>傳回值

如果此函式成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

如果標題控制項所包含的專案數超過可同時顯示的專案數，控制項可以顯示會滾動至不可見專案的溢位按鈕。 標題控制項必須有 HDS_OVERFLOW 和 HDF_SPLITBUTTON 樣式才能顯示溢位按鈕。 周框會括住溢位按鈕，而且只有在顯示溢位按鈕時才會存在。 如需詳細資訊，請參閱 [標題控制項樣式](/windows/win32/Controls/header-control-styles)。

這個方法會傳送 [HDM_GETOVERFLOWRECT](/windows/win32/Controls/hdm-getoverflowrect) 的訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例 `m_headerCtrl` 會定義用來存取目前標題控制項的變數。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>範例

下列程式碼範例會示範 `GetOverflowRect` 方法。 在程式碼的先前章節中，我們建立了具有五個數據行的標題控制項。 不過，您可以拖曳資料行分隔字元，這樣就不會顯示資料行。 如果看不到某些資料行，標題控制項會繪製溢位按鈕。 下列程式碼範例會在溢位按鈕的位置周圍繪製3D 矩形。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_15.cpp)]

## <a name="cheaderctrlhittest"></a><a name="hittest"></a> CHeaderCtrl：： System.windows.media.visualtreehelper.hittest

判斷哪個標頭專案（如果有的話）位於指定的點。

```
int HitTest(LPHDHITTESTINFO* phdhti);
```

### <a name="parameters"></a>參數

*phdhti*\
[in，out] [HDHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-hdhittestinfo) 結構的指標，指定測試及接收測試結果的點。

### <a name="return-value"></a>傳回值

標頭專案之以零為起始的索引（如果有的話），位於指定的位置;否則為-1。

### <a name="remarks"></a>備註

這個方法會傳送 [HDM_HITTEST](/windows/win32/Controls/hdm-hittest) 的訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例 `m_headerCtrl` 會定義用來存取目前標題控制項的變數。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>範例

下列程式碼範例會示範 `HitTest` 方法。 在此程式碼範例的先前章節中，我們建立了具有五個數據行的標題控制項。 不過，您可以拖曳資料行分隔字元，這樣就不會顯示資料行。 如果看得到資料行，此範例會報告資料行的索引，如果看不到資料行，則為-1。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_16.cpp)]

## <a name="cheaderctrlinsertitem"></a><a name="insertitem"></a> CHeaderCtrl：： InsertItem

將新專案插入標題控制項中指定的索引處。

```
int InsertItem(
    int nPos,
    HDITEM* phdi);
```

### <a name="parameters"></a>參數

*nPos*<br/>
要插入之項目之以零起始的索引。 如果值為零，則會在標題控制項的開頭插入專案。 如果值大於最大值，則會將專案插入標題控制項的結尾。

*phdi*<br/>
[HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw)結構的指標，其中包含要插入之專案的相關資訊。

### <a name="return-value"></a>傳回值

如果成功，則為新專案的索引;否則為-1。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#12](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_17.cpp)]

## <a name="cheaderctrllayout"></a><a name="layout"></a> CHeaderCtrl：： Layout

抓取指定矩形內的標題控制項大小和位置。

```
BOOL Layout(HDLAYOUT* pHeaderLayout);
```

### <a name="parameters"></a>參數

*pHeaderLayout*<br/>
[HDLAYOUT](/windows/win32/api/commctrl/ns-commctrl-hdlayout)結構的指標，其中包含用來設定標題控制項之大小和位置的資訊。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

這個函式是用來判斷新標題控制項的適當維度，以佔用指定的矩形。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#13](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_18.cpp)]

## <a name="cheaderctrlordertoindex"></a><a name="ordertoindex"></a> CHeaderCtrl：： OrderToIndex

根據標題控制項中的順序，抓取專案的索引值。

```
int OrderToIndex(int nOrder) const;
```

### <a name="parameters"></a>參數

*nOrder*<br/>
專案在標題控制項中顯示的以零為基底的順序，由左至右。

### <a name="return-value"></a>傳回值

專案的索引（根據其在標題控制項中的順序）。 索引會從左至右算起，從0開始計算。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 宏 [HDM_ORDERTOINDEX](/windows/win32/controls/hdm-ordertoindex)的行為。 它是提供來支援標頭專案順序。

## <a name="cheaderctrlsetbitmapmargin"></a><a name="setbitmapmargin"></a> CHeaderCtrl：： SetBitmapMargin

設定標題控制項中點陣圖邊界的寬度。

```
int SetBitmapMargin(int nWidth);
```

### <a name="parameters"></a>參數

*nWidth*<br/>
在現有標題控制項中圍繞點陣圖之邊界的寬度（以圖元為單位）。

### <a name="return-value"></a>傳回值

點陣圖邊界的寬度（以圖元為單位）。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [HDM_SETBITMAPMARGIN](/windows/win32/Controls/hdm-setbitmapmargin)的行為。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#14](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_19.cpp)]

## <a name="cheaderctrlsetfilterchangetimeout"></a><a name="setfilterchangetimeout"></a> CHeaderCtrl：： SetFilterChangeTimeout

設定篩選屬性中發生變更和張貼 [HDN_FILTERCHANGE](/windows/win32/Controls/hdn-filterchange) 通知之間的逾時間隔。

```
int SetFilterChangeTimeout(DWORD dwTimeOut);
```

### <a name="parameters"></a>參數

*dwTimeOut*<br/>
Timeout 值（以毫秒為單位）。

### <a name="return-value"></a>傳回值

正在修改之篩選控制項的索引。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [HDM_SETFILTERCHANGETIMEOUT](/windows/win32/Controls/hdm-setfilterchangetimeout)的行為。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#15](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_20.cpp)]

## <a name="cheaderctrlsetfocuseditem"></a><a name="setfocuseditem"></a> CHeaderCtrl：： SetFocusedItem

將焦點設定為目前標題控制項中的指定標頭專案。

```
BOOL SetFocusedItem(int iItem);
```

### <a name="parameters"></a>參數

*iItem*\
在以零為基底的標頭專案索引。

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送 [HDM_SETFOCUSEDITEM](/windows/win32/Controls/hdm-setfocuseditem) 的訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例 `m_headerCtrl` 會定義用來存取目前標題控制項的變數。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>範例

下列程式碼範例示範 `SetFocusedItem` 和 `GetFocusedItem` 方法。 在程式碼的先前章節中，我們建立了具有五個數據行的標題控制項。 不過，您可以拖曳資料行分隔字元，這樣就不會顯示資料行。 下列範例會設定並確認最後一個資料行標頭為焦點專案。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

## <a name="cheaderctrlsethotdivider"></a><a name="sethotdivider"></a> CHeaderCtrl：： SetHotDivider

變更標題專案之間的分隔線，以表示手動拖放標頭專案。

```
int SetHotDivider(CPoint pt);
int SetHotDivider(int nIndex);
```

### <a name="parameters"></a>參數

*pt*<br/>
指標的位置。 標題控制項會根據指標的位置反白顯示適當的分隔線。

*nIndex*<br/>
反白顯示之分隔線的索引。

### <a name="return-value"></a>傳回值

反白顯示之分隔線的索引。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [HDM_SETHOTDIVIDER](/windows/win32/Controls/hdm-sethotdivider)的行為。 它是提供來支援標頭專案拖放。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#16](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_21.cpp)]

## <a name="cheaderctrlsetimagelist"></a><a name="setimagelist"></a> CHeaderCtrl：： SetImageList

將影像清單指派給標題控制項。

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>參數

*pImageList*<br/>
物件的指標， `CImageList` 其中包含要指派給標題控制項的影像清單。

### <a name="return-value"></a>傳回值

先前指派給標題控制項之 [CImageList](../../mfc/reference/cimagelist-class.md) 物件的指標。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [HDM_SETIMAGELIST](/windows/win32/Controls/hdm-setimagelist)的行為。 `CImageList`傳回的指標指向的物件是暫存物件，並且會在下一次閒置時間處理時刪除。

### <a name="example"></a>範例

  請參閱 [CHeaderCtrl：： GetImageList](#getimagelist)的範例。

## <a name="cheaderctrlsetitem"></a><a name="setitem"></a> CHeaderCtrl：： SetItem

在標題控制項中設定指定專案的屬性。

```
BOOL SetItem(
    int nPos,
    HDITEM* pHeaderItem);
```

### <a name="parameters"></a>參數

*nPos*<br/>
要操作之專案的以零為基底的索引。

*pHeaderItem*<br/>
[HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw)結構的指標，其中包含新專案的相關資訊。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

  請參閱 [CHeaderCtrl：： GetItem](#getitem)的範例。

## <a name="cheaderctrlsetorderarray"></a><a name="setorderarray"></a> CHeaderCtrl：： SetOrderArray

設定標題控制項中專案的由左到右的順序。

```
BOOL SetOrderArray(
    int iCount,
    LPINT piArray);
```

### <a name="parameters"></a>參數

*iCount*<br/>
標題控制項專案的數目。

*piArray*<br/>
緩衝區位址的指標，此緩衝區會接收標題控制項中專案的索引值，順序是由左至右的順序。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 宏 [HDM_SETORDERARRAY](/windows/win32/Controls/hdm-setorderarray)的行為。 它是提供來支援標頭專案順序。

### <a name="example"></a>範例

  請參閱 [CHeaderCtrl：： GetOrderArray](#getorderarray)的範例。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CTabCtrl 類別](../../mfc/reference/ctabctrl-class.md)<br/>
[CListCtrl 類別](../../mfc/reference/clistctrl-class.md)<br/>
[CImageList 類別](../../mfc/reference/cimagelist-class.md)
