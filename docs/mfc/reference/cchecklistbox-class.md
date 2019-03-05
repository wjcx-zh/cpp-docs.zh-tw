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
ms.openlocfilehash: b34891c4f46679e43aea36a9b52d6399e020ef71
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273058"
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
|[CCheckListBox::Create](#create)|建立 Windows 檢查清單方塊，並將它附加至`CCheckListBox`物件。|
|[CCheckListBox::DrawItem](#drawitem)|當主控描繪清單方塊中變更的視覺外觀時，架構呼叫。|
|[CCheckListBox::Enable](#enable)|啟用或停用檢查清單方塊項目。|
|[CCheckListBox::GetCheck](#getcheck)|取得項目的核取方塊的狀態。|
|[CCheckListBox::GetCheckStyle](#getcheckstyle)|取得控制項的核取方塊的樣式。|
|[CCheckListBox::IsEnabled](#isenabled)|判斷是否已啟用項目。|
|[CCheckListBox::MeasureItem](#measureitem)|建立具有主控描繪樣式的清單方塊時，由架構呼叫。|
|[CCheckListBox::OnGetCheckPosition](#ongetcheckposition)|由架構呼叫以取得項目的核取方塊的位置。|
|[CCheckListBox::SetCheck](#setcheck)|設定項目的核取方塊的狀態。|
|[CCheckListBox::SetCheckStyle](#setcheckstyle)|設定控制項的核取方塊的樣式。|

## <a name="remarks"></a>備註

「 檢查清單方塊 」 顯示項目，例如檔案名稱的清單。 在清單中的每個項目有旁邊，使用者可以核取或清除核取方塊。

`CCheckListBox` 因為清單包含多個文字字串，則是只針對主控描繪的控制項。 簡單來說，檢查清單方塊包含文字字串和核取方塊，但您不需要完全的文字。 例如，您可能有一份小型點陣圖與每個項目旁的核取方塊。

若要建立您自己的檢查清單方塊，您必須衍生自己的類別，從`CCheckListBox`。 若要衍生您自己的類別，撰寫在衍生類別的建構函式，然後呼叫`Create`。

如果您想要處理的清單方塊傳送給其父代的 Windows 通知訊息 (通常是從衍生的類別[CDialog](../../mfc/reference/cdialog-class.md))，將訊息對應項目和訊息處理常式成員函式新增至每個訊息的父類別。

每個訊息對應項目都會使用下列格式：

**ON\_**_通知_ **(** _識別碼_， _memberFxn_ **)**

何處`id`指定傳送通知之控制項的子視窗識別碼和`memberFxn`是您撰寫來處理通知的父成員函式的名稱。

父代的函式原型如下所示：

`afx_msg void memberFxn();`

只有一個專為與訊息對應項目`CCheckListBox`(請參閱的訊息對應項目，但[CListBox](../../mfc/reference/clistbox-class.md)):

- ON_CLBN_CHKCHANGE 使用者已變更項目的核取方塊的狀態。

如果您檢查清單方塊的預設檢查清單方塊 （具有預設大小的核取方塊左邊的每個字串的清單），您可以使用預設[CCheckListBox::DrawItem](#drawitem)繪製檢查清單方塊。 否則，您必須覆寫[CListBox::CompareItem](../../mfc/reference/clistbox-class.md#compareitem)函式並[CCheckListBox::DrawItem](#drawitem)並[CCheckListBox::MeasureItem](#measureitem)函式。

從對話方塊範本，或是直接在您的程式碼中，您可以建立的檢查清單方塊。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListBox](../../mfc/reference/clistbox-class.md)

`CCheckListBox`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="cchecklistbox"></a>  CCheckListBox::CCheckListBox

建構 `CCheckListBox` 物件。

```
CCheckListBox();
```

### <a name="remarks"></a>備註

您建構`CCheckListBox`兩個步驟中的物件。 首先定義一個衍生自類別`CCheckListBox`，然後呼叫`Create`，其中初始化 Windows 檢查清單方塊，並將它附加至`CCheckListBox`物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#60](../../mfc/codesnippet/cpp/cchecklistbox-class_1.cpp)]

##  <a name="create"></a>  CCheckListBox::Create

建立 Windows 檢查清單方塊，並將它附加至`CCheckListBox`物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定的檢查清單方塊的樣式。 樣式必須是 LBS_HASSTRINGS 和 LBS_OWNERDRAWFIXED （清單中的所有項目都有相同的高度） 或 LBS_OWNERDRAWVARIABLE （清單中的項目都是不同高度的）。 這個樣式可以結合其他[清單方塊樣式](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)除了 LBS_USETABSTOPS。

*rect*<br/>
指定的檢查清單方塊的大小和位置。 可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](/windows/desktop/api/windef/ns-windef-tagrect)結構。

*pParentWnd*<br/>
指定檢查清單方塊的父視窗 (通常`CDialog`物件)。 它必須不是 NULL。

*nID*<br/>
指定檢查清單方塊的控制項 id。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

您建構`CCheckListBox`兩個步驟中的物件。 首先，定義一個衍生自類別`CcheckListBox`，然後呼叫`Create`，其中初始化 Windows 檢查清單方塊，並將它附加至`CCheckListBox`。 請參閱[CCheckListBox::CCheckListBox](#cchecklistbox)如需相關範例。

當`Create`執行時，Windows 會傳送[WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)， [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)， [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)，並[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)檢查清單方塊控制項的訊息。

根據預設，處理這些訊息[OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate)， [OnCreate](../../mfc/reference/cwnd-class.md#oncreate)， [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)，以及[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)成員函式在 `CWnd`基底類別。 若要擴充的預設訊息處理，將訊息對應至您的衍生的類別並覆寫先前的訊息處理常式成員函式。 覆寫`OnCreate`，例如，若要執行的新類別所需的初始設定。

套用下列[的視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)檢查清單方塊控制項：

- WS_CHILD 一律

- WS_VISIBLE 通常

- WS_DISABLED 很少

- WS_VSCROLL 若要新增 垂直捲軸

- WS_HSCROLL 若要新增 水平捲軸

- WS_GROUP 群組控制項

- WS_TABSTOP，以允許這個控制項定位停駐點

##  <a name="drawitem"></a>  CCheckListBox::DrawItem

由架構呼叫時變更為主控描繪的檢查清單方塊的視覺外觀。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>參數

*lpDrawItemStruct*<br/>
長指標[DRAWITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagdrawitemstruct)結構，其中包含的所需的繪圖類型的相關資訊。

### <a name="remarks"></a>備註

`itemAction`並`itemState`的成員`DRAWITEMSTRUCT`結構會定義要執行的繪圖動作。

根據預設，此函式會繪製預設核取方塊清單，其中包含字串的每個預設大小的核取方塊左邊的清單。 核取方塊清單的大小是在指定[建立](#create)。

若要實作繪製主控描繪檢查清單方塊不是預設值，例如檢查清單方塊的清單不是字串、 變動高度項目，或不在左邊的核取方塊，此成員函式會覆寫。 應用程式應該還原選取的顯示內容中提供所有的圖形裝置介面 (GDI) 物件*lpDrawItemStruct*之前終止此成員函式。

如果檢查清單方塊項目不是所有具有相同的高度，檢查清單方塊樣式 (依照`Create`) 必須是 * * LBS_OWNERVARIABLE，而且您必須覆寫[MeasureItem](#measureitem)函式。

##  <a name="enable"></a>  CCheckListBox::Enable

呼叫此函式可啟用或停用檢查清單方塊項目。

```
void Enable(
    int nIndex,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
若要啟用的檢查清單方塊項目的索引。

*bEnabled*<br/>
指定是否啟用或停用項目。

##  <a name="getcheck"></a>  CCheckListBox::GetCheck

擷取指定的核取方塊的狀態。

```
int GetCheck(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
包含在清單方塊的核取方塊以零為起始的索引。

### <a name="return-value"></a>傳回值

指定的核取方塊的狀態。 下表列出可能的值。

|值|描述|
|-----------|-----------------|
|BST_CHECKED|已核取方塊。|
|BST_UNCHECKED|不會檢查核取方塊。|
|BST_INDETERMINATE|核取方塊狀態為不定。|

##  <a name="getcheckstyle"></a>  CCheckListBox::GetCheckStyle

呼叫此函式可取得檢查清單方塊的樣式。

```
UINT GetCheckStyle();
```

### <a name="return-value"></a>傳回值

控制項的核取方塊的樣式。

### <a name="remarks"></a>備註

如需可能的樣式資訊，請參閱[SetCheckStyle](#setcheckstyle)。

##  <a name="isenabled"></a>  CCheckListBox::IsEnabled

呼叫此函式可判斷是否已啟用項目。

```
BOOL IsEnabled(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
項目的索引。

### <a name="return-value"></a>傳回值

如果項目啟用，則為非零否則為 0。

##  <a name="measureitem"></a>  CCheckListBox::MeasureItem

當您建立使用非預設樣式的檢查清單方塊時，由架構呼叫。

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>參數

*lpMeasureItemStruct*<br/>
長指標[MEASUREITEMSTRUCT](/windows/desktop/api/winuser/ns-winuser-tagmeasureitemstruct)結構。

### <a name="remarks"></a>備註

根據預設，此成員函式沒有任何作用。 覆寫此成員函式，並填寫`MEASUREITEMSTRUCT`結構以通知 Windows 的檢查清單方塊項目的維度。 如果檢查清單方塊以建立[LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式，架構會呼叫此成員函式的清單方塊中的每個項目。 否則，這個成員是只呼叫一次。

##  <a name="ongetcheckposition"></a>  CCheckListBox::OnGetCheckPosition

架構會呼叫此函式可取得的項目中的位置和大小的核取方塊。

```
virtual CRect OnGetCheckPosition(
    CRect rectItem,
    CRect rectCheckBox);
```

### <a name="parameters"></a>參數

*rectItem*<br/>
位置和大小的清單項目。

*rectCheckBox*<br/>
預設位置和大小的項目核取方塊。

### <a name="return-value"></a>傳回值

位置和大小的項目核取方塊。

### <a name="remarks"></a>備註

預設位置和大小的核取方塊，只會傳回預設實作 (`rectCheckBox`)。 根據預設，核取方塊對齊左上角的項目，而且是標準的核取方塊大小。 可能有您想要核取方塊，在右側，或想要放大或縮小的核取方塊的情況。 在這些情況下，覆寫`OnGetCheckPosition`變更核取方塊的位置和大小的項目中。

##  <a name="setcheck"></a>  CCheckListBox::SetCheck

設定指定的核取方塊的狀態。

```
void SetCheck(
    int nIndex,
    int nCheck);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
包含在清單方塊的核取方塊以零為起始的索引。

*nCheck*<br/>
指定的核取方塊，按鈕狀態。 請參閱 < 備註 > 一節，如需可能值。

### <a name="remarks"></a>備註

下表列出可能的值，如*n*參數。

|值|描述|
|-----------|-----------------|
|BST_CHECKED|選取指定的核取方塊。|
|BST_UNCHECKED|清除指定的核取方塊。|
|BST_INDETERMINATE|指定的核取方塊狀態設定為不定。<br /><br /> 只有使用核取方塊樣式是否 BS_AUTO3STATE 或 BS_3STATE 此狀態。 如需詳細資訊，請參閱 <<c0> [ 按鈕樣式](../../mfc/reference/styles-used-by-mfc.md#button-styles)。|

##  <a name="setcheckstyle"></a>  CCheckListBox::SetCheckStyle

呼叫此函式可將核取方塊的樣式設定檢查清單方塊中。

```
void SetCheckStyle(UINT nStyle);
```

### <a name="parameters"></a>參數

*nStyle*<br/>
決定在檢查清單方塊中的核取方塊的樣式。

### <a name="remarks"></a>備註

有效樣式有：

- BS_CHECKBOX

- BS_AUTOCHECKBOX

- BS_AUTO3STATE

- BS_3STATE

如需這些樣式資訊，請參閱[按鈕樣式](../../mfc/reference/styles-used-by-mfc.md#button-styles)。

## <a name="see-also"></a>另請參閱

[MFC 範例 TSTCON](../../visual-cpp-samples.md)<br/>
[CListBox 類別](../../mfc/reference/clistbox-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CListBox 類別](../../mfc/reference/clistbox-class.md)
