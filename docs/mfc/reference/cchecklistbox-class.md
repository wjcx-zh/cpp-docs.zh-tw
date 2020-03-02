---
title: CCheckListBox 類別
ms.date: 11/04/2016
f1_keywords:
- CCheckListBox
- AFXWIN/CCheckListBox
- AFXWIN/CCheckListBox::CCheckListBox
- AFXWIN/CCheckListBox::Create
- AFXWIN/CCheckListBox::DrawItem
- AFXWIN/CCheckListBox::Enable
- AFXWIN/CCheckListBox::GetCheck
- AFXWIN/CCheckListBox::GetCheckStyle
- AFXWIN/CCheckListBox::IsEnabled
- AFXWIN/CCheckListBox::MeasureItem
- AFXWIN/CCheckListBox::OnGetCheckPosition
- AFXWIN/CCheckListBox::SetCheck
- AFXWIN/CCheckListBox::SetCheckStyle
helpviewer_keywords:
- CCheckListBox [MFC], CCheckListBox
- CCheckListBox [MFC], Create
- CCheckListBox [MFC], DrawItem
- CCheckListBox [MFC], Enable
- CCheckListBox [MFC], GetCheck
- CCheckListBox [MFC], GetCheckStyle
- CCheckListBox [MFC], IsEnabled
- CCheckListBox [MFC], MeasureItem
- CCheckListBox [MFC], OnGetCheckPosition
- CCheckListBox [MFC], SetCheck
- CCheckListBox [MFC], SetCheckStyle
ms.assetid: 1dd78438-00e8-441c-b36f-9c4f9ac0d019
ms.openlocfilehash: cd50711813a3cfc1305cd5558c95e909ddbfc3f2
ms.sourcegitcommit: ab8d7b47b63b62892a1256a09b1324a9a136eccf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/02/2020
ms.locfileid: "78215516"
---
# <a name="cchecklistbox-class"></a>CCheckListBox 類別

提供 Windows 檢查清單方塊的功能。

## <a name="syntax"></a>語法

