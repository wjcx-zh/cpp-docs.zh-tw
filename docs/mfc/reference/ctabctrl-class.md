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
ms.openlocfilehash: 7d4a478b560be686e4da6f6dea623d6058626562
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365958"
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
|[CtCtrl::CTabCtrl](#ctabctrl)|建構 `CTabCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CtCtrl::調整](#adjustrect)|計算給定視窗矩形的制表符控制項的顯示區域,或計算對應於給定顯示區域的視窗矩形。|
|[CTabCtrl::建立](#create)|創建選項卡控制項並將其附加到`CTabCtrl`物件的實例。|
|[CTabCtrl::創建Ex](#createex)|使用指定的 Windows 擴充樣式創建選項卡控制項,並將`CTabCtrl`其附加到 物件的實例。|
|[CTabCtrl::DeleteAll專案](#deleteallitems)|從選項卡控制項中刪除所有項。|
|[CTabCtrl::Delete專案](#deleteitem)|從選項卡控制項中刪除項。|
|[CTabCtrl::Deselect全部](#deselectall)|重置選項卡控制項中的項目,清除任何按下的專案。|
|[CtCtrl::D原始專案](#drawitem)|繪製選項卡控制項指定項。|
|[CtCtrl:取得CurFocus](#getcurfocus)|檢索具有選項卡控件當前焦點的選項卡。|
|[CtCtrl::取得CurSel](#getcursel)|確定選項卡控制項中當前選擇的選項卡。|
|[CtCtrl::取得式延伸樣式](#getextendedstyle)|檢索當前用於選項卡控制項的擴充樣式。|
|[CTabCtrl:抓取影像清單](#getimagelist)|檢索與選項卡控件關聯的圖像清單。|
|[CTabCtrl:取得項目](#getitem)|檢索有關選項卡控件中選項卡的資訊。|
|[CTabCtrl::取得項目計數](#getitemcount)|檢索選項卡控件中的選項卡數。|
|[CTabCtrl::取得專案重新完成](#getitemrect)|檢索選項卡控制項中選項卡的邊界矩形。|
|[CTabCtrl::取得項目狀態](#getitemstate)|檢索指示的選項卡控制項的狀態。|
|[CtCtrl::獲取羅計數](#getrowcount)|檢索選項卡控件中當前數量的選項卡數。|
|[CTabCtrl:抓取工具提示](#gettooltips)|檢索與選項卡控件關聯的工具尖端控制項的句柄。|
|[CTabCtrl::亮點專案](#highlightitem)|設置選項卡項的突出顯示狀態。|
|[CtCtrl:hitTest](#hittest)|確定哪個選項卡(如果有)位於指定的螢幕位置。|
|[CTabCtrl::插入專案](#insertitem)|在選項卡控制項中插入新選項卡。|
|[CTabCtrl::刪除影像](#removeimage)|從選項卡控制件的圖像清單中刪除圖像。|
|[CtCtrl::設定CurFocus](#setcurfocus)|將焦點設定到選項卡控制項中的指定選項卡。|
|[CtCtrl::SetCurSel](#setcursel)|在選項卡控制項中選擇選項卡。|
|[CtCtrl::設定式延伸樣式](#setextendedstyle)|設置選項卡控制項的擴充樣式。|
|[CTabCtrl::設定影像清單](#setimagelist)|將影像清單分配給選項卡控制項。|
|[CTabCtrl::設定項目](#setitem)|設置選項卡的部分或全部屬性。|
|[CTabCtrl::設定項目額外](#setitemextra)|設置選項卡控制項中為應用程式定義的數據保留的每個選項卡的位元組數。|
|[CTabCtrl::設定項目大小](#setitemsize)|設置項目的寬度和高度。|
|[CTabCtrl::設定項目狀態](#setitemstate)|設置指示的選項卡控制項的狀態。|
|[CTabCtrl::設定明點寬度](#setmintabwidth)|設置選項卡控制項中專案的最小寬度。|
|[CTabCtrl::設定](#setpadding)|設置選項卡控制項中每個選項卡圖示和標籤周圍的空間量(填充)。|
|[CTabCtrl::設定工具提示](#settooltips)|將工具提示控制項分配給選項卡控制項。|

## <a name="remarks"></a>備註

選項卡控制件「類似於筆記本中的分隔符或檔櫃中的標籤。 藉由使用索引標籤控制項，應用程式可以定義視窗或對話方塊中同一個區域的多個頁面。 每個頁面由一組資訊或一組控件組成,當用戶選擇相應的選項卡時,應用程式會顯示這些資訊或控件組。特殊類型的選項卡控件顯示看起來像按鈕的選項卡。 按下按鈕應立即執行命令,而不是顯示頁面。

此控制項(因此該`CTabCtrl`類別)僅適用於在 Windows 95/98 和 Windows NT 版本 3.51 及更高版本下運行的程式。

有關`CTabCtrl`使用的詳細資訊,請參閱[控制項](../../mfc/controls-mfc.md)[與使用 CTabCtrl](../../mfc/using-ctabctrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CTabCtrl`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

## <a name="ctabctrladjustrect"></a><a name="adjustrect"></a>CtCtrl::調整

計算給定視窗矩形的制表符控制項的顯示區域,或計算對應於給定顯示區域的視窗矩形。

```
void AdjustRect(BOOL bLarger,   LPRECT lpRect);
```

### <a name="parameters"></a>參數

*b 更大*<br/>
指示要執行的操作。 如果此參數為*TRUE,lpRect*指定顯示矩形並接收相應的視窗矩形。 如果此參數為*FALSE,lpRect*指定一個視窗矩形並接收相應的顯示矩形。

*lpRect*<br/>
指向[RECT](/previous-versions/dd162897\(v=vs.85\))結構的指標,該結構指定給定的矩形並接收計算的矩形。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTabCtrl#1](../../mfc/reference/codesnippet/cpp/ctabctrl-class_1.cpp)]

## <a name="ctabctrlcreate"></a><a name="create"></a>CTabCtrl::建立

創建選項卡控制項並將其附加到`CTabCtrl`物件的實例。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定選項卡控制項樣式。 應用 Windows SDK 中描述的[選項卡控制項樣式](/windows/win32/Controls/tab-control-styles)的任意組合。 有關也可以應用於控制項的視窗樣式的清單,請參閱**備註**。

*矩形*<br/>
指定選項卡控制項大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](/previous-versions/dd162897\(v=vs.85\))結構。

*pparentwnd*<br/>
指定選項卡控制的父視窗,通常為`CDialog`。 它不得為 NULL。

*nID*<br/>
指定選項卡控制項的識別碼。

### <a name="return-value"></a>傳回值

如果物件的初始化成功,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

分兩步`CTabCtrl`構造物件。 首先調用建構函數,然後調用`Create`,這將創建選項卡控件並將其附加`CTabCtrl`到 物件。

除了選項卡控制樣式之外,還可以將以下視窗樣式應用於選項卡控制項:

- WS_CHILD創建表示選項卡控制項的子視窗。 不能與WS_POPUP樣式一起使用。

- WS_VISIBLE 創建最初可見的選項卡控制項。

- WS_DISABLED 創建最初禁用的視窗。

- WS_GROUP 指定一組控件的第一個控制項,用戶可以在其中使用箭頭鍵從一個控制項移動到下一個控制項。 在第一個控制項之後使用WS_GROUP樣式定義的所有控制項都屬於同一組。 具有WS_GROUP樣式的下一個控制項結束樣式組並啟動下一個組(即,一個組結束下一個組開始的位置)。

- WS_TABSTOP 指定使用者可以使用 TAB 鍵移動的任意數量的控制項之一。 TAB 鍵將使用者移動到WS_TABSTOP樣式指定的下一個控制項。

要建立式建立式選項卡控制項,請呼叫[CTabCtrl::createEx](#createex)而不是`Create`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTabCtrl#2](../../mfc/reference/codesnippet/cpp/ctabctrl-class_2.cpp)]

## <a name="ctabctrlcreateex"></a><a name="createex"></a>CTabCtrl::創建Ex

創建控制項(子視窗),並將其與`CTabCtrl`物件關聯。

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
指定選項卡控制項樣式。 應用 Windows SDK 中描述的[選項卡控制項樣式](/windows/win32/Controls/tab-control-styles)的任意組合。 請參閱[「創建」](#create)中**註釋**中查看也可以應用於控制項的視窗樣式清單。

*矩形*<br/>
對[RECT](/previous-versions/dd162897\(v=vs.85\))結構的引用,描述要創建的視窗的大小和位置,在*pParentWnd*的用戶端座標中。

*pparentwnd*<br/>
指向控件的父視窗的指標。

*nID*<br/>
控制項的子視窗 ID。

### <a name="return-value"></a>傳回值

如果成功,則為非零,否則為 0。

### <a name="remarks"></a>備註

使用`CreateEx`而不是[「創建](#create)」來應用擴展的 Windows 樣式,該樣式由 Windows 擴充樣式前言**WS_EX_** 指定。

`CreateEx`使用*dwExStyle*指定的擴展 Windows 樣式創建控制項。 使用[Set 擴充樣式](#setextendedstyle)設定特定於控制項的擴充樣式。 例如,用於`CreateEx`將此類樣式設置為WS_EX_CONTEXTHELP,但用於`SetExtendedStyle`將此類樣式設置為TCS_EX_FLATSEPARATORS。 有關詳細資訊,請參閱 Windows SDK 中的[選項卡控制元件擴展樣式](/windows/win32/Controls/tab-control-extended-styles)中描述的樣式。

## <a name="ctabctrlctabctrl"></a><a name="ctabctrl"></a>CtCtrl::CTabCtrl

建構 `CTabCtrl` 物件。

```
CTabCtrl();
```

## <a name="ctabctrldeleteallitems"></a><a name="deleteallitems"></a>CTabCtrl::DeleteAll專案

從選項卡控制項中刪除所有項。

```
BOOL DeleteAllItems();
```

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

## <a name="ctabctrldeleteitem"></a><a name="deleteitem"></a>CTabCtrl::Delete專案

從選項卡控制項中刪除指定的項目。

```
BOOL DeleteItem(int nItem);
```

### <a name="parameters"></a>參數

*nItem*<br/>
要刪除的項的零基值。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTabCtrl#3](../../mfc/reference/codesnippet/cpp/ctabctrl-class_3.cpp)]

## <a name="ctabctrldeselectall"></a><a name="deselectall"></a>CTabCtrl::Deselect全部

重置選項卡控制項中的項目,清除任何按下的專案。

```
void DeselectAll(BOOL fExcludeFocus);
```

### <a name="parameters"></a>參數

*f排除焦點*<br/>
指定專案取消選擇範圍的標誌。 如果此參數設置為 FALSE,則將重置所有選項卡按鈕。 如果將其設定為 TRUE,則除當前選擇的專案外的所有選項卡項都將重置。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[TCM_DESELECTALL](/windows/win32/Controls/tcm-deselectall)的行為,如 Windows SDK 中所述。

## <a name="ctabctrldrawitem"></a><a name="drawitem"></a>CtCtrl::D原始專案

當所有者繪製選項卡控制件的可視方面發生更改時,由框架調用。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>參數

*lpDraw 專案已結*<br/>
指向描述要繪製的項的[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)結構的指標。

### <a name="remarks"></a>備註

`DRAWITEMSTRUCT`結構`itemAction`的成員定義要執行的繪圖操作。

默認情況下,此成員函數不執行任何操作。 重寫此成員函數以擁有擁有者繪製物件的繪圖`CTabCtrl`。

應用程式應還原在此成員函數終止之前為*lpDrawItemStruct*中提供的顯示上下文選擇的所有圖形設備介面 (GDI) 物件。

## <a name="ctabctrlgetcurfocus"></a><a name="getcurfocus"></a>CtCtrl:取得CurFocus

檢索具有當前焦點的選項卡的索引。

```
int GetCurFocus() const;
```

### <a name="return-value"></a>傳回值

具有當前焦點的選項卡的零基索引。

## <a name="ctabctrlgetcursel"></a><a name="getcursel"></a>CtCtrl::取得CurSel

檢索選項卡控件中當前選擇的選項卡。

```
int GetCurSel() const;
```

### <a name="return-value"></a>傳回值

如果成功,則所選選項卡的零索引;如果未選擇選項卡,則為 - 1。

## <a name="ctabctrlgetextendedstyle"></a><a name="getextendedstyle"></a>CtCtrl::取得式延伸樣式

檢索當前用於選項卡控制項的擴充樣式。

```
DWORD GetExtendedStyle();
```

### <a name="return-value"></a>傳回值

表示當前用於選項卡控件的擴展樣式。 此值是[選項卡控制式裝置擴充樣式](/windows/win32/Controls/tab-control-extended-styles)的組合,如 Windows SDK 中所述。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[TCM_GETEXTENDEDSTYLE](/windows/win32/Controls/tcm-getextendedstyle)的行為,如 Windows SDK 中所述。

## <a name="ctabctrlgetimagelist"></a><a name="getimagelist"></a>CTabCtrl:抓取影像清單

擷取與索引標籤控制項關聯的影像清單。

```
CImageList* GetImageList() const;
```

### <a name="return-value"></a>傳回值

如果成功，則為指向索引標籤控制項影像清單的指標，否則為 NULL。

## <a name="ctabctrlgetitem"></a><a name="getitem"></a>CTabCtrl:取得項目

檢索有關選項卡控件中選項卡的資訊。

```
BOOL GetItem(int nItem,   TCITEM* pTabCtrlItem) const;
```

### <a name="parameters"></a>參數

*nItem*<br/>
選項卡的零索引。

*pTabCtrl專案*<br/>
指向[TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw)結構的指標,用於指定要檢索的資訊。 還用於接收有關選項卡的資訊。此結構與`InsertItem`、`GetItem``SetItem`成員函數一起使用。

### <a name="return-value"></a>傳回值

如果成功,則返回 TRUE;否則。

### <a name="remarks"></a>備註

送出訊息時,`mask`成員指定要返回的屬性。 如果`mask`成員指定TCIF_TEXT值,`pszText`則成員必須包含接收項文本的緩衝區的位址`cchTextMax`, 並且成員必須指定緩衝區的大小。

- `mask`

   指定要檢索`TCITEM`或設置的結構成員的值。 此成員可以是零或以下值的組合:

  - TCIF_TEXT`pszText`該成員有效。

  - TCIF_IMAGE該`iImage`成員有效。

  - TCIF_PARAM`lParam`該成員有效。

  - TCIF_RTLREADING 在`pszText`希 伯來語或阿拉伯語系統上使用從右到左的閱讀順序顯示 的文本。

  - TCIF_STATE`dwState`該成員有效。

- `pszText`

   如果結構包含有關選項卡的資訊,則指向包含選項卡文本的 null 端接字串的指標。如果結構正在接收資訊,則此成員指定接收選項卡文本的緩衝區的位址。

- `cchTextMax`

   指向`pszText`的緩衝區的大小。 如果結構未接收資訊,則忽略此成員。

- `iImage`索引到選項卡控制項的影像清單中,如果選項卡沒有影像,則為 - 1。

- `lParam`

   與選項卡關聯的應用程式定義數據。如果每個選項卡的應用程式定義數據超過四個字節,則應用程式必須定義結構並使用它而不是`TCITEM`結構。 應用程式定義結構的第一個成員必須是[TCITEMHEADER](/windows/win32/api/commctrl/ns-commctrl-tcitemheaderw)結構。 結構`TCITEMHEADER`與結構相同`TCITEM`, 但沒有`lParam`成員。 結構大小和`TCITEMHEADER`結構大小之間的差異應等於每個選項卡的額外位元組數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTabCtrl#4](../../mfc/reference/codesnippet/cpp/ctabctrl-class_4.cpp)]

## <a name="ctabctrlgetitemcount"></a><a name="getitemcount"></a>CTabCtrl::取得項目計數

檢索選項卡控件中的選項卡數。

```
int GetItemCount() const;
```

### <a name="return-value"></a>傳回值

選項卡控制項中的項數。

### <a name="example"></a>範例

  請參閱[CPropertySheet 的範例:getTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)。

## <a name="ctabctrlgetitemrect"></a><a name="getitemrect"></a>CTabCtrl::取得專案重新完成

檢索選項卡控制項中指定選項卡的邊界矩形。

```
BOOL GetItemRect(int nItem,   LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

*nItem*<br/>
選項卡項的零索引。

*lpRect*<br/>
指向接收選項卡邊界矩形的[RECT](/previous-versions/dd162897\(v=vs.85\))結構的指標。這些座標使用視口的當前映射模式。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

  請參閱[CPropertySheet 的範例:getTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)。

## <a name="ctabctrlgetitemstate"></a><a name="getitemstate"></a>CTabCtrl::取得項目狀態

檢索*nItem*標識的選項卡控制項的狀態。

```
DWORD GetItemState(
    int nItem,
    DWORD dwMask) const;
```

### <a name="parameters"></a>參數

*nItem*<br/>
要檢索狀態資訊的項的零基索引號。

*dwMask*<br/>
蒙版指定要返回哪個項的狀態標誌。 有關值清單,請參閱[TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw)結構的掩碼成員,如 Windows SDK 中所述。

### <a name="return-value"></a>傳回值

對接收狀態資訊的 DWORD 值的引用。 可以是下列其中一個值：

|值|描述|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|選擇了選項卡控制項。|
|TCIS_HIGHLIGHTED|選項卡控制項將突出顯示,並使用當前高光顏色繪製選項卡和文本。 使用高光顏色時,這將是真正的插值,而不是抖除的顏色。|

### <a name="remarks"></a>備註

項的狀態由`dwState``TCITEM`結構的成員指定。

## <a name="ctabctrlgetrowcount"></a><a name="getrowcount"></a>CtCtrl::獲取羅計數

檢索選項卡控制項中的當前行數。

```
int GetRowCount() const;
```

### <a name="return-value"></a>傳回值

選項卡控制項中的選項卡行數。

### <a name="remarks"></a>備註

只有具有TCS_MULTILINE樣式的選項卡控制項才能具有多行選項卡。

## <a name="ctabctrlgettooltips"></a><a name="gettooltips"></a>CTabCtrl:抓取工具提示

檢索與選項卡控件關聯的工具尖端控制項的句柄。

```
CToolTipCtrl* GetToolTips() const;
```

### <a name="return-value"></a>傳回值

如果成功,則處理工具尖端控制;否則 NULL。

### <a name="remarks"></a>備註

如果選項卡控制項具有TCS_TOOLTIPS樣式,則建立工具提示控制項。 您還可以使用`SetToolTips`成員函數將工具提示控制項分配給選項卡控制項。

## <a name="ctabctrlhighlightitem"></a><a name="highlightitem"></a>CTabCtrl::亮點專案

設置選項卡項的突出顯示狀態。

```
BOOL HighlightItem(int idItem,   BOOL fHighlight = TRUE);
```

### <a name="parameters"></a>參數

*idItem*<br/>
選項卡控項項的零基索引。

*f 突顯*<br/>
指定要設置的高光狀態的值。 如果此值為 TRUE,則選項卡將突出顯示;如果此值為 TRUE,則選項卡將突出顯示。如果 FALSE,則選項卡設置為其默認狀態。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[TCM_HIGHLIGHTITEM](/windows/win32/Controls/tcm-highlightitem),如 Windows SDK 中所述。

## <a name="ctabctrlhittest"></a><a name="hittest"></a>CtCtrl:hitTest

確定哪個選項卡(如果有)位於指定的螢幕位置。

```
int HitTest(TCHITTESTINFO* pHitTestInfo) const;
```

### <a name="parameters"></a>參數

*pHitTestInfo*<br/>
指向[TCHITTESTINFO](/windows/win32/api/commctrl/ns-commctrl-tchittestinfo)結構的指標,如 Windows SDK 中所述,該結構指定要測試的螢幕位置。

### <a name="return-value"></a>傳回值

如果指定位置沒有選項卡,則返回選項卡的零索引或 - 1。

## <a name="ctabctrlinsertitem"></a><a name="insertitem"></a>CTabCtrl::插入專案

在現有選項卡控制項中插入新選項卡。

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
新選項卡的零索引。

*pTabCtrl專案*<br/>
指向指定選項卡屬性的[TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw)結構的指標。

*lpszItem*<br/>
包含選項卡文字的 null 終止字串的位址。

*n 影像*<br/>
要從影像清單中插入的圖像的零基索引。

*nMask*<br/>
指定要`TCITEM`設置的結構屬性。 可以是零或以下值的組合:

- TCIF_TEXT`pszText`該成員有效。

- TCIF_IMAGE該`iImage`成員有效。

- TCIF_PARAM *lParam*成員有效。

- TCIF_RTLREADING 在`pszText`希 伯來語或阿拉伯語系統上使用從右到左的閱讀順序顯示 的文本。

- TCIF_STATE *dwState*成員有效。

*lParam*<br/>
與選項卡關聯的應用程式定義數據。

*德沃州*<br/>
指定項狀態的值。 有關詳細資訊,請參閱 Windows SDK 中的[TCITEM。](/windows/win32/api/commctrl/ns-commctrl-tcitemw)

*dwStateMask*<br/>
指定要設置哪些狀態。 有關詳細資訊,請參閱 Windows SDK 中的[TCITEM。](/windows/win32/api/commctrl/ns-commctrl-tcitemw)

### <a name="return-value"></a>傳回值

如果成功,則新選項卡的零基索引;否則 - 1。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CTabCtrl#5](../../mfc/reference/codesnippet/cpp/ctabctrl-class_5.cpp)]

## <a name="ctabctrlremoveimage"></a><a name="removeimage"></a>CTabCtrl::刪除影像

從選項卡控制件的圖像清單中刪除指定的圖像。

```
void RemoveImage(int nImage);
```

### <a name="parameters"></a>參數

*n 影像*<br/>
要刪除的圖像的零索引。

### <a name="remarks"></a>備註

選項卡控制項更新每個選項卡的影像索引,以便每個選項卡與同一圖像保持關聯。

## <a name="ctabctrlsetcurfocus"></a><a name="setcurfocus"></a>CtCtrl::設定CurFocus

將焦點設定到選項卡控制項中的指定選項卡。

```
void SetCurFocus(int nItem);
```

### <a name="parameters"></a>參數

*nItem*<br/>
指定獲取焦點的選項卡的索引。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[的行為TCM_SETCURFOCUS,](/windows/win32/Controls/tcm-setcurfocus)如 Windows SDK 中所述。

## <a name="ctabctrlsetcursel"></a><a name="setcursel"></a>CtCtrl::SetCurSel

在選項卡控制項中選擇選項卡。

```
int SetCurSel(int nItem);
```

### <a name="parameters"></a>參數

*nItem*<br/>
要選擇的項的零基索引。

### <a name="return-value"></a>傳回值

以前選擇的選項卡的零索引(如果成功,否則為 - 1)。

### <a name="remarks"></a>備註

使用此功能選擇選項卡時,選項卡控制項不會發送TCN_SELCHANGING或TCN_SELCHANGE通知訊息。 當用戶按下或使用鍵盤更改選項卡時,將使用WM_NOTIFY發送這些通知。

## <a name="ctabctrlsetextendedstyle"></a><a name="setextendedstyle"></a>CtCtrl::設定式延伸樣式

設置選項卡控制項的擴充樣式。

```
DWORD SetExtendedStyle(DWORD dwNewStyle,   DWORD dwExMask = 0);
```

### <a name="parameters"></a>參數

*dwNewStyle*<br/>
指定選項卡控制項擴充樣式組合的值。

*dwExMask*<br/>
DWORD 值,指示*dwNewStyle*中的哪些樣式將受到影響。 只有*dwExMask*中的擴展樣式才會更改。 所有其他樣式將保持不變。 如果此參數為零,則*dwNewStyle*中的所有樣式都將受到影響。

### <a name="return-value"></a>傳回值

包含上一個[選項卡控制項擴充樣式](/windows/win32/Controls/tab-control-extended-styles)的 DWORD 值,如 Windows SDK 中所述。

### <a name="return-value"></a>傳回值

此成員函數實現 win32 消息[的行為TCM_SETEXTENDEDSTYLE](/windows/win32/Controls/tcm-setextendedstyle),如Windows SDK中所述。

## <a name="ctabctrlsetimagelist"></a><a name="setimagelist"></a>CTabCtrl::設定影像清單

將影像清單分配給選項卡控制項。

```
CImageList* SetImageList(CImageList* pImageList);
```

### <a name="parameters"></a>參數

*pImageList*<br/>
指向要分配給選項卡控制件的影像清單的指標。

### <a name="return-value"></a>傳回值

如果沒有以前的圖像清單,則返回指向上一個圖像清單或 NULL 的指標。

## <a name="ctabctrlsetitem"></a><a name="setitem"></a>CTabCtrl::設定項目

設置選項卡的部分或全部屬性。

```
BOOL SetItem(int nItem,   TCITEM* pTabCtrlItem);
```

### <a name="parameters"></a>參數

*nItem*<br/>
項的零索引。

*pTabCtrl專案*<br/>
指向包含新項屬性的[TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw)結構的指標。 成員`mask`指定要設置的屬性。 如果`mask`成員指定TCIF_TEXT值,`pszText`則該成員是 null 終止字串的`cchTextMax`位址, 並且該成員將被忽略。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

  請參閱[GetItem](#getitem)的範例。

## <a name="ctabctrlsetitemextra"></a><a name="setitemextra"></a>CTabCtrl::設定項目額外

設置選項卡控制項中為應用程式定義的數據保留的每個選項卡的位元組數。

```
BOOL SetItemExtra(int nBytes);
```

### <a name="parameters"></a>參數

*n 位元組*<br/>
要設置的額外位元組數。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[TCM_SETITEMEXTRA](/windows/win32/Controls/tcm-setitemextra)的行為,如 Windows SDK 中所述。

## <a name="ctabctrlsetitemsize"></a><a name="setitemsize"></a>CTabCtrl::設定項目大小

設定索引標籤控制項項目的寬度和高度。

```
CSize SetItemSize(CSize size);
```

### <a name="parameters"></a>參數

*大小*<br/>
索引標籤控制項項目的新寬度和高度 (以像素為單位)。

### <a name="return-value"></a>傳回值

傳回索引標籤控制項項目的舊寬度和高度。

## <a name="ctabctrlsetitemstate"></a><a name="setitemstate"></a>CTabCtrl::設定項目狀態

設置*nItem*標識的選項卡控制項項目的狀態。

```
BOOL SetItemState(
    int nItem,
    DWORD dwMask,
    DWORD dwState);
```

### <a name="parameters"></a>參數

*nItem*<br/>
要為其設置狀態資訊的項的零基索引編號。

*dwMask*<br/>
蒙版指定要設置哪個項的狀態標誌。 有關值清單,請參閱[TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw)結構的掩碼成員,如 Windows SDK 中所述。

*德沃州*<br/>
對包含狀態資訊的 DWORD 值的引用。 可以是下列其中一個值：

|值|描述|
|-----------|-----------------|
|TCIS_BUTTONPRESSED|選擇了選項卡控制項。|
|TCIS_HIGHLIGHTED|選項卡控制項將突出顯示,並使用當前高光顏色繪製選項卡和文本。 使用高光顏色時,這將是真正的插值,而不是抖除的顏色。|

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

## <a name="ctabctrlsetmintabwidth"></a><a name="setmintabwidth"></a>CTabCtrl::設定明點寬度

設置選項卡控制項中專案的最小寬度。

```
int SetMinTabWidth(int cx);
```

### <a name="parameters"></a>參數

*殘雪*<br/>
要為選項卡控件項設置的最小寬度。 如果此參數設置為 -1,則控制項將使用預設選項卡寬度。

### <a name="return-value"></a>傳回值

上一個最小選項卡寬度。

### <a name="return-value"></a>傳回值

此成員函數實現 Win32 消息[TCM_SETMINTABWIDTH](/windows/win32/Controls/tcm-setmintabwidth)的行為,如 Windows SDK 中所述。

## <a name="ctabctrlsetpadding"></a><a name="setpadding"></a>CTabCtrl::設定

設置選項卡控制項中每個選項卡圖示和標籤周圍的空間量(填充)。

```
void SetPadding(CSize size);
```

### <a name="parameters"></a>參數

*大小*<br/>
設置選項卡控制項中每個選項卡圖示和標籤周圍的空間量(填充)。

## <a name="ctabctrlsettooltips"></a><a name="settooltips"></a>CTabCtrl::設定工具提示

將工具提示控制項分配給選項卡控制項。

```
void SetToolTips(CToolTipCtrl* pWndTip);
```

### <a name="parameters"></a>參數

*pwndTip*<br/>
工具尖端控件的手柄。

### <a name="remarks"></a>備註

您可以透過呼叫 來取得與定位表元控制的工具提示控制件`GetToolTips`。

### <a name="example"></a>範例

  請參閱[CPropertySheet 的範例:getTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CHeaderCtrl 類別](../../mfc/reference/cheaderctrl-class.md)<br/>
[CListCtrl 類別](../../mfc/reference/clistctrl-class.md)
