---
title: CListBox 類別
description: MFC CListBox 類別及其成員函式的描述。
ms.date: 01/22/2020
f1_keywords:
- CListBox
- AFXWIN/CListBox
- AFXWIN/CListBox::CListBox
- AFXWIN/CListBox::AddString
- AFXWIN/CListBox::CharToItem
- AFXWIN/CListBox::CompareItem
- AFXWIN/CListBox::Create
- AFXWIN/CListBox::DeleteItem
- AFXWIN/CListBox::DeleteString
- AFXWIN/CListBox::Dir
- AFXWIN/CListBox::DrawItem
- AFXWIN/CListBox::FindString
- AFXWIN/CListBox::FindStringExact
- AFXWIN/CListBox::GetAnchorIndex
- AFXWIN/CListBox::GetCaretIndex
- AFXWIN/CListBox::GetCount
- AFXWIN/CListBox::GetCurSel
- AFXWIN/CListBox::GetHorizontalExtent
- AFXWIN/CListBox::GetItemData
- AFXWIN/CListBox::GetItemDataPtr
- AFXWIN/CListBox::GetItemHeight
- AFXWIN/CListBox::GetItemRect
- AFXWIN/CListBox::GetListBoxInfo
- AFXWIN/CListBox::GetLocale
- AFXWIN/CListBox::GetSel
- AFXWIN/CListBox::GetSelCount
- AFXWIN/CListBox::GetSelItems
- AFXWIN/CListBox::GetText
- AFXWIN/CListBox::GetTextLen
- AFXWIN/CListBox::GetTopIndex
- AFXWIN/CListBox::InitStorage
- AFXWIN/CListBox::InsertString
- AFXWIN/CListBox::ItemFromPoint
- AFXWIN/CListBox::MeasureItem
- AFXWIN/CListBox::ResetContent
- AFXWIN/CListBox::SelectString
- AFXWIN/CListBox::SelItemRange
- AFXWIN/CListBox::SetAnchorIndex
- AFXWIN/CListBox::SetCaretIndex
- AFXWIN/CListBox::SetColumnWidth
- AFXWIN/CListBox::SetCurSel
- AFXWIN/CListBox::SetHorizontalExtent
- AFXWIN/CListBox::SetItemData
- AFXWIN/CListBox::SetItemDataPtr
- AFXWIN/CListBox::SetItemHeight
- AFXWIN/CListBox::SetLocale
- AFXWIN/CListBox::SetSel
- AFXWIN/CListBox::SetTabStops
- AFXWIN/CListBox::SetTopIndex
- AFXWIN/CListBox::VKeyToItem
helpviewer_keywords:
- CListBox [MFC], CListBox
- CListBox [MFC], AddString
- CListBox [MFC], CharToItem
- CListBox [MFC], CompareItem
- CListBox [MFC], Create
- CListBox [MFC], DeleteItem
- CListBox [MFC], DeleteString
- CListBox [MFC], Dir
- CListBox [MFC], DrawItem
- CListBox [MFC], FindString
- CListBox [MFC], FindStringExact
- CListBox [MFC], GetAnchorIndex
- CListBox [MFC], GetCaretIndex
- CListBox [MFC], GetCount
- CListBox [MFC], GetCurSel
- CListBox [MFC], GetHorizontalExtent
- CListBox [MFC], GetItemData
- CListBox [MFC], GetItemDataPtr
- CListBox [MFC], GetItemHeight
- CListBox [MFC], GetItemRect
- CListBox [MFC], GetListBoxInfo
- CListBox [MFC], GetLocale
- CListBox [MFC], GetSel
- CListBox [MFC], GetSelCount
- CListBox [MFC], GetSelItems
- CListBox [MFC], GetText
- CListBox [MFC], GetTextLen
- CListBox [MFC], GetTopIndex
- CListBox [MFC], InitStorage
- CListBox [MFC], InsertString
- CListBox [MFC], ItemFromPoint
- CListBox [MFC], MeasureItem
- CListBox [MFC], ResetContent
- CListBox [MFC], SelectString
- CListBox [MFC], SelItemRange
- CListBox [MFC], SetAnchorIndex
- CListBox [MFC], SetCaretIndex
- CListBox [MFC], SetColumnWidth
- CListBox [MFC], SetCurSel
- CListBox [MFC], SetHorizontalExtent
- CListBox [MFC], SetItemData
- CListBox [MFC], SetItemDataPtr
- CListBox [MFC], SetItemHeight
- CListBox [MFC], SetLocale
- CListBox [MFC], SetSel
- CListBox [MFC], SetTabStops
- CListBox [MFC], SetTopIndex
- CListBox [MFC], VKeyToItem
ms.assetid: 7ba3c699-c286-4cd9-9066-532c41ec05d1
ms.openlocfilehash: 30f28db746856303e10709417ad7545376fd4812
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231802"
---
# <a name="clistbox-class"></a>CListBox 類別

提供 Windows 清單方塊的功能。

## <a name="syntax"></a>語法