```
class CCheckListBox : public CListBox
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CCheckListBox::CCheckListBox](#cchecklistbox)|建構 `CCheckListBox` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CCheckListBox：： Create](#create)|建立 Windows 檢查清單方塊，並將其附加至 `CCheckListBox` 物件。|
|[CCheckListBox：:D rawItem](#drawitem)|當主控描繪清單方塊的視覺外觀變更時，由架構呼叫。|
|[CCheckListBox：： Enable](#enable)|啟用或停用檢查清單方塊專案。|
|[CCheckListBox::GetCheck](#getcheck)|取得專案核取方塊的狀態。|
|[CCheckListBox::GetCheckStyle](#getcheckstyle)|取得控制項之核取方塊的樣式。|
|[CCheckListBox：： IsEnabled](#isenabled)|判斷專案是否已啟用。|
|[CCheckListBox::MeasureItem](#measureitem)|當建立具有擁有者繪製樣式的清單方塊時，由架構呼叫。|
|[CCheckListBox::OnGetCheckPosition](#ongetcheckposition)|由架構呼叫以取得專案之核取方塊的位置。|
|[CCheckListBox：： SetCheck](#setcheck)|設定專案核取方塊的狀態。|
|[CCheckListBox::SetCheckStyle](#setcheckstyle)|設定控制項的核取方塊樣式。|

## <a name="remarks"></a>備註

[檢查清單方塊] 會顯示專案清單，例如檔案名。 清單中的每個專案都有一個核取方塊，使用者可加以檢查或清除。

`CCheckListBox` 僅適用于主控描繪的控制項，因為此清單包含超過個文字字串。 最簡單的是，檢查清單方塊包含文字字串和核取方塊，但您不需要有文字。 例如，您可以在每個專案旁邊有一個核取方塊的小型點陣圖清單。

若要建立您自己的檢查清單方塊，您必須從 `CCheckListBox`衍生您自己的類別。 若要衍生您自己的類別，請撰寫衍生類別的函式，然後呼叫 `Create`。

如果您想要處理清單方塊傳送到其父系的 Windows 通知訊息（通常是衍生自[CDialog](../../mfc/reference/cdialog-class.md)的類別），請將訊息對應專案和訊息處理常式成員函式新增至每個訊息的父類別。

每個訊息對應專案會採用下列格式：

**ON\_** _通知_ **（** _識別碼_、 _memberFxn_ **）**

其中 `id` 會指定傳送通知之控制項的子視窗識別碼，而 `memberFxn` 則是您已撰寫來處理通知之父成員函式的名稱。

父系的函數原型如下所示：

`afx_msg void memberFxn();`

只有一個訊息對應專案專門用於 `CCheckListBox` （但另請參閱[CListBox](../../mfc/reference/clistbox-class.md)的訊息對應專案）：

- ON_CLBN_CHKCHANGE 使用者已變更專案核取方塊的狀態。

如果您的檢查清單方塊是預設的檢查清單方塊（每個字串的左邊有預設大小的核取方塊），您可以使用預設的[CCheckListBox：:D rawitem](#drawitem)來繪製檢查清單方塊。 否則，您必須覆寫[CListBox：： CompareItem](../../mfc/reference/clistbox-class.md#compareitem)函數和[CCheckListBox：:D rawitem](#drawitem)和[CCheckListBox：： MeasureItem](#measureitem)函數。

您可以從對話方塊範本，或直接在程式碼中建立檢查清單方塊。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListBox](../../mfc/reference/clistbox-class.md)

`CCheckListBox`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="cchecklistbox"></a>CCheckListBox::CCheckListBox

建構 `CCheckListBox` 物件。

```
CCheckListBox();
```

### <a name="remarks"></a>備註

您可以使用兩個步驟來建立 `CCheckListBox` 物件。 先定義衍生自 `CCheckListBox`的類別，然後呼叫 `Create`，這會初始化 Windows 檢查清單方塊，並將其附加至 `CCheckListBox` 物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#60](../../mfc/codesnippet/cpp/cchecklistbox-class_1.cpp)]

##  <a name="create"></a>CCheckListBox：： Create

建立 Windows 檢查清單方塊，並將其附加至 `CCheckListBox` 物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定檢查清單方塊的樣式。 樣式必須是 LBS_HASSTRINGS 且 LBS_OWNERDRAWFIXED （清單中的所有專案都是相同的高度）或 LBS_OWNERDRAWVARIABLE （清單中的專案有不同的高度）。 此樣式可以與其他[清單方塊樣式](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)結合，但 LBS_USETABSTOPS 除外。

*各種*<br/>
指定檢查清單方塊大小和位置。 可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](/windows/win32/api/windef/ns-windef-rect)結構。

*pParentWnd*<br/>
指定檢查清單方塊的父視窗（通常是 `CDialog` 物件）。 它不得為 NULL。

*nID*<br/>
指定檢查清單方塊的控制項 ID。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

您可以使用兩個步驟來建立 `CCheckListBox` 物件。 首先，定義衍生自 `CcheckListBox` 的類別，然後呼叫 `Create`，這會初始化 Windows 檢查清單方塊，並將其附加至 `CCheckListBox`。 如需範例，請參閱[CCheckListBox：： CCheckListBox](#cchecklistbox) 。

當 `Create` 執行時，Windows 會將[WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)、 [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)、 [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)和[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)訊息傳送至檢查清單方塊控制項。

根據預設，這些訊息會由 `CWnd` 基類中的[OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate)、 [OnCreate](../../mfc/reference/cwnd-class.md#oncreate)、 [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)和[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)成員函式來處理。 若要擴充預設訊息處理，請將訊息對應加入至您的衍生類別，並覆寫先前的訊息處理常式成員函式。 例如，覆寫 `OnCreate`，以針對新的類別執行所需的初始化。

將下列[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)套用至檢查清單方塊控制項：

- 一律 WS_CHILD

- WS_VISIBLE 通常

- WS_DISABLED 很少

- WS_VSCROLL 加入垂直捲動條

- WS_HSCROLL 加入水準捲軸

- WS_GROUP 至群組控制項

- WS_TABSTOP 允許將此控制項按 tab 鍵

##  <a name="drawitem"></a>CCheckListBox：:D rawItem

當主控描繪的檢查清單方塊的視覺外觀變更時，由架構呼叫。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>參數

*lpDrawItemStruct*<br/>
[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)結構的長指標，其中包含所需繪圖類型的相關資訊。

### <a name="remarks"></a>備註

`DRAWITEMSTRUCT` 結構的 `itemAction` 和 `itemState` 成員，會定義要執行的繪圖動作。

根據預設，此函式會繪製預設的核取方塊清單，其中包含每個字串的清單，其中每一個都有左側的預設大小核取方塊。 核取方塊清單大小是 [[建立](#create)] 中指定的大小。

覆寫這個成員函式，以實作為非預設的主控描繪檢查清單方塊繪圖，例如清單方塊不是字串、具有變動高度的專案，或是沒有左邊的核取方塊。 在此成員函式終止之前，應用程式應該還原針對*lpDrawItemStruct*中提供的顯示內容所選取的所有圖形裝置介面（GDI）物件。

如果檢查清單方塊專案的高度不相同，則必須**LBS_OWNERVARIABLE**檢查清單方塊樣式（在 `Create`中指定），而且您必須覆寫[MeasureItem](#measureitem)函式。

##  <a name="enable"></a>CCheckListBox：： Enable

呼叫此函式可啟用或停用檢查清單方塊專案。

```
void Enable(
    int nIndex,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要啟用之檢查清單方塊專案的索引。

*bEnabled*<br/>
指定是否啟用或停用專案。

##  <a name="getcheck"></a>CCheckListBox::GetCheck

抓取指定核取方塊的狀態。

```
int GetCheck(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
清單方塊中包含之核取方塊的以零為起始的索引。

### <a name="return-value"></a>傳回值

指定核取方塊的狀態。 下表列出可能的值。

|值|描述|
|-----------|-----------------|
|BST_CHECKED|核取方塊已核取。|
|BST_UNCHECKED|未核取此核取方塊。|
|BST_INDETERMINATE|核取方塊狀態為 [不確定]。|

##  <a name="getcheckstyle"></a>CCheckListBox::GetCheckStyle

呼叫此函式可取得檢查清單方塊的樣式。

```
UINT GetCheckStyle();
```

### <a name="return-value"></a>傳回值

控制項的核取方塊樣式。

### <a name="remarks"></a>備註

如需可能樣式的詳細資訊，請參閱[SetCheckStyle](#setcheckstyle)。

##  <a name="isenabled"></a>CCheckListBox：： IsEnabled

呼叫此函式可判斷專案是否已啟用。

```
BOOL IsEnabled(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
專案的索引。

### <a name="return-value"></a>傳回值

如果專案已啟用，則為非零值;否則為0。

##  <a name="measureitem"></a>CCheckListBox::MeasureItem

當建立具有非預設樣式的檢查清單方塊時，由架構呼叫。

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>參數

*lpMeasureItemStruct*<br/>
[MEASUREITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-measureitemstruct)結構的長指標。

### <a name="remarks"></a>備註

根據預設，此成員函式不會執行任何工作。 覆寫這個成員函式並填入 `MEASUREITEMSTRUCT` 結構，以通知 Windows 檢查清單方塊專案的維度。 如果使用[LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式建立了檢查清單方塊，則架構會為清單方塊中的每個專案呼叫這個成員函式。 否則，這個成員只會呼叫一次。

##  <a name="ongetcheckposition"></a>CCheckListBox::OnGetCheckPosition

架構會呼叫這個函式，以取得專案中核取方塊的位置和大小。

```
virtual CRect OnGetCheckPosition(
    CRect rectItem,
    CRect rectCheckBox);
```

### <a name="parameters"></a>參數

*rectItem*<br/>
清單專案的位置和大小。

*rectCheckBox*<br/>
專案核取方塊的預設位置和大小。

### <a name="return-value"></a>傳回值

專案核取方塊的位置和大小。

### <a name="remarks"></a>備註

預設的執行只會傳回復選框的預設位置和大小（`rectCheckBox`）。 根據預設，核取方塊會在專案的左上角對齊，而且是標準的核取方塊大小。 在某些情況下，您可能會想要右邊的核取方塊，或需要較大或較小的核取方塊。 在這些情況下，請覆寫 `OnGetCheckPosition` 變更專案中的核取方塊位置和大小。

##  <a name="setcheck"></a>CCheckListBox：： SetCheck

設定指定核取方塊的狀態。

```
void SetCheck(
    int nIndex,
    int nCheck);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
清單方塊中包含之核取方塊的以零為起始的索引。

*nCheck*<br/>
指定核取方塊的按鈕狀態。 如需可能的值，請參閱備註一節。

### <a name="remarks"></a>備註

下表列出*nCheck*參數的可能值。

|值|描述|
|-----------|-----------------|
|BST_CHECKED|選取指定的核取方塊。|
|BST_UNCHECKED|清除指定的核取方塊。|
|BST_INDETERMINATE|將指定的核取方塊狀態設定為 [不確定]。<br /><br /> 只有當核取方塊樣式是 BS_AUTO3STATE 或 BS_3STATE 時，才可以使用此狀態。 如需詳細資訊，請參閱[按鈕樣式](../../mfc/reference/styles-used-by-mfc.md#button-styles)。|

##  <a name="setcheckstyle"></a>CCheckListBox::SetCheckStyle

呼叫此函式可設定檢查清單方塊中的核取方塊樣式。

```
void SetCheckStyle(UINT nStyle);
```

### <a name="parameters"></a>參數

*nStyle*<br/>
決定檢查清單方塊中核取方塊的樣式。

### <a name="remarks"></a>備註

有效的樣式包括：

- BS_CHECKBOX

- BS_AUTOCHECKBOX

- BS_AUTO3STATE

- BS_3STATE

如需這些樣式的詳細資訊，請參閱[按鈕樣式](../../mfc/reference/styles-used-by-mfc.md#button-styles)。

## <a name="see-also"></a>另請參閱

[MFC 範例 TSTCON](../../overview/visual-cpp-samples.md)<br/>
[CListBox 類別](../../mfc/reference/clistbox-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CListBox 類別](../../mfc/reference/clistbox-class.md)
