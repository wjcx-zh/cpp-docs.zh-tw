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
ms.openlocfilehash: 62915da703e1c938e65643ab389999b83c72d459
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741521"
---
# <a name="cheaderctrl-class"></a>CHeaderCtrl 類別

提供 Windows 通用標頭控制項的功能。

## <a name="syntax"></a>語法

```
class CHeaderCtrl : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CHeaderCtrl::CHeaderCtrl](#cheaderctrl)|建構 `CHeaderCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CHeaderCtrl::ClearAllFilters](#clearallfilters)|清除標題控制項的所有篩選。|
|[CHeaderCtrl::ClearFilter](#clearfilter)|清除標題控制項的篩選準則。|
|[CHeaderCtrl::Create](#create)|建立標題控制項並將其附加至`CHeaderCtrl`物件。|
|[CHeaderCtrl::CreateDragImage](#createdragimage)|在標題控制項內建立專案影像的透明版本。|
|[CHeaderCtrl::CreateEx](#createex)|使用指定的 Windows 擴充樣式建立標題控制項，並將其附加至`CListCtrl`物件。|
|[CHeaderCtrl::DeleteItem](#deleteitem)|刪除標題控制項中的專案。|
|[CHeaderCtrl::DrawItem](#drawitem)|繪製標題控制項的指定專案。|
|[CHeaderCtrl::EditFilter](#editfilter)|開始編輯標頭控制項的指定篩選。|
|[CHeaderCtrl::GetBitmapMargin](#getbitmapmargin)|抓取標題控制項中點陣圖邊界的寬度。|
|[CHeaderCtrl::GetFocusedItem](#getfocuseditem)|取得目前標題控制項中具有焦點之專案的識別碼。|
|[CHeaderCtrl::GetImageList](#getimagelist)|抓取用於在標題控制項中繪製標題專案之影像清單的控制碼。|
|[CHeaderCtrl::GetItem](#getitem)|抓取標題控制項中專案的相關資訊。|
|[CHeaderCtrl::GetItemCount](#getitemcount)|抓取標題控制項中的專案計數。|
|[CHeaderCtrl::GetItemDropDownRect](#getitemdropdownrect)|取得標題控制項中指定下拉按鈕的周框資訊。|
|[CHeaderCtrl::GetItemRect](#getitemrect)|抓取標題控制項中指定專案的周框。|
|[CHeaderCtrl::GetOrderArray](#getorderarray)|抓取標題控制項中專案的由左至右順序。|
|[CHeaderCtrl::GetOverflowRect](#getoverflowrect)|取得目前標題控制項之溢位按鈕的周框。|
|[CHeaderCtrl::HitTest](#hittest)|判斷哪個標頭專案（如果有的話）位於指定的點。|
|[CHeaderCtrl::InsertItem](#insertitem)|將新專案插入至標題控制項。|
|[CHeaderCtrl::Layout](#layout)|抓取指定矩形內標題控制項的大小和位置。|
|[CHeaderCtrl::OrderToIndex](#ordertoindex)|根據標題控制項中的順序，抓取專案的索引值。|
|[CHeaderCtrl::SetBitmapMargin](#setbitmapmargin)|設定標題控制項中點陣圖邊界的寬度。|
|[CHeaderCtrl::SetFilterChangeTimeout](#setfilterchangetimeout)|設定在篩選屬性中進行變更和張貼`HDN_FILTERCHANGE`通知之間的逾時間隔。|
|[CHeaderCtrl::SetFocusedItem](#setfocuseditem)|將焦點設定為目前標題控制項中的指定標題專案。|
|[CHeaderCtrl::SetHotDivider](#sethotdivider)|變更標頭專案之間的分隔線，以指示標頭專案的手動拖放。|
|[CHeaderCtrl::SetImageList](#setimagelist)|將影像清單指派給標題控制項。|
|[CHeaderCtrl::SetItem](#setitem)|設定標題控制項中指定專案的屬性。|
|[CHeaderCtrl::SetOrderArray](#setorderarray)|設定標題控制項中專案的由左至右順序。|

## <a name="remarks"></a>備註

標題控制項是一個視窗，通常位於一組文字或數位的資料行上方。 它包含每個資料行的標題，而且可以分成幾個部分。 使用者可以拖曳分隔各個部分的分隔線，以設定每個資料行的寬度。 如需標題控制項的圖例，請參閱[標頭控制項](/windows/win32/Controls/header-controls)。

這個控制項（因此`CHeaderCtrl`類別）僅適用于在 windows 95/98 和 windows NT 3.51 版和更新版本下執行的程式。

針對 Windows 95/Internet Explorer 4.0 通用控制項新增的功能包括下列各項：

- 標頭專案自訂順序。

- 標頭專案拖放，用於重新排列標頭專案。 當您建立`CHeaderCtrl`物件時，請使用 HDS_DRAGDROP 樣式。

- 資料行調整大小時，標題列文字持續可供查看。 當您建立`CHeaderCtrl`物件時，請使用 HDS_FULLDRAG 樣式。

- 標頭熱追蹤，這會在指標停留在標題專案上方時反白顯示。 當您建立`CHeaderCtrl`物件時，請使用 HDS_HOTTRACK 樣式。

- 影像清單支援。 標頭專案可以包含儲存在`CImageList`物件或文字中的影像。

如需使用`CHeaderCtrl`的詳細資訊，請參閱[控制項](../../mfc/controls-mfc.md)和[使用 CHeaderCtrl](../../mfc/using-cheaderctrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHeaderCtrl`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

##  <a name="cheaderctrl"></a>CHeaderCtrl：： CHeaderCtrl

建構 `CHeaderCtrl` 物件。

```
CHeaderCtrl();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_1.cpp)]

##  <a name="clearallfilters"></a>CHeaderCtrl：： ClearAllFilters

清除標題控制項的所有篩選。

```
BOOL ClearAllFilters();
```

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會以-1 的資料行值來執行 Win32 message [HDM_CLEARFILTER](/windows/win32/Controls/hdm-clearfilter)的行為，如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_2.cpp)]

##  <a name="clearfilter"></a>  CHeaderCtrl::ClearFilter

清除標題控制項的篩選準則。

```
BOOL ClearFilter(int nColumn);
```

### <a name="parameters"></a>參數

*nColumn*<br/>
指出要清除哪一個篩選的資料行值。

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會執行 Win32 message [HDM_CLEARFILTER](/windows/win32/Controls/hdm-clearfilter)的行為，如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_3.cpp)]

##  <a name="create"></a>CHeaderCtrl：： Create

建立標題控制項並將其附加至`CHeaderCtrl`物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定標題控制項的樣式。 如需標題控制項樣式的說明，請參閱 Windows SDK 中的[標題控制項樣式](/windows/win32/Controls/header-control-styles)。

*rect*<br/>
指定標題控制項的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](/previous-versions/dd162897\(v=vs.85\))結構。

*pParentWnd*<br/>
指定標題控制項的父視窗，通常是`CDialog`。 不得為 Null。

*nID*<br/>
指定標頭控制項的識別碼。

### <a name="return-value"></a>傳回值

如果初始化成功，則為非零;否則為零。

### <a name="remarks"></a>備註

您可以使用`CHeaderCtrl`兩個步驟來建立物件。 首先，呼叫此函式，然後`Create`呼叫，它會建立標頭控制項並將其`CHeaderCtrl`附加至物件。

除了標題控制項樣式以外，您還可以使用下列通用控制項樣式，來判斷標題控制項的位置和大小本身（如需詳細資訊，請參閱[常見的控制項樣式](/windows/win32/Controls/common-control-styles)）：

- CCS_BOTTOM 會讓控制項在父視窗的工作區底部放置自己的位置，並將寬度設定為與父視窗的寬度相同。

- CCS_NODIVIDER 可防止在控制項的頂端繪製兩個圖元的反白顯示。

- CCS_NOMOVEY 會導致控制項調整大小，並在回應 WM_SIZE 訊息時，以垂直方式移動其本身。 如果使用 CCS_NORESIZE 樣式，則不適用此樣式。 標題控制項預設具有此樣式。

- CCS_NOPARENTALIGN 可防止控制項自動移至父視窗的頂端或底部。 相反地，控制項會在父視窗中保留其位置，而不論父視窗的大小變更。 如果也使用 CCS_TOP 或 CCS_BOTTOM 樣式，則高度會調整為預設值，但位置和寬度會保持不變。

- CCS_NORESIZE 可防止控制項在設定其初始大小或新大小時，使用預設的寬度和高度。 相反地，控制項會使用建立或調整大小要求中所指定的寬度和高度。

- CCS_TOP 會讓控制項將本身放在父視窗工作區的頂端，並將寬度設定為與父視窗的寬度相同。

您也可以將下列視窗樣式套用至標題控制項（如需詳細資訊，請參閱[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)）：

- WS_CHILD 會建立子視窗。 不能與 WS_POPUP 樣式一起使用。

- WS_VISIBLE 會建立一開始顯示的視窗。

- WS_DISABLED 會建立一開始停用的視窗。

- WS_GROUP 指定控制項群組的第一個控制項，使用者可以在其中使用方向鍵從某個控制項移到下一個控制項。 在第一個控制項屬於相同群組之後，以 WS_GROUP 樣式定義的所有控制項。 下一個具有 WS_GROUP 樣式的控制項會結束樣式群組並啟動下一個群組（也就是一個群組結束于下一個開始的位置）。

- WS_TABSTOP 會指定使用者可以使用 TAB 鍵移動的任意數目的控制項。 TAB 鍵會將使用者移至 WS_TABSTOP 樣式所指定的下一個控制項。

如果您想要搭配控制項使用擴充的 windows 樣式，請呼叫[CreateEx](#createex) ， `Create`而不是。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_4.cpp)]

##  <a name="createex"></a>CHeaderCtrl：： CreateEx

建立控制項（子視窗），並將它與`CHeaderCtrl`物件產生關聯。

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
標題控制項的樣式。 如需標題控制項樣式的說明，請參閱 Windows SDK 中的[標題控制項樣式](/windows/win32/Controls/header-control-styles)。 如需其他樣式的清單，請參閱[建立](#create)。

*rect*<br/>
[矩形](/previous-versions/dd162897\(v=vs.85\))結構的參考，描述要建立之視窗的大小和位置，以*pParentWnd*的用戶端座標表示。

*pParentWnd*<br/>
做為控制項父系之視窗的指標。

*nID*<br/>
控制項的子視窗識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

使用`CreateEx`而非來套用擴充的 windows 樣式（由 Windows 擴充樣式指定于 WS_EX_ 的前面） `Create` 。

##  <a name="createdragimage"></a>CHeaderCtrl：： CreateDragImage

在標題控制項內建立專案影像的透明版本。

```
CImageList* CreateDragImage(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
標題控制項中專案之以零為起始的索引。 指派給這個專案的影像是透明影像的基礎。

### <a name="return-value"></a>傳回值

如果成功，則為[CImageList](../../mfc/reference/cimagelist-class.md)物件的指標;否則為 Null。 傳回的清單只包含一個影像。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [HDM_CREATEDRAGIMAGE](/windows/win32/Controls/hdm-createdragimage)的行為，如 Windows SDK 中所述。 它是提供來支援標頭專案拖放。

傳回的指標指向的物件是暫存物件，而且會在下一個閒置時間處理中刪除。`CImageList`

##  <a name="deleteitem"></a>CHeaderCtrl：:D eleteItem

刪除標題控制項中的專案。

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

##  <a name="drawitem"></a>CHeaderCtrl：:D rawItem

當主控描繪標題控制項的視覺外觀變更時，由架構呼叫。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>參數

*lpDrawItemStruct*<br/>
[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)結構的指標，描述要繪製的專案。

### <a name="remarks"></a>備註

`DRAWITEMSTRUCT`結構的成員會定義要執行的繪圖動作。 `itemAction`

根據預設，此成員函式不會執行任何工作。 覆寫這個成員函式，以執行主控描繪`CHeaderCtrl`物件的繪圖。

在此成員函式終止之前，應用程式應該還原為*lpDrawItemStruct*中提供的顯示內容所選取的所有圖形裝置介面（GDI）物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_6.cpp)]

##  <a name="editfilter"></a>CHeaderCtrl：： EditFilter

開始編輯標頭控制項的指定篩選。

```
BOOL EditFilter(
    int nColumn,
    BOOL bDiscardChanges);
```

### <a name="parameters"></a>參數

*nColumn*<br/>
要編輯的資料行。

*bDiscardChanges*<br/>
值，指定當傳送[HDM_EDITFILTER](/windows/win32/Controls/hdm-editfilter)訊息時，使用者正在編輯篩選的過程中，如何處理使用者的編輯變更。

指定 TRUE 以捨棄使用者所做的變更，或使用 FALSE 來接受使用者所做的變更。

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會執行 Win32 message [HDM_EDITFILTER](/windows/win32/Controls/hdm-editfilter)的行為，如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#7](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_7.cpp)]

##  <a name="getbitmapmargin"></a>CHeaderCtrl：： GetBitmapMargin

抓取標題控制項中點陣圖邊界的寬度。

```
int GetBitmapMargin() const;
```

### <a name="return-value"></a>傳回值

點陣圖邊界的寬度（以圖元為單位）。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [HDM_GETBITMAPMARGIN](/windows/win32/Controls/hdm-getbitmapmargin)的行為，如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#8](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_8.cpp)]

##  <a name="getfocuseditem"></a>CHeaderCtrl：： GetFocusedItem

取得在目前標題控制項中具有焦點之專案的索引。

```
int GetFocusedItem() const;
```

### <a name="return-value"></a>傳回值

具有焦點之標頭專案的以零為基底的索引。

### <a name="remarks"></a>備註

這個方法會傳送[HDM_GETFOCUSEDITEM](/windows/win32/Controls/hdm-getfocuseditem)訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義用來`m_headerCtrl`存取目前標題控制項的變數。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>範例

下列程式碼範例示範`SetFocusedItem`和`GetFocusedItem`方法。 在先前的程式碼區段中，我們建立了具有五個數據行的標題控制項。 不過，您可以拖曳資料行分隔符號，讓資料行看不見。 下列範例會設定並確認最後一個資料行標頭為焦點專案。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

##  <a name="getimagelist"></a>CHeaderCtrl：： GetImageList

抓取用於在標題控制項中繪製標題專案之影像清單的控制碼。

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>傳回值

[CImageList](../../mfc/reference/cimagelist-class.md)物件的指標。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [HDM_GETIMAGELIST](/windows/win32/Controls/hdm-getimagelist)的行為，如 Windows SDK 中所述。 傳回的指標指向的物件是暫存物件，而且會在下一個閒置時間處理中刪除。`CImageList`

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#9](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_11.cpp)]

##  <a name="getitem"></a>CHeaderCtrl：： GetItem

抓取標題控制項專案的相關資訊。

```
BOOL GetItem(
    int nPos,
    HDITEM* pHeaderItem) const;
```

### <a name="parameters"></a>參數

*nPos*<br/>
指定要抓取之專案的以零為起始的索引。

*pHeaderItem*<br/>
接收新專案之[HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw)結構的指標。 這個結構會與`InsertItem`和`SetItem`成員函式搭配使用。 `mask`元素中設定的任何旗標，可確保在傳回時適當地填入對應元素中的值。 `mask`如果專案設定為零，其他結構專案中的值就沒有意義。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#10](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_12.cpp)]

##  <a name="getitemcount"></a>CHeaderCtrl：： GetItemCount

抓取標題控制項中的專案計數。

```
int GetItemCount() const;
```

### <a name="return-value"></a>傳回值

如果成功，則為標頭控制項專案的數目;否則為-1。

### <a name="example"></a>範例

  請參閱[CHeaderCtrl：:D eleteitem](#deleteitem)的範例。

##  <a name="getitemdropdownrect"></a>CHeaderCtrl：： GetItemDropDownRect

取得目前標題控制項中標題專案之下拉按鈕的周框。

```
BOOL GetItemDropDownRect(
    int iItem,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

|參數|說明|
|---------------|-----------------|
|*iItem*|在標頭專案的以零為基底的索引，其樣式為 HDF_SPLITBUTTON。 如需詳細資訊，請`fmt`參閱[HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw)結構的成員。|
|*lpRect*|脫銷用來接收周框資訊之[RECT](/previous-versions/dd162897\(v=vs.85\))結構的指標。|

### <a name="return-value"></a>傳回值

如果此函式成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[HDM_GETITEMDROPDOWNRECT](/windows/win32/Controls/hdm-getitemdropdownrect)訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義用來`m_headerCtrl`存取目前標題控制項的變數。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>範例

下列程式碼範例示範`GetItemDropDownRect`方法。 在先前的程式碼區段中，我們建立了具有五個數據行的標題控制項。 下列程式碼範例會在保留給標頭下拉按鈕的第一個資料行上，繪製一個圍繞位置的3D 矩形。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_13.cpp)]

##  <a name="getitemrect"></a>CHeaderCtrl：： GetItemRect

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
接收周框資訊之[RECT](/previous-versions/dd162897\(v=vs.85\))結構位址的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

這個方法會執行 Win32 message [HDM_GETITEMRECT](/windows/win32/Controls/hdm-getitemrect)的行為，如 Windows SDK 中所述。

##  <a name="getorderarray"></a>CHeaderCtrl：： GetOrderArray

抓取標題控制項中專案的由左至右順序。

```
BOOL GetOrderArray(
    LPINT piArray,
    int iCount);
```

### <a name="parameters"></a>參數

*piArray*<br/>
緩衝區位址的指標，接收標頭控制項中專案的索引值（依其出現的順序）。

*iCount*<br/>
標題控制項專案的數目。 必須為非負數。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [HDM_GETORDERARRAY](/windows/win32/Controls/hdm-getorderarray)的行為，如 Windows SDK 中所述。 它是提供來支援標頭專案排序。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#11](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_14.cpp)]

##  <a name="getoverflowrect"></a>CHeaderCtrl：： GetOverflowRect

取得目前標題控制項之溢位按鈕的周框。

```
BOOL GetOverflowRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*lpRect*|脫銷接收周框資訊之[RECT](/previous-versions/dd162897\(v=vs.85\))結構的指標。|

### <a name="return-value"></a>傳回值

如果此函式成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

如果標題控制項所包含的專案數多於可以同時顯示的數目，控制項可以顯示會滾動至不可見專案的溢位按鈕。 標題控制項必須具有 HDS_OVERFLOW 和 HDF_SPLITBUTTON 樣式，才能顯示溢位按鈕。 周框方塊會括住溢位按鈕，只有在顯示溢位按鈕時才會存在。 如需詳細資訊，請參閱[標題控制項樣式](/windows/win32/Controls/header-control-styles)。

這個方法會傳送[HDM_GETOVERFLOWRECT](/windows/win32/Controls/hdm-getoverflowrect)訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義用來`m_headerCtrl`存取目前標題控制項的變數。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>範例

下列程式碼範例示範`GetOverflowRect`方法。 在先前的程式碼區段中，我們建立了具有五個數據行的標題控制項。 不過，您可以拖曳資料行分隔符號，讓資料行看不見。 如果看不到某些資料行，標題控制項會繪製溢位按鈕。 下列程式碼範例會在溢位按鈕的位置周圍繪製3D 矩形。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_15.cpp)]

##  <a name="hittest"></a>CHeaderCtrl：： HitTest

判斷哪個標頭專案（如果有的話）位於指定的點。

```
int HitTest(LPHDHITTESTINFO* phdhti);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*phdhti*|[in、out][HDHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-hdhittestinfo)結構的指標，指定要測試的點，並接收測試的結果。|

### <a name="return-value"></a>傳回值

在指定位置的標頭專案之以零為起始的索引（如果有的話）。否則為-1。

### <a name="remarks"></a>備註

這個方法會傳送[HDM_HITTEST](/windows/win32/Controls/hdm-hittest)訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義用來`m_headerCtrl`存取目前標題控制項的變數。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>範例

下列程式碼範例示範`HitTest`方法。 在此程式碼範例的先前章節中，我們建立了具有五個數據行的標題控制項。 不過，您可以拖曳資料行分隔符號，讓資料行看不見。 這個範例會報告資料行的索引（如果有的話），如果看不到資料行，則為-1。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_16.cpp)]

##  <a name="insertitem"></a>CHeaderCtrl：： InsertItem

將新專案插入至指定索引處的標頭控制項。

```
int InsertItem(
    int nPos,
    HDITEM* phdi);
```

### <a name="parameters"></a>參數

*nPos*<br/>
要插入之項目之以零起始的索引。 如果值為零，則會將專案插入標頭控制項的開頭。 如果值大於最大值，則會將專案插入標題控制項的結尾。

*phdi*<br/>
[HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw)結構的指標，其中包含要插入之專案的相關資訊。

### <a name="return-value"></a>傳回值

如果成功，則為新專案的索引;否則為-1。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#12](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_17.cpp)]

##  <a name="layout"></a>CHeaderCtrl：： Layout

抓取指定矩形內標題控制項的大小和位置。

```
BOOL Layout(HDLAYOUT* pHeaderLayout);
```

### <a name="parameters"></a>參數

*pHeaderLayout*<br/>
[HDLAYOUT](/windows/win32/api/commctrl/ns-commctrl-hdlayout)結構的指標，其中包含用來設定標題控制項之大小和位置的資訊。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此函式是用來為新的標題控制項決定適當的維度，以佔用指定的矩形。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#13](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_18.cpp)]

##  <a name="ordertoindex"></a>  CHeaderCtrl::OrderToIndex

根據標題控制項中的順序，抓取專案的索引值。

```
int OrderToIndex(int nOrder) const;
```

### <a name="parameters"></a>參數

*nOrder*<br/>
專案出現在標題控制項中的以零為起始的順序（由左至右）。

### <a name="return-value"></a>傳回值

專案的索引，根據其在標題控制項中的順序。 索引會從左至右算起，從0開始計算。

### <a name="remarks"></a>備註

此成員函式會實作用 Win32 宏[HDM_ORDERTOINDEX](/windows/win32/controls/hdm-ordertoindex)的行為，如 Windows SDK 中所述。 它是提供來支援標頭專案排序。

##  <a name="setbitmapmargin"></a>CHeaderCtrl：： SetBitmapMargin

設定標題控制項中點陣圖邊界的寬度。

```
int SetBitmapMargin(int nWidth);
```

### <a name="parameters"></a>參數

*nWidth*<br/>
在現有標題控制項內環繞點陣圖之邊界的寬度（以圖元為單位）。

### <a name="return-value"></a>傳回值

點陣圖邊界的寬度（以圖元為單位）。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [HDM_SETBITMAPMARGIN](/windows/win32/Controls/hdm-setbitmapmargin)的行為，如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#14](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_19.cpp)]

##  <a name="setfilterchangetimeout"></a>CHeaderCtrl：： SetFilterChangeTimeout

設定篩選屬性中發生變更的時間與張貼[HDN_FILTERCHANGE](/windows/win32/Controls/hdn-filterchange)通知之間的逾時間隔。

```
int SetFilterChangeTimeout(DWORD dwTimeOut);
```

### <a name="parameters"></a>參數

*dwTimeOut*<br/>
Timeout 值（以毫秒為單位）。

### <a name="return-value"></a>傳回值

正在修改之篩選控制項的索引。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [HDM_SETFILTERCHANGETIMEOUT](/windows/win32/Controls/hdm-setfilterchangetimeout)的行為，如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#15](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_20.cpp)]

##  <a name="setfocuseditem"></a>CHeaderCtrl：： SetFocusedItem

將焦點設定為目前標題控制項中的指定標題專案。

```
BOOL SetFocusedItem(int iItem);
```

### <a name="parameters"></a>參數

|參數|說明|
|---------------|-----------------|
|*iItem*|在標頭專案以零為基底的索引。|

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[HDM_SETFOCUSEDITEM](/windows/win32/Controls/hdm-setfocuseditem)訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義用來`m_headerCtrl`存取目前標題控制項的變數。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>範例

下列程式碼範例示範`SetFocusedItem`和`GetFocusedItem`方法。 在先前的程式碼區段中，我們建立了具有五個數據行的標題控制項。 不過，您可以拖曳資料行分隔符號，讓資料行看不見。 下列範例會設定並確認最後一個資料行標頭為焦點專案。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

##  <a name="sethotdivider"></a>CHeaderCtrl：： SetHotDivider

變更標頭專案之間的分隔線，以指示標頭專案的手動拖放。

```
int SetHotDivider(CPoint pt);
int SetHotDivider(int nIndex);
```

### <a name="parameters"></a>參數

*pt*<br/>
指標的位置。 標題控制項會根據指標的位置來反白顯示適當的分隔線。

*nIndex*<br/>
反白顯示之分隔線的索引。

### <a name="return-value"></a>傳回值

反白顯示之分隔線的索引。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [HDM_SETHOTDIVIDER](/windows/win32/Controls/hdm-sethotdivider)的行為，如 Windows SDK 中所述。 它是提供來支援標頭專案拖放。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#16](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_21.cpp)]

##  <a name="setimagelist"></a>CHeaderCtrl：： SetImageList

將影像清單指派給標題控制項。

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>參數

*pImageList*<br/>
`CImageList`物件的指標，包含要指派給標題控制項的影像清單。

### <a name="return-value"></a>傳回值

先前指派給標題控制項之[CImageList](../../mfc/reference/cimagelist-class.md)物件的指標。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [HDM_SETIMAGELIST](/windows/win32/Controls/hdm-setimagelist)的行為，如 Windows SDK 中所述。 傳回的指標指向的物件是暫存物件，而且會在下一個閒置時間處理中刪除。`CImageList`

### <a name="example"></a>範例

  請參閱[CHeaderCtrl：： GetImageList](#getimagelist)的範例。

##  <a name="setitem"></a>CHeaderCtrl：： SetItem

設定標題控制項中指定專案的屬性。

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

  請參閱[CHeaderCtrl：： GetItem](#getitem)的範例。

##  <a name="setorderarray"></a>  CHeaderCtrl::SetOrderArray

設定標題控制項中專案的由左至右順序。

```
BOOL SetOrderArray(
    int iCount,
    LPINT piArray);
```

### <a name="parameters"></a>參數

*iCount*<br/>
標題控制項專案的數目。

*piArray*<br/>
緩衝區位址的指標，接收標頭控制項中專案的索引值（依其出現的順序）。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式會實作用 Win32 宏[HDM_SETORDERARRAY](/windows/win32/Controls/hdm-setorderarray)的行為，如 Windows SDK 中所述。 它是提供來支援標頭專案排序。

### <a name="example"></a>範例

  請參閱[CHeaderCtrl：： GetOrderArray](#getorderarray)的範例。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CTabCtrl 類別](../../mfc/reference/ctabctrl-class.md)<br/>
[CListCtrl 類別](../../mfc/reference/clistctrl-class.md)<br/>
[CImageList 類別](../../mfc/reference/cimagelist-class.md)
