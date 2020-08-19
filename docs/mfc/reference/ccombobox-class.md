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
ms.openlocfilehash: 79bcb973046c418f0bea148084da239075414790
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561670"
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
|[CComboBox：： CComboBox](#ccombobox)|建構 `CComboBox` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CComboBox::AddString](#addstring)|將字串加入下拉式方塊清單方塊中清單的結尾，或在清單方塊的排序位置（具有 CBS_SORT 樣式）。|
|[CComboBox：： Clear](#clear)|刪除 (會在編輯控制項中清除) 目前的選取專案（如果有的話）。|
|[CComboBox：： CompareItem](#compareitem)|由架構呼叫，以判斷新清單專案在 [已排序的擁有者] 下拉式方塊中的相對位置。|
|[CComboBox：： Copy](#copy)|將目前的選取專案（如果有的話）複製到剪貼簿上的 CF_TEXT 格式。|
|[CComboBox：： Create](#create)|建立下拉式方塊，並將其附加至 `CComboBox` 物件。|
|[CComboBox：：剪下](#cut)|刪除 (剪下) 編輯控制項中目前的選取範圍（如果有的話），並將已刪除的文字複製到剪貼簿的 CF_TEXT 格式。|
|[CComboBox：:D eleteItem](#deleteitem)|從主控描繪下拉式方塊刪除清單專案時，由架構呼叫。|
|[CComboBox：:D eleteString](#deletestring)|從下拉式方塊的清單方塊中刪除字串。|
|[CComboBox：:D ir](#dir)|將檔案名清單新增至下拉式方塊的清單方塊。|
|[CComboBox：:D rawItem](#drawitem)|當主控描繪下拉式方塊的視覺外觀變更時，由架構呼叫。|
|[CComboBox：： FindString](#findstring)|在下拉式方塊的清單方塊中，尋找包含指定前置詞的第一個字串。|
|[CComboBox：： FindStringExact](#findstringexact)|在下拉式方塊中尋找符合指定字串的第一個清單方塊字串 () 。|
|[CComboBox：： GetComboBoxInfo](#getcomboboxinfo)|抓取物件的相關資訊 `CComboBox` 。|
|[CComboBox：： GetCount](#getcount)|抓取下拉式方塊清單方塊中的專案數。|
|[CComboBox：： GetCueBanner](#getcuebanner)|取得為下拉式方塊控制項顯示的提示文字。|
|[CComboBox：： GetCurSel](#getcursel)|在下拉式方塊的清單方塊中，抓取目前選取專案的索引（如果有的話）。|
|[CComboBox：： GetDroppedControlRect](#getdroppedcontrolrect)|抓取下拉式方塊中，) 清單方塊的可見 (的螢幕座標。|
|[CComboBox：： GetDroppedState](#getdroppedstate)|決定下拉式方塊的清單方塊是否可顯示 () ] 下拉式清單方塊。|
|[CComboBox：： GetDroppedWidth](#getdroppedwidth)|抓取下拉式方塊中下拉式清單方塊部分的允許寬度下限。|
|[CComboBox：： GetEditSel](#geteditsel)|取得下拉式方塊的編輯控制項中目前選取範圍的開始和結束字元位置。|
|[CComboBox：： GetExtendedUI](#getextendedui)|決定下拉式方塊是否有預設使用者介面或擴充的使用者介面。|
|[CComboBox：： GetHorizontalExtent](#gethorizontalextent)|傳回以圖元為單位的寬度（以圖元為單位），可水準滾動下拉式方塊的清單方塊部分。|
|[CComboBox：： GetItemData](#getitemdata)|抓取與指定的下拉式方塊專案相關聯之應用程式提供的32位值。|
|[CComboBox：： GetItemDataPtr](#getitemdataptr)|抓取與指定的下拉式方塊專案相關聯之應用程式提供的32位指標。|
|[CComboBox：： GetItemHeight](#getitemheight)|抓取下拉式方塊中清單專案的高度。|
|[CComboBox：： GetLBText](#getlbtext)|從下拉式方塊的清單方塊中取得字串。|
|[CComboBox：： GetLBTextLen](#getlbtextlen)|取得下拉式方塊清單方塊中字串的長度。|
|[CComboBox：： GetLocale](#getlocale)|抓取下拉式方塊的地區設定識別碼。|
|[CComboBox：： GetMinVisible](#getminvisible)|取得目前下拉式方塊的下拉式清單中可見專案的最小數目。|
|[CComboBox：： GetTopIndex](#gettopindex)|傳回下拉式方塊的清單方塊部分中，第一個可見專案的索引。|
|[CComboBox：： InitStorage](#initstorage)|會預先配置下拉式方塊的清單方塊部分中，專案和字串的記憶體區塊。|
|[CComboBox::InsertString](#insertstring)|將字串插入下拉式方塊的清單方塊中。|
|[CComboBox：： LimitText](#limittext)|限制使用者可在下拉式方塊的編輯控制項中輸入的文字長度。|
|[CComboBox：： MeasureItem](#measureitem)|建立主控描繪的下拉式方塊時，由架構呼叫以決定下拉式列示方塊的維度。|
|[CComboBox：:P aste](#paste)|將剪貼簿中的資料插入至目前游標位置的編輯控制項。 只有當剪貼簿包含 CF_TEXT 格式的資料時，才會插入資料。|
|[CComboBox：： ResetContent](#resetcontent)|從清單方塊中移除所有專案，並編輯下拉式方塊的控制項。|
|[CComboBox：： SelectString](#selectstring)|在下拉式方塊的清單方塊中搜尋字串，如果找到該字串，則選取清單方塊中的字串，並將字串複製到編輯控制項。|
|[CComboBox：： SetCueBanner](#setcuebanner)|設定為下拉式方塊控制項顯示的提示文字。|
|[CComboBox：： SetCurSel](#setcursel)|在下拉式方塊的清單方塊中選取字串。|
|[CComboBox：： SetDroppedWidth](#setdroppedwidth)|設定下拉式方塊中下拉式清單方塊部分的允許寬度下限。|
|[CComboBox：： SetEditSel](#seteditsel)|選取下拉式方塊的編輯控制項中的字元。|
|[CComboBox：： SetExtendedUI](#setextendedui)|為具有 CBS_DROPDOWN 或 CBS_DROPDOWNLIST 樣式的下拉式方塊，選取預設的使用者介面或擴充的使用者介面。|
|[CComboBox：： SetHorizontalExtent](#sethorizontalextent)|設定下拉式方塊的清單方塊部分可水準滾動的寬度（以圖元為單位）。|
|[CComboBox：： SetItemData](#setitemdata)|設定與下拉式方塊中指定之專案相關聯的32位值。|
|[CComboBox：： SetItemDataPtr](#setitemdataptr)|設定與下拉式方塊中指定之專案相關聯的32位指標。|
|[CComboBox：： SetItemHeight](#setitemheight)|設定下拉式方塊中清單專案的高度，或下拉式方塊的 [編輯] 控制項 (或靜態文字) 部分的高度。|
|[CComboBox：： SetLocale](#setlocale)|設定下拉式方塊的地區設定識別碼。|
|[CComboBox：： SetMinVisibleItems](#setminvisibleitems)|設定目前下拉式方塊的下拉式清單中可見專案的最小數目。|
|[CComboBox：： SetTopIndex](#settopindex)|告知下拉式方塊的清單方塊部分，在頂端顯示具有指定索引的專案。|
|[CComboBox：： ShowDropDown](#showdropdown)|顯示或隱藏有 CBS_DROPDOWN 或 CBS_DROPDOWNLIST 樣式之下拉式方塊的清單方塊。|

## <a name="remarks"></a>備註

下拉式方塊是由結合靜態控制項或編輯控制項的清單方塊所組成。 控制項的清單方塊部分可能會隨時顯示，或只在使用者選取控制項旁的下拉箭號時下拉。

目前選取的專案 (是否在 [靜態] 或 [編輯] 控制項中顯示清單方塊中的任何) 。 此外，如果下拉式方塊具有下拉式清單樣式，使用者可以輸入清單中其中一個專案的初始字元，而清單方塊（若可見的話）將會反白顯示具有該初始字元的下一個專案。

下表比較三個下拉式方塊 [樣式](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)。

|樣式|何時可以看見清單方塊|靜態或編輯控制項|
|-----------|-------------------------------|-----------------------------|
|簡單|一律|編輯|
|Drop-down|當下降時|編輯|
|下拉式清單|當下降時|靜態|

您可以 `CComboBox` 從對話方塊範本或直接在程式碼中建立物件。 在這兩種情況下，請先呼叫此函式 `CComboBox` 來建立 `CComboBox` 物件，然後呼叫 [create](#create) 成員函式來建立控制項，並將其附加至 `CComboBox` 物件。

如果您想要處理下拉式方區塊轉送的 Windows 通知訊息至其父系 (通常是衍生自) 的類別 `CDialog` ，請將訊息對應專案和訊息處理常式成員函式加入至每個訊息的父類別。

每個訊息對應專案都採用下列格式：

`ON_Notification( id, memberFxn )`

其中 `id` 指定傳送通知之下拉式方塊控制項的子視窗識別碼，以及 `memberFxn` 您所撰寫用來處理通知的父成員函式的名稱。

父系的函式原型如下：

`afx_msg void memberFxn( );`

將無法預測某些通知的傳送順序。 尤其是在 CBN_CLOSEUP 通知之前或之後，可能會發生 CBN_SELCHANGE 通知。

可能的訊息對應專案如下：

- ON_CBN_CLOSEUP (Windows 3.1 和更新版本。 ) 下拉式方塊的清單方塊已關閉。 此通知訊息不會傳送給具有 [CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 樣式的下拉式方塊。

- ON_CBN_DBLCLK 使用者按兩下下拉式方塊清單方塊中的字串。 此通知訊息只會針對具有 CBS_SIMPLE 樣式的下拉式方區塊轉送。 若為具有 [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 或 [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 樣式的下拉式方塊，就不會發生按兩下，因為按一下就會隱藏清單方塊。

- ON_CBN_DROPDOWN 下拉式方塊的清單方塊即將下拉 (會顯示) 。 只有具有 CBS_DROPDOWN 或 CBS_DROPDOWNLIST 樣式的下拉式方塊才會出現此通知訊息。

- ON_CBN_EDITCHANGE 使用者所採取的動作可能會改變下拉式方塊中編輯控制項部分的文字。 不同于 CBN_EDITUPDATE 訊息，此訊息會在 Windows 更新畫面之後傳送。 如果下拉式方塊具有 CBS_DROPDOWNLIST 樣式，則不會傳送。

- ON_CBN_EDITUPDATE 下拉式方塊的編輯控制項部分即將顯示變更的文字。 此通知訊息會在控制項格式化文字之後，但在顯示文字之前傳送。 如果下拉式方塊具有 CBS_DROPDOWNLIST 樣式，則不會傳送。

- ON_CBN_ERRSPACE 下拉式列示方塊無法配置足夠的記憶體來符合特定要求。

- ON_CBN_SELENDCANCEL (Windows 3.1 和更新版本。 ) 表示應取消使用者的選取專案。 使用者按一下專案，然後按一下另一個視窗或控制項，就可以隱藏下拉式方塊的清單方塊。 此通知訊息會在 CBN_CLOSEUP 通知訊息之前傳送，以指出應忽略使用者的選取專案。 即使在 CBS_SIMPLE 樣式) 的下拉式方塊案例中，CBN_CLOSEUP 通知訊息未傳送 (，也會傳送 CBN_SELENDCANCEL 或 CBN_SELENDOK 通知訊息。

- ON_CBN_SELENDOK 使用者選取專案，然後按下 ENTER 鍵或按一下向下鍵，即可隱藏下拉式方塊的清單方塊。 此通知訊息會在 CBN_CLOSEUP 訊息之前傳送，以指出應將使用者的選取範圍視為有效。 即使在 CBS_SIMPLE 樣式) 的下拉式方塊案例中，CBN_CLOSEUP 通知訊息未傳送 (，也會傳送 CBN_SELENDCANCEL 或 CBN_SELENDOK 通知訊息。

- ON_CBN_KILLFOCUS 下拉式方塊遺失輸入焦點。

- ON_CBN_SELCHANGE 下拉式方塊的清單方塊中的選取專案即將變更，因為使用者在清單方塊中按一下，或使用方向鍵來變更選取範圍的結果。 處理此訊息時，下拉式方塊的編輯控制項中的文字只能透過 `GetLBText` 或另一個類似的函數抓取。 `GetWindowText` 無法使用。

- ON_CBN_SETFOCUS 下拉式方塊會收到輸入焦點。

如果您 `CComboBox` 透過對話方塊資源) 在對話方塊中建立物件 (， `CComboBox` 當使用者關閉對話方塊時，就會自動終結物件。

如果您將 `CComboBox` 物件內嵌在另一個視窗物件內，則不需要終結它。 如果您在 `CComboBox` 堆疊上建立物件，它會自動終結。 如果您使用函式在 `CComboBox` 堆積上建立物件 **`new`** ，您必須 **`delete`** 在物件上呼叫，以在 Windows 下拉式方塊終結時終結它。

**注意** 如果您想要處理 WM_KEYDOWN 並 WM_CHAR 訊息，您必須將下拉式方塊的編輯和清單方塊控制項子類別化、從和衍生類別， `CEdit` `CListBox` 然後將這些訊息的處理常式加入至衍生的類別。 如需詳細資訊，請參閱 [CWnd：： SubclassWindow](../../mfc/reference/cwnd-class.md#subclasswindow)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CComboBox`

## <a name="requirements"></a>規格需求

**標題:** afxwin.h

## <a name="ccomboboxaddstring"></a><a name="addstring"></a> CComboBox：： AddString

將字串加入下拉式方塊的清單方塊中。

```
int AddString(LPCTSTR lpszString);
```

### <a name="parameters"></a>參數

*lpszString*<br/>
指向要加入之以 null 結束的字串。

### <a name="return-value"></a>傳回值

如果傳回值大於或等於0，它就是清單方塊中字串的以零為起始的索引。 如果發生錯誤，則傳回值為 CB_ERR;如果空間不足，無法儲存新的字串，則傳回值為 CB_ERRSPACE。

### <a name="remarks"></a>備註

如果未使用 [CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 樣式建立清單方塊，則會將字串加入至清單結尾。 否則，會將字串插入清單中，並排序清單。

> [!NOTE]
> Windows 控制項不支援這個函式 `ComboBoxEx` 。 如需此控制項的詳細資訊，請參閱 Windows SDK 中的 [ComboBoxEx 控制項](/windows/win32/Controls/comboboxex-controls) 。

若要將字串插入清單中的特定位置，請使用 [InsertString](#insertstring) 成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#3](../../mfc/reference/codesnippet/cpp/ccombobox-class_1.cpp)]

## <a name="ccomboboxccombobox"></a><a name="ccombobox"></a> CComboBox：： CComboBox

建構 `CComboBox` 物件。

```
CComboBox();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_2.cpp)]

## <a name="ccomboboxclear"></a><a name="clear"></a> CComboBox：： Clear

刪除 (會在下拉式方塊的編輯控制項中清除) 目前的選取專案（如果有的話）。

```cpp
void Clear();
```

### <a name="remarks"></a>備註

若要刪除目前的選取範圍，並將已刪除的內容放到剪貼簿上，請使用 [剪](#cut) 下成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#4](../../mfc/reference/codesnippet/cpp/ccombobox-class_3.cpp)]

## <a name="ccomboboxcompareitem"></a><a name="compareitem"></a> CComboBox：： CompareItem

由架構呼叫來判斷新專案在 [已排序的主控描繪] 下拉式方塊的清單方塊部分中的相對位置。

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>參數

*lpCompareItemStruct*<br/>
[COMPAREITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-compareitemstruct)結構的長指標。

### <a name="return-value"></a>傳回值

指出結構中所描述之兩個專案的相對位置 `COMPAREITEMSTRUCT` 。 可以是下列其中任何一個值：

|值|意義|
|-----------|-------------|
|- 1|專案1會在專案2之前排序。|
|0|專案1和專案2的排序方式相同。|
|1|專案1會在專案2之後排序。|

如需的說明，請參閱 [CWnd：： OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) `COMPAREITEMSTRUCT` 。

### <a name="remarks"></a>備註

依預設，此成員函式不會執行任何動作。 如果您建立具有 LBS_SORT 樣式的主控描繪下拉式方塊，您必須覆寫這個成員函式，以協助架構排序新增至清單方塊的新專案。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#5](../../mfc/reference/codesnippet/cpp/ccombobox-class_4.cpp)]

## <a name="ccomboboxcopy"></a><a name="copy"></a> CComboBox：： Copy

在下拉式方塊的編輯控制項中，將目前的選取專案（如果有的話）複製到剪貼簿的 CF_TEXT 格式。

```cpp
void Copy();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#6](../../mfc/reference/codesnippet/cpp/ccombobox-class_5.cpp)]

## <a name="ccomboboxcreate"></a><a name="create"></a> CComboBox：： Create

建立下拉式方塊，並將其附加至 `CComboBox` 物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定下拉式方塊的樣式。 將 [下拉式列示方塊樣式](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 的任何組合套用至方塊。

*矩形*<br/>
指向下拉式方塊的位置和大小。 可以是 [RECT 結構](/windows/win32/api/windef/ns-windef-rect) 或 `CRect` 物件。

*pParentWnd*<br/>
指定下拉式方塊的父視窗 (通常是 `CDialog`) 。 它不得為 NULL。

*nID*<br/>
指定下拉式方塊的控制項識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

您可以使用 `CComboBox` 兩個步驟來建立物件。 首先，呼叫此函式，然後呼叫 `Create` ，它會建立 Windows 下拉式方塊，並將其附加至 `CComboBox` 物件。

當 `Create` 執行時，Windows 會將 [WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)、 [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)、 [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)和 [WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) 訊息傳送至下拉式方塊。

根據預設，這些訊息是由基類中的 [OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate)、 [>oncreate](../../mfc/reference/cwnd-class.md#oncreate)、 [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)和 [OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo) 成員函式所處理 `CWnd` 。 若要擴充預設訊息處理、從衍生類別 `CComboBox` 、將訊息對應加入至新類別，以及覆寫先前的訊息處理常式成員函式。 `OnCreate`例如，覆寫以針對新類別執行所需的初始化。

將下列 [視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles) 套用至下拉式方塊控制項。 :

- 一律 WS_CHILD

- 通常 WS_VISIBLE

- WS_DISABLED 很少

- WS_VSCROLL 在下拉式方塊中加入清單方塊的垂直捲動條

- WS_HSCROLL，在下拉式方塊中新增清單方塊的水準捲軸

- WS_GROUP 至群組控制項

- WS_TABSTOP 在定位順序中包含下拉式方塊

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_6.cpp)]

## <a name="ccomboboxcut"></a><a name="cut"></a> CComboBox：：剪下

在下拉式方塊編輯控制項中刪除 (剪下) 目前的選取專案（如果有的話），並將已刪除的文字複製到剪貼簿的 CF_TEXT 格式。

```cpp
void Cut();
```

### <a name="remarks"></a>備註

若要刪除目前的選取範圍，而不將已刪除的文字放到剪貼簿上，請呼叫 [Clear](#clear) 成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#7](../../mfc/reference/codesnippet/cpp/ccombobox-class_7.cpp)]

## <a name="ccomboboxdeleteitem"></a><a name="deleteitem"></a> CComboBox：:D eleteItem

當使用者從擁有者繪圖物件中刪除專案或終結下拉式方塊時，由架構呼叫 `CComboBox` 。

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>參數

*lpDeleteItemStruct*<br/>
包含已刪除專案相關資訊之 Windows [DELETEITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-deleteitemstruct) 結構的長指標。 如需此結構的說明，請參閱 [CWnd：： OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) 。

### <a name="remarks"></a>備註

此函式的預設實作不做任何動作。 視需要覆寫此函式以重繪下拉式方塊。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#8](../../mfc/reference/codesnippet/cpp/ccombobox-class_8.cpp)]

## <a name="ccomboboxdeletestring"></a><a name="deletestring"></a> CComboBox：:D eleteString

從下拉式方塊刪除位置 *nIndex* 中的專案。

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定要刪除之字串的索引。

### <a name="return-value"></a>傳回值

如果傳回值大於或等於0，則為清單中剩餘字串的計數。 如果 *nIndex* 指定的索引大於清單中的專案數，則傳回值為 CB_ERR。

### <a name="remarks"></a>備註

*NIndex*之後的所有專案現在都會下移一個位置。 例如，如果下拉式方塊包含兩個專案，則刪除第一個專案會導致其餘的專案現在位於第一個位置。 第一個位置中專案的*nIndex*= 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#9](../../mfc/reference/codesnippet/cpp/ccombobox-class_9.cpp)]

## <a name="ccomboboxdir"></a><a name="dir"></a> CComboBox：:D ir

將檔案名或磁片磁碟機清單加入下拉式方塊的清單方塊中。

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>參數

*attr*<br/>
可以是 **`enum`** [CFile：： GetStatus](../../mfc/reference/cfile-class.md#getstatus) 中所述值的任何組合，或下列值的任何組合：

- 您可以讀取或寫入 DDL_READWRITE 的檔案。

- DDL_READONLY 檔案可以讀取，但不能寫入。

- DDL_HIDDEN 檔案是隱藏的，且不會出現在目錄清單中。

- DDL_SYSTEM 檔案是系統檔案。

- DDL_DIRECTORY *lpszWildCard* 指定的名稱會指定目錄。

- DDL_ARCHIVE 檔案已封存。

- DDL_DRIVES 包含符合 *lpszWildCard*所指定之名稱的所有磁片磁碟機。

- DDL_EXCLUSIVE 獨佔旗標。 如果設定了獨佔旗標，則只會列出指定之類型的檔案。 否則，除了「一般」檔案之外，還會列出指定類型的檔案。

*lpszWildCard*<br/>
指向檔案規格字串。 字串可以包含萬用字元 (例如 *。 \*) 。

### <a name="return-value"></a>傳回值

如果傳回值大於或等於0，它就是新增至清單的最後一個檔案名之以零為起始的索引。 如果發生錯誤，則傳回值為 CB_ERR;如果空間不足，無法存放新的字串，則傳回值為 CB_ERRSPACE。

### <a name="remarks"></a>備註

Windows 控制項不支援這個函式 `ComboBoxEx` 。 如需此控制項的詳細資訊，請參閱 Windows SDK 中的 [ComboBoxEx 控制項](/windows/win32/Controls/comboboxex-controls) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#10](../../mfc/reference/codesnippet/cpp/ccombobox-class_10.cpp)]

## <a name="ccomboboxdrawitem"></a><a name="drawitem"></a> CComboBox：:D rawItem

當主控描繪下拉式方塊的視覺外觀變更時，由架構呼叫。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>參數

*lpDrawItemStruct*<br/>
[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)結構的指標，其中包含所需繪圖類型的相關資訊。

### <a name="remarks"></a>備註

`itemAction`結構的成員 `DRAWITEMSTRUCT` 會定義要執行的繪圖動作。 如需此結構的說明，請參閱 [CWnd：： OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) 。

依預設，此成員函式不會執行任何動作。 覆寫這個成員函式，以針對主控描繪物件來執行繪圖 `CComboBox` 。 在這個成員函式終止之前，應用程式應該針對 *lpDrawItemStruct*中提供的顯示內容，還原選取的所有圖形裝置介面 (GDI) 物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#11](../../mfc/reference/codesnippet/cpp/ccombobox-class_11.cpp)]

## <a name="ccomboboxfindstring"></a><a name="findstring"></a> CComboBox：： FindString

在下拉式方塊的清單方塊中尋找包含指定前置詞的第一個字串，但不會選取它。

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszString) const;
```

### <a name="parameters"></a>參數

*nStartAfter*<br/>
在要搜尋的第一個專案之前，包含專案之以零為起始的索引。 當搜尋到達清單方塊的底部時，它會從清單方塊的頂端繼續移回 *nStartAfter*所指定的專案。 如果是-1，就會從一開始就搜尋整個清單方塊。

*lpszString*<br/>
指向以 null 終止的字串，其中包含要搜尋的前置詞。 搜尋不會區分大小寫，因此這個字串可以包含任何大小寫字母的組合。

### <a name="return-value"></a>傳回值

如果傳回值大於或等於0，則為相符專案的以零為基底的索引。 如果搜尋失敗，就會 CB_ERR。

### <a name="remarks"></a>備註

Windows 控制項不支援這個函式 `ComboBoxEx` 。 如需此控制項的詳細資訊，請參閱 Windows SDK 中的 [ComboBoxEx 控制項](/windows/win32/Controls/comboboxex-controls) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#12](../../mfc/reference/codesnippet/cpp/ccombobox-class_12.cpp)]

## <a name="ccomboboxfindstringexact"></a><a name="findstringexact"></a> CComboBox：： FindStringExact

呼叫成員函式 `FindStringExact` ，以找出下拉式方塊中的第一個清單方塊字串 (，) 與 *lpszFind*中指定的字串相符。

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>參數

*nIndexStart*<br/>
在要搜尋的第一個專案之前，指定專案以零為基底的索引。 當搜尋到達清單方塊的底部時，它會從清單方塊的頂端繼續移回 *nIndexStart*所指定的專案。 如果 *nIndexStart* 為-1，就會從一開始就搜尋整個清單方塊。

*lpszFind*<br/>
指向要搜尋的以 null 結束的字串。 這個字串可以包含完整的檔案名，包括副檔名。 搜尋不區分大小寫，因此這個字串可以包含任何大小寫字母的組合。

### <a name="return-value"></a>傳回值

符合專案之以零為起始的索引，如果搜尋失敗，則為 CB_ERR。

### <a name="remarks"></a>備註

如果下拉式方塊是使用主控描繪樣式來建立，但沒有 [CBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 樣式，則 `FindStringExact` 會嘗試比對雙 *lpszFind*值與值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#13](../../mfc/reference/codesnippet/cpp/ccombobox-class_13.cpp)]

## <a name="ccomboboxgetcomboboxinfo"></a><a name="getcomboboxinfo"></a> CComboBox：： GetComboBoxInfo

抓取物件的資訊 `CComboBox` 。

```
BOOL GetComboBoxInfo(PCOMBOBOXINFO pcbi) const;
```

### <a name="parameters"></a>參數

*pcbi*<br/>
[COMBOBOXINFO](/windows/win32/api/winuser/ns-winuser-comboboxinfo)結構的指標。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

此成員函式會模擬 [CB_GETCOMBOBOXINFO](/windows/win32/Controls/cb-getcomboboxinfo) 訊息的功能，如 Windows SDK 中所述。

## <a name="ccomboboxgetcount"></a><a name="getcount"></a> CComboBox：： GetCount

呼叫這個成員函式，以抓取下拉式方塊的清單方塊部分中的專案數。

```
int GetCount() const;
```

### <a name="return-value"></a>傳回值

項目數。 傳回的計數大於最後一個專案的索引值， (索引是以零為基底的) 。 如果發生錯誤，就會 CB_ERR。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#14](../../mfc/reference/codesnippet/cpp/ccombobox-class_14.cpp)]

## <a name="ccomboboxgetcuebanner"></a><a name="getcuebanner"></a> CComboBox：： GetCueBanner

取得為下拉式方塊控制項顯示的提示文字。

```
CString GetCueBanner() const;

BOOL GetCueBanner(
    LPTSTR lpszText,
    int cchText) const;
```

### <a name="parameters"></a>參數

*lpszText*\
擴展接收提示橫幅文字之緩衝區的指標。

*cchText*\
在 *LpszText* 參數所指向的緩衝區大小。

### <a name="return-value"></a>傳回值

在第一個多載中，包含提示橫幅文字（如果有的話）的 [CString](../../atl-mfc-shared/using-cstring.md) 物件;否則為 `CString` 長度為零的物件。

-或-

在第二個多載中，如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

提示文字是在下拉式方塊控制項的輸入區域中顯示的提示。 提示文字會顯示，直到使用者提供輸入為止。

這個方法會傳送 [CB_GETCUEBANNER](/windows/win32/Controls/cb-getcuebanner) 的訊息，如 Windows SDK 中所述。

## <a name="ccomboboxgetcursel"></a><a name="getcursel"></a> CComboBox：： GetCurSel

呼叫這個成員函式，以判斷選取下拉式方塊中的哪個專案。

```
int GetCurSel() const;
```

### <a name="return-value"></a>傳回值

下拉式方塊清單方塊中目前選取專案之以零為起始的索引，如果未選取任何專案，則為 CB_ERR。

### <a name="remarks"></a>備註

`GetCurSel` 傳回清單中的索引。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#15](../../mfc/reference/codesnippet/cpp/ccombobox-class_15.cpp)]

## <a name="ccomboboxgetdroppedcontrolrect"></a><a name="getdroppedcontrolrect"></a> CComboBox：： GetDroppedControlRect

呼叫成員函式 `GetDroppedControlRect` ，以抓取下拉式清單方塊的可見 (下拉) 清單方塊的螢幕座標。

```cpp
void GetDroppedControlRect(LPRECT lprect) const;
```

### <a name="parameters"></a>參數

*lprect*<br/>
指向要接收座標的 [RECT 結構](/windows/win32/api/windef/ns-windef-rect) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#16](../../mfc/reference/codesnippet/cpp/ccombobox-class_16.cpp)]

## <a name="ccomboboxgetdroppedstate"></a><a name="getdroppedstate"></a> CComboBox：： GetDroppedState

呼叫成員函式 `GetDroppedState` ，以判斷下拉式方塊的清單方塊是否為可見的 () ] 下拉式清單方塊。

```
BOOL GetDroppedState() const;
```

### <a name="return-value"></a>傳回值

如果看不到清單方塊，則為非零;否則為0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#17](../../mfc/reference/codesnippet/cpp/ccombobox-class_17.cpp)]

## <a name="ccomboboxgetdroppedwidth"></a><a name="getdroppedwidth"></a> CComboBox：： GetDroppedWidth

呼叫此函式可取得下拉式方塊清單方塊的最小允許寬度（以圖元為單位）。

```
int GetDroppedWidth() const;
```

### <a name="return-value"></a>傳回值

如果成功，則允許的最小寬度（以圖元為單位）;否則，CB_ERR。

### <a name="remarks"></a>備註

此函數僅適用于具有 [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 或 [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 樣式的下拉式方塊。

根據預設，下拉式清單方塊的允許寬度下限為0。 您可以藉由呼叫 [SetDroppedWidth](#setdroppedwidth)來設定允許的最小寬度。 當顯示下拉式方塊的清單方塊部分時，其寬度會是允許寬度下限或下拉式方塊寬度的較大寬度。

### <a name="example"></a>範例

  請參閱 [SetDroppedWidth](#setdroppedwidth)的範例。

## <a name="ccomboboxgeteditsel"></a><a name="geteditsel"></a> CComboBox：： GetEditSel

取得下拉式方塊的編輯控制項中目前選取範圍的開始和結束字元位置。

```
DWORD GetEditSel() const;
```

### <a name="return-value"></a>傳回值

32位值，其中包含低序位字組中的開始位置，以及在高序位字中選取範圍結尾之後的第一個 nonselected 字元位置。 如果在沒有編輯控制項的下拉式方塊上使用此函數，則會傳回 CB_ERR。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#18](../../mfc/reference/codesnippet/cpp/ccombobox-class_18.cpp)]

## <a name="ccomboboxgetextendedui"></a><a name="getextendedui"></a> CComboBox：： GetExtendedUI

呼叫成員函式 `GetExtendedUI` ，以判斷下拉式方塊是否有預設的使用者介面或擴充的使用者介面。

```
BOOL GetExtendedUI() const;
```

### <a name="return-value"></a>傳回值

如果下拉式方塊具有擴充的使用者介面，則為非零。否則為0。

### <a name="remarks"></a>備註

您可以利用下列方式來識別擴充的使用者介面：

- 按一下靜態控制項，只會顯示具有 [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 樣式之下拉式方塊的清單方塊。

- 按向下鍵會顯示 (F4 已停用的清單方塊) 。

當 (方向鍵已停用) 時，會停用靜態控制項中的滾動。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#19](../../mfc/reference/codesnippet/cpp/ccombobox-class_19.cpp)]

## <a name="ccomboboxgethorizontalextent"></a><a name="gethorizontalextent"></a> CComboBox：： GetHorizontalExtent

從下拉式方塊抓取以圖元為單位的寬度（以圖元為單位），而下拉式方塊的清單方塊部分可以水準滾動。

```
UINT GetHorizontalExtent() const;
```

### <a name="return-value"></a>傳回值

下拉式方塊的清單方塊部分可滾動的寬度（以圖元為單位）。

### <a name="remarks"></a>備註

這僅適用于下拉式方塊的清單方塊部分具有水準捲軸時。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#20](../../mfc/reference/codesnippet/cpp/ccombobox-class_20.cpp)]

## <a name="ccomboboxgetitemdata"></a><a name="getitemdata"></a> CComboBox：： GetItemData

抓取與指定的下拉式方塊專案相關聯之應用程式提供的32位值。

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
在下拉式方塊的清單方塊中包含專案之以零為起始的索引。

### <a name="return-value"></a>傳回值

與專案相關聯的32位值，如果發生錯誤，則為 CB_ERR。

### <a name="remarks"></a>備註

您可以使用[SetItemData](#setitemdata)成員函式呼叫的*dwItemData*參數來設定32位值。 `GetItemDataPtr`如果要抓取的32位值是指標 () ，請使用成員函式 **`void`** <strong>\*</strong> 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#21](../../mfc/reference/codesnippet/cpp/ccombobox-class_21.cpp)]

## <a name="ccomboboxgetitemdataptr"></a><a name="getitemdataptr"></a> CComboBox：： GetItemDataPtr

抓取與指定的下拉式方塊專案相關聯的應用程式所提供的32位值，做為 () 的指標 **`void`** <strong>\*</strong> 。

```cpp
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
在下拉式方塊的清單方塊中包含專案之以零為起始的索引。

### <a name="return-value"></a>傳回值

抓取指標，如果發生錯誤則為-1。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#22](../../mfc/reference/codesnippet/cpp/ccombobox-class_22.cpp)]

## <a name="ccomboboxgetitemheight"></a><a name="getitemheight"></a> CComboBox：： GetItemHeight

呼叫成員函式 `GetItemHeight` ，以在下拉式方塊中取出清單專案的高度。

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定要取出其高度的下拉式方塊元件。 如果 *nIndex* 參數為-1，則會抓取下拉式方塊的編輯控制項 (或靜態文字) 部分的高度。 如果下拉式方塊有 [CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 的樣式，則 *nIndex* 會指定要抓取其高度的清單專案之以零為起始的索引。 否則， *nIndex* 應該設定為0。

### <a name="return-value"></a>傳回值

下拉式方塊中指定專案的高度（以圖元為單位）。 如果發生錯誤，傳回值是 CB_ERR。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#23](../../mfc/reference/codesnippet/cpp/ccombobox-class_23.cpp)]

## <a name="ccomboboxgetlbtext"></a><a name="getlbtext"></a> CComboBox：： GetLBText

從下拉式方塊的清單方塊中取得字串。

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
包含要複製的清單方塊字串之以零為起始的索引。

*lpszText*<br/>
指向接收字串的緩衝區。 緩衝區必須有足夠的空間可供字串和終止的 null 字元使用。

*rString*<br/>
對 `CString` 的參考。

### <a name="return-value"></a>傳回值

字串的長度 (（以位元組為單位) ），不包括終止的 null 字元。 如果 *nIndex* 未指定有效的索引，則傳回值為 CB_ERR。

### <a name="remarks"></a>備註

此成員函式的第二個形式會 `CString` 以專案的文字填入物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#24](../../mfc/reference/codesnippet/cpp/ccombobox-class_24.cpp)]

## <a name="ccomboboxgetlbtextlen"></a><a name="getlbtextlen"></a> CComboBox：： GetLBTextLen

取得下拉式方塊清單方塊中字串的長度。

```
int GetLBTextLen(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
包含清單方塊字串的以零為起始的索引。

### <a name="return-value"></a>傳回值

字串的長度（以位元組為單位），不包括終止的 null 字元。 如果 *nIndex* 未指定有效的索引，則傳回值為 CB_ERR。

### <a name="example"></a>範例

  請參閱 [CComboBox：： GetLBText](#getlbtext)的範例。

## <a name="ccomboboxgetlocale"></a><a name="getlocale"></a> CComboBox：： GetLocale

抓取下拉式方塊所使用的地區設定。

```
LCID GetLocale() const;
```

### <a name="return-value"></a>傳回值

地區設定識別碼 () 下拉式方塊中字串的 LCID 值。

### <a name="remarks"></a>備註

例如，使用地區設定來決定排序下拉式方塊中字串的排序次序。

### <a name="example"></a>範例

  請參閱 [CComboBox：： SetLocale](#setlocale)的範例。

## <a name="ccomboboxgetminvisible"></a><a name="getminvisible"></a> CComboBox：： GetMinVisible

取得目前下拉式方塊控制項下拉式清單中可見專案的最小數目。

```
int GetMinVisible() const;
```

### <a name="return-value"></a>傳回值

目前下拉式清單中可見專案的最小數目。

### <a name="remarks"></a>備註

這個方法會傳送 [CB_GETMINVISIBLE](/windows/win32/Controls/cb-setminvisible) 的訊息，如 Windows SDK 中所述。

## <a name="ccomboboxgettopindex"></a><a name="gettopindex"></a> CComboBox：： GetTopIndex

在下拉式方塊的清單方塊部分中，抓取第一個可見專案的以零為起始的索引。

```
int GetTopIndex() const;
```

### <a name="return-value"></a>傳回值

如果成功，則為下拉式方塊的清單方塊部分中第一個可見專案的以零為基底的索引，否則為 CB_ERR。

### <a name="remarks"></a>備註

一開始，專案0位於清單方塊的頂端，但如果清單方塊已滾動，則其他專案可能位於頂端。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#25](../../mfc/reference/codesnippet/cpp/ccombobox-class_25.cpp)]

## <a name="ccomboboxinitstorage"></a><a name="initstorage"></a> CComboBox：： InitStorage

配置記憶體，以在下拉式方塊的清單方塊部分中儲存清單方塊專案。

```
int InitStorage(
    int nItems,
    UINT nBytes);
```

### <a name="parameters"></a>參數

*nItems*<br/>
指定要加入的專案數目。

*n*<br/>
指定要配置給專案字串的記憶體數量（以位元組為單位）。

### <a name="return-value"></a>傳回值

如果成功，則在需要記憶體重新配置之前，下拉式方塊的清單方塊部分可以儲存的最大專案數，否則 CB_ERRSPACE，表示沒有足夠的記憶體可用。

### <a name="remarks"></a>備註

將大量專案加入至的清單方塊部分之前，請先呼叫這個函數 `CComboBox` 。

僅限 Windows 95/98： *wParam* 參數限制為16位值。 這表示清單方塊不能包含超過32767個專案。 雖然限制專案數目，但清單方塊中的專案總大小只受到可用記憶體的限制。

此函式可協助加速初始化具有大量專案 (超過 100) 的清單方塊。 它會會預先配置指定的記憶體數量，讓後續的 [AddString](#addstring)、 [InsertString](#insertstring)和 [Dir](#dir) 函式可能會花費最短的時間。 您可以使用參數的估計值。 如果您高估值，則會配置一些額外的記憶體;如果您低估了，一般配置會用於超過預先配置數量的專案。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#26](../../mfc/reference/codesnippet/cpp/ccombobox-class_26.cpp)]

## <a name="ccomboboxinsertstring"></a><a name="insertstring"></a> CComboBox：： InsertString

將字串插入下拉式方塊的清單方塊中。

```
int InsertString(
    int nIndex,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
包含要接收字串之清單方塊中位置以零為基底的索引。 如果此參數為-1，則會將字串加入至清單結尾。

*lpszString*<br/>
指向要插入的 null 結尾字串。

### <a name="return-value"></a>傳回值

已插入字串之位置以零為基底的索引。 如果發生錯誤，傳回值是 CB_ERR。 如果空間不足，無法存放新的字串，傳回值是 CB_ERRSPACE。

### <a name="remarks"></a>備註

不像 [AddString](#addstring) 成員函式， `InsertString` 成員函式不會排序 [CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 樣式的清單。

> [!NOTE]
> Windows 控制項不支援這個函式 `ComboBoxEx` 。 如需此控制項的詳細資訊，請參閱 Windows SDK 中的 [ComboBoxEx 控制項](/windows/win32/Controls/comboboxex-controls) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#27](../../mfc/reference/codesnippet/cpp/ccombobox-class_27.cpp)]

## <a name="ccomboboxlimittext"></a><a name="limittext"></a> CComboBox：： LimitText

限制使用者可在下拉式方塊的編輯控制項中輸入的文字長度（以位元組為單位）。

```
BOOL LimitText(int nMaxChars);
```

### <a name="parameters"></a>參數

*nMaxChars*<br/>
指定使用者可輸入文字的長度 (位元組) 。 如果此參數為0，則文字長度會設定為65535個位元組。

### <a name="return-value"></a>傳回值

如果成功，則為非零。 如果針對樣式為 [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 的下拉式方塊或沒有編輯控制項的下拉式方塊呼叫，則傳回值為 CB_ERR。

### <a name="remarks"></a>備註

如果下拉式方塊沒有 [CBS_AUTOHSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)的樣式，將文字限制設定為大於編輯控制項的大小將不會有任何作用。

`LimitText` 只會限制使用者可以輸入的文字。 當傳送訊息時，它不會影響任何已在編輯控制項中的文字，也不會影響選取清單方塊中的字串時，複製到編輯控制項的文字長度。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#28](../../mfc/reference/codesnippet/cpp/ccombobox-class_28.cpp)]

## <a name="ccomboboxmeasureitem"></a><a name="measureitem"></a> CComboBox：： MeasureItem

當建立具有主控描繪樣式的下拉式列示方塊時，由架構呼叫。

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>參數

*lpMeasureItemStruct*<br/>
[MEASUREITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-measureitemstruct)結構的長指標。

### <a name="remarks"></a>備註

依預設，此成員函式不會執行任何動作。 覆寫這個成員函式並填入 `MEASUREITEMSTRUCT` 結構，以通知視窗下拉式方塊中清單方塊的維度。 如果以 [CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 樣式建立下拉式方塊，則架構會針對清單方塊中的每個專案呼叫此成員函式。 否則，只會呼叫這個成員一次。

在使用 [SubclassDlgItem](../../mfc/reference/cwnd-class.md#subclassdlgitem) 成員函式所建立的主控描繪下拉式方塊中使用 CBS_OWNERDRAWFIXED 樣式， `CWnd` 牽涉到進一步的程式設計考慮。 請參閱 [技術附注 14](../../mfc/tn014-custom-controls.md)中的討論。

如需結構的描述，請參閱 [CWnd：： OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) `MEASUREITEMSTRUCT` 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#29](../../mfc/reference/codesnippet/cpp/ccombobox-class_29.cpp)]

## <a name="ccomboboxpaste"></a><a name="paste"></a> CComboBox：:P aste

將剪貼簿中的資料插入目前游標位置之下拉式方塊的編輯控制項。

```cpp
void Paste();
```

### <a name="remarks"></a>備註

只有當剪貼簿包含 CF_TEXT 格式的資料時，才會插入資料。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#30](../../mfc/reference/codesnippet/cpp/ccombobox-class_30.cpp)]

## <a name="ccomboboxresetcontent"></a><a name="resetcontent"></a> CComboBox：： ResetContent

從清單方塊中移除所有專案，並編輯下拉式方塊的控制項。

```cpp
void ResetContent();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#31](../../mfc/reference/codesnippet/cpp/ccombobox-class_31.cpp)]

## <a name="ccomboboxselectstring"></a><a name="selectstring"></a> CComboBox：： SelectString

在下拉式方塊的清單方塊中搜尋字串，如果找到該字串，則選取清單方塊中的字串，並將它複製到編輯控制項。

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>參數

*nStartAfter*<br/>
在要搜尋的第一個專案之前，包含專案之以零為起始的索引。 當搜尋到達清單方塊的底部時，它會從清單方塊的頂端繼續移回 *nStartAfter*所指定的專案。 如果是-1，就會從一開始就搜尋整個清單方塊。

*lpszString*<br/>
指向以 null 終止的字串，其中包含要搜尋的前置詞。 搜尋不會區分大小寫，因此這個字串可以包含任何大小寫字母的組合。

### <a name="return-value"></a>傳回值

如果找到該字串，則為所選取專案以零為基底的索引。 如果搜尋失敗，則傳回值為 CB_ERR，且目前的選取範圍不會變更。

### <a name="remarks"></a>備註

只有當字串的初始字元 (從起始點) 符合前置詞字串中的字元時，才會選取字串。

請注意， `SelectString` 和 `FindString` 成員函式都會尋找字串，但成員函式 `SelectString` 也會選取字串。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#32](../../mfc/reference/codesnippet/cpp/ccombobox-class_32.cpp)]

## <a name="ccomboboxsetcuebanner"></a><a name="setcuebanner"></a> CComboBox：： SetCueBanner

設定為下拉式方塊控制項顯示的提示文字。

```
BOOL SetCueBanner(LPCTSTR lpszText);
```

### <a name="parameters"></a>參數

*lpszText*\
在包含提示文字之以 null 終止的緩衝區指標。

### <a name="return-value"></a>傳回值

如果方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

提示文字是在下拉式方塊控制項的輸入區域中顯示的提示。 提示文字會顯示，直到使用者提供輸入為止。

這個方法會傳送 [CB_SETCUEBANNER](/windows/win32/Controls/cb-setcuebanner) 的訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義用來以程式設計方式存取下拉式方塊控制項的變數（ *m_combobox*）。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>範例

下列程式碼範例會設定下拉式方塊控制項的提示橫幅。

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

## <a name="ccomboboxsetcursel"></a><a name="setcursel"></a> CComboBox：： SetCurSel

在下拉式方塊的清單方塊中選取字串。

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>參數

*nSelect*<br/>
指定要選取之字串的以零為基底的索引。 如果為-1，則會移除清單方塊中目前的選取範圍，並清除編輯控制項。

### <a name="return-value"></a>傳回值

如果訊息成功，則為所選取專案之以零為起始的索引。 如果 *nSelect* 大於清單中的專案數，或如果 *nSelect* 設定為-1 （清除選取專案），則傳回值為 CB_ERR。

### <a name="remarks"></a>備註

如有必要，清單方塊會將字串滾動至 view (如果) 顯示清單方塊。 下拉式方塊的編輯控制項中的文字會變更，以反映新的選取專案。 清單方塊中的任何先前選項都會被移除。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#33](../../mfc/reference/codesnippet/cpp/ccombobox-class_35.cpp)]

## <a name="ccomboboxsetdroppedwidth"></a><a name="setdroppedwidth"></a> CComboBox：： SetDroppedWidth

呼叫此函式可設定下拉式方塊清單方塊的允許寬度下限（以圖元為單位）。

```
int SetDroppedWidth(UINT nWidth);
```

### <a name="parameters"></a>參數

*nWidth*<br/>
下拉式方塊的清單方塊部分允許的最小寬度（以圖元為單位）。

### <a name="return-value"></a>傳回值

如果成功，則為清單方塊的新寬度，否則 CB_ERR。

### <a name="remarks"></a>備註

此函數僅適用于具有 [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 或 [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 樣式的下拉式方塊。

根據預設，下拉式清單方塊的允許寬度下限為0。 當顯示下拉式方塊的清單方塊部分時，其寬度會是允許寬度下限或下拉式方塊寬度的較大寬度。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#34](../../mfc/reference/codesnippet/cpp/ccombobox-class_36.cpp)]

## <a name="ccomboboxseteditsel"></a><a name="seteditsel"></a> CComboBox：： SetEditSel

選取下拉式方塊的編輯控制項中的字元。

```
BOOL SetEditSel(
    int nStartChar,
    int nEndChar);
```

### <a name="parameters"></a>參數

*nStartChar*<br/>
指定開始位置。 如果開始位置設定為-1，則會移除任何現有的選取專案。

*nEndChar*<br/>
指定結束位置。 如果結束位置設定為-1，則會選取從開始位置到編輯控制項中最後一個字元的所有文字。

### <a name="return-value"></a>傳回值

如果成員函式成功，則為非零;否則為0。 如果 `CComboBox` 有 [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 樣式或沒有清單方塊，就會 CB_ERR。

### <a name="remarks"></a>備註

這些位置以零為基底。 若要選取編輯控制項的第一個字元，請指定0的開始位置。 結束位置是緊接在最後一個要選取的字元之後的字元。 例如，若要選取編輯控制項的前四個字元，您可以使用0的開始位置和結束位置4。

> [!NOTE]
> Windows 控制項不支援這個函式 `ComboBoxEx` 。 如需此控制項的詳細資訊，請參閱 Windows SDK 中的 [ComboBoxEx 控制項](/windows/win32/Controls/comboboxex-controls) 。

### <a name="example"></a>範例

  請參閱 [CComboBox：： GetEditSel](#geteditsel)的範例。

## <a name="ccomboboxsetextendedui"></a><a name="setextendedui"></a> CComboBox：： SetExtendedUI

呼叫成員函式， `SetExtendedUI` 為具有 [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 或 [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 樣式的下拉式方塊選取預設使用者介面或擴充的使用者介面。

```
int SetExtendedUI(BOOL bExtended = TRUE);
```

### <a name="parameters"></a>參數

*bExtended*<br/>
指定下拉式方塊應使用擴充的使用者介面或預設使用者介面。 TRUE 值會選取擴充的使用者介面;FALSE 值會選取標準使用者介面。

### <a name="return-value"></a>傳回值

如果作業成功，則為 CB_OKAY，如果發生錯誤則為 CB_ERR。

### <a name="remarks"></a>備註

您可以利用下列方式來識別擴充的使用者介面：

- 按一下靜態控制項，只會顯示具有 CBS_DROPDOWNLIST 樣式之下拉式方塊的清單方塊。

- 按向下鍵會顯示 (F4 已停用的清單方塊) 。

當 (方向鍵已停用時，就會停用在靜態控制項中的滾動) 。

### <a name="example"></a>範例

  請參閱 [CComboBox：： GetExtendedUI](#getextendedui)的範例。

## <a name="ccomboboxsethorizontalextent"></a><a name="sethorizontalextent"></a> CComboBox：： SetHorizontalExtent

設定下拉式方塊的清單方塊部分可水準滾動的寬度（以圖元為單位）。

```cpp
void SetHorizontalExtent(UINT nExtent);
```

### <a name="parameters"></a>參數

*nExtent*<br/>
指定下拉式方塊的清單方塊部分可水準滾動的圖元數。

### <a name="remarks"></a>備註

如果清單方塊的寬度小於此值，水準捲軸會在清單方塊中以水準方式滾動專案。 如果清單方塊的寬度等於或大於此值，則會隱藏水準捲軸，或者，如果下拉式方塊的 [CBS_DISABLENOSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 樣式已停用。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#35](../../mfc/reference/codesnippet/cpp/ccombobox-class_37.cpp)]

## <a name="ccomboboxsetitemdata"></a><a name="setitemdata"></a> CComboBox：： SetItemData

設定與下拉式方塊中指定之專案相關聯的32位值。

```
int SetItemData(
    int nIndex,
    DWORD_PTR dwItemData);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
包含要設定之專案的以零為基底的索引。

*dwItemData*<br/>
包含要與專案產生關聯的新值。

### <a name="return-value"></a>傳回值

CB_ERR 是否發生錯誤。

### <a name="remarks"></a>備註

`SetItemDataPtr`如果32位專案是指標，請使用成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#36](../../mfc/reference/codesnippet/cpp/ccombobox-class_38.cpp)]

## <a name="ccomboboxsetitemdataptr"></a><a name="setitemdataptr"></a> CComboBox：： SetItemDataPtr

在下拉式方塊中，將與指定之專案相關聯的32位值設定為指定的指標 (**`void`** <strong>\*</strong>) 。

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
包含專案的以零為基底的索引。

*.Pdata*<br/>
包含要與專案相關聯的指標。

### <a name="return-value"></a>傳回值

CB_ERR 是否發生錯誤。

### <a name="remarks"></a>備註

這個指標會在下拉式方塊的存留期內保持有效狀態，即使在新增或移除專案時，下拉式方塊中的專案相對位置可能會變更也是一樣。 因此，方塊內的專案索引可能會變更，但指標仍保持可靠。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#37](../../mfc/reference/codesnippet/cpp/ccombobox-class_39.cpp)]

## <a name="ccomboboxsetitemheight"></a><a name="setitemheight"></a> CComboBox：： SetItemHeight

呼叫成員函式 `SetItemHeight` ，在下拉式方塊中設定清單專案的高度，或在下拉式方塊的 [編輯] 控制項 (或靜態文字) 部分設定高度。

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定是否設定下拉式方塊的清單專案高度或編輯控制項 (或靜態文字) 部分的高度。

如果下拉式方塊有 [CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 的樣式，則 *nIndex* 會指定要設定其高度的清單專案之以零為起始的索引;否則， *nIndex* 必須是0，而且會設定所有清單專案的高度。

如果 *nIndex* 為-1，則會設定下拉式方塊的編輯控制項或靜態文字部分的高度。

*cyItemHeight*<br/>
指定 *nIndex*所識別之下拉式方塊元件的高度（以圖元為單位）。

### <a name="return-value"></a>傳回值

如果索引或高度無效，則為 CB_ERR;否則為0。

### <a name="remarks"></a>備註

下拉式方塊的編輯控制項 (或靜態文字) 部分的高度，會與清單專案的高度分開設定。 應用程式必須確保編輯控制項 (或靜態文字) 部分的高度不會小於特定清單方塊專案的高度。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#38](../../mfc/reference/codesnippet/cpp/ccombobox-class_40.cpp)]

## <a name="ccomboboxsetlocale"></a><a name="setlocale"></a> CComboBox：： SetLocale

設定這個下拉式方塊的地區設定識別碼。

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>參數

*nNewLocale*<br/>
新的地區設定識別碼 (LCID) 值，以針對下拉式方塊進行設定。

### <a name="return-value"></a>傳回值

先前的地區設定識別碼 (此下拉式方塊的 LCID) 值。

### <a name="remarks"></a>備註

如果 `SetLocale` 未呼叫，就會從系統中取得預設的地區設定。 您可以使用主控台的區域 (或國際) 應用程式來修改此系統預設地區設定。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#39](../../mfc/reference/codesnippet/cpp/ccombobox-class_41.cpp)]

## <a name="ccomboboxsetminvisibleitems"></a><a name="setminvisibleitems"></a> CComboBox：： SetMinVisibleItems

設定目前下拉式方塊控制項下拉式清單中可見專案的最小數目。

```
BOOL SetMinVisibleItems(int iMinVisible);
```

### <a name="parameters"></a>參數

*iMinVisible*\
在指定可見專案的最小數目。

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送 [CB_SETMINVISIBLE](/windows/win32/Controls/cb-setminvisible) 的訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會定義用來以程式設計方式存取下拉式方塊控制項的變數（ *m_combobox*）。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>範例

下列程式碼範例會將20個專案插入下拉式方塊控制項的下拉式清單中。 然後，它會指定當使用者按下下拉箭號時，最少顯示10個專案。

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

## <a name="ccomboboxsettopindex"></a><a name="settopindex"></a> CComboBox：： SetTopIndex

確定下拉式方塊的清單方塊部分可以看到特定的專案。

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定清單方塊專案的以零為基底的索引。

### <a name="return-value"></a>傳回值

如果成功，則為零，如果發生錯誤，則為 CB_ERR。

### <a name="remarks"></a>備註

系統會滾動清單方塊，直到 *nIndex* 指定的專案出現在清單方塊的頂端，或達到最大捲軸範圍為止。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#40](../../mfc/reference/codesnippet/cpp/ccombobox-class_42.cpp)]

## <a name="ccomboboxshowdropdown"></a><a name="showdropdown"></a> CComboBox：： ShowDropDown

顯示或隱藏有 [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 或 [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 樣式之下拉式方塊的清單方塊。

```cpp
void ShowDropDown(BOOL bShowIt = TRUE);
```

### <a name="parameters"></a>參數

*bShowIt*<br/>
指定是否要顯示或隱藏下拉式清單方塊。 值為 TRUE 會顯示清單方塊。 FALSE 值會隱藏清單方塊。

### <a name="remarks"></a>備註

依預設，此樣式的下拉式方塊會顯示清單方塊。

這個成員函式不會影響使用 [CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 樣式所建立的下拉式方塊。

### <a name="example"></a>範例

  請參閱 [CComboBox：： GetDroppedState](#getdroppedstate)的範例。

## <a name="see-also"></a>另請參閱

[MFC 範例 CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[CButton 類別](../../mfc/reference/cbutton-class.md)<br/>
[CEdit 類別](../../mfc/reference/cedit-class.md)<br/>
[CListBox 類別](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar 類別](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic 類別](../../mfc/reference/cstatic-class.md)<br/>
[CDialog 類別](../../mfc/reference/cdialog-class.md)
