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
ms.openlocfilehash: dc0e80e80d61104a4d8cb5f1cfd4e26a64c42249
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752739"
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
|[C支票清單框:C支票清單框](#cchecklistbox)|建構 `CCheckListBox` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[C 檢查清單盒:建立](#create)|創建 Windows 檢查表框並將其`CCheckListBox`附加到 物件。|
|[CCheckListBox::D原始專案](#drawitem)|當所有者繪製清單框的可視方面發生更改時,由框架調用。|
|[CCheckListBox:啟用](#enable)|啟用或禁用清單框項。|
|[CCheckListBox:抓取檢查](#getcheck)|獲取專案的狀態複選框。|
|[CCheckListBox:抓取檢查樣式](#getcheckstyle)|獲取控制項複選框的樣式。|
|[CCheckListBox:已開啟](#isenabled)|確定是否啟用了項。|
|[CCheckListBox:測量專案](#measureitem)|創建具有擁有者繪製樣式的清單框時,由框架調用。|
|[CChecklistBox::打開檢查位置](#ongetcheckposition)|由框架調用以獲取專案的位置複選框。|
|[CCheckListBox:設定檢查](#setcheck)|設置項目的狀態複選框。|
|[CCheckListBox:設定檢查樣式](#setcheckstyle)|設置控件複選框的樣式。|

## <a name="remarks"></a>備註

「清單框」顯示項目清單,如檔名。 清單中的每個項旁邊都有一個複選框,用戶可以選中或清除。

`CCheckListBox`僅適用於所有者繪製的控制項,因為清單包含的比文本字串多。 最簡單的是,清單框包含文字字串和複選框,但您根本不需要文本。 例如,您可以有一個小位圖清單,每個項目旁邊都有一個複選框。

要創建自己的清單框,必須從`CCheckListBox`派生您自己的類。 要派生自己的類,請為派生類編寫一個構造函數,然後呼叫`Create`。

如果要處理清單框發送到其父項的 Windows 通知消息(通常是從[CDialog](../../mfc/reference/cdialog-class.md)派生的類),則為每個消息向父類添加消息映射條目和消息處理程式成員函數。

每個訊息對應項目以以下的檔案:

**開啟\_**_通知_**(ID** _ _,_成員Fxn_ **)**

其中`id`指定傳送通知的控制項的子視窗`memberFxn`ID,以及 您為處理通知而編寫的父成員函數的名稱。

父函數原型如下所示:

`afx_msg void memberFxn();`

只有一個消息映射項目專門與`CCheckListBox`(但也看到[CListBox](../../mfc/reference/clistbox-class.md)的消息映射項目 ):

- ON_CLBN_CHKCHANGE使用者已更改項目的複選框的狀態。

如果檢查表框是預設檢查表框(每個複選框左側的預設大小複選框的字串清單),則可以使用預設[CCheckListBox::DrawItem](#drawitem)繪製檢查表框。 否則,您必須覆蓋[CListBox:比較專案](../../mfc/reference/clistbox-class.md#compareitem)功能和[CCheckListBox::D原始專案和](#drawitem) [CCheckListBox:度量專案](#measureitem)函數。

可以從對話框範本或直接在代碼中創建檢查框。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListBox](../../mfc/reference/clistbox-class.md)

`CCheckListBox`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="cchecklistboxcchecklistbox"></a><a name="cchecklistbox"></a>C支票清單框:C支票清單框

建構 `CCheckListBox` 物件。

```
CCheckListBox();
```

### <a name="remarks"></a>備註

分兩步`CCheckListBox`構造物件。 首先定義派生自`CCheckListBox`的 類`Create`,然後調用 ,該類初始化 Windows`CCheckListBox`檢查表框並將其 附加到物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#60](../../mfc/codesnippet/cpp/cchecklistbox-class_1.cpp)]

## <a name="cchecklistboxcreate"></a><a name="create"></a>C 檢查清單盒:建立

創建 Windows 檢查表框並將其`CCheckListBox`附加到 物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定檢查表框的樣式。 樣式必須LBS_HASSTRINGS,並且LBS_OWNERDRAWFIXED(清單中的所有專案都具有相同的高度)或LBS_OWNERDRAWVARIABLE(清單中的專案高度不同)。 此樣式可以與其他[列表框樣式](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)組合,但LBS_USETABSTOPS除外。

*矩形*<br/>
指定檢查表框大小和位置。 可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](/windows/win32/api/windef/ns-windef-rect)結構。

*pparentwnd*<br/>
指定檢查表框的父視窗(通常是`CDialog`物件)。 它不得為 NULL。

*nID*<br/>
指定檢查表框的控制 ID。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

分兩步`CCheckListBox`構造物件。 首先,定義派生的`CcheckListBox`類別,然後呼`Create`叫,該類別初始化 Windows 檢查表框並將`CCheckListBox`其附加到 。 有關示例,請參閱[CCheckListBox:CCheckListBox。](#cchecklistbox)

執行`Create`時,Windows[WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)會將 WM_NCCREATE、WM_CREATE、WM_NCCALCSIZE 和[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)訊息發送到[WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)[WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)檢查表框控制項。

默認情況下,這些消息`CWnd`由基類中的[OnNcCreate、OnCreate、OnNcCalcsize](../../mfc/reference/cwnd-class.md#onnccreate)和[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)[OnCreate](../../mfc/reference/cwnd-class.md#oncreate)[OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)成員函數處理。 要擴展預設消息處理,請向派生類添加消息映射,並重寫前面的消息處理程序成員函數。 例如`OnCreate`,重寫以執行新類所需的初始化。

將以下[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)套用於檢查箱控制:

- WS_CHILD始終

- WS_VISIBLE 通常

- WS_DISABLED很少

- WS_VSCROLL捲動動

- WS_HSCROLL 新增水平捲動條

- WS_GROUP元件

- WS_TABSTOP 允許選項卡到此控制項

## <a name="cchecklistboxdrawitem"></a><a name="drawitem"></a>CCheckListBox::D原始專案

當所有者繪製的檢查表框的可視方面發生更改時,由框架調用。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>參數

*lpDraw 專案已結*<br/>
指向[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)結構的長指標,其中包含有關所需繪圖類型的資訊。

### <a name="remarks"></a>備註

結構`itemAction``itemState`和`DRAWITEMSTRUCT`成員定義要執行的繪圖操作。

預設情況下,此函數繪製一個預設複選框清單,該複選框清單由每個字串列表組成,每個字串列表左側有一個預設大小的複選框。 勾選方塊清單大小是在[「建立](#create)」 中指定的。

重寫此成員函數以實現不預設的擁有者繪製清單框的繪製,例如包含清單不是字串、具有可變高項或未在左側的複選框的檢查表框。 應用程式應還原在此成員函數終止之前為*lpDrawItemStruct*中提供的顯示上下文選擇的所有圖形設備介面 (GDI) 物件。

如果清單框項的高度不同,則清單框樣式(在`Create`) 中指定必須**LBS_OWNERVARIABLE**,並且必須覆蓋[度量項](#measureitem)函數。

## <a name="cchecklistboxenable"></a><a name="enable"></a>CCheckListBox:啟用

呼叫此函數以啟用或禁用檢查表框項。

```cpp
void Enable(
    int nIndex,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
要啟用的檢查表框項的索引。

*b 啟用*<br/>
指定項目是啟用還是禁用。

## <a name="cchecklistboxgetcheck"></a><a name="getcheck"></a>CCheckListBox:抓取檢查

檢索指定複選框的狀態。

```
int GetCheck(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
清單框中包含的複選框的零基索引。

### <a name="return-value"></a>傳回值

指定複選框的狀態。 下表列出了可能的值。

|值|描述|
|-----------|-----------------|
|BST_CHECKED|核取方塊已核取。|
|BST_UNCHECKED|未選中該複選框。|
|BST_INDETERMINATE|複選框狀態不確定。|

## <a name="cchecklistboxgetcheckstyle"></a><a name="getcheckstyle"></a>CCheckListBox:抓取檢查樣式

調用此函數獲取清單框的樣式。

```
UINT GetCheckStyle();
```

### <a name="return-value"></a>傳回值

控件複選框的樣式。

### <a name="remarks"></a>備註

有關可能樣式的資訊,請參閱[設定檢查樣式](#setcheckstyle)。

## <a name="cchecklistboxisenabled"></a><a name="isenabled"></a>CCheckListBox:已開啟

調用此函數以確定是否啟用了項。

```
BOOL IsEnabled(int nIndex);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
項的索引。

### <a name="return-value"></a>傳回值

如果啟用了項,則非零;否則 0。

## <a name="cchecklistboxmeasureitem"></a><a name="measureitem"></a>CCheckListBox:測量專案

創建具有非預設樣式的檢查表框時,由框架調用。

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>參數

*lp 測量項目結構*<br/>
指向[測量結構](/windows/win32/api/winuser/ns-winuser-measureitemstruct)的長指標。

### <a name="remarks"></a>備註

默認情況下,此成員函數不執行任何操作。 重寫此成員函數並填寫`MEASUREITEMSTRUCT`結構,以通知 Windows 檢查表框項的尺寸。 如果使用[LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)樣式創建檢查表框,則框架將針對清單框中的每個專案調用此成員函數。 否則,僅調用此成員一次。

## <a name="cchecklistboxongetcheckposition"></a><a name="ongetcheckposition"></a>CChecklistBox::打開檢查位置

框架呼叫此函數以獲取項中複選方塊的位置和大小。

```
virtual CRect OnGetCheckPosition(
    CRect rectItem,
    CRect rectCheckBox);
```

### <a name="parameters"></a>參數

*rectItem*<br/>
清單項目的位置和大小。

*rectCheckBox*<br/>
項目複選方塊的預設位置和大小。

### <a name="return-value"></a>傳回值

專案的位置和大小複選框。

### <a name="remarks"></a>備註

預設實現僅返回複選方塊`rectCheckBox`() 的預設位置和大小。 默認情況下,複選框在專案的左上角對齊,是標準複選框大小。 在某些情況下,您可能希望右側的複選框,或者需要更大或更小的複選框。 在這些情況下,重寫`OnGetCheckPosition`以更改物料中的複選框位置和大小。

## <a name="cchecklistboxsetcheck"></a><a name="setcheck"></a>CCheckListBox:設定檢查

設置指定複選框的狀態。

```cpp
void SetCheck(
    int nIndex,
    int nCheck);
```

### <a name="parameters"></a>參數

*nIndex*<br/>
清單框中包含的複選框的零基索引。

*N檢查*<br/>
指定複選框的按鈕狀態。 有關可能的值,請參閱備註部分。

### <a name="remarks"></a>備註

下表列出了*nCheck*參數的可能值。

|值|描述|
|-----------|-----------------|
|BST_CHECKED|選擇指定的複選框。|
|BST_UNCHECKED|清除指定的複選方塊。|
|BST_INDETERMINATE|將指定的複選框狀態設置為不確定。<br /><br /> 僅當複選框樣式BS_AUTO3STATE或BS_3STATE時,此狀態才可用。 有關詳細資訊,請參閱[按鍵樣式](../../mfc/reference/styles-used-by-mfc.md#button-styles)。|

## <a name="cchecklistboxsetcheckstyle"></a><a name="setcheckstyle"></a>CCheckListBox:設定檢查樣式

調用此函數以在檢查表框中設置複選框的樣式。

```cpp
void SetCheckStyle(UINT nStyle);
```

### <a name="parameters"></a>參數

*nStyle*<br/>
確定檢查表框中複選框的樣式。

### <a name="remarks"></a>備註

有效樣式包括:

- BS_CHECKBOX

- BS_AUTOCHECKBOX

- BS_AUTO3STATE

- BS_3STATE

有關這些樣式的資訊,請參閱[按鍵樣式](../../mfc/reference/styles-used-by-mfc.md#button-styles)。

## <a name="see-also"></a>另請參閱

[MFC 樣品 TSTCON](../../overview/visual-cpp-samples.md)<br/>
[CListBox 類別](../../mfc/reference/clistbox-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CListBox 類別](../../mfc/reference/clistbox-class.md)