```
class CListBox : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CListBox：： CListBox](#clistbox)|建構 `CListBox` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CListBox::AddString](#addstring)|將字串新增至清單方塊。|
|[CListBox：： CharToItem](#chartoitem)|覆寫以為沒有字串的主控描繪清單方塊提供自訂的 WM_CHAR 處理。|
|[CListBox：： CompareItem](#compareitem)|由架構呼叫，以判斷新專案在 [已排序的主控描繪] 清單方塊中的位置。|
|[CListBox：： Create](#create)|建立 Windows 清單方塊，並將其附加至 `CListBox` 物件。|
|[CListBox：:D eleteItem](#deleteitem)|當使用者從主控描繪清單方塊中刪除專案時，由架構呼叫。|
|[CListBox：:D eleteString](#deletestring)|刪除清單方塊中的字串。|
|[CListBox：:D ir](#dir)|將檔案名、磁片磁碟機或兩者都新增至清單方塊。|
|[CListBox：:D rawItem](#drawitem)|當主控描繪清單方塊的視覺外觀變更時，由架構呼叫。|
|[CListBox：： FindString](#findstring)|搜尋清單方塊中的字串。|
|[CListBox：： FindStringExact](#findstringexact)|尋找符合指定之字串的第一個清單方塊字串。|
|[CListBox：： GetAnchorIndex](#getanchorindex)|抓取清單方塊中目前錨點專案的以零為起始的索引。|
|[CListBox：： GetCaretIndex](#getcaretindex)|決定在多重選取清單方塊中具有焦點矩形之專案的索引。|
|[CListBox：： GetCount](#getcount)|傳回清單方塊中的字串數目。|
|[CListBox：： GetCurSel](#getcursel)|傳回清單方塊中目前選取之字串的以零為起始的索引。|
|[CListBox：： GetHorizontalExtent](#gethorizontalextent)|傳回清單方塊可水準滾動的寬度（以圖元為單位）。|
|[CListBox：： GetItemData](#getitemdata)|傳回與清單方塊專案相關聯的值。|
|[CListBox：： GetItemDataPtr](#getitemdataptr)|傳回清單方塊專案的指標。|
|[CListBox：： GetItemHeight](#getitemheight)|決定清單方塊中專案的高度。|
|[CListBox：： GetItemRect](#getitemrect)|傳回目前顯示之清單方塊專案的周框。|
|[CListBox：： GetListBoxInfo](#getlistboxinfo)|抓取每個資料行的專案數。|
|[CListBox：： GetLocale](#getlocale)|抓取清單方塊的地區設定識別碼。|
|[CListBox：： GetSel](#getsel)|傳回清單方塊專案的選取狀態。|
|[CListBox：： GetSelCount](#getselcount)|傳回在多重選取清單方塊中目前選取的字串數目。|
|[CListBox：： GetSelItems](#getselitems)|傳回清單方塊中目前選取之字串的索引。|
|[CListBox：： GetText](#gettext)|將清單方塊專案複製到緩衝區。|
|[CListBox：： GetTextLen](#gettextlen)|傳回清單方塊專案的長度（以位元組為單位）。|
|[CListBox：： GetTopIndex](#gettopindex)|傳回清單方塊中第一個可見字串的索引。|
|[CListBox：： InitStorage](#initstorage)|預先配置清單方塊專案和字串的記憶體區塊。|
|[CListBox::InsertString](#insertstring)|在清單方塊中的特定位置插入字串。|
|[CListBox：： ItemFromPoint](#itemfrompoint)|傳回最接近某個點的清單方塊專案的索引。|
|[CListBox：： MeasureItem](#measureitem)|建立主控描繪清單方塊以判斷清單方塊維度時，由架構呼叫。|
|[CListBox：： ResetContent](#resetcontent)|清除清單方塊中的所有專案。|
|[CListBox：： SelectString](#selectstring)|搜尋並選取單一挑選清單框中的字串。|
|[CListBox：： SelItemRange](#selitemrange)|選取或取消選取多重選取清單方塊中某個範圍的字串。|
|[CListBox：： SetAnchorIndex](#setanchorindex)|設定多重選取清單方塊中的錨點，以開始延伸選取範圍。|
|[CListBox：： SetCaretIndex](#setcaretindex)|將焦點矩形設定為多重選取清單方塊中指定索引處的專案。|
|[CListBox：： SetColumnWidth](#setcolumnwidth)|設定多欄清單方塊的資料行寬度。|
|[CListBox：： SetCurSel](#setcursel)|選取清單方塊字串。|
|[CListBox::SetHorizontalExtent](#sethorizontalextent)|設定可水準滾動清單方塊的寬度（以圖元為單位）。|
|[CListBox：： SetItemData](#setitemdata)|設定與清單方塊專案相關聯的值。|
|[CListBox：： SetItemDataPtr](#setitemdataptr)|設定清單方塊專案的指標。|
|[CListBox：： SetItemHeight](#setitemheight)|設定清單方塊中專案的高度。|
|[CListBox：： SetLocale](#setlocale)|設定清單方塊的地區設定識別碼。|
|[CListBox：： SetSel](#setsel)|在多重選取清單方塊中選取或取消選取清單方塊專案。|
|[CListBox：： SetTabStops](#settabstops)|設定清單方塊中的定位停駐點位置。|
|[CListBox：： SetTopIndex](#settopindex)|設定清單方塊中第一個可見字串的以零為基底的索引。|
|[CListBox：： VKeyToItem](#vkeytoitem)|覆寫以針對具有 LBS_WANTKEYBOARDINPUT 樣式設定的清單方塊提供自訂的 WM_KEYDOWN 處理。|

## <a name="remarks"></a>備註

清單方塊會顯示使用者可查看和選取的專案清單，例如檔案名。

在單一挑選清單框中，使用者只能選取一個專案。 在多重選取清單方塊中，可以選取某個範圍的專案。 當使用者選取專案時，系統會將其反白顯示，且清單方塊會將通知訊息傳送至父視窗。

您可以從對話方塊範本或直接在程式碼中建立清單方塊。 若要直接建立它，請建立 `CListBox` 物件，然後呼叫[create](#create)成員函式來建立 Windows 清單方塊控制項，並將它附加至 `CListBox` 物件。 若要在對話方塊範本中使用清單方塊，請在對話方塊類別中宣告清單方塊變數，然後 `DDX_Control` 在對話方塊類別的函式中使用，將 `DoDataExchange` 成員變數連接到控制項。 （當您將控制項變數新增至對話方塊類別時，就會自動為您完成此動作）。

在衍生自的類別中，結構可以是一個步驟的處理常式 `CListBox` 。 撰寫衍生類別的函式，並從函式 `Create` 內呼叫。

如果您想要處理清單方塊傳送到其父系的 Windows 通知訊息（通常是衍生自[CDialog](../../mfc/reference/cdialog-class.md)的類別），請將訊息對應專案和訊息處理常式成員函式新增至每個訊息的父類別。

每個訊息對應專案會採用下列格式：

`ON_Notification( id, memberFxn )`

其中 `id` 指定傳送通知之清單方塊控制項的子視窗識別碼，而且 `memberFxn` 是您已撰寫來處理通知之父成員函式的名稱。

父系的函數原型如下所示：

`afx_msg void memberFxn( );`

以下是可能的訊息對應專案清單，以及其會傳送至父系的案例描述：

- ON_LBN_DBLCLK 使用者按兩下清單方塊中的字串。 只有具有[LBS_NOTIFY](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式的清單方塊會傳送此通知訊息。

- ON_LBN_ERRSPACE 清單方塊無法配置足夠的記憶體來符合要求。

- ON_LBN_KILLFOCUS 清單方塊失去輸入焦點。

- ON_LBN_SELCANCEL 目前的清單方塊選取專案已取消。 只有當清單方塊具有 LBS_NOTIFY 樣式時，才會傳送此訊息。

- ON_LBN_SELCHANGE 清單方塊中的選取範圍已變更。 如果[CListBox：： SetCurSel](#setcursel)成員函式變更了選取範圍，則不會傳送此通知。 此通知僅適用于具有 LBS_NOTIFY 樣式的清單方塊。 每當使用者按下方向鍵時，就會傳送多個挑選清單框的 LBN_SELCHANGE 通知訊息，即使選取專案不會變更也是一樣。

- ON_LBN_SETFOCUS 清單方塊正在接收輸入焦點。

- ON_WM_CHARTOITEM 沒有任何字串的主控描繪清單方塊會收到 WM_CHAR 訊息。

- ON_WM_VKEYTOITEM 具有 LBS_WANTKEYBOARDINPUT 樣式的清單方塊會收到 WM_KEYDOWN 訊息。

如果您在 `CListBox` 對話方塊中建立物件（透過對話資源）， `CListBox` 當使用者關閉對話方塊時，就會自動終結物件。

如果您在 `CListBox` 視窗中建立物件，可能需要終結 `CListBox` 物件。 如果您在 `CListBox` 堆疊上建立物件，它會自動終結。 如果您使用函式在 `CListBox` 堆積上建立物件 **`new`** ，您必須 **`delete`** 在物件上呼叫，以便在使用者關閉父視窗時終結它。

如果您在物件中配置任何記憶體 `CListBox` ，請覆寫 `CListBox` 析構函式來處置配置。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CListBox`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="clistboxaddstring"></a><a name="addstring"></a>CListBox：： AddString

