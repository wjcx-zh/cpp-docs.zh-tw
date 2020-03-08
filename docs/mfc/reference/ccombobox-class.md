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
ms.openlocfilehash: b54a1913073ca0b23aeb17a57b16f589a074637b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2020
ms.locfileid: "78890797"
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
|[CComboBox::AddString](#addstring)|在下拉式方塊清單方塊中的清單結尾處，或在具有 CBS_SORT 樣式之清單方塊的已排序位置上加入字串。|
|[CComboBox：： Clear](#clear)|刪除（清除）編輯控制項中目前的選取範圍（如果有的話）。|
|[CComboBox：： CompareItem](#compareitem)|由架構呼叫，以判斷新清單專案在已排序的主控描繪下拉式方塊中的相對位置。|
|[CComboBox：： Copy](#copy)|將目前的選取範圍（如果有的話）複製到剪貼簿上 CF_TEXT 格式。|
|[CComboBox：： Create](#create)|建立下拉式方塊，並將其附加至 `CComboBox` 物件。|
|[CComboBox：： Cut](#cut)|在編輯控制項中刪除（剪下）目前的選取範圍（如果有的話），並以 CF_TEXT 格式將刪除的文字複製到剪貼簿。|
|[CComboBox：:D eleteItem](#deleteitem)|當從主控描繪的下拉式方塊中刪除清單專案時，由架構呼叫。|
|[CComboBox：:D eleteString](#deletestring)|從下拉式方塊的清單方塊中刪除字串。|
|[CComboBox：:D ir](#dir)|將檔案名清單加入下拉式方塊的清單方塊中。|
|[CComboBox：:D rawItem](#drawitem)|當主控描繪下拉式方塊的視覺外觀變更時，由架構呼叫。|
|[CComboBox：： FindString](#findstring)|在下拉式方塊的清單方塊中，尋找包含指定前置詞的第一個字串。|
|[CComboBox：： FindStringExact](#findstringexact)|尋找符合指定之字串的第一個清單方塊字串（在下拉式方塊中）。|
|[CComboBox：： GetComboBoxInfo](#getcomboboxinfo)|抓取 `CComboBox` 物件的相關資訊。|
|[CComboBox：： GetCount](#getcount)|抓取下拉式方塊清單方塊中的專案數。|
|[CComboBox：： GetCueBanner](#getcuebanner)|取得為下拉式方塊控制項顯示的提示文字。|
|[CComboBox：： GetCurSel](#getcursel)|在下拉式方塊的清單方塊中，抓取目前選取之專案的索引（如果有的話）。|
|[CComboBox：： GetDroppedControlRect](#getdroppedcontrolrect)|抓取下拉下拉式方塊的可見（下拉）清單方塊的螢幕座標。|
|[CComboBox：： GetDroppedState](#getdroppedstate)|決定下拉下拉式方塊的清單方塊是否可見（已中斷）。|
|[CComboBox：： GetDroppedWidth](#getdroppedwidth)|抓取下拉式方塊下拉式清單方塊部分所允許的最小寬度。|
|[CComboBox：： GetEditSel](#geteditsel)|取得下拉式方塊編輯控制項中目前選取範圍的開始和結束字元位置。|
|[CComboBox：： GetExtendedUI](#getextendedui)|決定下拉式方塊是否有預設的使用者介面或擴充的使用者介面。|
|[CComboBox：： GetHorizontalExtent](#gethorizontalextent)|傳回下拉式方塊的清單方塊部分可以水準滾動的寬度（以圖元為單位）。|
|[CComboBox：： GetItemData](#getitemdata)|抓取與指定的下拉式方塊專案相關聯的應用程式提供的32位值。|
|[CComboBox：： GetItemDataPtr](#getitemdataptr)|抓取與指定的下拉式方塊專案相關聯的應用程式提供的32位指標。|
|[CComboBox：： GetItemHeight](#getitemheight)|抓取下拉式方塊中清單專案的高度。|
|[CComboBox：： GetLBText](#getlbtext)|從下拉式方塊的清單方塊中取得字串。|
|[CComboBox：： GetLBTextLen](#getlbtextlen)|取得下拉式方塊清單方塊中的字串長度。|
|[CComboBox：： GetLocale](#getlocale)|抓取下拉式方塊的地區設定識別碼。|
|[CComboBox：： GetMinVisible](#getminvisible)|取得目前下拉式列示方塊下拉式清單中可見專案的最小數目。|
|[CComboBox：： GetTopIndex](#gettopindex)|傳回下拉式方塊清單方塊部分中第一個可見專案的索引。|
|[CComboBox：： InitStorage](#initstorage)|在下拉式方塊的清單方塊部分中，預先設定項目和字串的記憶體區塊。|
|[CComboBox::InsertString](#insertstring)|將字串插入下拉式方塊的清單方塊中。|
|[CComboBox：： LimitText](#limittext)|限制使用者可以在下拉式方塊的編輯控制項中輸入的文字長度。|
|[CComboBox：： MeasureItem](#measureitem)|建立主控描繪下拉式方塊時，由架構呼叫以判斷下拉式方塊維度。|
|[CComboBox：:P aste](#paste)|將剪貼簿中的資料插入目前游標位置的編輯控制項。 只有當剪貼簿包含 CF_TEXT 格式的資料時，才會插入資料。|
|[CComboBox：： ResetContent](#resetcontent)|從清單方塊中移除所有專案，並編輯下拉式方塊的控制項。|
|[CComboBox：： SelectString](#selectstring)|在下拉式方塊的清單方塊中搜尋字串，如果找到字串，會在清單方塊中選取字串，並將字串複製到編輯控制項。|
|[CComboBox：： SetCueBanner](#setcuebanner)|設定為下拉式方塊控制項顯示的提示文字。|
|[CComboBox：： SetCurSel](#setcursel)|在下拉式方塊的清單方塊中選取字串。|
|[CComboBox：： SetDroppedWidth](#setdroppedwidth)|為下拉式方塊的下拉式清單方塊部分設定允許的最小寬度。|
|[CComboBox：： SetEditSel](#seteditsel)|選取下拉式方塊編輯控制項中的字元。|
|[CComboBox：： SetExtendedUI](#setextendedui)|針對具有 [CBS_DROPDOWN] 或 [CBS_DROPDOWNLIST] 樣式的下拉式方塊，選取預設使用者介面或擴充使用者介面。|
|[CComboBox：： SetHorizontalExtent](#sethorizontalextent)|設定下拉式方塊的清單方塊部分可以水準滾動的寬度（以圖元為單位）。|
|[CComboBox：： SetItemData](#setitemdata)|設定與下拉式方塊中指定專案相關聯的32位值。|
|[CComboBox：： SetItemDataPtr](#setitemdataptr)|在下拉式方塊中設定與指定專案相關聯的32位指標。|
|[CComboBox：： SetItemHeight](#setitemheight)|設定下拉式方塊中清單專案的高度，或下拉式方塊的編輯控制項（或靜態文字）部分的高度。|
|[CComboBox：： SetLocale](#setlocale)|設定下拉式方塊的地區設定識別碼。|
|[CComboBox：： SetMinVisibleItems](#setminvisibleitems)|設定目前下拉式方塊下拉清單中可見專案的最小數目。|
|[CComboBox：： SetTopIndex](#settopindex)|告訴下拉式方塊的清單方塊部分，在頂端顯示具有指定索引的專案。|
|[CComboBox：： ShowDropDown](#showdropdown)|顯示或隱藏具有 [CBS_DROPDOWN] 或 [CBS_DROPDOWNLIST] 樣式之下拉式方塊的清單方塊。|

## <a name="remarks"></a>備註

下拉式方塊是由與靜態控制項或編輯控制項結合的清單方塊所組成。 控制項的清單方塊部分可能會隨時顯示，或只會在使用者選取控制項旁邊的下拉箭號時下拉。

清單方塊中目前選取的專案（如果有的話）會顯示在 [靜態] 或 [編輯] 控制項中。 此外，如果下拉式方塊具有下拉清單樣式，則使用者可以輸入清單中其中一個專案的初始字元，如果可見，清單方塊將會反白顯示含有該初始字元的下一個專案。

下表比較三個下拉式方塊[樣式](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)。

|樣式|何時可見清單方塊|靜態或編輯控制項|
|-----------|-------------------------------|-----------------------------|
|簡單|一律|編輯|
|Drop-down|當下降時|編輯|
|下拉式清單|當下降時|靜態|

您可以從對話方塊範本或直接在程式碼中建立 `CComboBox` 物件。 在這兩種情況下，請先呼叫 `CComboBox` 的構造函式，以建立 `CComboBox` 物件。然後呼叫[create](#create)成員函式來建立控制項，並將它附加至 `CComboBox` 物件。

如果您想要處理下拉式方區塊轉送給其父系的 Windows 通知訊息（通常是衍生自 `CDialog`的類別），請將訊息對應專案和訊息處理常式成員函式新增至每個訊息的父類別。

每個訊息對應專案會採用下列格式：

**ON\_** _通知_ **（** _識別碼_、 _memberFxn_ **）**

其中 `id` 會指定用來傳送通知之下拉式方塊控制項的子視窗識別碼，而 `memberFxn` 則是您已撰寫來處理通知之父成員函式的名稱。

父系的函數原型如下所示：

**afx_msg** `void` `memberFxn` **（）;**

無法預測傳送特定通知的順序。 特別的是，CBN_SELCHANGE 通知可能會在 CBN_CLOSEUP 通知之前或之後發生。

可能的訊息對應專案如下所示：

- ON_CBN_CLOSEUP （Windows 3.1 和更新版本）。下拉式方塊的清單方塊已關閉。 此通知訊息不會針對具有[CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式的下拉式方區塊轉送。

- ON_CBN_DBLCLK 使用者在下拉式方塊的清單方塊中按兩下字串。 此通知訊息只會針對具有 CBS_SIMPLE 樣式的下拉式方區塊轉送。 針對具有 [ [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) ] 或 [ [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) ] 樣式的下拉式方塊，因為按一下會隱藏清單方塊，所以不會發生按兩下。

- ON_CBN_DROPDOWN 下拉式方塊的清單方塊即將關閉（顯示為可見）。 只有具有 CBS_DROPDOWN 或 CBS_DROPDOWNLIST 樣式的下拉式方塊，才會出現此通知訊息。

- ON_CBN_EDITCHANGE 使用者採取的動作可能已更改下拉式方塊編輯控制部分中的文字。 不同于 CBN_EDITUPDATE 訊息，此訊息會在 Windows 更新螢幕之後傳送。 如果下拉式方塊具有 CBS_DROPDOWNLIST 樣式，則不會傳送。

- ON_CBN_EDITUPDATE 下拉式方塊的編輯控制部分即將顯示改變的文字。 此通知訊息會在控制項格式化文字之後，但在顯示文字之前傳送。 如果下拉式方塊具有 CBS_DROPDOWNLIST 樣式，則不會傳送。

- ON_CBN_ERRSPACE 下拉式方塊無法配置足夠的記憶體來符合特定要求。

- ON_CBN_SELENDCANCEL （Windows 3.1 和更新版本）。表示應取消使用者的選擇。 使用者按一下某個專案，然後按一下另一個視窗或控制項，即可隱藏下拉式方塊的清單方塊。 此通知訊息會在 CBN_CLOSEUP 通知訊息之前傳送，以指出應該忽略使用者的選取專案。 即使未傳送 CBN_CLOSEUP 通知訊息（如具有 CBS_SIMPLE 樣式的下拉式方塊），也會傳送 CBN_SELENDCANCEL 或 CBN_SELENDOK 通知訊息。

- ON_CBN_SELENDOK 使用者選取一個專案，然後按 ENTER 鍵或按一下向下箭號，即可隱藏下拉式方塊的清單方塊。 此通知訊息會在 CBN_CLOSEUP 訊息之前傳送，以指出應將使用者的選取專案視為有效。 即使未傳送 CBN_CLOSEUP 通知訊息（如具有 CBS_SIMPLE 樣式的下拉式方塊），也會傳送 CBN_SELENDCANCEL 或 CBN_SELENDOK 通知訊息。

- ON_CBN_KILLFOCUS 下拉式方塊失去輸入焦點。

- ON_CBN_SELCHANGE 下拉式方塊清單方塊中的選取專案即將變更，這是因為使用者在清單方塊中按一下，或使用方向鍵變更選取範圍的結果。 處理此訊息時，只能透過 `GetLBText` 或另一個類似的函式來抓取下拉式方塊編輯控制項中的文字。 `GetWindowText` 無法使用。

- ON_CBN_SETFOCUS 下拉式方塊會收到輸入焦點。

如果您在對話方塊中建立 `CComboBox` 物件（透過對話資源），當使用者關閉對話方塊時，就會自動終結 `CComboBox` 物件。

如果您在另一個視窗物件中內嵌 `CComboBox` 物件，就不需要將它摧毀。 如果您在堆疊上建立 `CComboBox` 物件，它就會自動終結。 如果您使用**新**的函式在堆積上建立 `CComboBox` 物件，您必須在物件上呼叫**delete** ，以在終結 Windows 下拉式方塊時終結它。

**注意**如果您想要處理 WM_KEYDOWN 並 WM_CHAR 訊息，您必須將下拉式方塊的編輯和清單方塊控制項子類別化、從 `CEdit` 和 `CListBox`衍生類別，然後將這些訊息的處理常式加入至衍生類別。 如需詳細資訊，請參閱[CWnd：： subclasswindow 前允許](../../mfc/reference/cwnd-class.md#subclasswindow)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CComboBox`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="addstring"></a>CComboBox：： AddString

將字串加入下拉式方塊的清單方塊中。

```
int AddString(LPCTSTR lpszString);
```

### <a name="parameters"></a>參數

*lpszString*<br/>
指向要加入的以 null 結束的字串。

### <a name="return-value"></a>傳回值

如果傳回值大於或等於0，則它是清單方塊中字串之以零為起始的索引。 如果發生錯誤，則傳回值為 CB_ERR;如果空間不足，無法儲存新的字串，傳回值就會 CB_ERRSPACE。

### <a name="remarks"></a>備註

如果清單方塊不是以[CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式建立，則字串會加入至清單的結尾。 否則，會將字串插入清單中，並排序清單。

> [!NOTE]
>  Windows `ComboBoxEx` 控制項不支援這個函式。 如需這個控制項的詳細資訊，請參閱 Windows SDK 中的[ComboBoxEx 控制項](/windows/win32/Controls/comboboxex-controls)。

若要將字串插入清單中的特定位置，請使用[InsertString](#insertstring)成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#3](../../mfc/reference/codesnippet/cpp/ccombobox-class_1.cpp)]

##  <a name="ccombobox"></a>CComboBox：： CComboBox

建構 `CComboBox` 物件。

```
CComboBox();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_2.cpp)]

##  <a name="clear"></a>CComboBox：： Clear

在下拉式方塊的編輯控制項中刪除（清除）目前的選取專案（如果有的話）。

```
void Clear();
```

### <a name="remarks"></a>備註

若要刪除目前的選取範圍，並將已刪除的內容放到剪貼簿上，請使用[Cut](#cut)成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#4](../../mfc/reference/codesnippet/cpp/ccombobox-class_3.cpp)]

##  <a name="compareitem"></a>CComboBox：： CompareItem

由架構呼叫，以判斷新專案在排序的主控描繪下拉式方塊的清單方塊部分中的相對位置。

```
virtual int CompareItem(LPCOMPAREITEMSTRUCT lpCompareItemStruct);
```

### <a name="parameters"></a>參數

*lpCompareItemStruct*<br/>
[COMPAREITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-compareitemstruct)結構的長指標。

### <a name="return-value"></a>傳回值

表示 `COMPAREITEMSTRUCT` 結構中所描述的兩個專案的相對位置。 可以是下列其中任何一個值：

|值|意義|
|-----------|-------------|
|- 1|專案1會在專案2之前排序。|
|0|專案1和專案2會排序相同的。|
|1|專案1會在專案2之後排序。|

如需 `COMPAREITEMSTRUCT`的描述，請參閱[CWnd：： OnCompareItem](../../mfc/reference/cwnd-class.md#oncompareitem) 。

### <a name="remarks"></a>備註

根據預設，此成員函式不會執行任何工作。 如果您建立具有 LBS_SORT 樣式的主控描繪下拉式方塊，您必須覆寫這個成員函式，以協助架構排序加入至清單方塊的新專案。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#5](../../mfc/reference/codesnippet/cpp/ccombobox-class_4.cpp)]

##  <a name="copy"></a>CComboBox：： Copy

將下拉式方塊的編輯控制項中的目前選取專案（如果有的話）複製到剪貼簿的 CF_TEXT 格式中。

```
void Copy();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#6](../../mfc/reference/codesnippet/cpp/ccombobox-class_5.cpp)]

##  <a name="create"></a>CComboBox：： Create

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
指定下拉式方塊的樣式。 將[下拉式列示方塊樣式](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)套用至方塊。

*各種*<br/>
指向下拉式方塊的位置和大小。 可以是[RECT 結構](/windows/win32/api/windef/ns-windef-rect)或 `CRect` 物件。

*pParentWnd*<br/>
指定下拉式方塊的父視窗（通常是 `CDialog`）。 它不得為 NULL。

*nID*<br/>
指定下拉式方塊的控制項識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

您可以使用兩個步驟來建立 `CComboBox` 物件。 首先，呼叫此函式，然後呼叫 `Create`，它會建立 Windows 下拉式方塊，並將其附加至 `CComboBox` 物件。

當 `Create` 執行時，Windows 會將[WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)、 [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)、 [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)和[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)訊息傳送至下拉式方塊。

根據預設，這些訊息會由 `CWnd` 基類中的[OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate)、 [OnCreate](../../mfc/reference/cwnd-class.md#oncreate)、 [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)和[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)成員函式來處理。 若要擴充預設訊息處理，請從 `CComboBox`衍生類別，將訊息對應加入至新的類別，並覆寫先前的訊息處理常式成員函式。 例如，覆寫 `OnCreate`，以針對新的類別執行所需的初始化。

將下列[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)套用至下拉式方塊控制項。 :

- 一律 WS_CHILD

- WS_VISIBLE 通常

- WS_DISABLED 很少

- WS_VSCROLL 在下拉式方塊中新增清單方塊的垂直捲動

- WS_HSCROLL 在下拉式方塊中新增清單方塊的水準滾動

- WS_GROUP 至群組控制項

- WS_TABSTOP 在 tab 鍵順序中包含下拉式方塊

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_6.cpp)]

##  <a name="cut"></a>CComboBox：： Cut

刪除（剪下）下拉式方塊編輯控制項中目前的選取範圍，並以 CF_TEXT 格式將刪除的文字複製到剪貼簿。

```
void Cut();
```

### <a name="remarks"></a>備註

若要刪除目前的選取範圍，而不將已刪除的文字放在剪貼簿上，請呼叫[Clear](#clear)成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#7](../../mfc/reference/codesnippet/cpp/ccombobox-class_7.cpp)]

##  <a name="deleteitem"></a>CComboBox：:D eleteItem

當使用者從主控描繪 `CComboBox` 物件中刪除專案，或終結下拉式方塊時，由架構呼叫。

```
virtual void DeleteItem(LPDELETEITEMSTRUCT lpDeleteItemStruct);
```

### <a name="parameters"></a>參數

*lpDeleteItemStruct*<br/>
Windows [DELETEITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-deleteitemstruct)結構的長指標，其中包含已刪除之專案的相關資訊。 如需此結構的說明，請參閱[CWnd：： OnDeleteItem](../../mfc/reference/cwnd-class.md#ondeleteitem) 。

### <a name="remarks"></a>備註

此函式的預設實作不做任何動作。 視需要覆寫此函式以重繪下拉式方塊。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#8](../../mfc/reference/codesnippet/cpp/ccombobox-class_8.cpp)]

##  <a name="deletestring"></a>CComboBox：:D eleteString

從下拉式方塊中刪除 [位置] *nIndex*中的專案。

```
int DeleteString(UINT nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定要刪除之字串的索引。

### <a name="return-value"></a>傳回值

如果傳回值大於或等於0，則為清單中剩餘的字串計數。 如果*nIndex*指定的索引大於清單中的專案數，則傳回值為 CB_ERR。

### <a name="remarks"></a>備註

*NIndex*之後的所有專案現在會向下移動一個位置。 例如，如果下拉式方塊包含兩個專案，刪除第一個專案會使其餘專案現在位於第一個位置。 *nIndex*= 0，代表第一個位置的專案。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#9](../../mfc/reference/codesnippet/cpp/ccombobox-class_9.cpp)]

##  <a name="dir"></a>CComboBox：:D ir

將檔案名或磁片磁碟機清單新增至下拉式方塊的清單方塊中。

```
int Dir(
    UINT attr,
    LPCTSTR lpszWildCard);
```

### <a name="parameters"></a>參數

*attr*<br/>
可以是[CFile：： GetStatus](../../mfc/reference/cfile-class.md#getstatus)中所描述之**列舉**值的任何組合，或下列值的任何組合：

- DDL_READWRITE 檔案可以讀取或寫入。

- DDL_READONLY 檔案可以讀取，但無法寫入。

- DDL_HIDDEN 檔案已隱藏，且不會出現在目錄清單中。

- DDL_SYSTEM 檔案是系統檔案。

- DDL_DIRECTORY *LpszWildCard*所指定的名稱會指定目錄。

- DDL_ARCHIVE 檔案已封存。

- DDL_DRIVES 包含符合*lpszWildCard*所指定之名稱的所有磁片磁碟機。

- DDL_EXCLUSIVE 獨佔旗標。 如果設定獨佔旗標，只會列出指定類型的檔案。 否則，除了 "normal" 檔案之外，還會列出指定類型的檔案。

*lpszWildCard*<br/>
指向檔案規格字串。 字串可以包含萬用字元（例如，*.\*）。

### <a name="return-value"></a>傳回值

如果傳回值大於或等於0，則它是最後新增至清單的檔案名之以零為起始的索引。 如果發生錯誤，則傳回值為 CB_ERR;如果空間不足，無法儲存新的字串，傳回值就會 CB_ERRSPACE。

### <a name="remarks"></a>備註

Windows `ComboBoxEx` 控制項不支援這個函式。 如需這個控制項的詳細資訊，請參閱 Windows SDK 中的[ComboBoxEx 控制項](/windows/win32/Controls/comboboxex-controls)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#10](../../mfc/reference/codesnippet/cpp/ccombobox-class_10.cpp)]

##  <a name="drawitem"></a>CComboBox：:D rawItem

當主控描繪下拉式列示方塊的視覺外觀變更時，由架構呼叫。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>參數

*lpDrawItemStruct*<br/>
[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)結構的指標，其中包含所需繪圖類型的相關資訊。

### <a name="remarks"></a>備註

`DRAWITEMSTRUCT` 結構的 `itemAction` 成員會定義要執行的繪圖動作。 如需此結構的說明，請參閱[CWnd：： OnDrawItem](../../mfc/reference/cwnd-class.md#ondrawitem) 。

根據預設，此成員函式不會執行任何工作。 覆寫這個成員函式，以針對主控描繪 `CComboBox` 物件來執行繪製。 在此成員函式終止之前，應用程式應該還原針對*lpDrawItemStruct*中提供的顯示內容所選取的所有圖形裝置介面（GDI）物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#11](../../mfc/reference/codesnippet/cpp/ccombobox-class_11.cpp)]

##  <a name="findstring"></a>CComboBox：： FindString

在下拉式方塊的清單方塊中，尋找（但不選取）包含指定前置詞的第一個字串。

```
int FindString(
    int nStartAfter,
    LPCTSTR lpszString) const;
```

### <a name="parameters"></a>參數

*nStartAfter*<br/>
包含專案之以零為基底的索引，這是要搜尋的第一個專案之前。 當搜尋到達清單方塊的底部時，它會從清單方塊的頂端繼續回到*nStartAfter*所指定的專案。 如果為-1，則會從頭開始搜尋整個清單方塊。

*lpszString*<br/>
指向以 null 終止的字串，其中包含要搜尋的前置詞。 搜尋會區分大小寫，因此這個字串可以包含大寫和小寫字母的任意組合。

### <a name="return-value"></a>傳回值

如果傳回值大於或等於0，則它是符合專案之以零為起始的索引。 如果搜尋失敗，則會 CB_ERR。

### <a name="remarks"></a>備註

Windows `ComboBoxEx` 控制項不支援這個函式。 如需這個控制項的詳細資訊，請參閱 Windows SDK 中的[ComboBoxEx 控制項](/windows/win32/Controls/comboboxex-controls)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#12](../../mfc/reference/codesnippet/cpp/ccombobox-class_12.cpp)]

##  <a name="findstringexact"></a>CComboBox：： FindStringExact

呼叫 `FindStringExact` 成員函式，尋找符合*lpszFind*中指定之字串的第一個清單方塊字串（在下拉式方塊中）。

```
int FindStringExact(
    int nIndexStart,
    LPCTSTR lpszFind) const;
```

### <a name="parameters"></a>參數

*nIndexStart*<br/>
在要搜尋的第一個專案之前，指定專案之以零為起始的索引。 當搜尋到達清單方塊的底部時，它會從清單方塊的頂端繼續回到*nIndexStart*所指定的專案。 如果*nIndexStart*為-1，則會從頭開始搜尋整個清單方塊。

*lpszFind*<br/>
指向要搜尋的以 null 結束的字串。 這個字串可以包含完整的檔案名，包括副檔名。 搜尋不區分大小寫，因此這個字串可以包含大寫和小寫字母的任意組合。

### <a name="return-value"></a>傳回值

符合專案之以零為起始的索引，如果搜尋失敗，則為 CB_ERR。

### <a name="remarks"></a>備註

如果下拉式方塊是使用擁有者繪製樣式所建立，但沒有[CBS_HASSTRINGS](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式，`FindStringExact` 會嘗試比對*lpszFind*的值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#13](../../mfc/reference/codesnippet/cpp/ccombobox-class_13.cpp)]

##  <a name="getcomboboxinfo"></a>CComboBox：： GetComboBoxInfo

抓取 `CComboBox` 物件的資訊。

```
BOOL GetComboBoxInfo(PCOMBOBOXINFO pcbi) const;
```

### <a name="parameters"></a>參數

*pcbi*<br/>
[COMBOBOXINFO](/windows/win32/api/winuser/ns-winuser-comboboxinfo)結構的指標。

### <a name="return-value"></a>傳回值

成功時傳回 TRUE，失敗時傳回 FALSE。

### <a name="remarks"></a>備註

此成員函式會模擬[CB_GETCOMBOBOXINFO](/windows/win32/Controls/cb-getcomboboxinfo)訊息的功能，如 Windows SDK 中所述。

##  <a name="getcount"></a>CComboBox：： GetCount

呼叫這個成員函式可抓取下拉式方塊清單方塊部分中的專案數。

```
int GetCount() const;
```

### <a name="return-value"></a>傳回值

項目數目。 傳回的計數大於最後一個專案的索引值（索引以零為基底）。 如果發生錯誤，就會 CB_ERR。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#14](../../mfc/reference/codesnippet/cpp/ccombobox-class_14.cpp)]

##  <a name="getcuebanner"></a>CComboBox：： GetCueBanner

取得為下拉式方塊控制項顯示的提示文字。

```
CString GetCueBanner() const;

BOOL GetCueBanner(
    LPTSTR lpszText,
    int cchText) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*lpszText*|脫銷接收提示橫幅文字之緩衝區的指標。|
|*cchText*|在*LpszText*參數所指向的緩衝區大小。|

### <a name="return-value"></a>傳回值

在第一個多載中， [CString](../../atl-mfc-shared/using-cstring.md)物件，其中包含提示橫幅文字（如果有的話）。否則為長度為零的 `CString` 物件。

-或-

在第二個多載中，如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

提示文字是在下拉式方塊控制項的輸入區域中顯示的提示。 提示文字會顯示，直到使用者提供輸入為止。

這個方法會傳送[CB_GETCUEBANNER](/windows/win32/Controls/cb-getcuebanner)訊息，如 Windows SDK 所述。

##  <a name="getcursel"></a>CComboBox：： GetCurSel

呼叫這個成員函式，以判斷下拉式方塊中所選取的專案。

```
int GetCurSel() const;
```

### <a name="return-value"></a>傳回值

下拉式方塊清單方塊中目前所選取專案的以零為起始的索引，如果未選取任何專案，則為 CB_ERR。

### <a name="remarks"></a>備註

`GetCurSel` 會傳回清單中的索引。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#15](../../mfc/reference/codesnippet/cpp/ccombobox-class_15.cpp)]

##  <a name="getdroppedcontrolrect"></a>CComboBox：： GetDroppedControlRect

呼叫 `GetDroppedControlRect` 成員函式，以抓取下拉下拉式方塊的可見（下拉）清單方塊的螢幕座標。

```
void GetDroppedControlRect(LPRECT lprect) const;
```

### <a name="parameters"></a>參數

*lprect*<br/>
指向用來接收座標的[矩形結構](/windows/win32/api/windef/ns-windef-rect)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#16](../../mfc/reference/codesnippet/cpp/ccombobox-class_16.cpp)]

##  <a name="getdroppedstate"></a>CComboBox：： GetDroppedState

呼叫 `GetDroppedState` 成員函式，以判斷下拉式方塊的清單方塊是否可見（已中斷）。

```
BOOL GetDroppedState() const;
```

### <a name="return-value"></a>傳回值

如果清單方塊為可見，則為非零。否則為0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#17](../../mfc/reference/codesnippet/cpp/ccombobox-class_17.cpp)]

##  <a name="getdroppedwidth"></a>CComboBox：： GetDroppedWidth

呼叫此函式可取得下拉式方塊清單方塊的最小允許寬度（以圖元為單位）。

```
int GetDroppedWidth() const;
```

### <a name="return-value"></a>傳回值

如果成功，則為允許的最小寬度（以圖元為單位）;否則，CB_ERR。

### <a name="remarks"></a>備註

此函式僅適用于具有[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式的下拉式方塊。

根據預設，下拉式清單方塊的允許寬度下限為0。 您可以呼叫[SetDroppedWidth](#setdroppedwidth)來設定允許的最小寬度。 當下拉式方塊的清單方塊部分顯示時，其寬度會大於允許寬度或下拉式方塊寬度的最小值。

### <a name="example"></a>範例

  請參閱[SetDroppedWidth](#setdroppedwidth)的範例。

##  <a name="geteditsel"></a>CComboBox：： GetEditSel

取得下拉式方塊編輯控制項中目前選取範圍的開始和結束字元位置。

```
DWORD GetEditSel() const;
```

### <a name="return-value"></a>傳回值

32位值，其中包含低序位字組中的開始位置，以及在高序位單字選取範圍結尾之後第一個 nonselected 字元的位置。 如果在沒有編輯控制項的下拉式方塊上使用此函式，則會傳回 CB_ERR。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#18](../../mfc/reference/codesnippet/cpp/ccombobox-class_18.cpp)]

##  <a name="getextendedui"></a>CComboBox：： GetExtendedUI

呼叫 `GetExtendedUI` 成員函式，以判斷下拉式方塊是否有預設的使用者介面或擴充的使用者介面。

```
BOOL GetExtendedUI() const;
```

### <a name="return-value"></a>傳回值

如果下拉式方塊具有延伸的使用者介面，則為非零值;否則為0。

### <a name="remarks"></a>備註

擴充的使用者介面可以透過下列方式識別：

- 按一下靜態控制項只會針對具有[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式的下拉式方塊顯示清單方塊。

- 按向下鍵會顯示清單方塊（F4 已停用）。

當專案清單不可見時，會停用靜態控制項中的滾動（方向鍵已停用）。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#19](../../mfc/reference/codesnippet/cpp/ccombobox-class_19.cpp)]

##  <a name="gethorizontalextent"></a>CComboBox：： GetHorizontalExtent

從下拉式方塊中抓取下拉式方塊的清單方塊部分可以水準滾動的寬度（以圖元為單位）。

```
UINT GetHorizontalExtent() const;
```

### <a name="return-value"></a>傳回值

下拉式方塊清單方塊部分的可滾動寬度（以圖元為單位）。

### <a name="remarks"></a>備註

只有在下拉式方塊的清單方塊部分有水準捲軸時，才適用這種情況。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#20](../../mfc/reference/codesnippet/cpp/ccombobox-class_20.cpp)]

##  <a name="getitemdata"></a>CComboBox：： GetItemData

抓取與指定的下拉式方塊專案相關聯的應用程式提供的32位值。

```
DWORD_PTR GetItemData(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
包含下拉式方塊清單方塊中專案之以零為起始的索引。

### <a name="return-value"></a>傳回值

與專案相關聯的32位值，如果發生錯誤，則為 CB_ERR。

### <a name="remarks"></a>備註

32位值可以使用[SetItemData](#setitemdata)成員函式呼叫的*dwItemData*參數來設定。 如果要抓取的32位值是指標（**void** <strong>\*</strong>），請使用 `GetItemDataPtr` 成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#21](../../mfc/reference/codesnippet/cpp/ccombobox-class_21.cpp)]

##  <a name="getitemdataptr"></a>CComboBox：： GetItemDataPtr

抓取與指定的下拉式方塊專案相關聯的應用程式提供的32位值做為指標（**void** <strong>\*</strong>）。

```
void* GetItemDataPtr(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
包含下拉式方塊清單方塊中專案之以零為起始的索引。

### <a name="return-value"></a>傳回值

抓取指標，如果發生錯誤，則為-1。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#22](../../mfc/reference/codesnippet/cpp/ccombobox-class_22.cpp)]

##  <a name="getitemheight"></a>CComboBox：： GetItemHeight

呼叫 `GetItemHeight` 成員函式，以取得下拉式方塊中清單專案的高度。

```
int GetItemHeight(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定要抓取其高度之下拉式方塊的元件。 如果*nIndex*參數為-1，則會抓取下拉式方塊的編輯控制項（或靜態文字）部分的高度。 如果下拉式方塊具有[CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式， *nIndex*會指定要抓取其高度的清單專案之以零為基底的索引。 否則， *nIndex*應該設定為0。

### <a name="return-value"></a>傳回值

下拉式方塊中指定專案的高度（以圖元為單位）。 如果發生錯誤，傳回值是 CB_ERR。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#23](../../mfc/reference/codesnippet/cpp/ccombobox-class_23.cpp)]

##  <a name="getlbtext"></a>CComboBox：： GetLBText

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
包含要複製的清單方塊字串之以零為基底的索引。

*lpszText*<br/>
指向要接收字串的緩衝區。 緩衝區必須有足夠的空間來表示字串和終止的 null 字元。

*rString*<br/>
`CString` 的參考。

### <a name="return-value"></a>傳回值

字串的長度（以位元組為單位），不包括終止的 null 字元。 如果*nIndex*未指定有效的索引，則會 CB_ERR 傳回值。

### <a name="remarks"></a>備註

這個成員函式的第二種形式會以專案的文字填入 `CString` 物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#24](../../mfc/reference/codesnippet/cpp/ccombobox-class_24.cpp)]

##  <a name="getlbtextlen"></a>CComboBox：： GetLBTextLen

取得下拉式方塊清單方塊中的字串長度。

```
int GetLBTextLen(int nIndex) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
包含清單方塊字串之以零為基底的索引。

### <a name="return-value"></a>傳回值

字串的長度（以位元組為單位），不包括終止的 null 字元。 如果*nIndex*未指定有效的索引，則會 CB_ERR 傳回值。

### <a name="example"></a>範例

  請參閱[CComboBox：： GetLBText](#getlbtext)的範例。

##  <a name="getlocale"></a>CComboBox：： GetLocale

抓取下拉式方塊所使用的地區設定。

```
LCID GetLocale() const;
```

### <a name="return-value"></a>傳回值

下拉式方塊中字串的地區設定識別碼（LCID）值。

### <a name="remarks"></a>備註

例如，會使用地區設定來決定排序下拉式方塊中的字串排序次序。

### <a name="example"></a>範例

  請參閱[CComboBox：： SetLocale](#setlocale)的範例。

##  <a name="getminvisible"></a>CComboBox：： GetMinVisible

取得目前下拉式方塊控制項下拉式清單中可見專案的最小數目。

```
int GetMinVisible() const;
```

### <a name="return-value"></a>傳回值

目前下拉式清單中可見專案的最小數目。

### <a name="remarks"></a>備註

這個方法會傳送[CB_GETMINVISIBLE](/windows/win32/Controls/cb-setminvisible)訊息，如 Windows SDK 所述。

##  <a name="gettopindex"></a>CComboBox：： GetTopIndex

在下拉式方塊的清單方塊部分中，抓取第一個可見專案之以零為起始的索引。

```
int GetTopIndex() const;
```

### <a name="return-value"></a>傳回值

如果成功，則為下拉式方塊的清單方塊部分中第一個可見專案之以零為起始的索引，否則為 CB_ERR。

### <a name="remarks"></a>備註

一開始，專案0位於清單方塊的頂端，但如果清單方塊已滾動，則另一個專案可能在頂端。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#25](../../mfc/reference/codesnippet/cpp/ccombobox-class_25.cpp)]

##  <a name="initstorage"></a>CComboBox：： InitStorage

配置記憶體，以在下拉式方塊的清單方塊部分中儲存清單方塊專案。

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

如果成功，則在需要重新配置記憶體之前，下拉式方塊的清單方塊部分可以儲存的最大專案數，否則 CB_ERRSPACE，表示沒有足夠的記憶體可用。

### <a name="remarks"></a>備註

先呼叫此函式，再將大量專案新增至 `CComboBox`的清單方塊部分。

僅限 Windows 95/98： *wParam*參數限制為16位值。 這表示清單方塊不能包含超過32767個專案。 雖然專案數受到限制，清單方塊中的專案總大小只受限於可用的記憶體。

此函式有助於加速初始化具有大量專案的清單方塊（超過100）。 它會預先配置指定的記憶體數量，讓後續的[AddString](#addstring)、 [InsertString](#insertstring)和[Dir](#dir)函式會採用最短的可能時間。 您可以使用參數的預估值。 如果您高估值，則會配置一些額外的記憶體;如果您低估了，一般配置會用於超過預先配置金額的專案。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#26](../../mfc/reference/codesnippet/cpp/ccombobox-class_26.cpp)]

##  <a name="insertstring"></a>CComboBox：： InsertString

將字串插入下拉式方塊的清單方塊中。

```
int InsertString(
    int nIndex,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
包含要接收字串之清單方塊中位置以零為基底的索引。 如果此參數為-1，則字串會加入至清單的結尾。

*lpszString*<br/>
指向要插入的 null 結尾字串。

### <a name="return-value"></a>傳回值

已插入字串之位置以零為基底的索引。 如果發生錯誤，傳回值是 CB_ERR。 如果空間不足，無法存放新的字串，傳回值是 CB_ERRSPACE。

### <a name="remarks"></a>備註

不像 [AddString](#addstring) 成員函式， `InsertString` 成員函式不會排序 [CBS_SORT](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) 樣式的清單。

> [!NOTE]
>  Windows `ComboBoxEx` 控制項不支援這個函式。 如需這個控制項的詳細資訊，請參閱 Windows SDK 中的[ComboBoxEx 控制項](/windows/win32/Controls/comboboxex-controls)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#27](../../mfc/reference/codesnippet/cpp/ccombobox-class_27.cpp)]

##  <a name="limittext"></a>CComboBox：： LimitText

限制使用者可以在下拉式方塊的編輯控制項中輸入的文字長度（以位元組為單位）。

```
BOOL LimitText(int nMaxChars);
```

### <a name="parameters"></a>參數

*nMaxChars*<br/>
指定使用者可以輸入之文字的長度（以位元組為單位）。 如果此參數為0，則文字長度會設定為65535個位元組。

### <a name="return-value"></a>傳回值

如果成功，則為非零值。 如果針對樣式為[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)的下拉式方塊或沒有編輯控制項的下拉式方塊呼叫，則傳回值會是 CB_ERR。

### <a name="remarks"></a>備註

如果下拉式方塊沒有樣式[CBS_AUTOHSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)，將文字限制設定為大於編輯控制項的大小，將不會有任何作用。

`LimitText` 只會限制使用者可以輸入的文字。 當傳送訊息時，它不會影響任何已在編輯控制項中的文字，也不會影響在選取清單方塊中的字串時，複製到編輯控制項的文字長度。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#28](../../mfc/reference/codesnippet/cpp/ccombobox-class_28.cpp)]

##  <a name="measureitem"></a>CComboBox：： MeasureItem

當建立具有擁有者繪製樣式的下拉式方塊時，由架構呼叫。

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>參數

*lpMeasureItemStruct*<br/>
[MEASUREITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-measureitemstruct)結構的長指標。

### <a name="remarks"></a>備註

根據預設，此成員函式不會執行任何工作。 覆寫這個成員函式並填入 `MEASUREITEMSTRUCT` 結構，以通知視窗下拉式方塊中清單方塊的維度。 如果使用[CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式建立下拉式方塊，則架構會為清單方塊中的每個專案呼叫這個成員函式。 否則，這個成員只會呼叫一次。

在以 `CWnd` 的[SubclassDlgItem](../../mfc/reference/cwnd-class.md#subclassdlgitem)成員函式建立的主控描繪下拉式方塊中使用 CBS_OWNERDRAWFIXED 樣式牽涉到進一步的程式設計考慮。 請參閱技術提示[14](../../mfc/tn014-custom-controls.md)中的討論。

如需 `MEASUREITEMSTRUCT` 結構的說明，請參閱[CWnd：： OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#29](../../mfc/reference/codesnippet/cpp/ccombobox-class_29.cpp)]

##  <a name="paste"></a>CComboBox：:P aste

將剪貼簿中的資料插入下拉式方塊在目前游標位置的編輯控制項。

```
void Paste();
```

### <a name="remarks"></a>備註

只有當剪貼簿包含 CF_TEXT 格式的資料時，才會插入資料。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#30](../../mfc/reference/codesnippet/cpp/ccombobox-class_30.cpp)]

##  <a name="resetcontent"></a>CComboBox：： ResetContent

從清單方塊中移除所有專案，並編輯下拉式方塊的控制項。

```
void ResetContent();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#31](../../mfc/reference/codesnippet/cpp/ccombobox-class_31.cpp)]

##  <a name="selectstring"></a>CComboBox：： SelectString

在下拉式方塊的清單方塊中搜尋字串，如果找到字串，會在清單方塊中選取字串，並將其複製到編輯控制項。

```
int SelectString(
    int nStartAfter,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>參數

*nStartAfter*<br/>
包含專案之以零為基底的索引，這是要搜尋的第一個專案之前。 當搜尋到達清單方塊的底部時，它會從清單方塊的頂端繼續回到*nStartAfter*所指定的專案。 如果為-1，則會從頭開始搜尋整個清單方塊。

*lpszString*<br/>
指向以 null 終止的字串，其中包含要搜尋的前置詞。 搜尋會區分大小寫，因此這個字串可以包含大寫和小寫字母的任意組合。

### <a name="return-value"></a>傳回值

如果找到字串，則為所選取專案的以零為起始的索引。 如果搜尋失敗，則傳回值為 CB_ERR，而且目前的選取範圍不會變更。

### <a name="remarks"></a>備註

只有在其初始字元（從起點）符合前置字串中的字元時，才會選取字串。

請注意，`SelectString` 和 `FindString` 成員函式都會尋找字串，但是 `SelectString` 成員函式也會選取字串。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#32](../../mfc/reference/codesnippet/cpp/ccombobox-class_32.cpp)]

##  <a name="setcuebanner"></a>CComboBox：： SetCueBanner

設定為下拉式方塊控制項顯示的提示文字。

```
BOOL SetCueBanner(LPCTSTR lpszText);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*lpszText*|在以 null 終止的緩衝區指標，其中包含提示文字。|

### <a name="return-value"></a>傳回值

如果方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

提示文字是在下拉式方塊控制項的輸入區域中顯示的提示。 提示文字會顯示，直到使用者提供輸入為止。

這個方法會傳送[CB_SETCUEBANNER](/windows/win32/Controls/cb-setcuebanner)訊息，如 Windows SDK 所述。

### <a name="example"></a>範例

下列程式碼範例會定義用來以程式設計方式存取下拉式方塊控制項的變數*m_combobox*。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>範例

下列程式碼範例會設定下拉式方塊控制項的提示橫幅。

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

##  <a name="setcursel"></a>CComboBox：： SetCurSel

在下拉式方塊的清單方塊中選取字串。

```
int SetCurSel(int nSelect);
```

### <a name="parameters"></a>參數

*N 請選取*<br/>
指定要選取之字串的以零為基底的索引。 如果為-1，則會移除清單方塊中目前的選取範圍，並清除編輯控制項。

### <a name="return-value"></a>傳回值

如果訊息成功，則為所選取之專案的以零為起始的索引。 如果*n 請選取*大於清單中的專案數，或如果*n 請選取*設定為-1 （清除選取範圍），則傳回值為 CB_ERR。

### <a name="remarks"></a>備註

如有必要，清單方塊會將字串滾動到 view （如果清單方塊為可見）。 下拉式方塊的編輯控制項中的文字會變更，以反映新的選取專案。 清單方塊中任何先前的選取專案都會被移除。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#33](../../mfc/reference/codesnippet/cpp/ccombobox-class_35.cpp)]

##  <a name="setdroppedwidth"></a>CComboBox：： SetDroppedWidth

呼叫此函式可設定下拉式方塊清單方塊的最小允許寬度（以圖元為單位）。

```
int SetDroppedWidth(UINT nWidth);
```

### <a name="parameters"></a>參數

*nWidth*<br/>
下拉式方塊的清單方塊部分允許的最小寬度（以圖元為單位）。

### <a name="return-value"></a>傳回值

如果成功，則為清單方塊的新寬度，否則 CB_ERR。

### <a name="remarks"></a>備註

此函式僅適用于具有[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式的下拉式方塊。

根據預設，下拉式清單方塊的允許寬度下限為0。 當下拉式方塊的清單方塊部分顯示時，其寬度會大於允許寬度或下拉式方塊寬度的最小值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#34](../../mfc/reference/codesnippet/cpp/ccombobox-class_36.cpp)]

##  <a name="seteditsel"></a>CComboBox：： SetEditSel

選取下拉式方塊編輯控制項中的字元。

```
BOOL SetEditSel(
    int nStartChar,
    int nEndChar);
```

### <a name="parameters"></a>參數

*nStartChar*<br/>
指定開始位置。 如果開始位置設定為-1，則會移除任何現有的選取專案。

*nEndChar*<br/>
指定結束位置。 如果結束位置設為-1，則會選取從開始位置到編輯控制項中最後一個字元的所有文字。

### <a name="return-value"></a>傳回值

如果成員函式成功，則為非零;否則為0。 如果 `CComboBox` 有[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式，或沒有清單方塊，就會 CB_ERR。

### <a name="remarks"></a>備註

這些位置是以零為基底。 若要選取編輯控制項的第一個字元，您可以指定開始位置為0。 結束位置是在要選取的最後一個字元之後的字元。 例如，若要選取編輯控制項的前四個字元，您可以使用0的開始位置和結束位置4。

> [!NOTE]
>  Windows `ComboBoxEx` 控制項不支援這個函式。 如需這個控制項的詳細資訊，請參閱 Windows SDK 中的[ComboBoxEx 控制項](/windows/win32/Controls/comboboxex-controls)。

### <a name="example"></a>範例

  請參閱[CComboBox：： GetEditSel](#geteditsel)的範例。

##  <a name="setextendedui"></a>CComboBox：： SetExtendedUI

呼叫 `SetExtendedUI` 成員函式，針對具有[CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)或[CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式的下拉式方塊選取預設使用者介面或擴充使用者介面。

```
int SetExtendedUI(BOOL bExtended = TRUE);
```

### <a name="parameters"></a>參數

*bExtended*<br/>
指定下拉式方塊是否應使用延伸使用者介面或預設使用者介面。 值為 TRUE 時，會選取擴充的使用者介面。值為 FALSE 時，會選取標準使用者介面。

### <a name="return-value"></a>傳回值

CB_OKAY 如果作業成功，則為，如果發生錯誤，則為 CB_ERR。

### <a name="remarks"></a>備註

擴充的使用者介面可以透過下列方式識別：

- 按一下靜態控制項只會針對具有 CBS_DROPDOWNLIST 樣式的下拉式方塊顯示清單方塊。

- 按向下鍵會顯示清單方塊（F4 已停用）。

當專案清單不可見時，會停用靜態控制項中的滾動（已停用方向鍵）。

### <a name="example"></a>範例

  請參閱[CComboBox：： GetExtendedUI](#getextendedui)的範例。

##  <a name="sethorizontalextent"></a>CComboBox：： SetHorizontalExtent

設定下拉式方塊的清單方塊部分可以水準滾動的寬度（以圖元為單位）。

```
void SetHorizontalExtent(UINT nExtent);
```

### <a name="parameters"></a>參數

*nExtent*<br/>
指定下拉式方塊的清單方塊部分可以水準滾動的圖元數目。

### <a name="remarks"></a>備註

如果清單方塊的寬度小於此值，水準捲軸會在清單方塊中水準滾動專案。 如果清單方塊的寬度等於或大於這個值，則會隱藏水準捲軸，或者，如果下拉式方塊具有[CBS_DISABLENOSCROLL](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式，則會停用。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#35](../../mfc/reference/codesnippet/cpp/ccombobox-class_37.cpp)]

##  <a name="setitemdata"></a>CComboBox：： SetItemData

設定與下拉式方塊中指定專案相關聯的32位值。

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

如果發生錯誤，CB_ERR。

### <a name="remarks"></a>備註

如果32位專案是指標，請使用 `SetItemDataPtr` 成員函式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#36](../../mfc/reference/codesnippet/cpp/ccombobox-class_38.cpp)]

##  <a name="setitemdataptr"></a>CComboBox：： SetItemDataPtr

將與下拉式列示方塊中指定專案相關聯的32位值設定為指定的指標（**void** <strong>\*</strong>）。

```
int SetItemDataPtr(
    int nIndex,
    void* pData);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
包含專案之以零為基底的索引。

*pData*<br/>
包含與專案相關聯的指標。

### <a name="return-value"></a>傳回值

如果發生錯誤，CB_ERR。

### <a name="remarks"></a>備註

這個指標在下拉式方塊的生命週期中仍然有效，即使在新增或移除專案時，下拉式方塊中的專案相對位置也可能會變更。 因此，方塊內的專案索引可能會變更，但指標仍然可靠。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#37](../../mfc/reference/codesnippet/cpp/ccombobox-class_39.cpp)]

##  <a name="setitemheight"></a>CComboBox：： SetItemHeight

呼叫 `SetItemHeight` 成員函式，以設定下拉式方塊中清單專案的高度，或下拉式方塊的編輯控制項（或靜態文字）部分的高度。

```
int SetItemHeight(
    int nIndex,
    UINT cyItemHeight);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定是否已設定清單專案的高度或下拉式方塊的編輯控制項（或靜態文字）部分的高度。

如果下拉式方塊具有[CBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式，則*nIndex*會指定要設定其高度的清單專案之以零為起始的索引。否則， *nIndex*必須是0，而且將會設定所有清單專案的高度。

如果*nIndex*為-1，則會設定下拉式方塊的編輯控制項或靜態文字部分的高度。

*cyItemHeight*<br/>
指定*nIndex*所識別之下拉式列示方塊元件的高度（以圖元為單位）。

### <a name="return-value"></a>傳回值

如果索引或高度無效，則為 CB_ERR;否則為0。

### <a name="remarks"></a>備註

下拉式方塊的編輯控制項（或靜態文字）部分的高度是設定為獨立于清單專案的高度。 應用程式必須確保編輯控制項（或靜態文字）部分的高度不會小於特定清單方塊專案的高度。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#38](../../mfc/reference/codesnippet/cpp/ccombobox-class_40.cpp)]

##  <a name="setlocale"></a>CComboBox：： SetLocale

設定此下拉式方塊的地區設定識別碼。

```
LCID SetLocale(LCID nNewLocale);
```

### <a name="parameters"></a>參數

*nNewLocale*<br/>
要針對下拉式方塊設定的新地區設定識別碼（LCID）值。

### <a name="return-value"></a>傳回值

此下拉式方塊的先前地區設定識別碼（LCID）值。

### <a name="remarks"></a>備註

如果未呼叫 `SetLocale`，則會從系統取得預設地區設定。 您可以使用控制台的區域（或國際）應用程式來修改這個系統預設的地區設定。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#39](../../mfc/reference/codesnippet/cpp/ccombobox-class_41.cpp)]

##  <a name="setminvisibleitems"></a>CComboBox：： SetMinVisibleItems

設定目前下拉式方塊控制項下拉式清單中可見專案的最小數目。

```
BOOL SetMinVisibleItems(int iMinVisible);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*iMinVisible*|在指定可見專案的最小數目。|

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[CB_SETMINVISIBLE](/windows/win32/Controls/cb-setminvisible)訊息，如 Windows SDK 所述。

### <a name="example"></a>範例

下列程式碼範例會定義用來以程式設計方式存取下拉式方塊控制項的變數*m_combobox*。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CComboBox_s1#1](../../mfc/reference/codesnippet/cpp/ccombobox-class_33.h)]

### <a name="example"></a>範例

下列程式碼範例會將20個專案插入下拉式方塊控制項的下拉式清單中。 然後，它會指定當使用者按下下拉箭號時，最少顯示10個專案。

[!code-cpp[NVC_MFC_CComboBox_s1#2](../../mfc/reference/codesnippet/cpp/ccombobox-class_34.cpp)]

##  <a name="settopindex"></a>CComboBox：： SetTopIndex

確保下拉式方塊的清單方塊部分可以看到特定專案。

```
int SetTopIndex(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定清單方塊專案以零為基底的索引。

### <a name="return-value"></a>傳回值

如果成功，則為零，如果發生錯誤，則為 CB_ERR。

### <a name="remarks"></a>備註

系統會滾動清單方塊，直到*nIndex*所指定的專案出現在清單方塊的頂端，或已達到最大滾動範圍為止。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CComboBox#40](../../mfc/reference/codesnippet/cpp/ccombobox-class_42.cpp)]

##  <a name="showdropdown"></a>CComboBox：： ShowDropDown

顯示或隱藏具有 [ [CBS_DROPDOWN](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) ] 或 [ [CBS_DROPDOWNLIST](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles) ] 樣式之下拉式方塊的清單方塊。

```
void ShowDropDown(BOOL bShowIt = TRUE);
```

### <a name="parameters"></a>參數

*bShowIt*<br/>
指定是否要顯示或隱藏下拉式清單方塊。 值為 TRUE 時，會顯示清單方塊。 值為 FALSE 時，會隱藏清單方塊。

### <a name="remarks"></a>備註

根據預設，此樣式的下拉式方塊會顯示清單方塊。

這個成員函式不會影響以[CBS_SIMPLE](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)樣式建立的下拉式方塊。

### <a name="example"></a>範例

  請參閱[CComboBox：： GetDroppedState](#getdroppedstate)的範例。

## <a name="see-also"></a>另請參閱

[MFC 範例 CTRLBARS](../../overview/visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[CButton 類別](../../mfc/reference/cbutton-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CListBox 類別](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar 類別](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic 類別](../../mfc/reference/cstatic-class.md)<br/>
[CDialog 類別](../../mfc/reference/cdialog-class.md)
