---
title: CComboBox 類別
ms.date: 11/04/2016
f1_keywords:
- CComboBox
- AFXWIN/CComboBox
- AFXWIN/CComboBox::CComboBox
- AFXWIN/CComboBox::AddString
- AFXWIN/CComboBox::Clear
- AFXWIN/CComboBox::CompareItem
- AFXWIN/CComboBox::Copy
- AFXWIN/CComboBox::Create
- AFXWIN/CComboBox::Cut
- AFXWIN/CComboBox::DeleteItem
- AFXWIN/CComboBox::DeleteString
- AFXWIN/CComboBox::Dir
- AFXWIN/CComboBox::DrawItem
- AFXWIN/CComboBox::FindString
- AFXWIN/CComboBox::FindStringExact
- AFXWIN/CComboBox::GetComboBoxInfo
- AFXWIN/CComboBox::GetCount
- AFXWIN/CComboBox::GetCueBanner
- AFXWIN/CComboBox::GetCurSel
- AFXWIN/CComboBox::GetDroppedControlRect
- AFXWIN/CComboBox::GetDroppedState
- AFXWIN/CComboBox::GetDroppedWidth
- AFXWIN/CComboBox::GetEditSel
- AFXWIN/CComboBox::GetExtendedUI
- AFXWIN/CComboBox::GetHorizontalExtent
- AFXWIN/CComboBox::GetItemData
- AFXWIN/CComboBox::GetItemDataPtr
- AFXWIN/CComboBox::GetItemHeight
- AFXWIN/CComboBox::GetLBText
- AFXWIN/CComboBox::GetLBTextLen
- AFXWIN/CComboBox::GetLocale
- AFXWIN/CComboBox::GetMinVisible
- AFXWIN/CComboBox::GetTopIndex
- AFXWIN/CComboBox::InitStorage
- AFXWIN/CComboBox::InsertString
- AFXWIN/CComboBox::LimitText
- AFXWIN/CComboBox::MeasureItem
- AFXWIN/CComboBox::Paste
- AFXWIN/CComboBox::ResetContent
- AFXWIN/CComboBox::SelectString
- AFXWIN/CComboBox::SetCueBanner
- AFXWIN/CComboBox::SetCurSel
- AFXWIN/CComboBox::SetDroppedWidth
- AFXWIN/CComboBox::SetEditSel
- AFXWIN/CComboBox::SetExtendedUI
- AFXWIN/CComboBox::SetHorizontalExtent
- AFXWIN/CComboBox::SetItemData
- AFXWIN/CComboBox::SetItemDataPtr
- AFXWIN/CComboBox::SetItemHeight
- AFXWIN/CComboBox::SetLocale
- AFXWIN/CComboBox::SetMinVisibleItems
- AFXWIN/CComboBox::SetTopIndex
- AFXWIN/CComboBox::ShowDropDown
helpviewer_keywords:
- CComboBox [MFC], CComboBox
- CComboBox [MFC], AddString
- CComboBox [MFC], Clear
- CComboBox [MFC], CompareItem
- CComboBox [MFC], Copy
- CComboBox [MFC], Create
- CComboBox [MFC], Cut
- CComboBox [MFC], DeleteItem
- CComboBox [MFC], DeleteString
- CComboBox [MFC], Dir
- CComboBox [MFC], DrawItem
- CComboBox [MFC], FindString
- CComboBox [MFC], FindStringExact
- CComboBox [MFC], GetComboBoxInfo
- CComboBox [MFC], GetCount
- CComboBox [MFC], GetCueBanner
- CComboBox [MFC], GetCurSel
- CComboBox [MFC], GetDroppedControlRect
- CComboBox [MFC], GetDroppedState
- CComboBox [MFC], GetDroppedWidth
- CComboBox [MFC], GetEditSel
- CComboBox [MFC], GetExtendedUI
- CComboBox [MFC], GetHorizontalExtent
- CComboBox [MFC], GetItemData
- CComboBox [MFC], GetItemDataPtr
- CComboBox [MFC], GetItemHeight
- CComboBox [MFC], GetLBText
- CComboBox [MFC], GetLBTextLen
- CComboBox [MFC], GetLocale
- CComboBox [MFC], GetMinVisible
- CComboBox [MFC], GetTopIndex
- CComboBox [MFC], InitStorage
- CComboBox [MFC], InsertString
- CComboBox [MFC], LimitText
- CComboBox [MFC], MeasureItem
- CComboBox [MFC], Paste
- CComboBox [MFC], ResetContent
- CComboBox [MFC], SelectString
- CComboBox [MFC], SetCueBanner
- CComboBox [MFC], SetCurSel
- CComboBox [MFC], SetDroppedWidth
- CComboBox [MFC], SetEditSel
- CComboBox [MFC], SetExtendedUI
- CComboBox [MFC], SetHorizontalExtent
- CComboBox [MFC], SetItemData
- CComboBox [MFC], SetItemDataPtr
- CComboBox [MFC], SetItemHeight
- CComboBox [MFC], SetLocale
- CComboBox [MFC], SetMinVisibleItems
- CComboBox [MFC], SetTopIndex
- CComboBox [MFC], ShowDropDown
ms.assetid: 4e73b5df-0d2e-4658-9706-38133fb10513
ms.openlocfilehash: df935bb924c7d8908b1166852dc553a73fc71ff3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369515"
---
# <a name="ccombobox-class"></a>CComboBox 類別

提供 Windows 下拉式方塊的功能。

## <a name="syntax"></a>語法

