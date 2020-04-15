---
title: CButton 類別
ms.date: 11/04/2016
f1_keywords:
- CButton
- AFXWIN/CButton
- AFXWIN/CButton::CButton
- AFXWIN/CButton::Create
- AFXWIN/CButton::DrawItem
- AFXWIN/CButton::GetBitmap
- AFXWIN/CButton::GetButtonStyle
- AFXWIN/CButton::GetCheck
- AFXWIN/CButton::GetCursor
- AFXWIN/CButton::GetIcon
- AFXWIN/CButton::GetIdealSize
- AFXWIN/CButton::GetImageList
- AFXWIN/CButton::GetNote
- AFXWIN/CButton::GetNoteLength
- AFXWIN/CButton::GetSplitGlyph
- AFXWIN/CButton::GetSplitImageList
- AFXWIN/CButton::GetSplitInfo
- AFXWIN/CButton::GetSplitSize
- AFXWIN/CButton::GetSplitStyle
- AFXWIN/CButton::GetState
- AFXWIN/CButton::GetTextMargin
- AFXWIN/CButton::SetBitmap
- AFXWIN/CButton::SetButtonStyle
- AFXWIN/CButton::SetCheck
- AFXWIN/CButton::SetCursor
- AFXWIN/CButton::SetDropDownState
- AFXWIN/CButton::SetIcon
- AFXWIN/CButton::SetImageList
- AFXWIN/CButton::SetNote
- AFXWIN/CButton::SetSplitGlyph
- AFXWIN/CButton::SetSplitImageList
- AFXWIN/CButton::SetSplitInfo
- AFXWIN/CButton::SetSplitSize
- AFXWIN/CButton::SetSplitStyle
- AFXWIN/CButton::SetState
- AFXWIN/CButton::SetTextMargin
helpviewer_keywords:
- CButton [MFC], CButton
- CButton [MFC], Create
- CButton [MFC], DrawItem
- CButton [MFC], GetBitmap
- CButton [MFC], GetButtonStyle
- CButton [MFC], GetCheck
- CButton [MFC], GetCursor
- CButton [MFC], GetIcon
- CButton [MFC], GetIdealSize
- CButton [MFC], GetImageList
- CButton [MFC], GetNote
- CButton [MFC], GetNoteLength
- CButton [MFC], GetSplitGlyph
- CButton [MFC], GetSplitImageList
- CButton [MFC], GetSplitInfo
- CButton [MFC], GetSplitSize
- CButton [MFC], GetSplitStyle
- CButton [MFC], GetState
- CButton [MFC], GetTextMargin
- CButton [MFC], SetBitmap
- CButton [MFC], SetButtonStyle
- CButton [MFC], SetCheck
- CButton [MFC], SetCursor
- CButton [MFC], SetDropDownState
- CButton [MFC], SetIcon
- CButton [MFC], SetImageList
- CButton [MFC], SetNote
- CButton [MFC], SetSplitGlyph
- CButton [MFC], SetSplitImageList
- CButton [MFC], SetSplitInfo
- CButton [MFC], SetSplitSize
- CButton [MFC], SetSplitStyle
- CButton [MFC], SetState
- CButton [MFC], SetTextMargin
ms.assetid: cdc76d5b-31da-43c5-bc43-fde4cb39de5b
ms.openlocfilehash: 05ad60855cd03115cf88ab2b51e56e6a26822035
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352438"
---
# <a name="cbutton-class"></a>CButton 類別

提供 Windows 按鈕控制項的功能。

## <a name="syntax"></a>語法

