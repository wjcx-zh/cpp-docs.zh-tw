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
ms.openlocfilehash: 6b5088526ad2c1f94fdc95ec3b84ab7cf64b59e1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366858"
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
|[斬首::斬首](#cheaderctrl)|建構 `CHeaderCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[斬首::清除所有篩選器](#clearallfilters)|清除標頭控制件的所有篩選器。|
|[斬首::清除過濾器](#clearfilter)|清除標頭控制的篩選器。|
|[斬首::建立](#create)|創建標頭控制項並將其附加到`CHeaderCtrl`物件。|
|[斬首::建立拖動影像](#createdragimage)|在標題控制項中創建項影像的透明版本。|
|[斬首::創建Ex](#createex)|使用指定的 Windows 擴充樣式創建標頭控制項並將`CListCtrl`其附加到 物件。|
|[CHeaderctrl::Delete專案](#deleteitem)|從標頭控制項中刪除項。|
|[斬首::D原始專案](#drawitem)|繪製標頭控件的指定項。|
|[斬首::編輯過濾器](#editfilter)|開始編輯標頭控制件的指定篩選器。|
|[斬首::獲取比特圖保證金](#getbitmapmargin)|檢索標頭控件中位圖邊距的寬度。|
|[斬首::取得焦點專案](#getfocuseditem)|獲取具有焦點的當前標頭控制項中的項的標識碼。|
|[斬首::抓取影像清單](#getimagelist)|檢索用於繪製標頭控制項標頭項的圖像清單的句柄。|
|[斬首::取得專案](#getitem)|檢索有關標頭控件中項的資訊。|
|[斬首::獲取項目計數](#getitemcount)|檢索標頭控件中的項計數。|
|[斬首::獲取專案下拉](#getitemdropdownrect)|獲取標題控制項中指定下拉按鈕的邊界矩形資訊。|
|[斬首::取得專案重新完成](#getitemrect)|檢索標頭控件中給定項的邊界矩形。|
|[斬首::獲取訂單陣列](#getorderarray)|檢索標頭控件中項的從左到右的順序。|
|[斬首::獲取溢出](#getoverflowrect)|獲取當前標頭控制件的溢出按鈕的邊界矩形。|
|[斬首::HitTest](#hittest)|確定指定點上的位置(如果有)標頭項。|
|[斬首::插入項目](#insertitem)|將新專案插入到標頭控制項中。|
|[斬首::佈局](#layout)|檢索給定矩形內標頭控制的大小和位置。|
|[斬首::訂單索引](#ordertoindex)|根據物料在標頭控件中的順序檢索物料的索引值。|
|[斬首::設定點陣圖頁距](#setbitmapmargin)|設置標題控制項中點陣圖邊距的寬度。|
|[斬首::設定篩選器更改逾時](#setfilterchangetimeout)|設置篩選器屬性中發生更改的時間與`HDN_FILTERCHANGE`通知的過帳之間的超時間隔。|
|[斬首::設定焦點專案](#setfocuseditem)|將焦點設定在當前標頭控制項中的指定標頭項。|
|[斬首::SetHotDivider](#sethotdivider)|更改標題項之間的分隔符以指示標題項的手動拖放。|
|[斬首::設定影像清單](#setimagelist)|將圖像清單分配給標頭控制項。|
|[斬首::設定項目](#setitem)|在標頭控制項中設置指定項的屬性。|
|[斬首::設定順序陣列](#setorderarray)|設置標頭控件中項的從左至右的順序。|

## <a name="remarks"></a>備註

標題控制項是通常位於一組文本或數位列上方的視窗。 它包含每列的標題,可以分為部分。 用戶可以拖動分隔零件的分隔符以設置每列的寬度。 有關標頭控制件的圖示,請參考[標題控制件](/windows/win32/Controls/header-controls)。

此控制項(因此類別`CHeaderCtrl`)僅適用於在 Windows 95/98 和 Windows NT 版本 3.51 及更高版本下運行的程式。

為 Windows 95/IE4.0 常見控制項添加的功能包括:

- 標題項自定義排序。

- 標題項拖放,用於重新排序標頭項。 創建`CHeaderCtrl`物件時使用HDS_DRAGDROP樣式。

- 標題列文字在列調整大小期間不斷查看。 創建`CHeaderCtrl`物件時使用HDS_FULLDRAG樣式。

- 頭熱跟蹤,當指標懸停在標題上時,它突出顯示標題項。 創建`CHeaderCtrl`物件時使用HDS_HOTTRACK樣式。

- 圖像清單支援。 標題項可以包含存儲在`CImageList`物件或文本中的圖像。

有關`CHeaderCtrl`使用的詳細資訊,請參閱[控制項](../../mfc/controls-mfc.md)與[CHeaderCtrl](../../mfc/using-cheaderctrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CHeaderCtrl`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

## <a name="cheaderctrlcheaderctrl"></a><a name="cheaderctrl"></a>斬首::斬首

建構 `CHeaderCtrl` 物件。

```
CHeaderCtrl();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_1.cpp)]

## <a name="cheaderctrlclearallfilters"></a><a name="clearallfilters"></a>斬首::清除所有篩選器

清除標頭控制件的所有篩選器。

```
BOOL ClearAllFilters();
```

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法實現 Win32 消息[HDM_CLEARFILTER](/windows/win32/Controls/hdm-clearfilter)的行為,列值為 -1,如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_2.cpp)]

## <a name="cheaderctrlclearfilter"></a><a name="clearfilter"></a>斬首::清除過濾器

清除標頭控制的篩選器。

```
BOOL ClearFilter(int nColumn);
```

### <a name="parameters"></a>參數

*nColumn*<br/>
列值,指示要清除的篩選器。

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法實現 Win32 消息[HDM_CLEARFILTER](/windows/win32/Controls/hdm-clearfilter)的行為,如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_3.cpp)]

## <a name="cheaderctrlcreate"></a><a name="create"></a>斬首::建立

創建標頭控制項並將其附加到`CHeaderCtrl`物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定標頭控制件的樣式。 有關標頭控制項樣式的說明,請參閱 Windows SDK 中的[標頭控制式樣式](/windows/win32/Controls/header-control-styles)。

*矩形*<br/>
指定標頭控制項大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](/previous-versions/dd162897\(v=vs.85\))結構。

*pparentwnd*<br/>
指定標頭控制的父視窗,通常為`CDialog`。 它不得為 NULL。

*nID*<br/>
指定標頭控制項的識別碼。

### <a name="return-value"></a>傳回值

初始化成功時非零;否則為零。

### <a name="remarks"></a>備註

分兩步`CHeaderCtrl`構造物件。 首先,調用構造函數,然後調用`Create`,這將創建標頭控件並將其附加`CHeaderCtrl`到 物件。

除了標頭控制樣式外,還可以使用以下通用控制樣式來確定標頭控制項的位置和調整本身的大小(有關詳細資訊,請參閱[通用控制樣式](/windows/win32/Controls/common-control-styles)):

- CCS_BOTTOM 使控制項將自己定位在父視窗工作區的底部,並將寬度設置為與父視窗的寬度相同。

- CCS_NODIVIDER 防止在控制式頂部繪製兩畫素高光。

- CCS_NOMOVEY 使控制項在水準(而不是垂直)上調整控制項的大小並移動自身,以回應WM_SIZE消息。 如果使用CCS_NORESIZE樣式,則此樣式不適用。 默認情況下,標頭控件具有此樣式。

- CCS_NOPARENTALIGN防止控制式自動移動到父視窗的頂部或底部。 相反,控制程式將其位置保留在父視窗中,儘管父視窗的大小發生了變化。 如果還使用CCS_TOP或CCS_BOTTOM樣式,則高度將調整為預設值,但位置和寬度保持不變。

- CCS_NORESIZE 防止控制項在設定其初始大小或新大小時使用預設寬度和高度。 相反,控制項使用創建或調整大小請求中指定的寬度和高度。

- CCS_TOP 使控制項將自己定位在父視窗工作區的頂部,並將寬度設置為與父視窗的寬度相同。

您還可以將以下視窗樣式應用於標頭控制項(有關詳細資訊,請參閱[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)):

- WS_CHILD 創建子視窗。 不能與WS_POPUP樣式一起使用。

- WS_VISIBLE 創建最初可見的視窗。

- WS_DISABLED 創建最初禁用的視窗。

- WS_GROUP 指定一組控件的第一個控制項,用戶可以在其中使用箭頭鍵從一個控制項移動到下一個控制項。 在第一個控制項之後使用WS_GROUP樣式定義的所有控制項都屬於同一組。 具有WS_GROUP樣式的下一個控制項結束樣式組並啟動下一個組(即,一個組結束下一個組開始的位置)。

- WS_TABSTOP 指定使用者可以使用 TAB 鍵移動的任意數量的控制項之一。 TAB 鍵將使用者移動到WS_TABSTOP樣式指定的下一個控制項。

如果要將延伸視窗樣式與控制項一起使用,請呼叫[CreateEx](#createex)`Create`而不是 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_4.cpp)]

## <a name="cheaderctrlcreateex"></a><a name="createex"></a>斬首::創建Ex

創建控制項(子視窗)並將其與`CHeaderCtrl`物件關聯。

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
指定要創建的控制項的擴充樣式。 有關擴展 Windows 樣式的清單,請參閱 Windows SDK 中[創建 WindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*參數。

*dwStyle*<br/>
標頭控件的樣式。 有關標頭控制項樣式的說明,請參閱 Windows SDK 中的[標頭控制式樣式](/windows/win32/Controls/header-control-styles)。 有關其他樣式的清單,請參閱[建立](#create)。

*矩形*<br/>
對[RECT](/previous-versions/dd162897\(v=vs.85\))結構的引用,描述要創建的視窗的大小和位置,在*pParentWnd*的用戶端座標中。

*pparentwnd*<br/>
指向控件的父視窗的指標。

*nID*<br/>
控制項的子視窗 ID。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

使用`CreateEx``Create`而不是應用擴展的 Windows 樣式,由 Windows 擴充樣式前言**WS_EX_** 指定。

## <a name="cheaderctrlcreatedragimage"></a><a name="createdragimage"></a>斬首::建立拖動影像

在標題控制項中創建項影像的透明版本。

```
CImageList* CreateDragImage(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
標頭控件中項的零基索引。 分配給此項的圖像是透明圖像的基礎。

### <a name="return-value"></a>傳回值

如果成功,指向[CImageList](../../mfc/reference/cimagelist-class.md)物件的指標;否則 NULL。 返回的清單僅包含一個圖像。

### <a name="remarks"></a>備註

此成員函數實現 win32 消息[HDM_CREATEDRAGIMAGE](/windows/win32/Controls/hdm-createdragimage)的行為,如Windows SDK中所述。 它用於支持標題項的拖放。

返回`CImageList`的指標指向的對像是臨時物件,並在下次空閒時處理中被刪除。

## <a name="cheaderctrldeleteitem"></a><a name="deleteitem"></a>CHeaderctrl::Delete專案

從標頭控制項中刪除項。

```
BOOL DeleteItem(int nPos);
```

### <a name="parameters"></a>參數

*nPos*<br/>
指定要刪除的項的零基索引。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#5](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_5.cpp)]

## <a name="cheaderctrldrawitem"></a><a name="drawitem"></a>斬首::D原始專案

當所有者繪製標頭控件的可視方面發生更改時,由框架調用。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>參數

*lpDraw 專案已結*<br/>
指向描述要繪製的項的[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)結構的指標。

### <a name="remarks"></a>備註

`DRAWITEMSTRUCT`結構`itemAction`的成員定義要執行的繪圖操作。

默認情況下,此成員函數不執行任何操作。 重寫此成員函數以擁有擁有者繪製物件的繪圖`CHeaderCtrl`。

應用程式應還原在此成員函數終止之前為*lpDrawItemStruct*中提供的顯示上下文選擇的所有圖形設備介面 (GDI) 物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_6.cpp)]

## <a name="cheaderctrleditfilter"></a><a name="editfilter"></a>斬首::編輯過濾器

開始編輯標頭控制件的指定篩選器。

```
BOOL EditFilter(
    int nColumn,
    BOOL bDiscardChanges);
```

### <a name="parameters"></a>參數

*nColumn*<br/>
要編輯的欄。

*b 放棄變更*<br/>
指定在發送[HDM_EDITFILTER](/windows/win32/Controls/hdm-editfilter)訊息時使用者正在編輯篩選器時如何處理使用者的編輯更改的值。

指定 TRUE 以放棄使用者所做的更改,或指定 FALSE 以接受使用者所做的更改。

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法實現 win32 消息[HDM_EDITFILTER](/windows/win32/Controls/hdm-editfilter)的行為,如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#7](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_7.cpp)]

## <a name="cheaderctrlgetbitmapmargin"></a><a name="getbitmapmargin"></a>斬首::獲取比特圖保證金

檢索標頭控件中位圖邊距的寬度。

```
int GetBitmapMargin() const;
```

### <a name="return-value"></a>傳回值

位圖邊距的寬度(以像素為單位)。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[HDM_GETBITMAPMARGIN](/windows/win32/Controls/hdm-getbitmapmargin)的行為,如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#8](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_8.cpp)]

## <a name="cheaderctrlgetfocuseditem"></a><a name="getfocuseditem"></a>斬首::取得焦點專案

獲取當前標頭控件中具有焦點的項的索引。

```
int GetFocusedItem() const;
```

### <a name="return-value"></a>傳回值

具有焦點的標頭項的零基索引。

### <a name="remarks"></a>備註

此方法發送[HDM_GETFOCUSEDITEM](/windows/win32/Controls/hdm-getfocuseditem)消息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

以下代碼範例定義用於存取目前的標頭控制`m_headerCtrl`的元件的變數 。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>範例

以下代碼示例演示`SetFocusedItem``GetFocusedItem`和 方法。 在代碼的早期版本中,我們創建了一個包含五列的標頭控件。 但是,您可以拖動列分隔符,以便該列不可見。 以下示例將設置,然後將最後一個列標頭確認為焦點項。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

## <a name="cheaderctrlgetimagelist"></a><a name="getimagelist"></a>斬首::抓取影像清單

檢索用於繪製標頭控制項標頭項的圖像清單的句柄。

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>傳回值

指向[CImageList](../../mfc/reference/cimagelist-class.md)物件的指標。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[HDM_GETIMAGELIST](/windows/win32/Controls/hdm-getimagelist)的行為,如 Windows SDK 中所述。 返回`CImageList`的指標指向的對像是臨時物件,並在下次空閒時處理中被刪除。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#9](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_11.cpp)]

## <a name="cheaderctrlgetitem"></a><a name="getitem"></a>斬首::取得專案

檢索有關標頭控件項的資訊。

```
BOOL GetItem(
    int nPos,
    HDITEM* pHeaderItem) const;
```

### <a name="parameters"></a>參數

*nPos*<br/>
指定要檢索的項的零基索引。

*pHeader 專案*<br/>
指向接收新專案的[HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw)結構的指標。 此結構與`InsertItem`和`SetItem`成員函數一起使用。 `mask`元素中設置的任何標誌都可確保在返回時正確填充相應元素中的值。 如果元素`mask`設置為零,則其他結構元素中的值毫無意義。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#10](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_12.cpp)]

## <a name="cheaderctrlgetitemcount"></a><a name="getitemcount"></a>斬首::獲取項目計數

檢索標頭控件中的項計數。

```
int GetItemCount() const;
```

### <a name="return-value"></a>傳回值

標頭控制項數(如果成功);否則 - 1。

### <a name="example"></a>範例

  請參閱[CHeaderCtrl::DeleteItem](#deleteitem)) 的範例。

## <a name="cheaderctrlgetitemdropdownrect"></a><a name="getitemdropdownrect"></a>斬首::獲取專案下拉

獲取當前標頭控制項中頭項的下拉按鈕的邊界矩形。

```
BOOL GetItemDropDownRect(
    int iItem,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*iItem*|[在]其樣式為HDF_SPLITBUTTON的標頭項的從零為基礎的索引。 有關詳細資訊,請參閱`fmt`[HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw)結構的成員。|
|*lpRect*|[出]指向[RECT](/previous-versions/dd162897\(v=vs.85\))結構以接收邊界矩形資訊的指標。|

### <a name="return-value"></a>傳回值

如果此函數成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法發送[HDM_GETITEMDROPDOWNRECT](/windows/win32/Controls/hdm-getitemdropdownrect)消息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

以下代碼範例定義用於存取目前的標頭控制`m_headerCtrl`的元件的變數 。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>範例

以下代碼範例展示該方法`GetItemDropDownRect`。 在代碼的早期版本中,我們創建了一個包含五列的標頭控件。 以下代碼示例圍繞為標題下拉按鈕保留的第一列上的位置繪製一個 3D 矩形。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#2](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_13.cpp)]

## <a name="cheaderctrlgetitemrect"></a><a name="getitemrect"></a>斬首::取得專案重新完成

檢索標頭控件中給定項的邊界矩形。

```
BOOL GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
標頭控件項的零基索引。

*lpRect*<br/>
指向接收邊界矩形資訊的[RECT](/previous-versions/dd162897\(v=vs.85\))結構位址的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此方法實現 Win32 消息[HDM_GETITEMRECT](/windows/win32/Controls/hdm-getitemrect)的行為,如 Windows SDK 中所述。

## <a name="cheaderctrlgetorderarray"></a><a name="getorderarray"></a>斬首::獲取訂單陣列

檢索標頭控件中項的從左到右的順序。

```
BOOL GetOrderArray(
    LPINT piArray,
    int iCount);
```

### <a name="parameters"></a>參數

*皮拉裡*<br/>
指向緩衝區位址的指標,該緩衝區接收標頭控件中項的索引值,其顯示順序從左到右。

*i. Count*<br/>
標頭控制項數。 必須是非負數。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[HDM_GETORDERARRAY](/windows/win32/Controls/hdm-getorderarray)的行為,如 Windows SDK 中所述。 它用於支援標頭項排序。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#11](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_14.cpp)]

## <a name="cheaderctrlgetoverflowrect"></a><a name="getoverflowrect"></a>斬首::獲取溢出

獲取當前標頭控制件的溢出按鈕的邊界矩形。

```
BOOL GetOverflowRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*lpRect*|[出]指向接收邊界矩形資訊的[RECT](/previous-versions/dd162897\(v=vs.85\))結構的指標。|

### <a name="return-value"></a>傳回值

如果此函數成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

如果標題控制項包含的專案多於可以同時顯示的項,則控件可以顯示一個溢出按鈕,該按鈕滾動到不可見的專案。 標頭控件必須具有HDS_OVERFLOW和HDF_SPLITBUTTON樣式才能顯示溢出按鈕。 邊界矩形將溢出按鈕封閉起來,僅在顯示溢出按鈕時才存在。 有關詳細資訊,請參閱[標題控制項樣式](/windows/win32/Controls/header-control-styles)。

此方法發送[HDM_GETOVERFLOWRECT](/windows/win32/Controls/hdm-getoverflowrect)訊息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

以下代碼範例定義用於存取目前的標頭控制`m_headerCtrl`的元件的變數 。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>範例

以下代碼範例展示該方法`GetOverflowRect`。 在代碼的早期版本中,我們創建了一個包含五列的標頭控件。 但是,您可以拖動列分隔符,以便該列不可見。 如果某些列不可見,則標題控制項將繪製溢出按鈕。 以下代碼示例圍繞溢出按鈕的位置繪製一個 3D 矩形。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#3](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_15.cpp)]

## <a name="cheaderctrlhittest"></a><a name="hittest"></a>斬首::HitTest

確定指定點上的位置(如果有)標頭項。

```
int HitTest(LPHDHITTESTINFO* phdhti);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*phdhti*|[進出]指向[HDHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-hdhittestinfo)結構的指標,該結構指定要測試的點並接收測試結果。|

### <a name="return-value"></a>傳回值

標題項的零索引(如果有)位於指定位置;否則,-1。

### <a name="remarks"></a>備註

此方法發送[HDM_HITTEST](/windows/win32/Controls/hdm-hittest)消息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

以下代碼範例定義用於存取目前的標頭控制`m_headerCtrl`的元件的變數 。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>範例

以下代碼範例展示該方法`HitTest`。 在本代碼示例的早期版本中,我們創建了一個包含五列的標頭控制項。 但是,您可以拖動列分隔符,以便該列不可見。 此示例報告列的索引(如果該列為可見)和 -1(如果列不可見)。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#1](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_16.cpp)]

## <a name="cheaderctrlinsertitem"></a><a name="insertitem"></a>斬首::插入項目

將新項目插入指定索引的標頭控制項。

```
int InsertItem(
    int nPos,
    HDITEM* phdi);
```

### <a name="parameters"></a>參數

*nPos*<br/>
要插入之項目之以零起始的索引。 如果值為零,則項將插入到標頭控件的開頭。 如果該值大於最大值,則項將插入到標頭控件的末尾。

*菲迪*<br/>
指向[HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw)結構的指標,該結構包含有關要插入的項的資訊。

### <a name="return-value"></a>傳回值

新專案的索引(如果成功);否則 - 1。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#12](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_17.cpp)]

## <a name="cheaderctrllayout"></a><a name="layout"></a>斬首::佈局

檢索給定矩形內標頭控制的大小和位置。

```
BOOL Layout(HDLAYOUT* pHeaderLayout);
```

### <a name="parameters"></a>參數

*pHeader 佈局*<br/>
指向[HDLAYOUT](/windows/win32/api/commctrl/ns-commctrl-hdlayout)結構的指標,其中包含用於設置標頭控件的大小和位置的資訊。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此函數用於確定要佔用給定矩形的新標頭控件的適當維度。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#13](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_18.cpp)]

## <a name="cheaderctrlordertoindex"></a><a name="ordertoindex"></a>斬首::訂單索引

根據物料在標頭控件中的順序檢索物料的索引值。

```
int OrderToIndex(int nOrder) const;
```

### <a name="parameters"></a>參數

*N訂單*<br/>
項從左至右顯示在標頭控制件中的零基順序。

### <a name="return-value"></a>傳回值

項的索引,基於其在標頭控件中的順序。 索引從左到右計數,從 0 開始。

### <a name="remarks"></a>備註

此成員函數實現 Win32 宏[HDM_ORDERTOINDEX](/windows/win32/controls/hdm-ordertoindex)的行為,如 Windows SDK 中所述。 它用於支援標頭項排序。

## <a name="cheaderctrlsetbitmapmargin"></a><a name="setbitmapmargin"></a>斬首::設定點陣圖頁距

設置標題控制項中點陣圖邊距的寬度。

```
int SetBitmapMargin(int nWidth);
```

### <a name="parameters"></a>參數

*n 寬度*<br/>
在現有標頭控制項中圍繞位圖的邊距的寬度(以圖元為單位指定)。

### <a name="return-value"></a>傳回值

位圖邊距的寬度(以像素為單位)。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[HDM_SETBITMAPMARGIN](/windows/win32/Controls/hdm-setbitmapmargin)的行為,如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#14](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_19.cpp)]

## <a name="cheaderctrlsetfilterchangetimeout"></a><a name="setfilterchangetimeout"></a>斬首::設定篩選器更改逾時

設置篩選器屬性中發生更改的時間與[發佈HDN_FILTERCHANGE](/windows/win32/Controls/hdn-filterchange)通知之間的超時間隔。

```
int SetFilterChangeTimeout(DWORD dwTimeOut);
```

### <a name="parameters"></a>參數

*dwTimeOut*<br/>
超時值,以毫秒為單位。

### <a name="return-value"></a>傳回值

要修改的篩選器控制件的索引。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[HDM_SETFILTERCHANGETIMEOUT](/windows/win32/Controls/hdm-setfilterchangetimeout)的行為,如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#15](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_20.cpp)]

## <a name="cheaderctrlsetfocuseditem"></a><a name="setfocuseditem"></a>斬首::設定焦點專案

將焦點設定在當前標頭控制項中的指定標頭項。

```
BOOL SetFocusedItem(int iItem);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*iItem*|[在]標頭項的零索引。|

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法發送[HDM_SETFOCUSEDITEM](/windows/win32/Controls/hdm-setfocuseditem)消息,這在Windows SDK中介紹。

### <a name="example"></a>範例

以下代碼範例定義用於存取目前的標頭控制`m_headerCtrl`的元件的變數 。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#6](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_9.h)]

### <a name="example"></a>範例

以下代碼示例演示`SetFocusedItem``GetFocusedItem`和 方法。 在代碼的早期版本中,我們創建了一個包含五列的標頭控件。 但是,您可以拖動列分隔符,以便該列不可見。 以下示例將設置,然後將最後一個列標頭確認為焦點項。

[!code-cpp[NVC_MFC_CHeaderCtrl_s4#4](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_10.cpp)]

## <a name="cheaderctrlsethotdivider"></a><a name="sethotdivider"></a>斬首::SetHotDivider

更改標題項之間的分隔符以指示標題項的手動拖放。

```
int SetHotDivider(CPoint pt);
int SetHotDivider(int nIndex);
```

### <a name="parameters"></a>參數

*pt*<br/>
指標的位置。 頭控件根據指標的位置突出顯示相應的分隔線。

*nIndex*<br/>
突出顯示的分隔符的索引。

### <a name="return-value"></a>傳回值

突出顯示的分隔符的索引。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[的行為HDM_SETHOTDIVIDER,](/windows/win32/Controls/hdm-sethotdivider)如 Windows SDK 中所述。 它用於支持標題項的拖放。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CHeaderCtrl#16](../../mfc/reference/codesnippet/cpp/cheaderctrl-class_21.cpp)]

## <a name="cheaderctrlsetimagelist"></a><a name="setimagelist"></a>斬首::設定影像清單

將圖像清單分配給標頭控制項。

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>參數

*pImageList*<br/>
指向包含要分配給`CImageList`標頭控制件的影像清單的物件的指標。

### <a name="return-value"></a>傳回值

指向以前分配給標頭控制件的[CImageList](../../mfc/reference/cimagelist-class.md)物件的指標。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[HDM_SETIMAGELIST](/windows/win32/Controls/hdm-setimagelist)的行為,如 Windows SDK 中所述。 返回`CImageList`的指標指向的對像是臨時物件,並在下次空閒時處理中被刪除。

### <a name="example"></a>範例

  請參考[CHeaderCtrl 的範例::抓取影像清單](#getimagelist)。

## <a name="cheaderctrlsetitem"></a><a name="setitem"></a>斬首::設定項目

在標頭控制項中設置指定項的屬性。

```
BOOL SetItem(
    int nPos,
    HDITEM* pHeaderItem);
```

### <a name="parameters"></a>參數

*nPos*<br/>
要操作的項的零基索引。

*pHeader 專案*<br/>
指向包含新專案資訊的[HDITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw)結構的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

  請參考[CHeaderCtrl 的範例::抓取項目](#getitem)。

## <a name="cheaderctrlsetorderarray"></a><a name="setorderarray"></a>斬首::設定順序陣列

設置標頭控件中項的從左至右的順序。

```
BOOL SetOrderArray(
    int iCount,
    LPINT piArray);
```

### <a name="parameters"></a>參數

*i. Count*<br/>
標頭控制項數。

*皮拉裡*<br/>
指向緩衝區位址的指標,該緩衝區接收標頭控件中項的索引值,其顯示順序從左到右。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函數實現 Win32 宏[HDM_SETORDERARRAY](/windows/win32/Controls/hdm-setorderarray)的行為,如 Windows SDK 中所述。 它用於支援標頭項排序。

### <a name="example"></a>範例

  請參考[CHeaderCtrl 的範例:取得Orderarray](#getorderarray)。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CTabCtrl 類別](../../mfc/reference/ctabctrl-class.md)<br/>
[CListCtrl 類別](../../mfc/reference/clistctrl-class.md)<br/>
[CImageList 類別](../../mfc/reference/cimagelist-class.md)