```
class CComboBox : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CComboBox:CComboBox](#ccombobox)|建構 `CComboBox` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComboBox::AddString](#addstring)|將字串添加到組合框的清單框中或具有CBS_SORT樣式的清單框的排序位置。|
|[CComboBox:清除](#clear)|刪除(清除)編輯控制項中的當前選擇(如果有)。|
|[CComboBox:比較項目](#compareitem)|由框架調用以確定新清單項在排序的擁有者繪製組合框中的相對位置。|
|[CComboBox:複製](#copy)|以CF_TEXT格式將當前選擇(如果有)複製到剪貼簿上。|
|[CComboBox:建立](#create)|創建組合框並將其附加到`CComboBox`物件。|
|[CComboBox:切割](#cut)|刪除(剪切)編輯控制項中的目前選擇(如果有),並將刪除的文本以CF_TEXT格式複製到剪貼簿。|
|[CComboBox::Delete專案](#deleteitem)|當從擁有者繪製的組合框中刪除清單項時,由框架調用。|
|[CComboBox::DeleteString](#deletestring)|從組合框的清單框中移除字串。|
|[CComboBox::Dir](#dir)|將檔案名清單添加到組合框的清單框中。|
|[CComboBox::D原始專案](#drawitem)|當所有者繪製的組合框的可視方面發生更改時,由框架調用。|
|[CComboBox::尋找字串](#findstring)|在組合框的清單框中尋找包含指定前置碼的第一個字串。|
|[CComboBox::尋找字串精確](#findstringexact)|尋找與指定字串匹配的第一個列表框字串(在組合框中)。|
|[CComboBox:取得ComboBox資訊](#getcomboboxinfo)|檢索有關`CComboBox`物件的資訊。|
|[CComboBox:取得計數](#getcount)|檢索組合框清單框中的項目數。|
|[CComboBox:GetCueBanner](#getcuebanner)|獲取為組合框控制器顯示的提示文本。|
|[CComboBox:取得CurSel](#getcursel)|在組合框的清單框中檢索當前選定項(如果有)的索引。|
|[CComboBox:取得已放棄控制](#getdroppedcontrolrect)|檢索下拉組合框的可見(下拉)列表框的螢幕座標。|
|[CComboBox:抓取放棄狀態](#getdroppedstate)|確定下拉組合框的清單框是否可見(下拉)。|
|[CComboBox:取得刪除寬度](#getdroppedwidth)|檢索組合框的下拉列表框部分的最小允許寬度。|
|[CComboBox:取得編輯塞爾](#geteditsel)|在組合框的編輯控制項中獲取當前選擇的起始和結束字元位置。|
|[CComboBox:取得擴充 UI](#getextendedui)|確定組合框是否具有預設使用者介面或擴展的用戶介面。|
|[CComboBox:取得橫向範圍](#gethorizontalextent)|返回組合框的清單框部分可以水平滾動的寬度。|
|[CComboBox:抓取項目資料](#getitemdata)|檢索與指定的組合框項關聯的應用程式提供的 32 位值。|
|[CComboBox:抓取項目資料Ptr](#getitemdataptr)|檢索與指定的組合框項關聯的應用程式提供的 32 位指標。|
|[CComboBox:取得專案高度](#getitemheight)|檢索組合框中清單項的高度。|
|[CComboBox:取得LBText](#getlbtext)|從組合框的清單框中獲取字串。|
|[CComboBox:取得LBTextLen](#getlbtextlen)|取得組合框清單框中字串的長度。|
|[CComboBox:抓取本地化](#getlocale)|檢索組合框的區域設置標識符。|
|[CComboBox:取得可見](#getminvisible)|取得目前組合框下拉清單中的最小可見項數。|
|[CComboBox:取得TopIndex](#gettopindex)|返回組合框列表框部分中第一個可見項的索引。|
|[CComboBox::在內存儲](#initstorage)|預分配群組框清單框部分中的項目和字串的記憶體區塊。|
|[CComboBox::InsertString](#insertstring)|將字串插入下拉式方塊的清單方塊中。|
|[CComboBox:限制文字](#limittext)|限制用戶可以輸入到組合框的編輯控制項中的文本長度。|
|[CComboBox:測量專案](#measureitem)|由框架呼叫,以確定建立所有者繪製組合框時組合框尺寸。|
|[CComboBox::Paste](#paste)|將剪輯簿中的資料插入到目前游標位置的編輯控制項中。 僅當剪貼簿以CF_TEXT格式包含數據時,才會插入數據。|
|[CComboBox:重置內容](#resetcontent)|從清單框中移除所有專案,並編輯組合框控制項。|
|[CComboBox:選擇字串](#selectstring)|在組合框的清單框中搜索字串,如果找到該字串,則選擇清單框中的字串並將該字串複製到編輯控制項。|
|[CComboBox::SetCueBanner](#setcuebanner)|設定為組合框控制器顯示的提示文本。|
|[CComboBox::SetCurSel](#setcursel)|在組合框的清單框中選擇字串。|
|[CComboBox::設置丟棄寬度](#setdroppedwidth)|設置組合框的下拉列表框部分的最小允許寬度。|
|[CComboBox:設定編輯塞爾](#seteditsel)|選擇組合框的編輯控制項中的字元。|
|[CComboBox::設定擴充UI](#setextendedui)|為具有CBS_DROPDOWN或CBS_DROPDOWNLIST樣式的組合框選擇默認使用者介面或擴展使用者介面。|
|[CComboBox::設定水平範圍](#sethorizontalextent)|設定組合框的清單框部分可以水平滾動的圖元寬度。|
|[CComboBox::設定項目資料](#setitemdata)|在組合框中設置與指定項關聯的 32 位值。|
|[CComboBox::設定項目資料Ptr](#setitemdataptr)|在組合框中設置與指定項關聯的 32 位指標。|
|[CComboBox::設定專案高度](#setitemheight)|設定組合框中列表項的高度或組合框的編輯控制項(或靜態文字)部分的高度。|
|[CComboBox::設定本地端](#setlocale)|設定組合框的區域設置標識符。|
|[CComboBox:設定明目數專案](#setminvisibleitems)|設定當前組合框下拉清單中的最小可見項數。|
|[CComboBox::SetTopIndex](#settopindex)|告訴組合框的清單框部分以顯示頂部具有指定索引的項。|
|[CComboBox::顯示下拉](#showdropdown)|顯示或隱藏具有CBS_DROPDOWN或CBS_DROPDOWNLIST樣式的組合框的列表框。|

## <a name="remarks"></a>備註

組合框由清單框與靜態控制項或編輯控制件結合而成。 控制項清單框部分可能隨時顯示,也可能僅在用戶選擇控制者旁邊的下拉箭頭時下拉。

清單框中選取的專案(如果有)顯示在靜態控制件或編輯控制項中。 此外,如果組合框具有下拉列表樣式,用戶可以鍵入清單中某一項的初始字元,如果顯示列表框將突出顯示具有該初始字元的下一個專案。

下表比較了三種組合框[樣式](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)。

|Style|何時是清單框可見|靜態或編輯控制項|
|-----------|-------------------------------|-----------------------------|
|Simple|一律|編輯|
|Drop-down|下落時|編輯|
|下拉式清單|下落時|靜態|

可以從對話框範本或`CComboBox`直接在代碼中創建物件。 在這兩種情況下,首先調用構造函數`CComboBox`來構`CComboBox`造 物件;否則,請先調用構造函數來構造該物件。然後調用[Create](#create)成員函數以創建控制項並將其`CComboBox`附加到 物件。

如果要處理組合框發送到其父級的 Windows 通知消息(通常是派`CDialog`生自的類),則會為每個郵件向父類添加消息映射條目和消息處理程式成員函數。

每個訊息對應項目以以下的檔案:

**開啟\_**_通知_**(ID** _ _,_成員Fxn_ **)**

其中`id`指定傳送通知的組合框控制項的子視窗`memberFxn`ID,以及 您為處理通知而編寫的父成員函數的名稱。

父函數原型如下所示:

afx_msg ( **);** **afx_msg** `void` `memberFxn`

無法預測發送某些通知的順序。 特別是,CBN_SELCHANGE通知可能發生在通知CBN_CLOSEUP之前或之後。

潛在的消息對應項目如下:

- ON_CBN_CLOSEUP(Windows 3.1 及更高版本)。組合框的清單框已關閉。 對於具有[CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式的組合框,不會發送此通知消息。

- ON_CBN_DBLCLK 使用者雙擊組合框清單框中的字串。 此通知消息僅為具有CBS_SIMPLE樣式的組合框發送。 對於具有[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式的組合框,無法按兩下,因為按一下將隱藏清單框。

- ON_CBN_DROPDOWN 組合框的清單框即將下拉(可見)。 此通知消息只能針對具有CBS_DROPDOWN或CBS_DROPDOWNLIST風格的組合框。

- ON_CBN_EDITCHANGE使用者已執行的操作可能更改了組合框的編輯控制部分中的文本。 與CBN_EDITUPDATE消息不同,此消息是在Windows更新螢幕後發送的。 如果組合框具有CBS_DROPDOWNLIST樣式,則不發送該組合框。

- ON_CBN_EDITUPDATE 組合框的編輯控制部分即將顯示更改的文本。 此通知消息在控件格式化文本後發送,但在顯示文本之前發送。 如果組合框具有CBS_DROPDOWNLIST樣式,則不發送該組合框。

- ON_CBN_ERRSPACE 組合框無法分配足夠的記憶體以滿足特定請求。

- ON_CBN_SELENDCANCEL(Windows 3.1 及更高版本)。指示應取消用戶的選擇。 使用者按一下某個項目,然後單擊另一個視窗或控制項以隱藏組合框的清單框。 此通知消息在CBN_CLOSEUP通知消息之前發送,以指示應忽略使用者的選擇。 即使未發送CBN_CLOSEUP通知消息(例如,具有CBS_SIMPLE樣式的組合框),也會發送CBN_SELENDCANCEL或CBN_SELENDOK通知消息。

- ON_CBN_SELENDOK 用戶選擇項目,然後按 ENTER 鍵或按下向下箭頭鍵以隱藏組合框的清單框。 此通知消息在CBN_CLOSEUP消息之前發送,以指示使用者的選擇應被視為有效。 即使未發送CBN_CLOSEUP通知消息(例如,具有CBS_SIMPLE樣式的組合框),也會發送CBN_SELENDCANCEL或CBN_SELENDOK通知消息。

- ON_CBN_KILLFOCUS組合框正在失去輸入焦點。

- ON_CBN_SELCHANGE 組合框的清單框中的選擇將因使用者按一下清單方塊或使用箭頭鍵更改所選內容而更改。 處理此消息時,只能通過`GetLBText`或其他類似函數檢索組合框的編輯控件中的文本。 `GetWindowText`無法使用。

- ON_CBN_SETFOCUS組合框接收輸入焦點。

如果在對話框中創建`CComboBox`物件(通過對話框資源),則當使用者關閉對話方塊`CComboBox`時, 該物件將自動銷毀。

如果將物件嵌入到另`CComboBox`一個視窗物件中,則無需銷毀它。 如果在堆疊上`CComboBox`創建物件,則會自動銷毀該物件。 如果使用新函數在`CComboBox`堆上創建物件,則必須調**new**用 物件**上的 delete**以在銷毀 Windows 組合框時銷毀該物件。

**注意**如果要處理WM_KEYDOWN和WM_CHAR消息,必須對組合框的編輯和列表框控件進行子類,從 派`CEdit`生 類派生`CListBox`類, 並將這些消息的處理程式添加到派生類。 有關詳細資訊,請參閱[CWnd::子類視窗](../../mfc/reference/cwnd-class.md#subclasswindow)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CComboBox`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="ccomboboxaddstring"></a><a name="addstring"></a>CComboBox::添加String