```
class CButton : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[C按鈕::C按鈕](#cbutton)|建構 `CButton` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[C 按鈕:建立](#create)|創建 Windows 按鈕控制件並將其`CButton`附加到 物件。|
|[CButton::D原始專案](#drawitem)|覆蓋以繪製所有者繪製`CButton`的物件。|
|[C按鈕::取得點陣圖](#getbitmap)|檢索以前使用[SetBitmap](#setbitmap)設置的位圖的句柄。|
|[C按鈕::取得按鈕樣式](#getbuttonstyle)|檢索有關按鈕控制樣式的資訊。|
|[C按鈕::取得檢查](#getcheck)|檢索按鈕控件的檢查狀態。|
|[C按鈕::取得游標](#getcursor)|檢索以前使用[SetCursor](#setcursor)設定的游標影像的句柄。|
|[C按鈕::取得圖示](#geticon)|檢索以前使用[SetIcon](#seticon)設定的圖示的句柄。|
|[C按鈕::取得理想尺寸](#getidealsize)|檢索按鈕控制的理想大小。|
|[C 按鈕:抓取圖片清單](#getimagelist)|檢索按鈕控制件的影像清單。|
|[C按鈕::取得筆記](#getnote)|檢索目前命令連結控制件的註釋元件。|
|[C按鈕::取得註解長度](#getnotelength)|檢索目前命令連結控制件的註釋文本的長度。|
|[C按鈕::取得分割字形](#getsplitglyph)|檢索與當前拆分按鈕控件關聯的字形。|
|[C 按鈕:抓取分割影像清單](#getsplitimagelist)|檢索目前拆分按鈕控制件的影像清單。|
|[C 按鈕:抓取分資訊](#getsplitinfo)|檢索定義當前拆分按鈕控制件的資訊。|
|[C 按鈕::取得分割大小](#getsplitsize)|檢索當前拆分按鈕控制件的下拉元件的邊界矩形。|
|[C按鈕::取得分割樣式](#getsplitstyle)|檢索定義當前拆分按鈕控制的拆分按鈕樣式。|
|[C按鈕::取得狀態](#getstate)|檢索按鈕控制器的檢查狀態、突出顯示狀態和對焦狀態。|
|[C按鈕::取得文字保證金](#gettextmargin)|檢索按鈕控制的文字邊距。|
|[C按鈕::設定點陣圖](#setbitmap)|指定要顯示在按鈕上的點陣圖。|
|[C按鈕::設定按鈕樣式](#setbuttonstyle)|更改按鈕的樣式。|
|[C按鈕::設定檢查](#setcheck)|設置按鈕控制件的檢查狀態。|
|[CButton::設定游標](#setcursor)|指定要顯示在按鈕上的游標圖像。|
|[C按鈕::設定下拉狀態](#setdropdownstate)|設置當前拆分按鈕控件的下拉狀態。|
|[C按鈕::設定圖示](#seticon)|指定要顯示在按鈕上的圖示。|
|[C按鈕::設定影像清單](#setimagelist)|設置按鈕控制的影像清單。|
|[C按鈕::設定注](#setnote)|在當前命令連結控制件上設置註釋。|
|[C按鈕::設定分割字形](#setsplitglyph)|將指定的字形與當前拆分按鈕控制項關聯。|
|[CButton::設定分割影像清單](#setsplitimagelist)|將圖像清單與當前拆分按鈕控制項關聯。|
|[CButton::設定分割資訊](#setsplitinfo)|指定定義目前的分割按鈕控制件的資訊。|
|[C 按鈕::設定分割大小](#setsplitsize)|設置當前拆分按鈕控制件的下拉元件的邊界矩形。|
|[C按鈕::設定分割樣式](#setsplitstyle)|設置當前拆分按鈕控件的樣式。|
|[C按鈕::設定狀態](#setstate)|設置按鈕控制的突出顯示狀態。|
|[C 按鈕::設定文字邊緣](#settextmargin)|設置按鈕控制的文字邊距。|

## <a name="remarks"></a>備註

按鈕控制項是可按下和關閉的小型矩形子視窗。 按鈕可以單獨使用,也可以單獨使用,也可以單獨使用,也可以在沒有文本的情況下顯示。 當用戶按下按鈕時,按鈕通常會更改外觀。

典型的按鈕是複選框、單選按鈕和按鈕。 根據`CButton` [Create](#create)成員函數在初始化時指定的[按鈕樣式](../../mfc/reference/styles-used-by-mfc.md#button-styles),物件可以成為其中任何一個。

此外,派生自的`CButton` [CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)類支援創建帶有位圖圖像而不是文本標記的按鈕控制項。 可以為`CBitmapButton`按鈕的上、下、焦點和禁用狀態提供單獨的位圖。

可以從對話框範本或直接在代碼中創建按鈕控制項。 在這兩種情況下,首先調用構造函數`CButton`來構`CButton`造 物件;否則,請先調用構造函數來構造該物件。然後調用`Create`成員函數以創建 Windows 按鈕控制件並將其`CButton`附加到 物件。

構造可以是派生自`CButton`的類中的一個步驟。 為派生類編寫一個構造函數,並從`Create`構造函數內部調用。

如果要處理按鈕控制件發送到其父級的 Windows 通知訊息(通常是從[CDialog](../../mfc/reference/cdialog-class.md)派生的類),則為每個消息向父類添加消息映射條目和消息處理程式成員函數。

每個訊息對應項目以以下的檔案:

**開啟\_**_通知_**(ID** _ _,_成員Fxn_ **)**

*其中 ID*指定發送通知的控制項的子視窗 ID,*而成員Fxn*是您為處理通知而編寫的父成員函數的名稱。

父函數原型如下所示:

`afx_msg void memberFxn();`

潛在的消息對應項目的以下的目如下所示:

|對應項目|何時發送給父級...|
|---------------|----------------------------|
|ON_BN_CLICKED|用戶按一下按鈕。|
|ON_BN_DOUBLECLICKED|用戶按兩下按鈕。|

如果從對話框資源`CButton`創建物件,則當使用者關閉對話`CButton`框 時,該物件將自動銷毀。

如果在視窗中創建`CButton`物件,則可能需要銷毀它。 如果使用新函數在`CButton`堆上創建物件,則必須調**new**用 物件**上的 delete**以在使用者關閉 Windows 按鈕控制件時銷毀該物件。 如果在堆疊上`CButton`創建物件,或者該物件嵌入到父對話框物件中,則會自動銷毀該物件。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CButton`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="cbuttoncbutton"></a><a name="cbutton"></a>C按鈕::C按鈕