將字串新增至清單方塊。

```
int AddString(LPCTSTR lpszItem);
```

### <a name="parameters"></a>參數

*lpszItem*<br/>
指向要加入的以 null 結束的字串。

### <a name="return-value"></a>傳回值

清單方塊中字串之以零為起始的索引。 如果發生錯誤，則傳回值為 LB_ERR;如果空間不足，無法儲存新的字串，傳回值就會 LB_ERRSPACE。

### <a name="remarks"></a>備註

如果清單方塊不是以[LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式建立，則字串會加入至清單的結尾。 否則，會將字串插入清單中，並排序清單。 如果清單方塊是以 LBS_SORT 樣式（而不是[LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式）所建立，則架構會根據成員函式的一或多個呼叫來排序清單 `CompareItem` 。

使用[InsertString](#insertstring)將字串插入清單方塊內的特定位置。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#3](../../mfc/codesnippet/cpp/clistbox-class_1.cpp)]

## <a name="clistboxchartoitem"></a><a name="chartoitem"></a>CListBox：： CharToItem

當清單方塊的父視窗收到清單方塊中的 WM_CHARTOITEM 訊息時，由架構呼叫。

```
virtual int CharToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>參數

*nKey*<br/>
使用者輸入之字元的 ANSI 代碼。

*nIndex*<br/>
清單方塊插入號的目前位置。

### <a name="return-value"></a>傳回值

傳回-1 或-2 代表沒有進一步的動作或非負數，以指定清單方塊專案的索引，以在其上執行擊鍵的預設動作。 預設的實值會傳回-1。

### <a name="remarks"></a>備註

WM_CHARTOITEM 訊息會在收到 WM_CHAR 訊息時由清單方塊傳送，但只有在清單方塊符合下列所有條件時：

- 是主控描繪清單方塊。

- 未設定[LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式。

- 至少有一個專案。

您不應該自行呼叫此函數。 覆寫此函式，以提供您自己自訂的鍵盤訊息處理。

在您的覆寫中，您必須傳回值，告訴架構您執行了什麼動作。 傳回值-1 或-2 表示您已處理選取專案的所有層面，而且清單方塊不需要進一步的動作。 傳回-1 或-2 之前，您可以設定選取範圍或移動插入號或兩者。 若要設定選取專案，請使用[SetCurSel](#setcursel)或[SetSel](#setsel)。 若要移動插入號，請使用[SetCaretIndex](#setcaretindex)。

傳回值為0或以上會指定清單方塊中專案的索引，並指出清單方塊應該對指定專案上的擊鍵執行預設動作。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#4](../../mfc/codesnippet/cpp/clistbox-class_2.cpp)]

## <a name="clistboxclistbox"></a><a name="clistbox"></a>CListBox：： CListBox

建構 `CListBox` 物件。

```
CListBox();
```

### <a name="remarks"></a>備註

您可以使用 `CListBox` 兩個步驟來建立物件。 首先，呼叫此函式， `ClistBox` 然後呼叫 `Create` ，它會初始化 Windows 清單方塊，並將其附加至 `CListBox` 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#1](../../mfc/codesnippet/cpp/clistbox-class_3.cpp)]

## <a name="clistboxcompareitem"></a><a name="compareitem"></a>CListBox：： CompareItem

由架構呼叫，以判斷新專案在 [已排序的主控描繪] 清單方塊中的相對位置。

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>參數

*lpCompareItemStruct*<br/>
結構的長指標 `COMPAREITEMSTRUCT` 。

### <a name="return-value"></a>傳回值

指出[COMPAREITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-compareitemstruct)結構中所描述的兩個專案的相對位置。 它可以是下列任何一個值：

|值|意義|
|-----------|-------------|
|-1|專案1會在專案2之前排序。|
|0|專案1和專案2會排序相同的。|
|1|專案1會在專案2之後排序。|

如需結構的說明，請參閱[CWnd：： OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) `COMPAREITEMSTRUCT` 。

### <a name="remarks"></a>備註

根據預設，此成員函式不會執行任何工作。 如果您建立具有 LBS_SORT 樣式的主控描繪清單方塊，則必須覆寫此成員函式，以協助架構排序加入至清單方塊的新專案。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#5](../../mfc/codesnippet/cpp/clistbox-class_4.cpp)]

## <a name="clistboxcreate"></a><a name="create"></a>CListBox：： Create

建立 Windows 清單方塊，並將其附加至 `CListBox` 物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定清單方塊的樣式。 將[清單方塊樣式](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)的任何組合套用至方塊。

*各種*<br/>
指定清單方塊的大小和位置。 可以是 `CRect` 物件或 `RECT` 結構。

*pParentWnd*<br/>
指定清單方塊的父視窗（通常是 `CDialog` 物件）。 它不得為 NULL。

*nID*<br/>
指定清單方塊的控制項 ID。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

您可以使用 `CListBox` 兩個步驟來建立物件。 首先，呼叫此函式，然後呼叫 `Create` ，它會初始化 Windows 清單方塊，並將其附加至 `CListBox` 物件。

當 `Create` 執行時，Windows 會將[WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)、 [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)、 [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)和[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)訊息傳送至清單方塊控制項。

根據預設，這些訊息會由基類中的[OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate)、 [OnCreate](../../mfc/reference/cwnd-class.md#oncreate)、 [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)和[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)成員函式來處理 `CWnd` 。 若要擴充預設訊息處理，請從衍生類別 `CListBox` ，將訊息對應加入至新的類別，並覆寫先前的訊息處理常式成員函式。 `OnCreate`例如，覆寫以執行新類別所需的初始化。

將下列[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)套用至清單方塊控制項。

- 一律 WS_CHILD

- WS_VISIBLE 通常

- WS_DISABLED 很少

- WS_VSCROLL 加入垂直捲動條

- WS_HSCROLL 加入水準捲軸

- WS_GROUP 至群組控制項

- WS_TABSTOP 允許將此控制項按 tab 鍵

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#2](../../mfc/codesnippet/cpp/clistbox-class_5.cpp)]

## <a name="clistboxdeleteitem"></a><a name="deleteitem"></a>CListBox：:D eleteItem

當使用者從主控描繪物件中刪除專案或損毀清單方塊時，由架構呼叫 `CListBox` 。

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>參數

*lpDeleteItemStruct*<br/>
Windows [DELETEITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-deleteitemstruct)結構的長指標，其中包含已刪除之專案的相關資訊。

### <a name="remarks"></a>備註

此函式的預設實作不做任何動作。 視需要覆寫此函式以重繪主控描繪清單方塊。

如需結構的說明，請參閱[CWnd：： OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) `DELETEITEMSTRUCT` 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#6](../../mfc/codesnippet/cpp/clistbox-class_6.cpp)]

## <a name="clistboxdeletestring"></a><a name="deletestring"></a>CListBox：:D eleteString

從清單方塊中刪除位置*nIndex*中的專案。

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定要刪除之字串的以零為基底的索引。

### <a name="return-value"></a>傳回值

清單中剩餘的字串計數。 如果*nIndex*指定的索引大於清單中的專案數，則傳回值為 LB_ERR。

### <a name="remarks"></a>備註

*NIndex*之後的所有專案現在會向下移動一個位置。 例如，如果清單方塊包含兩個專案，刪除第一個專案會使其餘專案現在位於第一個位置。 *nIndex*= 0，代表第一個位置的專案。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#7](../../mfc/codesnippet/cpp/clistbox-class_7.cpp)]

## <a name="clistboxdir"></a><a name="dir"></a>CListBox：:D ir

將檔案名、磁片磁碟機或兩者的清單新增至清單方塊。

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>參數

*attr*<br/>
可以是 **`enum`** s 中所述值的任何組合 `CFile::GetStatu` [ ](../../mfc/reference/cfile-class.md#getstatus)，或下列值的任何組合：

|值|意義|
|-----------|-------------|
|0x0000|檔案可以讀取或寫入。|
|0x0001|檔案可以讀取，但無法寫入。|
|0x0002|檔案已隱藏且不會出現在目錄清單中。|
|0x0004|檔案是系統檔案。|
|0x0010|*LpszWildCard*所指定的名稱會指定目錄。|
|0x0020|檔案已封存。|
|0x4000|包含所有符合*lpszWildCard*所指定名稱的磁片磁碟機。|
|0x8000|獨佔旗標。 如果設定獨佔旗標，只會列出指定類型的檔案。 否則，除了 "normal" 檔案之外，還會列出指定類型的檔案。|

*lpszWildCard*<br/>
指向檔案規格字串。 字串可以包含萬用字元（例如，*. \* ）。

### <a name="return-value"></a>傳回值

新增至清單的最後一個檔案名之以零為起始的索引。 如果發生錯誤，則傳回值為 LB_ERR;如果空間不足，無法儲存新的字串，傳回值就會 LB_ERRSPACE。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#8](../../mfc/codesnippet/cpp/clistbox-class_8.cpp)]

## <a name="clistboxdrawitem"></a><a name="drawitem"></a>CListBox：:D rawItem

當主控描繪清單方塊的視覺外觀變更時，由架構呼叫。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>參數

*lpDrawItemStruct*<br/>
[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)結構的長指標，其中包含所需繪圖類型的相關資訊。

### <a name="remarks"></a>備註

`itemAction`結構的和 `itemState` 成員 `DRAWITEMSTRUCT` 會定義要執行的繪圖動作。

根據預設，此成員函式不會執行任何工作。 覆寫這個成員函式，以執行主控描繪物件的繪圖 `CListBox` 。 在此成員函式終止之前，應用程式應該還原為*lpDrawItemStruct*中提供的顯示內容所選取的所有圖形裝置介面（GDI）物件。

如需結構的說明，請參閱[CWnd：： OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) `DRAWITEMSTRUCT` 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#9](../../mfc/codesnippet/cpp/clistbox-class_9.cpp)]

## <a name="clistboxfindstring"></a><a name="findstring"></a>CListBox：： FindString

在清單方塊中尋找包含指定前置詞的第一個字串，但不變更清單方塊選取專案。

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszItem) const;
```

### <a name="parameters"></a>參數

*nStartAfter*<br/>
包含專案之以零為基底的索引，這是要搜尋的第一個專案之前。 當搜尋到達清單方塊的底部時，它會從清單方塊的頂端繼續回到*nStartAfter*所指定的專案。 如果*nStartAfter*為-1，則會從頭開始搜尋整個清單方塊。

*lpszItem*<br/>
指向以 null 終止的字串，其中包含要搜尋的前置詞。 搜尋會區分大小寫，因此此字串可能包含大寫和小寫字母的任何組合。

### <a name="return-value"></a>傳回值

符合專案之以零為起始的索引，如果搜尋失敗，則為 LB_ERR。

### <a name="remarks"></a>備註

使用[SelectString](#selectstring)成員函式來尋找並選取字串。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#10](../../mfc/codesnippet/cpp/clistbox-class_10.cpp)]

## <a name="clistboxfindstringexact"></a><a name="findstringexact"></a>CListBox：： FindStringExact

尋找符合*lpszFind*中指定之字串的第一個清單方塊字串。

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>參數

*nIndexStart*<br/>
在要搜尋的第一個專案之前，指定專案之以零為起始的索引。 當搜尋到達清單方塊的底部時，它會從清單方塊的頂端繼續回到*nIndexStart*所指定的專案。 如果*nIndexStart*為-1，則會從頭開始搜尋整個清單方塊。

*lpszFind*<br/>
指向要搜尋的以 null 結束的字串。 這個字串可以包含完整的檔案名，包括副檔名。 搜尋不區分大小寫，因此字串可以包含大寫和小寫字母的任意組合。

### <a name="return-value"></a>傳回值

相符專案的索引，如果搜尋失敗，則為 LB_ERR。

### <a name="remarks"></a>備註

如果清單方塊是使用擁有者繪製樣式所建立，但沒有[LBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式，則成員函式 `FindStringExact` 會嘗試比對*lpszFind*的值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#11](../../mfc/codesnippet/cpp/clistbox-class_11.cpp)]

## <a name="clistboxgetanchorindex"></a><a name="getanchorindex"></a>CListBox：： GetAnchorIndex

抓取清單方塊中目前錨點專案的以零為起始的索引。

```
int GetAnchorIndex() const;
```

### <a name="return-value"></a>傳回值

如果成功，則為目前錨點專案的索引;否則 LB_ERR。

### <a name="remarks"></a>備註

在多重選取清單方塊中，錨定專案是連續選取專案區塊中的第一個或最後一個專案。

### <a name="example"></a>範例

  請參閱[CListBox：： SetAnchorIndex](#setanchorindex)的範例。

## <a name="clistboxgetcaretindex"></a><a name="getcaretindex"></a>CListBox：： GetCaretIndex

決定在多重選取清單方塊中具有焦點矩形之專案的索引。

```
int GetCaretIndex() const;
```

### <a name="return-value"></a>傳回值

在清單方塊中具有焦點矩形之專案的以零為起始的索引。 如果清單方塊是單一挑選清單框，則傳回值會是所選取之專案的索引（如果有的話）。

### <a name="remarks"></a>備註

不一定會選取此專案。

### <a name="example"></a>範例

  請參閱[CListBox：： SetCaretIndex](#setcaretindex)的範例。

## <a name="clistboxgetcount"></a><a name="getcount"></a>CListBox：： GetCount

抓取清單方塊中的專案數。

```
int GetCount() const;
```

### <a name="return-value"></a>傳回值

清單方塊中的專案數，或在發生錯誤時 LB_ERR。

### <a name="remarks"></a>備註

傳回的計數大於最後一個專案的索引值（索引以零為基底）。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#12](../../mfc/codesnippet/cpp/clistbox-class_12.cpp)]

## <a name="clistboxgetcursel"></a><a name="getcursel"></a>CListBox：： GetCurSel

在單一挑選清單框中，抓取目前選取之專案的以零為起始的索引（如果有的話）。

```
int GetCurSel() const;
```

### <a name="return-value"></a>傳回值

目前選取之專案的以零為起始的索引（如果它是單一挑選清單框）。 如果目前未選取任何專案，就會 LB_ERR。

在多重選取清單方塊中，具有焦點之專案的索引。

### <a name="remarks"></a>備註

不要 `GetCurSel` 針對多重選取清單方塊呼叫。 請改用[CListBox：： GetSelItems](#getselitems) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#13](../../mfc/codesnippet/cpp/clistbox-class_13.cpp)]

## <a name="clistboxgethorizontalextent"></a><a name="gethorizontalextent"></a>CListBox：： GetHorizontalExtent

從清單方塊抓取，其寬度以圖元為單位，以水準方式滾動。

```
int GetHorizontalExtent() const;
```

### <a name="return-value"></a>傳回值

清單方塊的可滾動寬度（以圖元為單位）。

### <a name="remarks"></a>備註

只有當清單方塊有水準捲軸時，才適用這種情況。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#14](../../mfc/codesnippet/cpp/clistbox-class_14.cpp)]

## <a name="clistboxgetitemdata"></a><a name="getitemdata"></a>CListBox：： GetItemData

抓取與指定的清單方塊專案關聯的應用程式提供的雙聯數值。

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定清單方塊中專案以零為基底的索引。

### <a name="return-value"></a>傳回值

與專案相關聯的值，或在發生錯誤時 LB_ERR。

### <a name="remarks"></a>備註

[雙字] 值是[SetItemData](#setitemdata)呼叫的*dwItemData*參數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#15](../../mfc/codesnippet/cpp/clistbox-class_15.cpp)]

## <a name="clistboxgetitemdataptr"></a><a name="getitemdataptr"></a>CListBox：： GetItemDataPtr

將與指定清單方塊專案關聯的應用程式提供的32位值，抓取為指標（ **`void`** <strong>\*</strong> ）。

```cpp
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定清單方塊中專案以零為基底的索引。

### <a name="return-value"></a>傳回值

抓取指標，如果發生錯誤，則為-1。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#16](../../mfc/codesnippet/cpp/clistbox-class_16.cpp)]

## <a name="clistboxgetitemheight"></a><a name="getitemheight"></a>CListBox：： GetItemHeight

決定清單方塊中專案的高度。

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定清單方塊中專案以零為基底的索引。 只有在清單方塊具有 LBS_OWNERDRAWVARIABLE 樣式時，才會使用這個參數。否則，應該設定為0。

### <a name="return-value"></a>傳回值

清單方塊中專案的高度（以圖元為單位）。 如果清單方塊具有[LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式，則傳回值會是*nIndex*所指定之專案的高度。 如果發生錯誤，則傳回值為 LB_ERR。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#17](../../mfc/codesnippet/cpp/clistbox-class_17.cpp)]

## <a name="clistboxgetitemrect"></a><a name="getitemrect"></a>CListBox：： GetItemRect

抓取目前顯示在清單方塊視窗中的清單方塊專案所用的矩形維度。

```
int GetItemRect(
    int nIndex,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定專案之以零為基底的索引。

*lpRect*<br/>
指定[矩形結構](/windows/win32/api/windef/ns-windef-rect)的長指標，此方塊會接收專案的清單方塊用戶端座標。

### <a name="return-value"></a>傳回值

如果發生錯誤，LB_ERR。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#18](../../mfc/codesnippet/cpp/clistbox-class_18.cpp)]

## <a name="clistboxgetlistboxinfo"></a><a name="getlistboxinfo"></a>CListBox：： GetListBoxInfo

抓取每個資料行的專案數。

```
DWORD GetListBoxInfo() const;
```

### <a name="return-value"></a>傳回值

物件每個資料行的專案數 `CListBox` 。

### <a name="remarks"></a>備註

此成員函式會模擬[LB_GETLISTBOXINFO](/windows/win32/Controls/lb-getlistboxinfo)訊息的功能，如 Windows SDK 中所述。

## <a name="clistboxgetlocale"></a><a name="getlocale"></a>CListBox：： GetLocale

抓取清單方塊所使用的地區設定。

```
LCID GetLocale() const;
```

### <a name="return-value"></a>傳回值

清單方塊中字串的地區設定識別碼（LCID）值。

### <a name="remarks"></a>備註

例如，會使用地區設定來判斷字串在已排序清單方塊中的排序次序。

### <a name="example"></a>範例

  請參閱[CListBox：： SetLocale](#setlocale)的範例。

## <a name="clistboxgetsel"></a><a name="getsel"></a>CListBox：： GetSel

抓取專案的選取狀態。

```
int GetSel(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定專案之以零為基底的索引。

### <a name="return-value"></a>傳回值

如果已選取指定的專案，則為正數;否則，它是0。 如果發生錯誤，則傳回值為 LB_ERR。

### <a name="remarks"></a>備註

這個成員函式適用于單一和多重選取清單方塊。

若要取得目前所選清單方塊專案的索引，請使用[CListBox：： GetCurSel](#getcursel)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#19](../../mfc/codesnippet/cpp/clistbox-class_19.cpp)]

## <a name="clistboxgetselcount"></a><a name="getselcount"></a>CListBox：： GetSelCount

抓取多重選取清單方塊中選取專案的總數。

```
int GetSelCount() const;
```

### <a name="return-value"></a>傳回值

清單方塊中選取專案的計數。 如果清單方塊是單一挑選清單框，則傳回值會是 LB_ERR。

### <a name="example"></a>範例

  請參閱[CListBox：： GetSelItems](#getselitems)的範例。

## <a name="clistboxgetselitems"></a><a name="getselitems"></a>CListBox：： GetSelItems

以整數陣列填滿緩衝區，指定多重選取清單方塊中選取專案的專案編號。

```
int GetSelItems(
    int nMaxItems,
    LPINT rgIndex) const;
```

### <a name="parameters"></a>參數

*nMaxItems*<br/>
指定要將專案編號放在緩衝區中的選取專案數上限。

*rgIndex*<br/>
針對*nMaxItems*所指定的整數數目，指定夠大的緩衝區指標。

### <a name="return-value"></a>傳回值

放在緩衝區中的實際專案數目。 如果清單方塊是單一挑選清單框，則傳回值為 `LB_ERR` 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#20](../../mfc/codesnippet/cpp/clistbox-class_20.cpp)]

## <a name="clistboxgettext"></a><a name="gettext"></a>CListBox：： GetText

取得清單方塊中的字串。

```
int GetText(
    int nIndex,
    LPTSTR lpszBuffer) const;

void GetText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定要抓取之字串的以零為起始的索引。

*lpszBuffer*<br/>
指向接收字串的緩衝區。 緩衝區必須有足夠的空間來表示字串和終止的 null 字元。 您可以藉由呼叫成員函式，預先決定字串的大小 `GetTextLen` 。

*rString*<br/>
`CString` 物件的參考。

### <a name="return-value"></a>傳回值

字串的長度（以位元組為單位），不包括終止的 null 字元。 如果*nIndex*未指定有效的索引，則會 LB_ERR 傳回值。

### <a name="remarks"></a>備註

此成員函式的第二種形式會 `CString` 以字串文字填入物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#21](../../mfc/codesnippet/cpp/clistbox-class_21.cpp)]

## <a name="clistboxgettextlen"></a><a name="gettextlen"></a>CListBox：： GetTextLen

取得清單方塊專案中的字串長度。

```
int GetTextLen(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定字串之以零為基底的索引。

### <a name="return-value"></a>傳回值

字串的長度（以字元為單位），不包括結束的 null 字元。 如果*nIndex*未指定有效的索引，則會 LB_ERR 傳回值。

### <a name="example"></a>範例

  請參閱[CListBox：： GetText](#gettext)的範例。

## <a name="clistboxgettopindex"></a><a name="gettopindex"></a>CListBox：： GetTopIndex

抓取清單方塊中第一個可見專案的以零為基底的索引。

```
int GetTopIndex() const;
```

### <a name="return-value"></a>傳回值

如果成功，則為清單方塊中第一個可見專案之以零為起始的索引，否則為 LB_ERR。

### <a name="remarks"></a>備註

一開始，專案0位於清單方塊的頂端，但如果清單方塊已滾動，則另一個專案可能在頂端。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#22](../../mfc/codesnippet/cpp/clistbox-class_22.cpp)]

## <a name="clistboxinitstorage"></a><a name="initstorage"></a>CListBox：： InitStorage

配置記憶體以儲存清單方塊專案。

```
int InitStorage(
    int nItems,
    UINT nBytes);
```

### <a name="parameters"></a>參數

*nItems*<br/>
指定要加入的專案數。

*nBytes*<br/>
指定要為專案字串配置的記憶體數量（以位元組為單位）。

### <a name="return-value"></a>傳回值

如果成功，則需要記憶體重新配置之前，清單方塊可以儲存的最大專案數，否則 LB_ERRSPACE，表示沒有足夠的記憶體可用。

### <a name="remarks"></a>備註

先呼叫此函式，再將大量專案新增至 `CListBox` 。

此函式有助於加速初始化具有大量專案的清單方塊（超過100）。 它會預先配置指定的記憶體數量，讓後續的[AddString](#addstring)、 [InsertString](#insertstring)和[Dir](#dir)函式會採用最短的可能時間。 您可以使用參數的預估值。 如果您高估值，則會配置一些額外的記憶體;如果您低估了，一般配置會用於超過預先配置金額的專案。

僅限 Windows 95/98： *nItems*參數限制為16位值。 這表示清單方塊不能包含超過32767個專案。 雖然專案數受到限制，清單方塊中的專案總大小只受限於可用的記憶體。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#23](../../mfc/codesnippet/cpp/clistbox-class_23.cpp)]

## <a name="clistboxinsertstring"></a><a name="insertstring"></a>CListBox：： InsertString

將字串插入清單方塊中。

```
int InsertString(
    int nIndex,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定要插入字串的位置之以零為起始的索引。 如果此參數為-1，則字串會加入至清單的結尾。

*lpszItem*<br/>
指向要插入的 null 結尾字串。

### <a name="return-value"></a>傳回值

已插入字串之位置以零為基底的索引。 如果發生錯誤，則傳回值為 LB_ERR;如果空間不足，無法儲存新的字串，傳回值就會 LB_ERRSPACE。

### <a name="remarks"></a>備註

不同于[AddString](#addstring)成員函式，不 `InsertString` 會造成具有[LBS_SORT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式的清單進行排序。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#24](../../mfc/codesnippet/cpp/clistbox-class_24.cpp)]

## <a name="clistboxitemfrompoint"></a><a name="itemfrompoint"></a>CListBox：： ItemFromPoint

判斷最接近*pt*中所指定點的清單方塊專案。

```
UINT ItemFromPoint(
    CPoint pt,
    BOOL& bOutside) const;
```

### <a name="parameters"></a>參數

*pt*<br/>
要尋找最接近專案的點，指定相對於清單方塊的工作區左上角。

*bOutside*<br/>
如果*pt*位於清單方塊的工作區之外，則為 TRUE 的 BOOL 變數參考 *，如果 pt 位於清單*框的工作區中，則為 FALSE。

### <a name="return-value"></a>傳回值

以*pt*指定之點最近的專案索引。

### <a name="remarks"></a>備註

您可以使用此函式來判斷滑鼠游標移至哪個清單方塊專案。

### <a name="example"></a>範例

  請參閱[CListBox：： SetAnchorIndex](#setanchorindex)的範例。

## <a name="clistboxmeasureitem"></a><a name="measureitem"></a>CListBox：： MeasureItem

當建立具有擁有者繪製樣式的清單方塊時，由架構呼叫。

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>參數

*lpMeasureItemStruct*<br/>
[MEASUREITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-measureitemstruct)結構的長指標。

### <a name="remarks"></a>備註

根據預設，此成員函式不會執行任何工作。 覆寫這個成員函式並填入 `MEASUREITEMSTRUCT` 結構，以通知視窗清單方塊的維度。 如果清單方塊是使用[LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式所建立，則架構會為清單方塊中的每個專案呼叫這個成員函式。 否則，這個成員只會呼叫一次。

如需在以成員函式建立的主控描繪清單方塊中使用[LBS_OWNERDRAWFIXED](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式的進一步資訊 `SubclassDlgItem` `CWnd` ，請參閱[技術提示 14](../../mfc/tn014-custom-controls.md)中的討論。

如需結構的說明，請參閱[CWnd：： OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) `MEASUREITEMSTRUCT` 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#25](../../mfc/codesnippet/cpp/clistbox-class_25.cpp)]

## <a name="clistboxresetcontent"></a><a name="resetcontent"></a>CListBox：： ResetContent

將所有專案從清單方塊中移除。

```cpp
void ResetContent();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#26](../../mfc/codesnippet/cpp/clistbox-class_26.cpp)]

## <a name="clistboxselectstring"></a><a name="selectstring"></a>CListBox：： SelectString

搜尋符合指定之字串的清單方塊專案，如果找到相符的專案，則選取該專案。

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszItem);
```

### <a name="parameters"></a>參數

*nStartAfter*<br/>
包含專案之以零為基底的索引，這是要搜尋的第一個專案之前。 當搜尋到達清單方塊的底部時，它會從清單方塊的頂端繼續回到*nStartAfter*所指定的專案。 如果*nStartAfter*為-1，則會從頭開始搜尋整個清單方塊。

*lpszItem*<br/>
指向以 null 終止的字串，其中包含要搜尋的前置詞。 搜尋會區分大小寫，因此此字串可能包含大寫和小寫字母的任何組合。

### <a name="return-value"></a>傳回值

若搜尋成功，則為所選取專案的索引。 如果搜尋失敗，則傳回值為 LB_ERR，而且目前的選取範圍不會變更。

### <a name="remarks"></a>備註

如有必要，會滾動清單方塊以將選取的專案帶到視野中。

這個成員函式不能與具有[LBS_MULTIPLESEL](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式的清單方塊一起使用。

只有當專案的初始字元（從起點）符合*lpszItem*所指定之字串中的字元時，才會選取專案。

使用成員函式 `FindString` 來尋找字串，而不選取該專案。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#27](../../mfc/codesnippet/cpp/clistbox-class_27.cpp)]

## <a name="clistboxselitemrange"></a><a name="selitemrange"></a>CListBox：： SelItemRange

在多重選取清單方塊中選取多個連續專案。

```
int SelItemRange(
    BOOL bSelect,
    int nFirstItem,
    int nLastItem);
```

### <a name="parameters"></a>參數

*bSelect*<br/>
指定如何設定選取範圍。 如果*bSelect*為 TRUE，則會選取並反白顯示字串。若為 FALSE，則會移除反白顯示，而且不會再選取字串。

*nFirstItem*<br/>
指定要設定的第一個專案之以零為基底的索引。

*nLastItem*<br/>
指定要設定的最後一個專案之以零為起始的索引。

### <a name="return-value"></a>傳回值

如果發生錯誤，LB_ERR。

### <a name="remarks"></a>備註

此成員函式只能與多個挑選清單框搭配使用。 如果您只需要在多重選取清單方塊中選取一個專案，也就是，如果*nFirstItem*等於*nLastItem* ，請改為呼叫[SetSel](#setsel)成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#28](../../mfc/codesnippet/cpp/clistbox-class_28.cpp)]

## <a name="clistboxsetanchorindex"></a><a name="setanchorindex"></a>CListBox：： SetAnchorIndex

設定多重選取清單方塊中的錨點，以開始延伸選取範圍。

```cpp
void SetAnchorIndex(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定將作為錨點之清單方塊專案的以零為起始的索引。

### <a name="remarks"></a>備註

在多重選取清單方塊中，錨定專案是連續選取專案區塊中的第一個或最後一個專案。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#29](../../mfc/codesnippet/cpp/clistbox-class_29.cpp)]

## <a name="clistboxsetcaretindex"></a><a name="setcaretindex"></a>CListBox：： SetCaretIndex

將焦點矩形設定為多重選取清單方塊中指定索引處的專案。

```
int SetCaretIndex(
    int nIndex,
    BOOL bScroll = TRUE);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定要接收清單方塊中焦點矩形之專案的以零為起始的索引。

*bScroll*<br/>
如果此值為0，則會滾動專案，直到完全可見為止。 如果這個值不是0，則專案會一直滾動到至少部分可見為止。

### <a name="return-value"></a>傳回值

如果發生錯誤，LB_ERR。

### <a name="remarks"></a>備註

如果看不到該專案，則會將它滾動到 view。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#30](../../mfc/codesnippet/cpp/clistbox-class_30.cpp)]

## <a name="clistboxsetcolumnwidth"></a><a name="setcolumnwidth"></a>CListBox：： SetColumnWidth

設定多欄清單方塊中所有資料行的寬度（以圖元為單位）（以[LBS_MULTICOLUMN](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式建立）。

```cpp
void SetColumnWidth(int cxWidth);
```

### <a name="parameters"></a>參數

*cxWidth*<br/>
指定所有資料行的寬度（以圖元為單位）。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#31](../../mfc/codesnippet/cpp/clistbox-class_31.cpp)]

## <a name="clistboxsetcursel"></a><a name="setcursel"></a>CListBox：： SetCurSel

選取字串，並視需要將它滾動到 view。

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>參數

*N 請選取*<br/>
指定要選取之字串的以零為基底的索引。 如果*n 請選取*為-1，則清單方塊會設定為沒有選取專案。

### <a name="return-value"></a>傳回值

如果發生錯誤，LB_ERR。

### <a name="remarks"></a>備註

選取新的字串時，清單方塊會從先前選取的字串中移除反白顯示。

此成員函式只能與單一挑選清單框搭配使用。

若要在多重選取清單方塊中設定或移除選取範圍，請使用[CListBox：： SetSel](#setsel)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#32](../../mfc/codesnippet/cpp/clistbox-class_32.cpp)]

## <a name="clistboxsethorizontalextent"></a><a name="sethorizontalextent"></a>CListBox：： SetHorizontalExtent

設定可水準滾動清單方塊的寬度（以圖元為單位）。

```cpp
void SetHorizontalExtent(int cxExtent);
```

### <a name="parameters"></a>參數

*cxExtent*<br/>
指定可水準滾動清單方塊的圖元數目。

### <a name="remarks"></a>備註

如果清單方塊的大小小於此值，水準捲軸會在清單方塊中水準滾動專案。 如果清單方塊大小大於或等於這個值，則會隱藏水準捲軸。

若要回應的呼叫 `SetHorizontalExtent` ，清單方塊必須已經使用[WS_HSCROLL](../../mfc/reference/styles-used-by-mfc.md#window-styles)樣式定義。

這個成員函式對多欄清單方塊而言並不實用。 針對多行清單方塊，呼叫 `SetColumnWidth` 成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#33](../../mfc/codesnippet/cpp/clistbox-class_33.cpp)]

## <a name="clistboxsetitemdata"></a><a name="setitemdata"></a>CListBox：： SetItemData

在清單方塊中設定與指定專案相關聯的值。

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定專案之以零為基底的索引。

*dwItemData*<br/>
指定要與專案相關聯的值。

### <a name="return-value"></a>傳回值

如果發生錯誤，LB_ERR。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#34](../../mfc/codesnippet/cpp/clistbox-class_34.cpp)]

## <a name="clistboxsetitemdataptr"></a><a name="setitemdataptr"></a>CListBox：： SetItemDataPtr

將與清單方塊中指定專案相關聯的32位值設定為指定的指標（ **`void`** <strong>\*</strong> ）。

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定專案之以零為基底的索引。

*pData*<br/>
指定要與專案相關聯的指標。

### <a name="return-value"></a>傳回值

如果發生錯誤，LB_ERR。

### <a name="remarks"></a>備註

這個指標在清單方塊的生命週期中仍然有效，即使專案在清單方塊內的相對位置可能會隨著新增或移除專案而變更。 因此，方塊內的專案索引可能會變更，但指標仍然可靠。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#35](../../mfc/codesnippet/cpp/clistbox-class_35.cpp)]

## <a name="clistboxsetitemheight"></a><a name="setitemheight"></a>CListBox：： SetItemHeight

設定清單方塊中專案的高度。

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定清單方塊中專案以零為基底的索引。 只有在清單方塊具有 LBS_OWNERDRAWVARIABLE 樣式時，才會使用這個參數。否則，應該設定為0。

*cyItemHeight*<br/>
指定專案的高度（以圖元為單位）。

### <a name="return-value"></a>傳回值

如果索引或高度無效，則 LB_ERR。

### <a name="remarks"></a>備註

如果清單方塊具有[LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式，則此函式會設定*nIndex*所指定之專案的高度。 否則，此函式會設定清單方塊中所有專案的高度。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#36](../../mfc/codesnippet/cpp/clistbox-class_36.cpp)]

## <a name="clistboxsetlocale"></a><a name="setlocale"></a>CListBox：： SetLocale

設定此清單方塊的地區設定識別碼。

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>參數

*nNewLocale*<br/>
要為清單方塊設定的新地區設定識別碼（LCID）值。

### <a name="return-value"></a>傳回值

此清單方塊的先前地區設定識別碼（LCID）值。

### <a name="remarks"></a>備註

如果 `SetLocale` 未呼叫，則會從系統取得預設地區設定。 您可以使用控制台的區域（或國際）應用程式來修改這個系統預設的地區設定。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#37](../../mfc/codesnippet/cpp/clistbox-class_37.cpp)]

## <a name="clistboxsetsel"></a><a name="setsel"></a>CListBox：： SetSel

選取多重選取清單方塊中的字串。

```
int SetSel(
    int nIndex,
    BOOL bSelect = TRUE);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
包含要設定之字串的以零為基底的索引。 如果為-1，則會根據*bSelect*的值，將選取範圍加入或移除所有字串。

*bSelect*<br/>
指定如何設定選取範圍。 如果*bSelect*為 TRUE，則會選取並反白顯示字串。若為 FALSE，則會移除反白顯示，而且不會再選取字串。 預設會選取並反白顯示指定的字串。

### <a name="return-value"></a>傳回值

如果發生錯誤，LB_ERR。

### <a name="remarks"></a>備註

此成員函式只能與多個挑選清單框搭配使用。

若要從單一挑選清單框中選取專案，請使用[CListBox：： SetCurSel](#setcursel)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#38](../../mfc/codesnippet/cpp/clistbox-class_38.cpp)]

## <a name="clistboxsettabstops"></a><a name="settabstops"></a>CListBox：： SetTabStops

設定清單方塊中的定位停駐點位置。

```cpp
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>參數

*cxEachStop*<br/>
索引標籤會在每個*cxEachStop*對話方塊單位上設定。 如需對話單位的說明，請參閱*rgTabStops* 。

*nTabStops*<br/>
指定清單方塊中要有的定位停駐點數目。

*rgTabStops*<br/>
指向整數陣列的第一個成員，其中包含對話方塊單元中的索引標籤停止位置。 對話單位是水準或垂直距離。 一個水準對話單位等於目前對話基底寬度單位的四分之一，而一個垂直對話單位等於目前對話基底高度單位的八分之一。 對話方塊基本單位是根據目前系統字型的高度和寬度計算。 Windows 函式會傳回 `GetDialogBaseUnits` 目前的對話方塊基底單位（以圖元為單位）。 定位停駐點必須以遞增順序排序;不允許使用 [上一頁] 索引標籤。

### <a name="return-value"></a>傳回值

如果已設定所有索引標籤，則為非零值;否則為0。

### <a name="remarks"></a>備註

若要將 tab 鍵停駐于預設大小2個對話方塊單位，請呼叫此成員函式的無參數版本。 若要將 tab 鍵停駐于2以外的大小，請使用*cxEachStop*引數呼叫版本。

若要將 tab 鍵停駐于大小陣列，請使用版本搭配*rgTabStops*和*nTabStops*引數。 系統會針對*rgTabStops*中的每個值（最多為*nTabStops*所指定的數位）設定制表位。

若要回應成員函式的呼叫 `SetTabStops` ，必須使用[LBS_USETABSTOPS](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式建立清單方塊。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#39](../../mfc/codesnippet/cpp/clistbox-class_39.cpp)]

## <a name="clistboxsettopindex"></a><a name="settopindex"></a>CListBox：： SetTopIndex

確保可以看見特定的清單方塊專案。

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定清單方塊專案以零為基底的索引。

### <a name="return-value"></a>傳回值

如果成功，則為零，如果發生錯誤，則為 LB_ERR。

### <a name="remarks"></a>備註

系統會滾動清單方塊，直到*nIndex*所指定的專案出現在清單方塊的頂端，或已達到最大滾動範圍為止。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#40](../../mfc/codesnippet/cpp/clistbox-class_40.cpp)]

## <a name="clistboxvkeytoitem"></a><a name="vkeytoitem"></a>CListBox：： VKeyToItem

當清單方塊的父視窗收到清單方塊中的 WM_VKEYTOITEM 訊息時，由架構呼叫。

```
virtual int VKeyToItem(
    UINT nKey,
    UINT nIndex);
```

### <a name="parameters"></a>參數

*nKey*<br/>
使用者所按下之金鑰的虛擬按鍵碼。 如需標準虛擬按鍵代碼的清單，請參閱 Winuser。

*nIndex*<br/>
清單方塊插入號的目前位置。

### <a name="return-value"></a>傳回值

傳回-2 表示不進行進一步的動作，-1 代表預設動作，或非負數指定清單方塊專案的索引，以在其上執行擊鍵的預設動作。

### <a name="remarks"></a>備註

WM_VKEYTOITEM 訊息會在收到 WM_KEYDOWN 訊息時由清單方塊傳送，但只有在清單方塊符合下列兩項時：

- 已設定[LBS_WANTKEYBOARDINPUT](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式。

- 至少有一個專案。

您不應該自行呼叫此函數。 覆寫此函式，以提供您自己自訂的鍵盤訊息處理。

您必須傳回值，以告知架構您的覆寫所執行的動作。 傳回值-2 表示應用程式已處理選取專案的所有層面，而且清單方塊不需要進一步的動作。 傳回-2 之前，您可以設定選取範圍或移動插入號或兩者。 若要設定選取專案，請使用[SetCurSel](#setcursel)或[SetSel](#setsel)。 若要移動插入號，請使用[SetCaretIndex](#setcaretindex)。

傳回值-1 表示清單方塊應執行預設動作以回應按鍵。預設的實值會傳回-1。

傳回值為0或以上會指定清單方塊中專案的索引，並指出清單方塊應該對指定專案上的擊鍵執行預設動作。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CListBox#41](../../mfc/codesnippet/cpp/clistbox-class_41.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[CButton 類別](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox 類別](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit 類別](../../mfc/reference/cedit-class.md)<br/>
[CScrollBar 類別](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic 類別](../../mfc/reference/cstatic-class.md)