將字串添加到組合框的清單框中。

```
int AddString(LPCTSTR lpszString);
```

### <a name="parameters"></a>參數

*lpszString*<br/>
指向要新增的 null 終止字串。

### <a name="return-value"></a>傳回值

如果返回值大於或等於 0,則它是列表框中字串的零基索引。 如果發生錯誤,返回值CB_ERR;如果沒有足夠的空間來存儲新字串,則返回值CB_ERRSPACE。

### <a name="remarks"></a>備註

如果未使用[CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式建立清單框,則字串將添加到清單的末尾。 否則,字串將插入到清單中,並排序列表。

> [!NOTE]
> Windows`ComboBoxEx`控制項不支援此功能。 有關此控制項的詳細資訊,請參閱 Windows SDK 中的[ComboBoxEx 控制項](/windows/win32/Controls/comboboxex-controls)。

若要將字串插入到清單中的特定位置,請使用[InsertString](#insertstring)成員函數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#3](../../mfc/reference/codesnippet/cpp/ccombobox-class_1.cpp)]

## <a name="ccomboboxccombobox"></a><a name="ccombobox"></a>CComboBox:CComboBox

建構 `CComboBox` 物件。

```
CComboBox();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_2.cpp)]

## <a name="ccomboboxclear"></a><a name="clear"></a>CComboBox:清除

刪除(清除)組合框的編輯控制項中的當前選擇(如果有)。

```
void Clear();
```

### <a name="remarks"></a>備註

要刪除當前選擇並將已刪除的內容放在剪貼簿上,請使用[「剪切](#cut)」成員功能。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#4](../../mfc/reference/codesnippet/cpp/ccombobox-class_3.cpp)]

## <a name="ccomboboxcompareitem"></a><a name="compareitem"></a>CComboBox:比較項目

由框架調用以確定新專案在排序的擁有者繪製組合框的清單框部分的相對位置。

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>參數

*lp比較項目結構*<br/>
指向[比較結構](/windows/win32/api/winuser/ns-winuser-compareitemstruct)的長指標。

### <a name="return-value"></a>傳回值

指示結構中描述的兩個項目的相對`COMPAREITEMSTRUCT`位置。 可以是下列其中任何一個值：

|值|意義|
|-----------|-------------|
|- 1|專案 1 在專案 2 之前排序。|
|0|專案 1 和專案 2 排序相同。|
|1|專案 1 在專案 2 之後排序。|

有關的說明,請參閱[CWnd:OnCompare 專案](../../mfc/reference/cwnd-class.md#oncompareitem)`COMPAREITEMSTRUCT`。

### <a name="remarks"></a>備註

默認情況下,此成員函數不執行任何操作。 如果創建具有LBS_SORT樣式的所有者繪製組合框,則必須重寫此成員函數,以説明框架對添加到清單框的新項進行排序。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#5](../../mfc/reference/codesnippet/cpp/ccombobox-class_4.cpp)]

## <a name="ccomboboxcopy"></a><a name="copy"></a>CComboBox:複製

以CF_TEXT格式將組合框的編輯控制項中的當前選擇(如果有)複製到剪貼簿。

```
void Copy();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#6](../../mfc/reference/codesnippet/cpp/ccombobox-class_5.cpp)]

## <a name="ccomboboxcreate"></a><a name="create"></a>CComboBox:建立

創建組合框並將其附加到`CComboBox`物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定組合框的樣式。 將[組合框樣式](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)的任意組合應用於該框。

*矩形*<br/>
指向組合框的位置和大小。 可以是[RECT](/windows/win32/api/windef/ns-windef-rect)`CRect`結構 或 物件。

*pparentwnd*<br/>
指定的視窗視窗(通常為 。 `CDialog` 它不得為 NULL。

*nID*<br/>
指定組合框的控制 ID。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

分兩步`CComboBox`構造物件。 首先,調用構造函數,然後調用`Create`,這將創建 Windows 組合框並將`CComboBox`其附加到 物件。

執行`Create`時,Windows[WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)會將 WM_NCCREATE、WM_CREATE、WM_NCCALCSIZE 和[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)[WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)[WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)消息發送到組合框。

默認情況下,這些消息`CWnd`由基類中的[OnNcCreate、OnCreate、OnNcCalcsize](../../mfc/reference/cwnd-class.md#onnccreate)和[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)[OnCreate](../../mfc/reference/cwnd-class.md#oncreate)[OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)成員函數處理。 要擴展預設消息處理,從`CComboBox`派生類,向新類添加消息映射,並重寫前面的消息處理程式成員函數。 例如`OnCreate`,重寫以執行新類所需的初始化。

將以下[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)應用於組合框控制元件。 :

- WS_CHILD始終

- WS_VISIBLE 通常

- WS_DISABLED很少

- WS_VSCROLL 新增組合框中列表框垂直捲動

- WS_HSCROLL 新增組合框中列表框的水平捲動

- WS_GROUP元件

- WS_TABSTOP要將組合框包括在制表順序中

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_6.cpp)]

## <a name="ccomboboxcut"></a><a name="cut"></a>CComboBox:切割

刪除(剪切)組合框編輯控制項中的當前選擇(如果有),以CF_TEXT格式將刪除的文本複製到剪貼簿中。

```
void Cut();
```

### <a name="remarks"></a>備註

要刪除當前選擇而不將刪除的文本放在剪貼簿上,請呼叫[「清除](#clear)」成員函數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#7](../../mfc/reference/codesnippet/cpp/ccombobox-class_7.cpp)]

## <a name="ccomboboxdeleteitem"></a><a name="deleteitem"></a>CComboBox::Delete專案

當使用者從擁有者繪製`CComboBox`物件中刪除專案或銷毀組合框時,由框架調用。

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>參數

*lp 刪除項目已移除*<br/>
指向 Windows [DELETEITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-deleteitemstruct)結構的長指標,其中包含有關已刪除項的資訊。 有關此結構的說明,請參閱[CWnd:onDeleteItem。](../../mfc/reference/cwnd-class.md#ondeleteitem)

### <a name="remarks"></a>備註

此函式的預設實作不做任何動作。 根據需要重寫此函數以重繪組合框。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#8](../../mfc/reference/codesnippet/cpp/ccombobox-class_8.cpp)]

## <a name="ccomboboxdeletestring"></a><a name="deletestring"></a>CComboBox::DeleteString

從組合框中刪除位置*nIndex*中的專案。

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定要刪除的字串的索引。

### <a name="return-value"></a>傳回值

如果返回值大於或等於 0,則它是清單中剩餘字串的計數。 如果*nIndex*指定的索引大於清單中的項數,則返回值CB_ERR。

### <a name="remarks"></a>備註

*nIndex*之後的所有項目現在向下移動一個位置。 例如,如果組合框包含兩個項目,刪除第一個項將導致其餘項現在處於第一個位置。 *nIndex*#0 表示第一個位置中的項。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#9](../../mfc/reference/codesnippet/cpp/ccombobox-class_9.cpp)]

## <a name="ccomboboxdir"></a><a name="dir"></a>CComboBox::Dir

將檔案名或驅動器的清單添加到組合框的清單框中。

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>參數

*attr*<br/>
可以是 CFile 中描述的**enle**的任何組合[:取得狀態](../../mfc/reference/cfile-class.md#getstatus)或以下值的任意組合:

- DDL_READWRITE 檔可以從讀取或寫入。

- DDL_READONLY 檔案可以從讀取,但不能寫入。

- DDL_HIDDEN檔是隱藏的,並且不會顯示在目錄清單中。

- DDL_SYSTEM 檔是一個系統檔。

- DDL_DIRECTORY *lpszWildCard*指定的名稱指定一個目錄。

- DDL_ARCHIVE檔已存檔。

- DDL_DRIVES 包括與*lpszWildCard*指定的名稱匹配的所有驅動器。

- DDL_EXCLUSIVE專用標誌。 如果設置了獨佔標誌,則僅列出指定類型的檔。 否則,除了「正常」檔外,還列出指定類型的檔。

*lpsz通配子*<br/>
指向檔規範字串。 字串可以包含通配符(例如 ,*.\*

### <a name="return-value"></a>傳回值

如果返回值大於或等於 0,則它是添加到清單中的姓氏的零基索引。 如果發生錯誤,返回值CB_ERR;如果沒有足夠的空間來存儲新字串,則返回值CB_ERRSPACE。

### <a name="remarks"></a>備註

Windows`ComboBoxEx`控制項不支援此功能。 有關此控制項的詳細資訊,請參閱 Windows SDK 中的[ComboBoxEx 控制項](/windows/win32/Controls/comboboxex-controls)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#10](../../mfc/reference/codesnippet/cpp/ccombobox-class_10.cpp)]

## <a name="ccomboboxdrawitem"></a><a name="drawitem"></a>CComboBox::D原始專案

當所有者繪製組合框的可視方面發生更改時,由框架調用。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>參數

*lpDraw 專案已結*<br/>
指向[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)結構的指標,其中包含有關所需繪圖類型的資訊。

### <a name="remarks"></a>備註

`DRAWITEMSTRUCT`結構`itemAction`的成員定義要執行的繪圖操作。 有關此結構的說明,請參閱[CWnd:onDrawItem。](../../mfc/reference/cwnd-class.md#ondrawitem)

默認情況下,此成員函數不執行任何操作。 重寫此成員函數以擁有擁有者繪製物件的繪圖`CComboBox`。 在此成員函數終止之前,應用程式應還原為*lpDrawItemStruct*中提供的顯示上下文選擇的所有圖形設備介面 (GDI) 物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#11](../../mfc/reference/codesnippet/cpp/ccombobox-class_11.cpp)]

## <a name="ccomboboxfindstring"></a><a name="findstring"></a>CComboBox::尋找字串

尋找但不選擇在組合框的清單框中包含指定首碼的第一個字串。

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszString) const;
```

### <a name="parameters"></a>參數

*N 開始後*<br/>
包含要搜索的第一個項之前項的零基索引。 當搜索到達清單框的底部時,它將從列表框的頂部繼續到*nStartAfter*指定的項。 如果為 -1,則從一開始就搜索整個列表框。

*lpszString*<br/>
包含要搜尋的前置字串。 搜尋是獨立於大小寫,因此此字串可以包含大寫字母和小寫字母的任意組合。

### <a name="return-value"></a>傳回值

如果返回值大於或等於 0,則它是匹配項的零基索引。 如果搜索不成功,則CB_ERR。

### <a name="remarks"></a>備註

Windows`ComboBoxEx`控制項不支援此功能。 有關此控制項的詳細資訊,請參閱 Windows SDK 中的[ComboBoxEx 控制項](/windows/win32/Controls/comboboxex-controls)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#12](../../mfc/reference/codesnippet/cpp/ccombobox-class_12.cpp)]

## <a name="ccomboboxfindstringexact"></a><a name="findstringexact"></a>CComboBox::尋找字串精確

調用`FindStringExact`成員函數尋找與*lpszFind*中指定的字串匹配的第一個清單框字串(在組合框中)。

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>參數

*nIndex 開始*<br/>
指定要搜索的第一個項之前項的零基索引。 當搜索到達清單框的底部時,它將從列表框的頂部繼續到*nIndexStart*指定的項。 如果*nIndexStart*為 -1,則從一開始就搜索整個列表框。

*lpszFind*<br/>
指向要搜尋的 null 終止字串。 此字串可以包含完整的檔名,包括副檔名。 搜尋不區分大小寫,因此此字串可以包含大寫字母和小寫字母的任意組合。

### <a name="return-value"></a>傳回值

匹配項的零基索引,如果搜索不成功,CB_ERR。

### <a name="remarks"></a>備註

如果組合框創建具有擁有者繪製樣式,但沒有[CBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣`FindStringExact`式, 則嘗試將雙字值與*lpszFind*的值匹配。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#13](../../mfc/reference/codesnippet/cpp/ccombobox-class_13.cpp)]

## <a name="ccomboboxgetcomboboxinfo"></a><a name="getcomboboxinfo"></a>CComboBox:取得ComboBox資訊

檢索`CComboBox`物件的資訊。

```
BOOL GetComboBoxInfo(PCOMBOBOXINFO pcbi) const;
```

### <a name="parameters"></a>參數

*多吉*<br/>
指向[COMBOBOXINFO](/windows/win32/api/winuser/ns-winuser-comboboxinfo)結構的指標。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

此成員函數類比[CB_GETCOMBOBOXINFO](/windows/win32/Controls/cb-getcomboboxinfo)消息的功能,如 Windows SDK 中所述。

## <a name="ccomboboxgetcount"></a><a name="getcount"></a>CComboBox:取得計數

呼叫此成員函數以檢索組合框列表框部分中的項目數。

```
int GetCount() const;
```

### <a name="return-value"></a>傳回值

項目數。 返回的計數大於最後一個項的索引值(索引為零)。 如果發生錯誤,CB_ERR。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#14](../../mfc/reference/codesnippet/cpp/ccombobox-class_14.cpp)]

## <a name="ccomboboxgetcuebanner"></a><a name="getcuebanner"></a>CComboBox:GetCueBanner

獲取為組合框控制器顯示的提示文本。

```
CString GetCueBanner() const;

BOOL GetCueBanner(
    LPTSTR lpszText,
    int cchText) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*lpszText*|[出]指向接收提示橫幅文本的緩衝區的指標。|
|*cchText*|[在]*lpszText*參數指向的緩衝區的大小。|

### <a name="return-value"></a>傳回值

在第一個重載中,包含提示橫幅文本的[CString](../../atl-mfc-shared/using-cstring.md)物件(如果存在);否則,長度`CString`為零的物件。

-或-

在第二個重載中,如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

提示文字是顯示在組合框控制項的輸入區域中的提示。 提示文本顯示,直到使用者提供輸入。

此方法發送[CB_GETCUEBANNER](/windows/win32/Controls/cb-getcuebanner)訊息,這在 Windows SDK 中介紹。

## <a name="ccomboboxgetcursel"></a><a name="getcursel"></a>CComboBox:取得CurSel

調用此成員函數以確定選擇了組合框中的哪個項。

```
int GetCurSel() const;
```

### <a name="return-value"></a>傳回值

組合框清單框中當前選定項的零索引,如果未選擇任何項,則CB_ERR。

### <a name="remarks"></a>備註

`GetCurSel`將索引返回到清單中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#15](../../mfc/reference/codesnippet/cpp/ccombobox-class_15.cpp)]

## <a name="ccomboboxgetdroppedcontrolrect"></a><a name="getdroppedcontrolrect"></a>CComboBox:取得已放棄控制

調用`GetDroppedControlRect`成員函數以檢索下拉組合框的可見(下拉)列表框的螢幕座標。

```
void GetDroppedControlRect(LPRECT lprect) const;
```

### <a name="parameters"></a>參數

*lprect*<br/>
收送座標的[RECT 結構](/windows/win32/api/windef/ns-windef-rect)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#16](../../mfc/reference/codesnippet/cpp/ccombobox-class_16.cpp)]

## <a name="ccomboboxgetdroppedstate"></a><a name="getdroppedstate"></a>CComboBox:抓取放棄狀態

呼叫`GetDroppedState`成員函數以確定下拉組合框的清單框是否可見(下拉)。

```
BOOL GetDroppedState() const;
```

### <a name="return-value"></a>傳回值

如果列表框可見,則非零;否則 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#17](../../mfc/reference/codesnippet/cpp/ccombobox-class_17.cpp)]

## <a name="ccomboboxgetdroppedwidth"></a><a name="getdroppedwidth"></a>CComboBox:取得刪除寬度

呼叫此函數以檢索組合框列表框的最小允許寬度(以像素為單位)。

```
int GetDroppedWidth() const;
```

### <a name="return-value"></a>傳回值

如果成功,最小允許寬度(以像素為單位);否則,CB_ERR。

### <a name="remarks"></a>備註

此功能僅適用於具有[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式的組合框。

默認情況下,下拉清單框的最小允許寬度為 0。 最小允許寬度可以通過調用[SetDroppedWidth](#setdroppedwidth)來設置。 顯示組合框的清單框部分時,其寬度是最小允許寬度或組合框寬度的較大部分。

### <a name="example"></a>範例

  請參閱[「設置放棄寬度」](#setdroppedwidth)的範例。

## <a name="ccomboboxgeteditsel"></a><a name="geteditsel"></a>CComboBox:取得編輯塞爾

在組合框的編輯控制項中獲取當前選擇的起始和結束字元位置。

```
DWORD GetEditSel() const;
```

### <a name="return-value"></a>傳回值

包含低階單詞中的起始位置和高階單詞中所選內容結束後第一個未選擇字元的位置的 32 位值。 如果在沒有編輯控制件的組合框中使用此函數,則返回CB_ERR。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#18](../../mfc/reference/codesnippet/cpp/ccombobox-class_18.cpp)]

## <a name="ccomboboxgetextendedui"></a><a name="getextendedui"></a>CComboBox:取得擴充 UI

調用`GetExtendedUI`成員函數以確定組合框是否具有默認使用者介面或擴展的用戶介面。

```
BOOL GetExtendedUI() const;
```

### <a name="return-value"></a>傳回值

如果組合框具有擴展的用戶介面,則非零;否則 0。

### <a name="remarks"></a>備註

擴充的使用者介面可透過以下方式進行識別碼 :

- 按下靜態控制項僅顯示具有[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式的組合框的清單框。

- 按下「向下箭頭」鍵將顯示列表框(已禁用 F4)。

當專案清單不可見時,將禁用靜態控件中的滾動(禁用箭頭鍵)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#19](../../mfc/reference/codesnippet/cpp/ccombobox-class_19.cpp)]

## <a name="ccomboboxgethorizontalextent"></a><a name="gethorizontalextent"></a>CComboBox:取得橫向範圍

從組合框檢索可水準滾動組合框列表框部分的寬度(以像素為單位)。

```
UINT GetHorizontalExtent() const;
```

### <a name="return-value"></a>傳回值

組合框清單框部分的可滾動寬度(以像素為單位)。

### <a name="remarks"></a>備註

僅當組合框的清單框部分具有水平滾動條時,才適用此選項。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#20](../../mfc/reference/codesnippet/cpp/ccombobox-class_20.cpp)]

## <a name="ccomboboxgetitemdata"></a><a name="getitemdata"></a>CComboBox:抓取項目資料

檢索與指定的組合框項關聯的應用程式提供的 32 位值。

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
在組合框的清單框中包含項的零基索引。

### <a name="return-value"></a>傳回值

與項關聯的 32 位值,如果發生錯誤,CB_ERR。

### <a name="remarks"></a>備註

32 位值可以使用[SetItemData](#setitemdata)成員函數調用的*dwItemData*參數進行設置。 如果要檢索`GetItemDataPtr`的 32 位值是指針 **(void),**<strong>\*</strong>請使用成員函數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#21](../../mfc/reference/codesnippet/cpp/ccombobox-class_21.cpp)]

## <a name="ccomboboxgetitemdataptr"></a><a name="getitemdataptr"></a>CComboBox:抓取項目資料Ptr

檢索與指定群組框項目關聯的應用程式提供的 32 位值作為指標(**空**<strong>\*</strong>)。

```
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
在組合框的清單框中包含項的零基索引。

### <a name="return-value"></a>傳回值

如果發生錯誤,則檢索指標,或 -1。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#22](../../mfc/reference/codesnippet/cpp/ccombobox-class_22.cpp)]

## <a name="ccomboboxgetitemheight"></a><a name="getitemheight"></a>CComboBox:取得專案高度

調用`GetItemHeight`成員函數以檢索組合框中列表項的高度。

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定要檢索其高度的組合框的元件。 如果*nIndex*參數為 -1,則檢索組合框的編輯控制(或靜態文字)部分的高度。 如果組合框具有[CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式 *,nIndex*指定要檢索其高度的清單項的零基索引。 否則 *,nIndex*應設置為 0。

### <a name="return-value"></a>傳回值

組合框中指定專案的高度(以像素為單位)。 如果發生錯誤，傳回值是 CB_ERR。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#23](../../mfc/reference/codesnippet/cpp/ccombobox-class_23.cpp)]

## <a name="ccomboboxgetlbtext"></a><a name="getlbtext"></a>CComboBox:取得LBText

從組合框的清單框中獲取字串。

```
int GetLBText(
    int nIndex,
    LPTSTR lpszText) const;

void GetLBText(
    int nIndex,
    CString& rString) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
包含要複製的清單框字串的零基索引。

*lpszText*<br/>
指向要接收字串的緩衝區。 緩衝區必須有足夠的空間用於字串和終止空字元。

*rString*<br/>
對 `CString` 的參考。

### <a name="return-value"></a>傳回值

字串的長度(以位元組為單位),不包括終止空字元。 如果*nIndex*未指定有效的索引,則返回值將CB_ERR。

### <a name="remarks"></a>備註

此成員函數的第二種形式使用項的文本填充`CString`物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#24](../../mfc/reference/codesnippet/cpp/ccombobox-class_24.cpp)]

## <a name="ccomboboxgetlbtextlen"></a><a name="getlbtextlen"></a>CComboBox:取得LBTextLen

取得組合框清單框中字串的長度。

```
int GetLBTextLen(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
包含清單框字串的零基索引。

### <a name="return-value"></a>傳回值

字串的長度(以位元組為單位),不包括終止空字元。 如果*nIndex*未指定有效的索引,則返回值將CB_ERR。

### <a name="example"></a>範例

  請參考[CComboBox 的範例:取得 LBText](#getlbtext)。

## <a name="ccomboboxgetlocale"></a><a name="getlocale"></a>CComboBox:抓取本地化

檢索組合框使用區域設置。

```
LCID GetLocale() const;
```

### <a name="return-value"></a>傳回值

組合框中字串區域設置標識符 (LCID) 值。

### <a name="remarks"></a>備註

例如,區域設置用於確定排序組合框中字串的排序順序。

### <a name="example"></a>範例

  請參考[CComboBox 的範例::設定區域設定](#setlocale)。

## <a name="ccomboboxgetminvisible"></a><a name="getminvisible"></a>CComboBox:取得可見

取得目前組合框控制元件的下拉清單中的最小可見項數。

```
int GetMinVisible() const;
```

### <a name="return-value"></a>傳回值

當前下拉清單中的可見項的最小數量。

### <a name="remarks"></a>備註

此方法發送[CB_GETMINVISIBLE](/windows/win32/Controls/cb-setminvisible)訊息,這在 Windows SDK 中介紹。

## <a name="ccomboboxgettopindex"></a><a name="gettopindex"></a>CComboBox:取得TopIndex

檢索組合框清單框部分中第一個可見項的零基索引。

```
int GetTopIndex() const;
```

### <a name="return-value"></a>傳回值

如果成功,組合框清單框部分中第一個可見項的零基索引(如果成功)CB_ERR否則。

### <a name="remarks"></a>備註

最初,專案 0 位於清單框的頂部,但如果滾動清單框,則另一項可能位於頂部。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#25](../../mfc/reference/codesnippet/cpp/ccombobox-class_25.cpp)]

## <a name="ccomboboxinitstorage"></a><a name="initstorage"></a>CComboBox::在內存儲

分配記憶體以將清單框項存儲在組合框的列表框部分。

```
int InitStorage(
    int nItems,
    UINT nBytes);
```

### <a name="parameters"></a>參數

*n 專案*<br/>
指定要添加的項目。

*n 位元組*<br/>
指定要為項字串分配的記憶體量(以位元組為單位)。

### <a name="return-value"></a>傳回值

如果成功,則組合框的列表框部分在需要重新分配記憶體之前可以存儲的最大項數,否則CB_ERRSPACE,這意味著記憶體不足。

### <a name="remarks"></a>備註

將大量項目新增到的清單盒部份之前,請呼叫此函數`CComboBox`。

僅限 Windows 95/98:wParam 參數限制為 16 位值。 *wParam* 這意味著清單框不能包含超過 32,767 個專案。 儘管專案數受到限制,但列表框中專案的總大小僅受可用記憶體的限制。

此功能有助於加快初始化具有大量項(超過 100 個)的清單框。 它預分配指定的記憶體量,以便後續[的 AddString、InsertString](#addstring)和[Dir](#dir)函數花費[InsertString](#insertstring)盡可能短的時間。 您可以使用參數的估計值。 如果高估,將分配一些額外的記憶體;如果估計過高,則分配一些額外的記憶體。如果低估,則正常分配用於超過預分配金額的物料。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#26](../../mfc/reference/codesnippet/cpp/ccombobox-class_26.cpp)]

## <a name="ccomboboxinsertstring"></a><a name="insertstring"></a>CComboBox:插入字串

將字串插入下拉式方塊的清單方塊中。

```
int InsertString(
    int nIndex,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
包含要接收字串之清單方塊中位置以零為基底的索引。 如果此參數為 -1,則字串將添加到清單的末尾。

*lpszString*<br/>
指向要插入的 null 結尾字串。

### <a name="return-value"></a>傳回值

已插入字串之位置以零為基底的索引。 如果發生錯誤，傳回值是 CB_ERR。 如果空間不足，無法存放新的字串，傳回值是 CB_ERRSPACE。

### <a name="remarks"></a>備註

不像 [AddString](#addstring) 成員函式， `InsertString` 成員函式不會排序 [CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 樣式的清單。

> [!NOTE]
> Windows`ComboBoxEx`控制項不支援此功能。 有關此控制項的詳細資訊,請參閱 Windows SDK 中的[ComboBoxEx 控制項](/windows/win32/Controls/comboboxex-controls)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#27](../../mfc/reference/codesnippet/cpp/ccombobox-class_27.cpp)]

## <a name="ccomboboxlimittext"></a><a name="limittext"></a>CComboBox:限制文字

限制用戶可以輸入到組合框的編輯控制項中的文字長度( 以位元組為單位)。

```
BOOL LimitText(int nMaxChars);
```

### <a name="parameters"></a>參數

*nMaxChars*<br/>
指定使用者可以輸入的文本的長度(以位元組為單位)。 如果此參數為 0,則文本長度設置為 65,535 位元組。

### <a name="return-value"></a>傳回值

如果成功,則為非零。 如果調用具有樣式[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)組合框或沒有編輯控制項的組合框,則返回值CB_ERR。

### <a name="remarks"></a>備註

如果組合框沒有[樣式CBS_AUTOHSCROLL,](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)則將文本限制設置為大於編輯控制項的大小將不起作用。

`LimitText`僅限制使用者可以輸入的文本。 它在發送郵件時對編輯控制項中已有的任何文本沒有影響,也不會影響在選擇清單框中的字串時複製到編輯控制項的文本的長度。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#28](../../mfc/reference/codesnippet/cpp/ccombobox-class_28.cpp)]

## <a name="ccomboboxmeasureitem"></a><a name="measureitem"></a>CComboBox:測量專案

創建具有擁有者繪製樣式的組合框時,由框架調用。

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>參數

*lp 測量項目結構*<br/>
指向[測量結構](/windows/win32/api/winuser/ns-winuser-measureitemstruct)的長指標。

### <a name="remarks"></a>備註

默認情況下,此成員函數不執行任何操作。 覆蓋此成員函數並填充`MEASUREITEMSTRUCT`結構,以通知 Windows 組合框中列表框的尺寸。 如果組合框使用[CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式創建,則框架將針對清單框中的每個專案調用此成員函數。 否則,僅調用此成員一次。

使用與[SubclassDlgItem](../../mfc/reference/cwnd-class.md#subclassdlgitem)成員函數創建的所有者繪製組合框中的CBS_OWNERDRAWFIXED`CWnd`樣式 涉及進一步的程式設計注意事項。 請參閱[技術說明 14](../../mfc/tn014-custom-controls.md)中的討論。

有關`MEASUREITEMSTRUCT`結構的說明,請參閱[CWnd:onMeasureItem。](../../mfc/reference/cwnd-class.md#onmeasureitem)

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#29](../../mfc/reference/codesnippet/cpp/ccombobox-class_29.cpp)]

## <a name="ccomboboxpaste"></a><a name="paste"></a>CComboBox::Paste

將剪貼簿中的數據插入到當前游標位置組合框的編輯控制項中。

```
void Paste();
```

### <a name="remarks"></a>備註

僅當剪貼簿以CF_TEXT格式包含數據時,才會插入數據。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#30](../../mfc/reference/codesnippet/cpp/ccombobox-class_30.cpp)]

## <a name="ccomboboxresetcontent"></a><a name="resetcontent"></a>CComboBox:重置內容

從清單框中移除所有專案,並編輯組合框控制項。

```
void ResetContent();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#31](../../mfc/reference/codesnippet/cpp/ccombobox-class_31.cpp)]

## <a name="ccomboboxselectstring"></a><a name="selectstring"></a>CComboBox:選擇字串

在組合框的清單框中搜索字串,如果找到該字串,則選擇清單框中的字串並將其複製到編輯控制件。

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>參數

*N 開始後*<br/>
包含要搜索的第一個項之前項的零基索引。 當搜索到達清單框的底部時,它將從列表框的頂部繼續到*nStartAfter*指定的項。 如果為 -1,則從一開始就搜索整個列表框。

*lpszString*<br/>
包含要搜尋的前置字串。 搜尋是獨立於大小寫,因此此字串可以包含大寫字母和小寫字母的任意組合。

### <a name="return-value"></a>傳回值

如果找到字串,則所選項的零基索引。 如果搜索不成功,則返回值CB_ERR,並且當前選擇不會更改。

### <a name="remarks"></a>備註

僅當字串的初始字元(從起始點)與首碼字串中的字元匹配時,才會選擇字串。

請注意,`SelectString``FindString`與成員函數都找到字串,`SelectString`但成員函數也選擇字串。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#32](../../mfc/reference/codesnippet/cpp/ccombobox-class_32.cpp)]

## <a name="ccomboboxsetcuebanner"></a><a name="setcuebanner"></a>CComboBox::SetCueBanner

設定為組合框控制器顯示的提示文本。

```
BOOL SetCueBanner(LPCTSTR lpszText);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*lpszText*|[在]指向包含提示文字的 null 連接器接緩衝區的指標。|

### <a name="return-value"></a>傳回值

如果方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

提示文字是顯示在組合框控制項的輸入區域中的提示。 提示文本顯示,直到使用者提供輸入。

此方法發送[CB_SETCUEBANNER](/windows/win32/Controls/cb-setcuebanner)消息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

以下代碼範例定義用於以程式設計方式存取組合框控制元件的變數*m_combobox*。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>範例

以下代碼示例設置組合框控制件的提示橫幅。

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

## <a name="ccomboboxsetcursel"></a><a name="setcursel"></a>CComboBox::SetCurSel

在組合框的清單框中選擇字串。

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>參數

*n 選擇*<br/>
指定要選擇的字串的零基索引。 如果 -1,則刪除清單框中的任何當前選擇並清除編輯控制項。

### <a name="return-value"></a>傳回值

如果消息成功,則選擇的項的零基索引。 如果*nSelect*大於清單中的項數,或者*nSelect*設置為 -1(清除所選內容),則返回值為 CB_ERR。

### <a name="remarks"></a>備註

如有必要,清單框將字串滾動到檢視中(如果列表框可見)。 組合框的編輯控制件中的文本將更改為反映新選擇。 刪除清單框中的任何以前的選擇。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#33](../../mfc/reference/codesnippet/cpp/ccombobox-class_35.cpp)]

## <a name="ccomboboxsetdroppedwidth"></a><a name="setdroppedwidth"></a>CComboBox::設置丟棄寬度

呼叫此函數可設定組合框列表框的最小允許寬度(以像素為單位)。

```
int SetDroppedWidth(UINT nWidth);
```

### <a name="parameters"></a>參數

*n 寬度*<br/>
組合框清單框部分的最小允許寬度(以像素為單位)。

### <a name="return-value"></a>傳回值

如果成功,則列表框的新寬度,否則CB_ERR。

### <a name="remarks"></a>備註

此功能僅適用於具有[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式的組合框。

默認情況下,下拉清單框的最小允許寬度為 0。 顯示組合框的清單框部分時,其寬度是最小允許寬度或組合框寬度的較大部分。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#34](../../mfc/reference/codesnippet/cpp/ccombobox-class_36.cpp)]

## <a name="ccomboboxseteditsel"></a><a name="seteditsel"></a>CComboBox:設定編輯塞爾

選擇組合框的編輯控制項中的字元。

```
BOOL SetEditSel(
    int nStartChar,
    int nEndChar);
```

### <a name="parameters"></a>參數

*nStartChar*<br/>
指定起始位置。 如果起始位置設置為 -1,則刪除任何現有選擇。

*nEndChar*<br/>
指定結束位置。 如果結束位置設置為 -1,則選擇從起始位置到編輯控制項中最後一個字元的所有文本。

### <a name="return-value"></a>傳回值

如果成員函數成功,則非零;否則 0。 如果`CComboBox`[CBS_DROPDOWNLIST樣式或](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)沒有清單框,則CB_ERR。

### <a name="remarks"></a>備註

倉位為零。 要選擇編輯控制件的第一個字元,請指定起始位置為 0。 結束位置是在最後一個字元之後。 例如,要選擇編輯控制件的前四個字元,請使用起始位置 0 和結束位置 4。

> [!NOTE]
> Windows`ComboBoxEx`控制項不支援此功能。 有關此控制項的詳細資訊,請參閱 Windows SDK 中的[ComboBoxEx 控制項](/windows/win32/Controls/comboboxex-controls)。

### <a name="example"></a>範例

  請參考[CComboBox 的範例::取得編輯塞爾](#geteditsel)。

## <a name="ccomboboxsetextendedui"></a><a name="setextendedui"></a>CComboBox::設定擴充UI

呼叫`SetExtendedUI`成員函數,為具有[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式的組合框選擇默認使用者介面或擴展使用者介面。

```
int SetExtendedUI(BOOL bExtended = TRUE);
```

### <a name="parameters"></a>參數

*b 延伸*<br/>
指定組合框應使用擴展的使用者介面還是默認用戶介面。 TRUE 的值選擇擴展的用戶介面;FALSE 的值選擇標準用戶介面。

### <a name="return-value"></a>傳回值

如果操作成功,CB_OKAY,如果發生錯誤,則CB_ERR。

### <a name="remarks"></a>備註

擴充的使用者介面可透過以下方式進行識別碼 :

- 按一下靜態控制項僅顯示具有CBS_DROPDOWNLIST樣式的組合框的清單框。

- 按下「向下箭頭」鍵將顯示列表框(已禁用 F4)。

當項目清單不可見(箭頭鍵被禁用)時,將禁用靜態控件中的滾動。

### <a name="example"></a>範例

  請參考[CComboBox 的範例:取得延伸 UI](#getextendedui)。

## <a name="ccomboboxsethorizontalextent"></a><a name="sethorizontalextent"></a>CComboBox::設定水平範圍

設置以像素為單位的寬度,通過該寬度可以水準滾動組合框的列表框部分。

```
void SetHorizontalExtent(UINT nExtent);
```

### <a name="parameters"></a>參數

*n 範圍*<br/>
指定可以水平滾動組合框的列表框部分的像素數。

### <a name="remarks"></a>備註

如果清單框的寬度小於此值,則水準滾動條將水準滾動清單框中的專案。 如果清單框的寬度等於或大於此值,則水準滾動條將隱藏,或者如果組合框具有[CBS_DISABLENOSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式,則禁用。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#35](../../mfc/reference/codesnippet/cpp/ccombobox-class_37.cpp)]

## <a name="ccomboboxsetitemdata"></a><a name="setitemdata"></a>CComboBox::設定項目資料

在組合框中設置與指定項關聯的 32 位值。

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
包含要設置的項的零基索引。

*dwItemData*<br/>
包含要與項關聯的新值。

### <a name="return-value"></a>傳回值

如果發生錯誤,CB_ERR。

### <a name="remarks"></a>備註

如果`SetItemDataPtr`32 位項為指標,請使用成員函數。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#36](../../mfc/reference/codesnippet/cpp/ccombobox-class_38.cpp)]

## <a name="ccomboboxsetitemdataptr"></a><a name="setitemdataptr"></a>CComboBox::設定項目資料Ptr

將組合框中與指定項關聯的 32 位值設置為指定的指標 **(void)。** <strong>\*</strong>

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
包含項的零索引。

*pData*<br/>
包含要與項關聯的指標。

### <a name="return-value"></a>傳回值

如果發生錯誤,CB_ERR。

### <a name="remarks"></a>備註

此指標在組合框的生命週期內仍然有效,即使專案在組合框中的相對位置可能會隨著專案添加或刪除而改變。 因此,框中的項索引可以更改,但指標保持可靠。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#37](../../mfc/reference/codesnippet/cpp/ccombobox-class_39.cpp)]

## <a name="ccomboboxsetitemheight"></a><a name="setitemheight"></a>CComboBox::設定專案高度

呼叫`SetItemHeight`成員函數以設定組合框中列表項目的高度或組合框的編輯控制(或靜態文字)部分的高度。

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定是設定清單項目的高度還是組合框的編輯控制(或靜態文字)部分的高度。

如果組合框具有CBS_OWNERDRAWVARIABLE樣式 *,nIndex*指定要設置其高度的清單項的零基索引;如果組合框具有[CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式,則指定要設置其高度的列表項的零基索引。否則 *,nIndex*必須為 0,並將設置所有清單項的高度。

如果*nIndex*為 -1,則要設置組合框的編輯控制或靜態文本部分的高度。

*cyItemHeight*<br/>
指定*nIndex*識別的組合框元件的高度(以像素為單位)。

### <a name="return-value"></a>傳回值

如果索引或高度無效,CB_ERR;否則 0。

### <a name="remarks"></a>備註

組合框的編輯控制(或靜態文字)部分的高度設置獨立於清單項的高度。 應用程式必須確保編輯控制件(或靜態文本)部分的高度不小於特定清單框項的高度。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#38](../../mfc/reference/codesnippet/cpp/ccombobox-class_40.cpp)]

## <a name="ccomboboxsetlocale"></a><a name="setlocale"></a>CComboBox::設定本地端

設定此組合框的區域設置標識符。

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>參數

*n 新地*<br/>
要為組合框設置的新區域設置標識符 (LCID) 值。

### <a name="return-value"></a>傳回值

此組合框的上一個區域設置標識符 (LCID) 值。

### <a name="remarks"></a>備註

如果未`SetLocale`調用,則從系統獲取預設區域設置。 此系統預設區域設置可以使用控制面板的區域(或國際)應用程式進行修改。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#39](../../mfc/reference/codesnippet/cpp/ccombobox-class_41.cpp)]

## <a name="ccomboboxsetminvisibleitems"></a><a name="setminvisibleitems"></a>CComboBox:設定明目數專案

設定當前組合框控制件的下拉清單中的最小可見項數。

```
BOOL SetMinVisibleItems(int iMinVisible);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*iMin 可見*|[在]指定可見項的最小數量。|

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法發送[CB_SETMINVISIBLE](/windows/win32/Controls/cb-setminvisible)消息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

以下代碼範例定義用於以程式設計方式存取組合框控制元件的變數*m_combobox*。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>範例

以下代碼示例將 20 個專案插入到組合框控制項的下拉清單中。 然後,它指定當使用者按下下拉箭頭時,至少顯示 10 個專案。

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

## <a name="ccomboboxsettopindex"></a><a name="settopindex"></a>CComboBox::SetTopIndex

確保特定專案在組合框的清單框部分中可見。

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定清單框項的零基索引。

### <a name="return-value"></a>傳回值

如果成功,則為零,如果發生錯誤,則CB_ERR。

### <a name="remarks"></a>備註

系統滾動清單框,直到*nIndex*指定的項顯示在列表框的頂部或已達到最大滾動範圍。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#40](../../mfc/reference/codesnippet/cpp/ccombobox-class_42.cpp)]

## <a name="ccomboboxshowdropdown"></a><a name="showdropdown"></a>CComboBox::顯示下拉

顯示或隱藏具有[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式的組合框的清單框。

```
void ShowDropDown(BOOL bShowIt = TRUE);
```

### <a name="parameters"></a>參數

*b 顯示它*<br/>
指定下拉清單框是顯示還是隱藏。 "TRUE"值顯示列表框。 FALSE 的值將隱藏清單框。

### <a name="remarks"></a>備註

預設情況下,此樣式的組合框將顯示列表框。

此成員函數對使用[CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式創建的組合框沒有影響。

### <a name="example"></a>範例

  請參考[CComboBox 的範例:抓取放棄狀態](#getdroppedstate)。

## <a name="see-also"></a>另請參閱

[MFC 樣品 CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[CButton 類別](../../mfc/reference/cbutton-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CListBox 類別](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar 類別](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic 類別](../../mfc/reference/cstatic-class.md)<br/>
[CDialog 類別](../../mfc/reference/cdialog-class.md)