建構 `CButton` 物件。

```
CButton();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CButton#1](../../mfc/reference/codesnippet/cpp/cbutton-class_1.cpp)]

## <a name="cbuttoncreate"></a><a name="create"></a>C 按鈕:建立

創建 Windows 按鈕控制件並將其`CButton`附加到 物件。

```
virtual BOOL Create(
    LPCTSTR lpszCaption,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*lpszCaption*<br/>
指定按鈕控制的文字。

*dwStyle*<br/>
指定按鈕控制的樣式。 將[按鈕樣式](../../mfc/reference/styles-used-by-mfc.md#button-styles)的任意組合應用於按鈕。

*矩形*<br/>
指定按鈕控制的大小和位置。 它可以是`CRect`對`RECT`象或結構。

*pparentwnd*<br/>
指定按鍵控制檔的父視窗(通常為`CDialog`。 它不得為 NULL。

*nID*<br/>
指定按鈕控制項的識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

分兩步`CButton`構造物件。 首先,調用構造函數,然後調用`Create`,這將創建 Windows 按鈕控件並將`CButton`其附加到 物件。

如果提供了WS_VISIBLE樣式,Windows將發送按鈕控制程式激活並顯示按鈕所需的所有消息。

將以下[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)套用於按鈕控制項:

- WS_CHILD始終

- WS_VISIBLE 通常

- WS_DISABLED很少

- WS_GROUP元件

- WS_TABSTOP 在定位表順序中包含按鈕

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CButton#2](../../mfc/reference/codesnippet/cpp/cbutton-class_2.cpp)]

## <a name="cbuttondrawitem"></a><a name="drawitem"></a>CButton::D原始專案

當所有者繪製按鈕的可視方面已更改時,由框架調用。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>參數

*lpDraw 專案已結*<br/>
指向[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)結構的長指標。 結構包含有關要繪製的項和所需繪圖類型的資訊。

### <a name="remarks"></a>備註

擁有者繪製的按鈕已設置BS_OWNERDRAW樣式。 重寫此成員函數以實現所有者繪製`CButton`對象的繪圖。 應用程式應還原在成員函數終止之前為*lpDrawItemStruct*中提供的顯示上下文選擇的所有圖形設備介面 (GDI) 物件。

另請參閱[BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles)樣式值。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CButton#3](../../mfc/reference/codesnippet/cpp/cbutton-class_3.cpp)]

## <a name="cbuttongetbitmap"></a><a name="getbitmap"></a>C按鈕::取得點陣圖

調用此成員函數獲取與按鈕關聯的位圖的句柄,該位圖以前使用[SetBitmap](#setbitmap)設置。

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>傳回值

位圖的句柄。 如果以前未指定位圖,則為 NULL。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

## <a name="cbuttongetbuttonstyle"></a><a name="getbuttonstyle"></a>C按鈕::取得按鈕樣式

檢索有關按鈕控制樣式的資訊。

```
UINT GetButtonStyle() const;
```

### <a name="return-value"></a>傳回值

返回此`CButton`物件的按鈕樣式。 此函數僅返回[BS_](../../mfc/reference/styles-used-by-mfc.md#button-styles)樣式值,而不是返回任何其他視窗樣式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

## <a name="cbuttongetcheck"></a><a name="getcheck"></a>C按鈕::取得檢查

檢索單選按鈕或複選框的複選框。

```
int GetCheck() const;
```

### <a name="return-value"></a>傳回值

使用BS_AUTOCHECKBOX、BS_AUTORADIOBUTTON、BS_AUTO3STATE、BS_CHECKBOX、BS_RADIOBUTTON或BS_3STATE樣式創建的按鈕控制項的返回值是以下值之一:

|值|意義|
|-----------|-------------|
|BST_UNCHECKED|未選中按鈕狀態。|
|BST_CHECKED|選中按鈕狀態。|
|BST_INDETERMINATE|按鈕狀態不確定(僅當按鈕具有BS_3STATE或BS_AUTO3STATE樣式時才適用)。|

如果按鈕具有任何其他樣式,則返回值BST_UNCHECKED。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

## <a name="cbuttongetcursor"></a><a name="getcursor"></a>C按鈕::取得游標

呼叫此成員函數以獲取以前使用[SetCursor](#setcursor)設定的與按鈕關聯的游標的句柄。

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>傳回值

游標圖像的句柄。 如果以前未指定游標,則為 NULL。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

## <a name="cbuttongeticon"></a><a name="geticon"></a>C按鈕::取得圖示

呼叫此成員函數以獲取以前使用[SetIcon](#seticon)設定的與按鈕關聯的圖示的句柄。

```
HICON GetIcon() const;
```

### <a name="return-value"></a>傳回值

圖示的控制代碼。 如果以前未指定任何圖示,則為 NULL。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

## <a name="cbuttongetidealsize"></a><a name="getidealsize"></a>C按鈕::取得理想尺寸

檢索按鈕控制的理想大小。

```
BOOL GetIdealSize(SIZE* psize);
```

### <a name="parameters"></a>參數

*psize*<br/>
指向按鈕當前大小的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函數類比BCM_GETIDEALSIZE訊息的功能,如 Windows SDK 的[「按鈕」](/windows/win32/controls/buttons)部分所述。

## <a name="cbuttongetimagelist"></a><a name="getimagelist"></a>C 按鈕:抓取圖片清單

呼叫此方法從按鈕控制項獲取影像清單。

```
BOOL GetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>參數

*p 按鍵影像清單*<br/>
指向物件影像清單的`CButton`指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函數模擬BCM_GETIMAGELIST消息的功能,如 Windows SDK 的[「按鈕」](/windows/win32/controls/buttons)部分所述。

## <a name="cbuttongetnote"></a><a name="getnote"></a>C按鈕::取得筆記

檢索與當前命令連結控件關聯的註釋文本。

```
CString GetNote() const;

BOOL GetNote(
    LPTSTR lpszNote,
    UINT* cchNote) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*lpszNote*|[出]指向緩衝區的指標,調用方負責分配和釋放緩衝區。 如果返回值為 TRUE,緩衝區將包含與當前命令連結控件關聯的註釋文本;如果返回值為 TRUE,則緩衝區包含與當前命令連結控件關聯的註釋文本。否則,緩衝區將保持不變。|
|*cchNote*|[進出]指向無符號整數變數的指標。<br /><br /> 呼叫此方法時,變數包含*lpszNote*參數指定的緩衝區的大小。<br /><br /> 當此方法返回時,如果返回值為 TRUE,則變數包含與當前命令連結控件關聯的註釋的大小。 如果返回值為 FALSE,則變數包含包含註釋所需的緩衝區大小。|

### <a name="return-value"></a>傳回值

在第一個重載中,包含與當前命令連結控件關聯的註釋文本的[CString](../../atl-mfc-shared/using-cstring.md)物件。

-或-

在第二個重載中,如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

僅對按鈕樣式為BS_COMMANDLINK或BS_DEFCOMMANDLINK的控制項使用此方法。

此方法發送[BCM_GETNOTE](/windows/win32/Controls/bcm-getnote)消息,這在 Windows SDK 中介紹。

## <a name="cbuttongetnotelength"></a><a name="getnotelength"></a>C按鈕::取得註解長度

檢索目前命令連結控制件的註釋文本的長度。

```
UINT GetNoteLength() const;
```

### <a name="return-value"></a>傳回值

當前命令連結控制項的註釋文本的長度(以16位 Unicode 字元表示)。

### <a name="remarks"></a>備註

僅對按鈕樣式為BS_COMMANDLINK或BS_DEFCOMMANDLINK的控制項使用此方法。

此方法發送[BCM_GETNOTELENGTH](/windows/win32/Controls/bcm-getnotelength)消息,這在 Windows SDK 中介紹。

## <a name="cbuttongetsplitglyph"></a><a name="getsplitglyph"></a>C按鈕::取得分割字形

檢索與當前拆分按鈕控件關聯的字形。

```
TCHAR GetSplitGlyph() const;
```

### <a name="return-value"></a>傳回值

與當前拆分按鈕控制件關聯的字形字元。

### <a name="remarks"></a>備註

字形是特定字體中字元的物理表示形式。 例如,拆分按鈕控制項可能用 Unicode 複選標記字元 (U+2713) 的字形進行修飾。

此方法僅對按鈕樣式為BS_SPLITBUTTON或BS_DEFSPLITBUTTON的控制項使用。

此方法使用BCSIF_GLYPH標誌初始化`mask`[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)結構的成員,然後在 Windows SDK 中描述的[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)訊息中發送該結構。 當消息函數返回時,此方法從結構`himlGlyph`的成員中檢索字形。

## <a name="cbuttongetsplitimagelist"></a><a name="getsplitimagelist"></a>C 按鈕:抓取分割影像清單

檢索目前分割按鈕控制檔[的影像清單](../../mfc/reference/cimagelist-class.md)。

```
CImageList* GetSplitImageList() const;
```

### <a name="return-value"></a>傳回值

指向[CImageList](../../mfc/reference/cimagelist-class.md)物件的指標。

### <a name="remarks"></a>備註

此方法僅對按鈕樣式為BS_SPLITBUTTON或BS_DEFSPLITBUTTON的控制項使用。

此方法使用BCSIF_IMAGE標誌初始化`mask`[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)結構的成員,然後在 Windows SDK 中描述的[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)消息中發送該結構。 當消息函數返回時,此方法從結構`himlGlyph`的成員檢索圖像清單。

## <a name="cbuttongetsplitinfo"></a><a name="getsplitinfo"></a>C 按鈕:抓取分資訊

檢索確定 Windows 如何繪製當前拆分按鈕控制項的參數。

```
BOOL GetSplitInfo(PBUTTON_SPLITINFO pInfo) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*pInfo*|[出]指向接收有關當前拆分按鈕控制件的[資訊的BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)結構的指標。 調用方負責分配結構。|

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法僅對按鈕樣式為BS_SPLITBUTTON或BS_DEFSPLITBUTTON的控制項使用。

此方法發送[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)消息,這在 Windows SDK 中介紹。

## <a name="cbuttongetsplitsize"></a><a name="getsplitsize"></a>C 按鈕::取得分割大小

檢索當前拆分按鈕控制件的下拉元件的邊界矩形。

```
BOOL GetSplitSize(LPSIZE pSize) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*pSize*|[出]指向接收矩形描述的[SIZE](/windows/win32/api/windef/ns-windef-size)結構的指標。|

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法僅對按鈕樣式為BS_SPLITBUTTON或BS_DEFSPLITBUTTON的控制項使用。

展開拆分按鈕控制項時,它可以顯示下拉元件,如清單控制件或尋呼器控制件。 此方法檢索包含下拉元件的邊界矩形。

此方法使用BCSIF_SIZE標誌初始化`mask`[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)結構的成員,然後在 Windows SDK 中描述的[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)消息中發送該結構。 當消息函數返回時,此方法從結構`size`的成員檢索邊界矩形。

## <a name="cbuttongetsplitstyle"></a><a name="getsplitstyle"></a>C按鈕::取得分割樣式

檢索定義當前拆分按鈕控制的拆分按鈕樣式。

```
UINT GetSplitStyle() const;
```

### <a name="return-value"></a>傳回值

拆分按鈕樣式的位組合。 有關詳細資訊,請參閱`uSplitStyle`[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)結構的成員。

### <a name="remarks"></a>備註

此方法僅對按鈕樣式為BS_SPLITBUTTON或BS_DEFSPLITBUTTON的控制項使用。

拆分按鈕樣式指定 Windows 繪製拆分按鈕圖示的對齊、縱橫比和圖形格式。

此方法使用BCSIF_STYLE標誌初始化`mask`[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)結構的成員,然後在 Windows SDK 中描述的[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)消息中發送該結構。 當消息函數返回時,此方法從結構`uSplitStyle`的成員中檢索拆分按鈕樣式。

## <a name="cbuttongetstate"></a><a name="getstate"></a>C按鈕::取得狀態

檢索按鈕控件的狀態。

```
UINT GetState() const;
```

### <a name="return-value"></a>傳回值

包含指示按鈕控制項當前狀態的值組合的位欄位。 下表列出了可能的值。

|按鍵狀態|值|描述|
|------------------|-----------|-----------------|
|BST_UNCHECKED|0x0000|初始狀態。|
|BST_CHECKED|0x0001|檢查按鈕控制件。|
|BST_INDETERMINATE|0x0002|狀態不確定(僅當按鈕控制項具有三種狀態時才可能)。|
|BST_PUSHED|0x0004|按下按鈕控制件。|
|BST_FOCUS|0x0008|按鈕控制項具有焦點。|

### <a name="remarks"></a>備註

具有BS_3STATE或BS_AUTO3STATE按鈕樣式的按鈕控制項將創建一個複選框,該複選框具有第三個狀態,稱為不確定狀態。 不確定狀態表示未選中或未選中複選框。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

## <a name="cbuttongettextmargin"></a><a name="gettextmargin"></a>C按鈕::取得文字保證金

呼叫此方法獲取`CButton`物件的文字邊距。

```
BOOL GetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>參數

*pmargin*<br/>
指向物件的文字邊距的`CButton`指標。

### <a name="return-value"></a>傳回值

返回文本邊距。

### <a name="remarks"></a>備註

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函數模擬BCM_GETTEXTMARGIN消息的功能,如 Windows SDK 的[「按鈕」](/windows/win32/controls/buttons)部分所述。

## <a name="cbuttonsetbitmap"></a><a name="setbitmap"></a>C按鈕::設定點陣圖

調用此成員函數以將新的位圖與按鈕關聯。

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>參數

*hBitmap*<br/>
位圖的句柄。

### <a name="return-value"></a>傳回值

以前與按鈕關聯的位圖的句柄。

### <a name="remarks"></a>備註

位圖將自動放置在按鈕的面上,默認情況下居中。 如果位圖對於按鈕太大,則該位圖將在任一側剪切。 您可以選擇其他對齊選項,包括:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

與每個按鈕使用四個位圖的[CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)`SetBitmap`不同, 每個按鈕僅使用一個點陣圖。 按下按鈕時,位圖將顯示向下和向右移動。

完成位圖后,您有責任釋放它。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CButton#4](../../mfc/reference/codesnippet/cpp/cbutton-class_4.cpp)]

## <a name="cbuttonsetbuttonstyle"></a><a name="setbuttonstyle"></a>C按鈕::設定按鈕樣式

更改按鈕的樣式。

```
void SetButtonStyle(
    UINT nStyle,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>參數

*nStyle*<br/>
指定[按鍵樣式](../../mfc/reference/styles-used-by-mfc.md#button-styles)。

*bredraw*<br/>
指定是否要重繪按鈕。 非零值重繪按鈕。 0 值不會重繪按鈕。 默認情況下,該按鈕將重繪。

### <a name="remarks"></a>備註

使用`GetButtonStyle`成員函數檢索按鈕樣式。 完整按鈕樣式的低階字是特定於按鈕的樣式。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CButton#5](../../mfc/reference/codesnippet/cpp/cbutton-class_5.cpp)]

## <a name="cbuttonsetcheck"></a><a name="setcheck"></a>C按鈕::設定檢查

設置或重置單選按鈕或複選框的複選框。

```
void SetCheck(int nCheck);
```

### <a name="parameters"></a>參數

*N檢查*<br/>
指定檢查狀態。 此參數可以是下列其中一項：

|值|意義|
|-----------|-------------|
|BST_UNCHECKED|將按鈕狀態設置為取消選中。|
|BST_CHECKED|將按鈕狀態設置為選中。|
|BST_INDETERMINATE|將按鈕狀態設置為不確定。 僅當按鈕具有BS_3STATE或BS_AUTO3STATE樣式時,才能使用此值。|

### <a name="remarks"></a>備註

此成員函數對按鈕沒有影響。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CButton#6](../../mfc/reference/codesnippet/cpp/cbutton-class_6.cpp)]

## <a name="cbuttonsetcursor"></a><a name="setcursor"></a>CButton::設定游標

調用此成員函數以將新游標與按鈕關聯。

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>參數

*h游標*<br/>
游標的句柄。

### <a name="return-value"></a>傳回值

以前與按鈕關聯的游標的句柄。

### <a name="remarks"></a>備註

游標將自動放置在按鈕的面上,默認情況下居中。 如果游標太大,無法用於按鈕,則該游標將在任一側被剪切。 您可以選擇其他對齊選項,包括:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

與每個按鈕使用四個位圖的[CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)`SetCursor`不同, 每個按鈕只使用一個游標。 按下按鈕時,游標將向下和向右移動。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CButton#7](../../mfc/reference/codesnippet/cpp/cbutton-class_7.cpp)]

## <a name="cbuttonsetdropdownstate"></a><a name="setdropdownstate"></a>C按鈕::設定下拉狀態

設置當前拆分按鈕控件的下拉狀態。

```
BOOL SetDropDownState(BOOL fDropDown);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*f 向下*|[在]TRUE 設置為BST_DROPDOWNPUSHED狀態;否則,FALSE。|

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

拆分按鈕控件具有BS_SPLITBUTTON或BS_DEFSPLITBUTTON樣式,其右側由按鈕和下拉箭頭組成。 有關詳細資訊,請參閱[按鍵樣式](/windows/win32/Controls/button-styles)。 通常,當用戶單擊下拉箭頭時,將設置下拉狀態。 使用此方法以程式設計方式設置控制項的下拉狀態。 下拉箭頭繪製為下拉箭頭,以指示狀態。

此方法發送[BCM_SETDROPDOWNSTATE](/windows/win32/Controls/bcm-setdropdownstate)消息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

以下代碼範例定義用於以程式設計方式存取分割按鈕控制項的變數*m_splitButton*。 以下示例使用此變數。

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>範例

以下代碼示例設置拆分按鈕控件的狀態,以指示按下下拉箭頭。

[!code-cpp[NVC_MFC_CButton_s1#6](../../mfc/reference/codesnippet/cpp/cbutton-class_11.cpp)]

## <a name="cbuttonsetelevationrequired"></a><a name="setelevationrequired"></a>C按鈕::設定所需的提升

將當前按鈕控制項的狀態設置為`elevation required`,這是控制項顯示提升的安全圖示所必需的。

```
BOOL SetElevationRequired(BOOL fElevationRequired);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*f 海拔要求*|[在]設置為"TRUE"`elevation required`否則,FALSE。|

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

如果按鈕或命令連結控制項需要提升的安全許可權才能執行操作,則將控制項設定為`elevation required`狀態。 隨後,Windows 會在控制項上顯示使用者帳戶控制 (UAC) 遮罩圖示。 有關詳細資訊,請參閱[MSDN](https://go.microsoft.com/fwlink/p/?linkid=18507)的「使用者帳戶控制」。

此方法發送[BCM_SETSHIELD](/windows/win32/Controls/bcm-setshield)訊息,這在 Windows SDK 中介紹。

## <a name="cbuttonseticon"></a><a name="seticon"></a>C按鈕::設定圖示

調用此成員函數將新圖示與按鈕關聯。

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>參數

*hIcon*<br/>
圖示的句柄。

### <a name="return-value"></a>傳回值

以前與按鈕關聯的圖示的句柄。

### <a name="remarks"></a>備註

該圖示將自動放置在按鈕的面上,默認情況下居中。 如果圖示太大,無法用於按鈕,則該圖示將在任一側被剪切。 您可以選擇其他對齊選項,包括:

- BS_TOP

- BS_LEFT

- BS_RIGHT

- BS_CENTER

- BS_BOTTOM

- BS_VCENTER

與每個按鈕使用四個位圖的[CBitmapButton](../../mfc/reference/cbitmapbutton-class.md)`SetIcon`不同, 每個按鈕只使用一個圖示。 按下按鈕時,圖示將顯示向下和向右移動。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CButton#8](../../mfc/reference/codesnippet/cpp/cbutton-class_8.cpp)]

## <a name="cbuttonsetimagelist"></a><a name="setimagelist"></a>C按鈕::設定影像清單

呼叫此方法以設置`CButton`物件的影像清單。

```
BOOL SetImageList(PBUTTON_IMAGELIST pbuttonImagelist);
```

### <a name="parameters"></a>參數

*p 按鍵影像清單*<br/>
指向新圖像清單的指標。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

此成員函數模擬BCM_SETIMAGELIST消息的功能,如 Windows SDK 的[「按鈕」](/windows/win32/controls/buttons)部分所述。

## <a name="cbuttonsetnote"></a><a name="setnote"></a>C按鈕::設定注

設定目前命令連結控制件的註釋文本。

```
BOOL SetNote(LPCTSTR lpszNote);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*lpszNote*|[在]指向 Unicode 字串的指標,該字串設定為命令連結控制項的註釋文本。|

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

僅對按鈕樣式為BS_COMMANDLINK或BS_DEFCOMMANDLINK的控制項使用此方法。

此方法發送[BCM_SETNOTE](/windows/win32/Controls/bcm-setnote)消息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

以下代碼範例定義用於以程式設計方式存取命令連結控制元件的變數*m_cmdLink*。 以下示例使用此變數。

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>範例

以下代碼示例設置命令連結控制項的註釋文本。

[!code-cpp[NVC_MFC_CButton_s1#7](../../mfc/reference/codesnippet/cpp/cbutton-class_12.cpp)]

## <a name="cbuttonsetsplitglyph"></a><a name="setsplitglyph"></a>C按鈕::設定分割字形

將指定的字形與當前拆分按鈕控制項關聯。

```
BOOL SetSplitGlyph(TCHAR chGlyph);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*chGlyph*|[在]指定用作分割按鈕下拉箭頭的字形的字元。|

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

僅對具有按鈕樣式BS_SPLITBUTTON或BS_DEFSPLITBUTTON的控制項使用此方法。

字形是特定字體中字元的物理表示形式。 *chGlyph*參數不用作字形,而是用於從一組系統定義的字形中選擇字形。 預設下拉箭頭字形由字元「6」指定,類似於 Unicode 字元「黑色向下-點角圖」(U+25BC)。

此方法使用BCSIF_GLYPH標誌初始化`mask`[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)結構的成員,使用*chGlyph*`himlGlyph`參數來初始化該結構,然後在 Windows SDK 中描述的[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)消息中發送該結構。

## <a name="cbuttonsetsplitimagelist"></a><a name="setsplitimagelist"></a>CButton::設定分割影像清單

將[圖像清單](../../mfc/reference/cimagelist-class.md)與當前拆分按鈕控制項關聯。

```
BOOL SetSplitImageList(CImageList* pSplitImageList);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*p 分割影像清單*|[在]指向[CImageList](../../mfc/reference/cimagelist-class.md)物件的指標,以分配給當前拆分按鈕控制項。|

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法僅對按鈕樣式為BS_SPLITBUTTON或BS_DEFSPLITBUTTON的控制項使用。

此方法使用BCSIF_IMAGE標誌和`mask`*pSplitImageList*參數初始化`himlGlyph`[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)結構 的成員,然後在 Windows SDK 中描述的[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)消息中發送該結構。

## <a name="cbuttonsetsplitinfo"></a><a name="setsplitinfo"></a>CButton::設定分割資訊

指定確定 Windows 如何繪製目前的按鈕控制項的參數。

```
BOOL SetSplitInfo(PBUTTON_SPLITINFO pInfo);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*pInfo*|[在]指向定義當前拆分按鈕控制的[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)結構的指標。|

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法僅對按鈕樣式為BS_SPLITBUTTON或BS_DEFSPLITBUTTON的控制項使用。

此方法發送[BCM_SETSPLITINFO](/windows/win32/Controls/bcm-setsplitinfo)消息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

以下代碼範例定義用於以程式設計方式存`m_splitButton`取 分割按鈕控制項的變數 。

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>範例

以下代碼示例更改用於拆分按鈕下拉箭頭的字形。 該示例將向上的三角形字形替換為預設的向下指向三角形字形。 顯示的字形取決於您在`himlGlyph``BUTTON_SPLITINFO`結構成員中指定的字元。 向下指向三角形字形由字元"6"指定,上指三角形字形由字元"5"指定。 有關比較,請參閱方便方法[CButton::setSplitGlyph](#setsplitglyph)。

[!code-cpp[NVC_MFC_CButton_s1#4](../../mfc/reference/codesnippet/cpp/cbutton-class_13.cpp)]

## <a name="cbuttonsetsplitsize"></a><a name="setsplitsize"></a>C 按鈕::設定分割大小

設置當前拆分按鈕控制件的下拉元件的邊界矩形。

```
BOOL SetSplitSize(LPSIZE pSize);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*pSize*|[在]指向描述邊界矩形的[SIZE](/windows/win32/api/windef/ns-windef-size)結構的指標。|

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法僅對按鈕樣式為BS_SPLITBUTTON或BS_DEFSPLITBUTTON的控制項使用。

展開拆分按鈕控制項時,它可以顯示下拉元件,如清單控制件或尋呼器控制件。 此方法指定包含下拉元件的邊界矩形的大小。

此方法使用 BCSIF_SIZE`mask`標誌和*pSize*參數`size`初始化[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)結構 的成員,然後在 Windows SDK 中描述的[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)訊息中發送該結構。

### <a name="example"></a>範例

以下代碼範例定義用於以程式設計方式存`m_splitButton`取 分割按鈕控制項的變數 。 以下示例使用此變數。

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>範例

以下代碼示例將拆分按鈕下拉箭頭的大小加倍。

[!code-cpp[NVC_MFC_CButton_s1#5](../../mfc/reference/codesnippet/cpp/cbutton-class_14.cpp)]

## <a name="cbuttonsetsplitstyle"></a><a name="setsplitstyle"></a>C按鈕::設定分割樣式

設置當前拆分按鈕控件的樣式。

```
BOOL SetSplitStyle(UINT uSplitStyle);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*uSplit 樣式*|[在]拆分按鈕樣式的位組合。 有關詳細資訊,請參閱`uSplitStyle`[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)結構的成員。|

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法僅對按鈕樣式為BS_SPLITBUTTON或BS_DEFSPLITBUTTON的控制項使用。

拆分按鈕樣式指定 Windows 繪製拆分按鈕圖示的對齊、縱橫比和圖形格式。 有關詳細資訊,請參閱`uSplitStyle`[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)結構的成員。

此方法使用BCSIF_STYLE標誌初始化`mask`[BUTTON_SPLITINFO](/windows/win32/api/commctrl/ns-commctrl-button_splitinfo)BUTTON_SPLITINFO`uSplitStyle`結構 的成員,使用*uSplitStyle*參數來初始化該結構,然後在Windows SDK中描述的[BCM_GETSPLITINFO](/windows/win32/Controls/bcm-getsplitinfo)訊息中發送該結構。

### <a name="example"></a>範例

以下代碼範例定義用於以程式設計方式存`m_splitButton`取 分割按鈕控制項的變數 。

[!code-cpp[NVC_MFC_CButton_s1#1](../../mfc/reference/codesnippet/cpp/cbutton-class_10.h)]

### <a name="example"></a>範例

以下代碼示例設置拆分按鈕下拉箭頭的樣式。 BCSS_ALIGNLEFT樣式顯示按鈕左側的箭頭,BCSS_STRETCH樣式在調整按鈕大小時保留下拉箭頭的比例。

[!code-cpp[NVC_MFC_CButton_s1#3](../../mfc/reference/codesnippet/cpp/cbutton-class_15.cpp)]

## <a name="cbuttonsetstate"></a><a name="setstate"></a>C按鈕::設定狀態

設置按鈕控制檔是否突出顯示。

```
void SetState(BOOL bHighlight);
```

### <a name="parameters"></a>參數

*b 高光*<br/>
指定按鈕是否突出顯示。 非零值突出顯示按鈕;非零值突出顯示按鈕。0 值刪除任何突出顯示。

### <a name="remarks"></a>備註

突出顯示會影響按鈕控制件的外部。 它對單選按鈕或複選框的複選框的複選框沒有影響。

當用戶按下並持有滑鼠左鍵時,按鈕控制項會自動突出顯示。 當使用者釋放滑鼠按鈕時,將刪除突出顯示。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CButton#9](../../mfc/reference/codesnippet/cpp/cbutton-class_9.cpp)]

## <a name="cbuttonsettextmargin"></a><a name="settextmargin"></a>C 按鈕::設定文字邊緣

呼叫此方法以設定`CButton`物件的文字邊距。

```
BOOL SetTextMargin(RECT* pmargin);
```

### <a name="parameters"></a>參數

*pmargin*<br/>
指向新文字邊距的指標。

### <a name="return-value"></a>傳回值

成功時返回 TRUE,在失敗時返回 FALSE。

### <a name="remarks"></a>備註

此成員函數模擬BCM_SETTEXTMARGIN消息的功能,如 Windows SDK 的[「按鈕」](/windows/win32/controls/buttons)部分所述。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[CComboBox 類別](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit Class](../../mfc/reference/cedit-class.md)<br/>
[CListBox 類別](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar 類別](../../mfc/reference/cscrollbar-class.md)<br/>
[CStatic 類別](../../mfc/reference/cstatic-class.md)<br/>
[CBitmapButton 類別](../../mfc/reference/cbitmapbutton-class.md)<br/>
[CDialog 類別](../../mfc/reference/cdialog-class.md)
