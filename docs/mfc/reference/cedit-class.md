---
title: CEdit Class
ms.date: 09/12/2018
f1_keywords:
- CEdit
- AFXWIN/CEdit
- AFXWIN/CEdit::CEdit
- AFXWIN/CEdit::CanUndo
- AFXWIN/CEdit::CharFromPos
- AFXWIN/CEdit::Clear
- AFXWIN/CEdit::Copy
- AFXWIN/CEdit::Create
- AFXWIN/CEdit::Cut
- AFXWIN/CEdit::EmptyUndoBuffer
- AFXWIN/CEdit::FmtLines
- AFXWIN/CEdit::GetCueBanner
- AFXWIN/CEdit::GetFirstVisibleLine
- AFXWIN/CEdit::GetHandle
- AFXWIN/CEdit::GetHighlight
- AFXWIN/CEdit::GetLimitText
- AFXWIN/CEdit::GetLine
- AFXWIN/CEdit::GetLineCount
- AFXWIN/CEdit::GetMargins
- AFXWIN/CEdit::GetModify
- AFXWIN/CEdit::GetPasswordChar
- AFXWIN/CEdit::GetRect
- AFXWIN/CEdit::GetSel
- AFXWIN/CEdit::HideBalloonTip
- AFXWIN/CEdit::LimitText
- AFXWIN/CEdit::LineFromChar
- AFXWIN/CEdit::LineIndex
- AFXWIN/CEdit::LineLength
- AFXWIN/CEdit::LineScroll
- AFXWIN/CEdit::Paste
- AFXWIN/CEdit::PosFromChar
- AFXWIN/CEdit::ReplaceSel
- AFXWIN/CEdit::SetCueBanner
- AFXWIN/CEdit::SetHandle
- AFXWIN/CEdit::SetHighlight
- AFXWIN/CEdit::SetLimitText
- AFXWIN/CEdit::SetMargins
- AFXWIN/CEdit::SetModify
- AFXWIN/CEdit::SetPasswordChar
- AFXWIN/CEdit::SetReadOnly
- AFXWIN/CEdit::SetRect
- AFXWIN/CEdit::SetRectNP
- AFXWIN/CEdit::SetSel
- AFXWIN/CEdit::SetTabStops
- AFXWIN/CEdit::ShowBalloonTip
- AFXWIN/CEdit::Undo
helpviewer_keywords:
- CEdit [MFC], CEdit
- CEdit [MFC], CanUndo
- CEdit [MFC], CharFromPos
- CEdit [MFC], Clear
- CEdit [MFC], Copy
- CEdit [MFC], Create
- CEdit [MFC], Cut
- CEdit [MFC], EmptyUndoBuffer
- CEdit [MFC], FmtLines
- CEdit [MFC], GetCueBanner
- CEdit [MFC], GetFirstVisibleLine
- CEdit [MFC], GetHandle
- CEdit [MFC], GetHighlight
- CEdit [MFC], GetLimitText
- CEdit [MFC], GetLine
- CEdit [MFC], GetLineCount
- CEdit [MFC], GetMargins
- CEdit [MFC], GetModify
- CEdit [MFC], GetPasswordChar
- CEdit [MFC], GetRect
- CEdit [MFC], GetSel
- CEdit [MFC], HideBalloonTip
- CEdit [MFC], LimitText
- CEdit [MFC], LineFromChar
- CEdit [MFC], LineIndex
- CEdit [MFC], LineLength
- CEdit [MFC], LineScroll
- CEdit [MFC], Paste
- CEdit [MFC], PosFromChar
- CEdit [MFC], ReplaceSel
- CEdit [MFC], SetCueBanner
- CEdit [MFC], SetHandle
- CEdit [MFC], SetHighlight
- CEdit [MFC], SetLimitText
- CEdit [MFC], SetMargins
- CEdit [MFC], SetModify
- CEdit [MFC], SetPasswordChar
- CEdit [MFC], SetReadOnly
- CEdit [MFC], SetRect
- CEdit [MFC], SetRectNP
- CEdit [MFC], SetSel
- CEdit [MFC], SetTabStops
- CEdit [MFC], ShowBalloonTip
- CEdit [MFC], Undo
ms.assetid: b1533c30-7f10-4663-88d3-8b7f2c9f7024
ms.openlocfilehash: 295a58a86f35fca3b8d25706857162facc9cb3ea
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503738"
---
# <a name="cedit-class"></a>CEdit Class

提供 Windows 編輯控制項的功能。

## <a name="syntax"></a>語法

```
class CEdit : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CEdit::CEdit](#cedit)|建構`CEdit`控制項物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CEdit::CanUndo](#canundo)|判斷是否可以復原的編輯控制項作業。|
|[CEdit::CharFromPos](#charfrompos)|擷取字元的最接近的指定位置的行和字元索引。|
|[CEdit::Clear](#clear)|刪除 （清除） 目前的選取範圍 （如果有的話） 中編輯控制項。|
|[CEdit::Copy](#copy)|複製目前的選取範圍 （如果有的話） 中編輯控制項到 CF_TEXT 格式剪貼簿。|
|[CEdit::Create](#create)|建立 Windows 編輯控制項，並將它附加至`CEdit`物件。|
|[CEdit::Cut](#cut)|刪除 （切割） 目前的選取範圍 （如果有的話） 中編輯控制項，並複製到剪貼簿 CF_TEXT 刪除的文字格式。|
|[CEdit::EmptyUndoBuffer](#emptyundobuffer)|重設 （清除） 復原旗標的編輯控制項。|
|[CEdit::FmtLines](#fmtlines)|設定開啟或關閉軟換行字元包含在多行編輯控制項。|
|[CEdit::GetCueBanner](#getcuebanner)|擷取做為文字提示或提示，當控制項為空白，且未取得焦點的編輯控制項中顯示的文字。|
|[CEdit::GetFirstVisibleLine](#getfirstvisibleline)|決定在編輯控制項中的最上層的可見行。|
|[CEdit::GetHandle](#gethandle)|擷取多行編輯控制項的目前配置的記憶體的控制代碼。|
|[CEdit::GetHighlight](#gethighlight)|取得開始和結束目前的編輯控制項中反白顯示的文字範圍中的字元的索引。|
|[CEdit::GetLimitText](#getlimittext)|取得這個文字的最大數量`CEdit`可以包含。|
|[CEdit::GetLine](#getline)|擷取編輯控制項中的文字行。|
|[CEdit::GetLineCount](#getlinecount)|擷取多行編輯控制項中的行數。|
|[CEdit::GetMargins](#getmargins)|取得這個左、 右邊界`CEdit`。|
|[CEdit::GetModify](#getmodify)|判斷是否已修改的編輯控制項內容。|
|[CEdit::GetPasswordChar](#getpasswordchar)|擷取使用者輸入文字時，在編輯控制項中顯示的密碼字元。|
|[CEdit::GetRect](#getrect)|取得編輯控制項的格式化矩形。|
|[CEdit::GetSel](#getsel)|取得目前的選取範圍，在編輯控制項中的第一個和最後一個字元位置。|
|[CEdit::HideBalloonTip](#hideballoontip)|會隱藏任何目前的編輯控制項相關聯的汽球提示。|
|[CEdit::LimitText](#limittext)|限制使用者可以輸入編輯控制項文字的長度。|
|[CEdit::LineFromChar](#linefromchar)|擷取包含指定的字元索引的那一行的行號。|
|[CEdit::LineIndex](#lineindex)|擷取線，以多行編輯控制項中的字元索引。|
|[CEdit::LineLength](#linelength)|擷取編輯控制項中的資料行的長度。|
|[CEdit::LineScroll](#linescroll)|捲動的多行編輯控制項的文字。|
|[CEdit::Paste](#paste)|從剪貼簿將資料插入在目前游標位置的編輯控制項。 只有當剪貼簿包含 CF_TEXT 格式的資料插入資料。|
|[CEdit::PosFromChar](#posfromchar)|擷取指定的字元索引的左上角的座標。|
|[CEdit::ReplaceSel](#replacesel)|取代指定的文字編輯控制項中目前的選取範圍。|
|[CEdit::SetCueBanner](#setcuebanner)|設定會顯示為文字提示或提示，當控制項為空白，且未取得焦點的編輯控制項中的文字。|
|[CEdit::SetHandle](#sethandle)|設定將多行編輯控制項所使用的本機記憶體控制代碼。|
|[CEdit::SetHighlight](#sethighlight)|反白顯示的範圍會顯示在目前的文字編輯控制項。|
|[CEdit::SetLimitText](#setlimittext)|設定這個文字的最大數量`CEdit`可以包含。|
|[CEdit::SetMargins](#setmargins)|設定這個左、 右邊界`CEdit`。|
|[CEdit::SetModify](#setmodify)|設定或清除編輯控制項的修改旗標。|
|[CEdit::SetPasswordChar](#setpasswordchar)|設定或移除時使用者輸入文字編輯控制項中顯示的密碼字元。|
|[CEdit::SetReadOnly](#setreadonly)|設定編輯控制項的唯讀狀態。|
|[CEdit::SetRect](#setrect)|設定多行編輯控制項的格式化矩形並更新控制項。|
|[CEdit::SetRectNP](#setrectnp)|設定多行編輯控制項的格式化矩形，而不需要重新繪製控制項的視窗。|
|[CEdit::SetSel](#setsel)|在編輯控制項中選取字元的範圍。|
|[CEdit::SetTabStops](#settabstops)|設定定位停駐點在多行編輯控制項。|
|[CEdit::ShowBalloonTip](#showballoontip)|顯示與目前的編輯控制項相關聯的汽球提示。|
|[CEdit::Undo](#undo)|反轉上一個編輯控制項作業。|

## <a name="remarks"></a>備註

編輯控制項是使用者可以在其中輸入文字的矩形的子視窗。

從對話方塊範本，或是直接在您的程式碼中，您可以建立一個編輯控制項。 在這兩種情況下，第一次呼叫建構函式`CEdit`來建構`CEdit`物件，然後呼叫[建立](#create)成員函式來建立 Windows 編輯控制項，並將其附加至`CEdit`物件。

建構可以是單一步驟中的處理序類別，衍生自`CEdit`。 寫入的建構函式在衍生的類別並呼叫`Create`從建構函式內。

`CEdit` 繼承重要的功能，從`CWnd`。 設定及擷取成文字檔`CEdit`物件，請使用`CWnd`成員函式[SetWindowText](cwnd-class.md#setwindowtext)並[GetWindowText](cwnd-class.md#getwindowtext)，編輯的整個內容所控制的 set 或 get，即使它是多行的控制項。 在多行控制項中的文字行分隔 '\r\n' 字元序列。 此外，如果多行編輯控制項，取得並設定控制項的文字的一部分，藉由呼叫`CEdit`成員函式[GetLine](#getline)， [SetSel](#setsel)， [GetSel](#getsel)，以及[ReplaceSel](#replacesel)。

如果您想要處理 Windows 通知訊息傳送給其父代的編輯控制項 (通常是從衍生的類別`CDialog`)，將訊息對應項目和訊息處理常式成員函式新增至每個訊息的父類別。

每個訊息對應項目都會使用下列格式：

  **ON_** _NOTIFICATION_ **(** _id_ **,** _memberFxn_ **)**

何處`id`指定傳送通知，編輯控制項的子視窗識別碼和`memberFxn`是您撰寫來處理通知的父成員函式的名稱。

父代的函式原型如下所示：

**afx_msg** void memberFxn **( );**

以下是一份潛在的訊息對應項目並在其中它們就會傳送到父代的案例的描述：

- ON_EN_CHANGE 使用者所執行的動作，可能已變更編輯控制項中的文字。 不同於 EN_UPDATE 通知訊息時，Windows 更新顯示之後，會傳送此通知訊息。

- ON_EN_ERRSPACE 編輯控制項無法配置足夠的記憶體，以滿足特定的要求。

- ON_EN_HSCROLL 使用者按一下編輯控制項的水平捲軸。 父視窗會收到通知，才會更新畫面。

- ON_EN_KILLFOCUS 編輯控制項失去輸入的焦點。

- ON_EN_MAXTEXT 目前的插入動作已超過指定的編輯控制項的字元數，且已遭截斷。 也傳送時編輯控制項並沒有 ES_AUTOHSCROLL 樣式，而且要插入的字元數會超過編輯控制項的寬度。 也傳送時編輯控制項並沒有 ES_AUTOVSCROLL 樣式，而且所產生的文字插入幾行的總數會超過編輯控制項的高度。

- 當編輯控制項收到輸入的焦點時，就會傳送 ON_EN_SETFOCUS。

- ON_EN_UPDATE 編輯控制項即將變更的顯示文字。 控制項已格式化文字後，但它螢幕文字，以便可以變更視窗大小，必要時傳送。

- ON_EN_VSCROLL 使用者按一下編輯控制項的垂直捲軸。 父視窗會收到通知，才會更新畫面。

如果您建立`CEdit` 對話方塊中，物件`CEdit`使用者關閉對話方塊時，即會自動終結物件。

如果您建立`CEdit`從對話方塊資源使用對話方塊編輯器中，物件`CEdit`使用者關閉對話方塊時，即會自動終結物件。

如果您建立`CEdit`物件內的視窗中，您可能也需要終結它。 如果您建立`CEdit`物件在堆疊上，它會自動終結。 如果您建立`CEdit`物件上使用堆積**新**函式，您必須呼叫**刪除**物件終結它，當使用者終止 Windows 編輯控制項。 如果您配置任何記憶體`CEdit`物件，覆寫`CEdit`解構函式來進行處置的配置。

若要修改特定樣式的編輯控制項 （例如 ES_READONLY) 必須將特定訊息傳送至控制項而不是使用[ModifyStyle](cwnd-class.md#modifystyle)。 請參閱[編輯控制項的樣式](/windows/desktop/Controls/edit-control-styles)Windows SDK 中。

如需詳細資訊`CEdit`，請參閱 <<c2> [ 控制項](../../mfc/controls-mfc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

`CEdit`

## <a name="requirements"></a>需求

**標題:** afxwin.h

##  <a name="canundo"></a>  CEdit::CanUndo

呼叫此函式來判斷是否可以復原上次的編輯作業。

```
BOOL CanUndo() const;
```

### <a name="return-value"></a>傳回值

非零值，如果可以復原上次的編輯作業，藉由呼叫`Undo`成員函式; 0，如果無法復原。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [EM_CANUNDO](/windows/desktop/Controls/em-canundo) Windows SDK 中。

### <a name="example"></a>範例

  範例，請參閱[CEdit::Undo](#undo)。

##  <a name="cedit"></a>  CEdit::CEdit

建構 `CEdit` 物件。

```
CEdit();
```

### <a name="remarks"></a>備註

使用[建立](#create)建構 Windows 編輯控制項。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#1](../../mfc/reference/codesnippet/cpp/cedit-class_1.cpp)]

##  <a name="charfrompos"></a>  CEdit::CharFromPos

呼叫此函式可擷取的以零為起始的行和字元的字元，最接近指定點在此索引`CEdit`控制項

```
int CharFromPos(CPoint pt) const;
```

### <a name="parameters"></a>參數

*pt*<br/>
工作區中此點的座標`CEdit`物件。

### <a name="return-value"></a>傳回值

低序位字組中的字元索引，高序位文字中的行索引。

### <a name="remarks"></a>備註

> [!NOTE]
>  此成員函式是從 Windows 95 和 Windows NT 4.0。

如需詳細資訊，請參閱 < [EM_CHARFROMPOS](/windows/desktop/Controls/em-charfrompos) Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#3](../../mfc/reference/codesnippet/cpp/cedit-class_2.cpp)]

##  <a name="clear"></a>  CEdit::Clear

呼叫此函式來刪除 （清除） 目前的選取範圍 （如果有的話） 中編輯控制項。

```
void Clear();
```

### <a name="remarks"></a>備註

刪除由`Clear`可以藉由呼叫復原[復原](#undo)成員函式。

若要刪除目前選取範圍，並將已刪除的內容放到剪貼簿，請呼叫[剪下](#cut)成員函式。

如需詳細資訊，請參閱 < [WM_CLEAR](/windows/desktop/dataxchg/wm-clear) Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#4](../../mfc/reference/codesnippet/cpp/cedit-class_3.cpp)]

##  <a name="copy"></a>  CEdit::Copy

呼叫此函式以下列方式複製目前的選取範圍 （如果有的話） 到剪貼簿格式 CF_TEXT 編輯控制項中。

```
void Copy();
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [WM_COPY](/windows/desktop/dataxchg/wm-copy) Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#5](../../mfc/reference/codesnippet/cpp/cedit-class_4.cpp)]

##  <a name="create"></a>  CEdit::Create

建立 Windows 編輯控制項，並將它附加至`CEdit`物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定編輯控制項的樣式。 套用的任何組合[編輯樣式](styles-used-by-mfc.md#edit-styles)至控制項。

*rect*<br/>
指定編輯控制項的大小和位置。 可以是`CRect`物件或`RECT`結構。

*pParentWnd*<br/>
指定編輯控制項的父視窗 (通常`CDialog`)。 它必須不是 NULL。

*nID*<br/>
指定編輯控制項的識別碼。

### <a name="return-value"></a>傳回值

如果初始化成功則為非零否則為 0。

### <a name="remarks"></a>備註

您建構`CEdit`兩個步驟中的物件。 首先，呼叫`CEdit`建構函式，然後呼叫`Create`，這會建立 Windows 編輯控制項，並將它附加至`CEdit`物件。

當`Create`執行時，Windows 會傳送[WM_NCCREATE](/windows/desktop/winmsg/wm-nccreate)， [WM_NCCALCSIZE](/windows/desktop/winmsg/wm-nccalcsize)， [WM_CREATE](/windows/desktop/winmsg/wm-create)，並[WM_GETMINMAXINFO](/windows/desktop/winmsg/wm-getminmaxinfo)編輯控制項的訊息。

根據預設，處理這些訊息[OnNcCreate](cwnd-class.md#onnccreate)， [OnNcCalcSize](cwnd-class.md#onnccalcsize)， [OnCreate](cwnd-class.md#oncreate)，以及[OnGetMinMaxInfo](cwnd-class.md#ongetminmaxinfo)成員函式在 `CWnd`基底類別。 若要擴充的預設訊息處理，衍生的類別`CEdit`、 將訊息對應新增至新的類別，並覆寫上述的訊息處理常式成員函式。 覆寫`OnCreate`，例如，若要執行的新類別所需的初始設定。

套用下列[的視窗樣式](styles-used-by-mfc.md#window-styles)至編輯控制項。

- WS_CHILD 一律

- WS_VISIBLE 通常

- WS_DISABLED 很少

- WS_GROUP 群組控制項

- 若要在 tab 鍵順序中包含編輯控制項的 WS_TABSTOP

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#2](../../mfc/reference/codesnippet/cpp/cedit-class_5.cpp)]

##  <a name="cut"></a>  CEdit::Cut

呼叫此函式來刪除 （剪下） 編輯控制項中目前的選取範圍 （如果有的話），並將已刪除的文字複製到剪貼簿 CF_TEXT 格式。

```
void Cut();
```

### <a name="remarks"></a>備註

刪除由`Cut`可以藉由呼叫復原[復原](#undo)成員函式。

若要刪除目前選取範圍，不需將刪除的文字放到剪貼簿，請呼叫[清除](#clear)成員函式。

如需詳細資訊，請參閱 < [WM_CUT](/windows/desktop/dataxchg/wm-cut) Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#6](../../mfc/reference/codesnippet/cpp/cedit-class_6.cpp)]

##  <a name="emptyundobuffer"></a>  CEdit::EmptyUndoBuffer

編輯控制項的復原旗標呼叫此函式來重設 （清除）。

```
void EmptyUndoBuffer();
```

### <a name="remarks"></a>備註

編輯控制項現在無法復原最後一個作業。 編輯控制項中的作業可以進行復原時，會設定復原旗標。

復原旗標會自動清除每當[SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)或是[sethandle，然後](#sethandle)`CWnd`呼叫成員函式。

如需詳細資訊，請參閱 < [EM_EMPTYUNDOBUFFER](/windows/desktop/Controls/em-emptyundobuffer) Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#7](../../mfc/reference/codesnippet/cpp/cedit-class_7.cpp)]

##  <a name="fmtlines"></a>  CEdit::FmtLines

呼叫此函式可設定多行編輯控制項中包含的軟換行字元 on 或 off。

```
BOOL FmtLines(BOOL bAddEOL);
```

### <a name="parameters"></a>參數

*bAddEOL*<br/>
指定是否要插入軟換行字元。 如果為 true 會插入下列字元:;值為 FALSE 可移除它們。

### <a name="return-value"></a>傳回值

如果有任何非零值，會進行格式化;否則為 0。

### <a name="remarks"></a>備註

軟換行符號是由兩個歸位字元和換行字元插入已中斷，因為自動換行尾所組成。 硬碟換行符號是由一個歸位字元和換行字元所組成。 不會影響硬碟換行符號結尾的行`FmtLines`。

如果只會回應 Windows`CEdit`物件是多行編輯控制項。

`FmtLines` 只會影響所傳回的緩衝區[GetHandle](#gethandle)和所傳回的文字[WM_GETTEXT](/windows/desktop/winmsg/wm-gettext)。 它的文字編輯控制項中顯示沒有任何影響。

如需詳細資訊，請參閱 < [EM_FMTLINES](/windows/desktop/Controls/em-fmtlines) Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#8](../../mfc/reference/codesnippet/cpp/cedit-class_8.cpp)]

##  <a name="getcuebanner"></a>  CEdit::GetCueBanner

擷取做為文字提示或提示，在編輯控制項的控制項是空白時顯示的文字。

```
BOOL GetCueBanner(
    LPWSTR lpszText,
    int cchText) const;

CString GetCueBanner() const;
```

### <a name="parameters"></a>參數

*lpszText*<br/>
[out]包含提示文字的字串指標。

*cchText*<br/>
[in]可以接收到的字元數。 這個數目包括結束的 NULL 字元。

### <a name="return-value"></a>傳回值

第一個多載而言，TRUE 如果方法成功，否則為 FALSE。

第二個多載而言， [CString](../../atl-mfc-shared/using-cstring.md)其中包含提示文字，如果方法成功，否則為空字串 ("")。

### <a name="remarks"></a>備註

這個方法會傳送[EM_GETCUEBANNER](/windows/desktop/Controls/em-getcuebanner)訊息，Windows SDK 中所述。 如需詳細資訊，請參閱 < [Edit_GetCueBannerText](/windows/desktop/api/commctrl/nf-commctrl-edit_getcuebannertext)巨集。

##  <a name="getfirstvisibleline"></a>  CEdit::GetFirstVisibleLine

呼叫此函式來判斷最上層的可見行編輯控制項中。

```
int GetFirstVisibleLine() const;
```

### <a name="return-value"></a>傳回值

最上層的可見行以零為起始的索引。 單行編輯控制項，傳回的值為 0。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [EM_GETFIRSTVISIBLELINE](/windows/desktop/Controls/em-getfirstvisibleline) Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#9](../../mfc/reference/codesnippet/cpp/cedit-class_9.cpp)]

##  <a name="gethandle"></a>  CEdit::GetHandle

呼叫此函式來擷取多行編輯控制項的目前配置的記憶體的控制代碼。

```
HLOCAL GetHandle() const;
```

### <a name="return-value"></a>傳回值

本機記憶體控制代碼識別保留的編輯控制項內容的緩衝區。 如果發生錯誤，例如傳送訊息至單一行編輯控制項，則傳回的值為 0。

### <a name="remarks"></a>備註

控制代碼的本機記憶體控制代碼，而且可由任一**本機**採用本機記憶體的 Windows 記憶體函式處理做為參數。

`GetHandle` 處理只能由多行編輯控制項。

呼叫`GetHandle`多行編輯控制項在對話方塊中，只有當對話方塊中已建立設定 DS_LOCALEDIT 樣式旗標。 如果未設定 DS_LOCALEDIT 樣式，仍會得到零的傳回值，但不是能使用傳回的值。

> [!NOTE]
> `GetHandle` 不適用於 Windows 95/98。 如果您呼叫`GetHandle`在 Windows 95/98，它會傳回 NULL。 `GetHandle` 可在 Windows NT 3.51 及更新版本下所述。

如需詳細資訊，請參閱 < [EM_GETHANDLE](/windows/desktop/Controls/em-gethandle) Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#10](../../mfc/reference/codesnippet/cpp/cedit-class_10.cpp)]

##  <a name="gethighlight"></a>  CEdit::GetHighlight

在目前的編輯控制項中反白顯示的文字範圍中取得的第一個和最後一個字元的索引。

```
BOOL GetHighlight(
    int* pichStart,
    int* pichEnd) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*pichStart*|[out]反白顯示的文字範圍中的第一個字元的以零為起始索引。|
|*pichEnd*|[out]反白顯示的文字範圍中的最後一個字元的以零為起始索引。|

### <a name="return-value"></a>傳回值

如果成功，這個方法，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[EM_GETHILITE](/windows/desktop/Controls/em-gethilite)訊息，Windows SDK 中所述。 兩者`SetHighlight`和`GetHighlight`UNICODE 組建只目前已啟用。

##  <a name="getlimittext"></a>  CEdit::GetLimitText

呼叫此成員函式，以取得此文字限制`CEdit`物件。

```
UINT GetLimitText() const;
```

### <a name="return-value"></a>傳回值

目前文字中的限制，TCHARs，這個`CEdit`物件。

### <a name="remarks"></a>備註

文字限制為文字，請在 TCHARs，編輯控制項可接受的最大數量。

> [!NOTE]
>  此成員函式是從 Windows 95 和 Windows NT 4.0。

如需詳細資訊，請參閱 < [EM_GETLIMITTEXT](/windows/desktop/Controls/em-getlimittext) Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#11](../../mfc/reference/codesnippet/cpp/cedit-class_11.cpp)]

##  <a name="getline"></a>  CEdit::GetLine

呼叫此函式來擷取編輯控制項中的文字行，並將它放入*lpszBuffer*。

```
int GetLine(
    int nIndex,
    LPTSTR lpszBuffer) const;

int GetLine(
    int nIndex,
    LPTSTR lpszBuffer,
    int nMaxLength) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
指定的行號，來擷取多行編輯控制項。 行號是以零為起始;值為 0 指定的第一行。 單行編輯控制項，會忽略這個參數。

*lpszBuffer*<br/>
指向接收一份列的緩衝區。 緩衝區的第一個字組必須指定可以複製到緩衝區的 TCHARs 的最大數目。

*nMaxLength*<br/>
指定 TCHAR 可以複製到緩衝區的字元的數目上限。 `GetLine` 將此值放在第一個文字*lpszBuffer*進行呼叫 Windows 之前。

### <a name="return-value"></a>傳回值

實際複製的字元數。 傳回值為 0，如果所指定的行號*nIndex*大於編輯控制項中的行數。

### <a name="remarks"></a>備註

所複製的行不包含 null 結束字元。

如需詳細資訊，請參閱 < [EM_GETLINE](/windows/desktop/Controls/em-getline) Windows SDK 中。

### <a name="example"></a>範例

  範例，請參閱[CEdit::GetLineCount](#getlinecount)。

##  <a name="getlinecount"></a>  CEdit::GetLineCount

呼叫此函式來擷取多行編輯控制項中的行數。

```
int GetLineCount() const;
```

### <a name="return-value"></a>傳回值

包含多行中的行號的整數的編輯控制項。 如果沒有文字輸入至編輯控制項，則傳回的值為 1。

### <a name="remarks"></a>備註

`GetLineCount` 只會處理多行編輯控制項。

如需詳細資訊，請參閱 < [EM_GETLINECOUNT](/windows/desktop/Controls/em-getlinecount) Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#12](../../mfc/reference/codesnippet/cpp/cedit-class_12.cpp)]

##  <a name="getmargins"></a>  CEdit::GetMargins

呼叫此成員函式，來擷取此編輯控制項的左邊和右邊邊界。

```
DWORD GetMargins() const;
```

### <a name="return-value"></a>傳回值

在低序位字組和高序位文字的右邊界的寬度左邊界的寬度。

### <a name="remarks"></a>備註

邊界被測量單位為像素。

> [!NOTE]
>  此成員函式是從 Windows 95 和 Windows NT 4.0。

如需詳細資訊，請參閱 < [EM_GETMARGINS](/windows/desktop/Controls/em-getmargins) Windows SDK 中。

### <a name="example"></a>範例

  範例，請參閱[CEditView::GetEditCtrl](ceditview-class.md#geteditctrl)。

##  <a name="getmodify"></a>  CEdit::GetModify

呼叫此函式可判斷是否已經修改編輯控制項的內容。

```
BOOL GetModify() const;
```

### <a name="return-value"></a>傳回值

非零值，如果已修改的編輯控制項內容;0，如果它們維持不變。

### <a name="remarks"></a>備註

Windows 會維護內部的旗標，指出是否已變更編輯控制項的內容。 當編輯控制項第一次建立時可能也會清除藉由呼叫時，清除這個旗標[SetModify](#setmodify)成員函式。

如需詳細資訊，請參閱 < [EM_GETMODIFY](/windows/desktop/Controls/em-getmodify) Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#13](../../mfc/reference/codesnippet/cpp/cedit-class_13.cpp)]

##  <a name="getpasswordchar"></a>  CEdit::GetPasswordChar

呼叫此函式可擷取使用者輸入文字時，會將編輯控制項中顯示的密碼字元。

```
TCHAR GetPasswordChar() const;
```

### <a name="return-value"></a>傳回值

指定要顯示而不是使用者所輸入字元的字元。 如果沒有密碼字元存在，則傳回的值是 NULL。

### <a name="remarks"></a>備註

如果您建立的 ES_PASSWORD 樣式的編輯控制項，則支援控制 DLL 會決定預設密碼字元。 資訊清單或[InitCommonControlsEx](/windows/desktop/api/commctrl/nf-commctrl-initcommoncontrolsex)方法會判斷 DLL 支援編輯控制項。 如果 user32.dll 支援編輯控制項的預設密碼字元是星號 ('* '，U + 002A)。 如果 comctl32.dll 版本 6 支援編輯控制項的預設字元是黑色圓形 （'●'，U + 25CF）。 如需有關哪些 DLL 和版本支援的通用控制項，請參閱[殼層和通用控制項版本](/previous-versions/windows/desktop/legacy/bb776779\(v=vs.85\))。

這個方法會傳送[EM_GETPASSWORDCHAR](/windows/desktop/Controls/em-getpasswordchar)訊息，Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#14](../../mfc/reference/codesnippet/cpp/cedit-class_14.cpp)]

##  <a name="getrect"></a>  CEdit::GetRect

呼叫此函式來取得編輯控制項的格式化矩形。

```
void GetRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向`RECT`接收格式化矩形的結構。

### <a name="remarks"></a>備註

格式化矩形是大小的文字，也就是大小的獨立的編輯控制項視窗限制的矩形。

可以藉由修改多行編輯控制項的格式化矩形[SetRect](#setrect)並[SetRectNP](#setrectnp)成員函式。

如需詳細資訊，請參閱 < [EM_GETRECT](/windows/desktop/Controls/em-getrect) Windows SDK 中。

### <a name="example"></a>範例

  範例，請參閱[CEdit::LimitText](#limittext)。

##  <a name="getsel"></a>  CEdit::GetSel

呼叫此函式可取得的起始和結束目前的選取範圍 （如果有的話） 中編輯控制項，使用傳回的值或參數的字元位置。

```
DWORD GetSel() const;

void GetSel(
    int& nStartChar,
    int& nEndChar) const;
```

### <a name="parameters"></a>參數

*nStartChar*<br/>
整數，會在目前的選取範圍中收到的第一個字元的位置參考。

*nEndChar*<br/>
整數，將會收到的未選取的第一個字元，超過目前的選取範圍結尾的位置參考。

### <a name="return-value"></a>傳回值

會傳回 DWORD 的版本會傳回包含高序位文字中的選取範圍結束之後的低序位字組中的開始位置和位置的第一個未選取字元的值。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [EM_GETSEL](/windows/desktop/Controls/em-getsel) Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#15](../../mfc/reference/codesnippet/cpp/cedit-class_15.cpp)]

##  <a name="hideballoontip"></a>  CEdit::HideBalloonTip

會隱藏任何目前的編輯控制項相關聯的汽球提示。

```
BOOL HideBalloonTip();
```

### <a name="return-value"></a>傳回值

如果成功，這個方法，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

此函式會將[EM_HIDEBALLOONTIP](/windows/desktop/Controls/em-hideballoontip)訊息，Windows SDK 中所述。

##  <a name="limittext"></a>  CEdit::LimitText

呼叫此函式來限制使用者可能會在編輯控制項中輸入文字的長度。

```
void LimitText(int nChars = 0);
```

### <a name="parameters"></a>參數

*nChars*<br/>
指定使用者可以輸入之文字的長度 （以 TCHARs)。 如果此參數為 0，會將文字長度設 UINT_MAX 位元組。 這是預設行為。

### <a name="remarks"></a>備註

變更文字限制會限制只有使用者可以輸入的文字。 它不會影響任何文字中已有編輯控制項，也不會影響複製到編輯控制項的文字長度[SetWindowText](cwnd-class.md#setwindowtext)成員函式中的`CWnd`。 如果應用程式使用`SetWindowText`函式，將更多的文字編輯控制項的呼叫中指定以外`LimitText`，使用者可以刪除任何編輯控制項中的文字。 不過，文字限制會防止使用者以新文字取代現有的文字，除非刪除目前選取範圍會導致低於文字限制的文字。

> [!NOTE]
>  在 Win32 中 （Windows NT 和 Windows 95/98） [SetLimitText](#setlimittext)會取代此函式。

如需詳細資訊，請參閱 < [EM_LIMITTEXT](/windows/desktop/Controls/em-limittext) Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#17](../../mfc/reference/codesnippet/cpp/cedit-class_16.cpp)]

##  <a name="linefromchar"></a>  CEdit::LineFromChar

呼叫此函式來擷取包含指定的字元索引的那一行的行號。

```
int LineFromChar(int nIndex = -1) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
包含編輯控制項的文字中所需的字元的以零為起始的索引值，或包含-1。 如果*nIndex*為-1，它會指定目前這一行，也就是包含插入號的行。

### <a name="return-value"></a>傳回值

包含所指定的字元索引的那一行的以零為起始的行號*nIndex*。 如果*nIndex*為-1，會傳回包含選取範圍的第一個字元的行號。 如果沒有選取範圍，則會傳回目前的行號。

### <a name="remarks"></a>備註

字元索引是編輯控制項的開頭的字元數。

此成員函式只會使用多行編輯控制項。

如需詳細資訊，請參閱 < [EM_LINEFROMCHAR](/windows/desktop/Controls/em-linefromchar) Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#18](../../mfc/reference/codesnippet/cpp/cedit-class_17.cpp)]

##  <a name="lineindex"></a>  CEdit::LineIndex

呼叫此函式來擷取多行編輯控制項中列的字元索引。

```
int LineIndex(int nLine = -1) const;
```

### <a name="parameters"></a>參數

*nLine*<br/>
包含編輯控制項的文字行的索引值，或包含-1。 如果*n 行*為-1，它會指定目前這一行，也就是包含插入號的行。

### <a name="return-value"></a>傳回值

在指定的行的字元索引*n 行*則為-1 大於編輯控制項中的行數的指定的行號。

### <a name="remarks"></a>備註

字元索引是從一開始編輯控制項的指定行的字元數目。

此成員函式只會處理多行編輯控制項。

如需詳細資訊，請參閱 < [EM_LINEINDEX](/windows/desktop/controls/em-lineindex) Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#19](../../mfc/reference/codesnippet/cpp/cedit-class_18.cpp)]

##  <a name="linelength"></a>  CEdit::LineLength

擷取編輯控制項中的資料行的長度。

```
int LineLength(int nLine = -1) const;
```

### <a name="parameters"></a>參數

*nLine*<br/>
其長度是要擷取的行中的字元以零為起始的索引。 預設值為 -1。

### <a name="return-value"></a>傳回值

單行編輯控制項，傳回的值會是編輯控制項中文字的長度，在 TCHARs。

對於多行編輯控制項，傳回的值是由指定的行的長度，以 TCHARs， *n 行*參數。 ANSI 文字的長度是在行中的位元組數目Unicode 文字的長度為行中的字元數。 長度不包含行尾的歸位字元。

如果*n 行*參數大於控制項中的字元數、 傳回值為零。

如果*n 行*參數值-1，則傳回的值為未選取中的字元數行，其中包含所選的字元。 例如，如果從一條從下一行的結尾的第八個字元的第四個字元，延伸選取範圍，傳回的值為 10。 也就是說，三個字元的第一行和七個下一步。

如需 TCHAR 類型的詳細資訊，請參閱 TCHAR 中的資料列中的資料表[Windows 資料類型](/windows/desktop/WinProg/windows-data-types)。

### <a name="remarks"></a>備註

這個方法受到[EM_LINELENGTH](/windows/desktop/Controls/em-linelength)訊息，Windows SDK 中所述。

### <a name="example"></a>範例

  範例，請參閱[CEdit::LineIndex](#lineindex)。

##  <a name="linescroll"></a>  CEdit::LineScroll

呼叫此函式可捲動的多行編輯控制項的文字。

```
void LineScroll(
    int nLines,
    int nChars = 0);
```

### <a name="parameters"></a>參數

*nLines*<br/>
指定要垂直捲動行的數。

*nChars*<br/>
指定以水平捲動的字元位置數目。 如果編輯控制項有 ES_RIGHT] 或是 [ES_CENTER 樣式，則會忽略此值。

### <a name="remarks"></a>備註

多行編輯控制項只會處理此成員函式。

編輯控制項不會以垂直方式捲動過去的文字編輯控制項中的最後一行。 如果目前的行加上所指定的行數*nLines*超過的編輯控制項中的總行數，此值會調整，以便編輯控制項的最後一行會捲動至編輯控制項視窗的頂端。

`LineScroll` 可用來水平捲動的任一行之最後一個字元。

如需詳細資訊，請參閱 < [EM_LINESCROLL](/windows/desktop/Controls/em-linescroll) Windows SDK 中。

### <a name="example"></a>範例

  範例，請參閱[CEdit::GetFirstVisibleLine](#getfirstvisibleline)。

##  <a name="paste"></a>  CEdit::Paste

呼叫此函式可將資料從剪貼簿插入`CEdit`的插入點。

```
void Paste();
```

### <a name="remarks"></a>備註

只有當剪貼簿包含 CF_TEXT 格式的資料插入資料。

如需詳細資訊，請參閱 < [WM_PASTE](/windows/desktop/dataxchg/wm-paste) Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#20](../../mfc/reference/codesnippet/cpp/cedit-class_19.cpp)]

##  <a name="posfromchar"></a>  CEdit::PosFromChar

呼叫此函式可取得指定的字元，在這個位置 （左上角）`CEdit`物件。

```
CPoint PosFromChar(UINT nChar) const;
```

### <a name="parameters"></a>參數

*nChar*<br/>
指定的字元以零為起始的索引。

### <a name="return-value"></a>傳回值

所指定的字元左上角的座標*nChar*。

### <a name="remarks"></a>備註

藉由提供其以零為起始的索引值，指定的字元。 如果*nChar*大於最後一個字元，在此索引`CEdit`物件，傳回的值在此指定剛好超過最後一個字元的字元位置的座標`CEdit`物件。

> [!NOTE]
>  此成員函式是從 Windows 95 和 Windows NT 4.0。

如需詳細資訊，請參閱 < [EM_POSFROMCHAR](/windows/desktop/Controls/em-posfromchar) Windows SDK 中。

### <a name="example"></a>範例

  範例，請參閱[CEdit::LineFromChar](#linefromchar)。

##  <a name="replacesel"></a>  CEdit::ReplaceSel

呼叫此函式，以取代所指定的文字編輯控制項中目前的選取範圍*lpszNewText*。

```
void ReplaceSel(LPCTSTR lpszNewText, BOOL bCanUndo = FALSE);
```

### <a name="parameters"></a>參數

*lpszNewText*<br/>
指向以 null 終止的字串，包含取代文字。

*bCanUndo*<br/>
若要指定此函式可以復原，設定此參數的值為 TRUE。 預設值為 FALSE。

### <a name="remarks"></a>備註

取代只包含編輯控制項中文字的一部分。 如果您要取代的所有文字，請使用[CWnd::SetWindowText](cwnd-class.md#setwindowtext)成員函式。

如果沒有目前的選取項目，取代文字會插入在目前游標位置。

如需詳細資訊，請參閱 < [EM_REPLACESEL](/windows/desktop/Controls/em-replacesel) Windows SDK 中。

### <a name="example"></a>範例

  範例，請參閱[CEdit::LineIndex](#lineindex)。

##  <a name="setcuebanner"></a>  CEdit::SetCueBanner

設定會顯示為文字提示，或提示，在編輯控制當控制項是空白的文字。

```
BOOL SetCueBanner(LPCWSTR lpszText);

BOOL SetCueBanner(
    LPCWSTR lpszText,
    BOOL fDrawWhenFocused = FALSE);
```

### <a name="parameters"></a>參數

*lpszText*<br/>
[in]包含要編輯控制項中顯示提示的字串指標。

*fDrawWhenFocused*<br/>
[in]如果為 FALSE，是不會繪製提示橫幅，當使用者在編輯控制項中按一下，並提供控制項焦點。

如果為 TRUE，即使控制項有焦點時，才繪製提示橫幅。 當使用者開始輸入控制項中時，就會消失提示橫幅。

預設值為 FALSE。

### <a name="return-value"></a>傳回值

如果方法成功，則為 TRUE否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[EM_SETCUEBANNER](/windows/desktop/Controls/em-setcuebanner)訊息，Windows SDK 中所述。 如需詳細資訊，請參閱 < [Edit_SetCueBannerTextFocused](/windows/desktop/api/commctrl/nf-commctrl-edit_setcuebannertextfocused)巨集。

### <a name="example"></a>範例

下列範例示範[CEdit::SetCueBanner](#setcuebanner)方法。

[!code-cpp[NVC_MFC_CEdit_s1#2](../../mfc/reference/codesnippet/cpp/cedit-class_20.cpp)]

##  <a name="sethandle"></a>  CEdit::SetHandle

呼叫此函式可將多行編輯控制項所使用的本機記憶體設定的控制代碼。

```
void SetHandle(HLOCAL hBuffer);
```

### <a name="parameters"></a>參數

*hBuffer*<br/>
包含本機記憶體的控制代碼。 這個控制代碼必須都由先前呼叫[LocalAlloc](/windows/desktop/api/winbase/nf-winbase-localalloc)使用 LMEM_MOVEABLE 旗標的 Windows 函式。 記憶體會假設包含以 null 結束的字串。 如果這不是這樣，就應該配置的記憶體中的第一個位元組設定為 0。

### <a name="remarks"></a>備註

然後編輯控制項就會使用這個緩衝區，來儲存目前顯示的文字，而不是它自己的緩衝區配置。

多行編輯控制項只會處理此成員函式。

應用程式設定新的記憶體處理之前，應該使用[GetHandle](#gethandle)成員函式來取得目前的記憶體緩衝區中的控制代碼，並釋放該記憶體使用`LocalFree`Windows 函式。

`SetHandle` 清除復原緩衝區 ( [CanUndo](#canundo)成員函式則會傳回 0) 和內部修改旗標 ( [GetModify](#getmodify)成員函式則會傳回 0)。 編輯控制項的視窗會重新繪製。

只有當您設定 DS_LOCALEDIT 樣式旗標建立對話方塊中，您可以在對話方塊中使用多行編輯控制項中的此成員函式。

> [!NOTE]
> `GetHandle` 不適用於 Windows 95/98。 如果您呼叫`GetHandle`在 Windows 95/98，它會傳回 NULL。 `GetHandle` 可在 Windows NT 3.51 及更新版本下所述。

如需詳細資訊，請參閱 < [EM_SETHANDLE](/windows/desktop/Controls/em-sethandle)， [LocalAlloc](/windows/desktop/api/winbase/nf-winbase-localalloc)，並[LocalFree](/windows/desktop/api/winbase/nf-winbase-localfree) Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#22](../../mfc/reference/codesnippet/cpp/cedit-class_21.cpp)]

##  <a name="sethighlight"></a>  CEdit::SetHighlight

反白顯示的範圍會顯示在目前的文字編輯控制項。

```
void SetHighlight(
    int ichStart,
    int ichEnd);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*ichStart*|[in]反白顯示的文字範圍中的第一個字元的以零為起始索引。|
|*ichEnd*|[in]反白顯示的文字範圍中的最後一個字元的以零為起始索引。|

### <a name="remarks"></a>備註

這個方法會傳送[EM_SETHILITE](/windows/desktop/Controls/em-sethilite)訊息，Windows SDK 中所述。  這個方法會傳送[EM_SETHILITE](/windows/desktop/Controls/em-sethilite)訊息，Windows SDK 中所述。 兩者`SetHighlight`和`GetHighlight`UNICODE 組建只會啟用。

##  <a name="setlimittext"></a>  CEdit::SetLimitText

呼叫此成員函式，若要設定此文字限制`CEdit`物件。

```
void SetLimitText(UINT nMax);
```

### <a name="parameters"></a>參數

*nMax*<br/>
新文字的限制，以字元為單位。

### <a name="remarks"></a>備註

文字限制為文字，請在編輯控制項可接受的字元的最大數量。

變更文字限制會限制只有使用者可以輸入的文字。 它不會影響任何文字中已有編輯控制項，也不會影響複製到編輯控制項的文字長度[SetWindowText](cwnd-class.md#setwindowtext)成員函式中的`CWnd`。 如果應用程式使用`SetWindowText`函式，將更多的文字編輯控制項的呼叫中指定以外`LimitText`，使用者可以刪除任何編輯控制項中的文字。 不過，文字限制會防止使用者以新文字取代現有的文字，除非刪除目前選取範圍會導致低於文字限制的文字。

此函數會取代[LimitText](#limittext)在 Win32 中。

如需詳細資訊，請參閱 < [EM_SETLIMITTEXT](/windows/desktop/Controls/em-setlimittext) Windows SDK 中。

### <a name="example"></a>範例

  範例，請參閱[CEditView::GetEditCtrl](ceditview-class.md#geteditctrl)。

##  <a name="setmargins"></a>  CEdit::SetMargins

呼叫這個方法來設定此編輯控制項的左邊和右邊邊界。

```
void SetMargins(
    UINT nLeft,
    UINT nRight);
```

### <a name="parameters"></a>參數

*nLeft*<br/>
新的左邊界，單位為像素的寬度。

*nRight*<br/>
新的右邊界，單位為像素的寬度。

### <a name="remarks"></a>備註

> [!NOTE]
>  此成員函式是從 Windows 95 和 Windows NT 4.0。

如需詳細資訊，請參閱 < [EM_SETMARGINS](/windows/desktop/Controls/em-setmargins) Windows SDK 中。

### <a name="example"></a>範例

  範例，請參閱[CEditView::GetEditCtrl](ceditview-class.md#geteditctrl)。

##  <a name="setmodify"></a>  CEdit::SetModify

呼叫此函式可設定或清除編輯控制項修改的旗標。

```
void SetModify(BOOL bModified = TRUE);
```

### <a name="parameters"></a>參數

*bModified*<br/>
如果為 true 值表示已修改的文字，，和 FALSE 值，指出它是未經修改。 根據預設，會設定已修改的旗標。

### <a name="remarks"></a>備註

修改的旗標表示已修改的文字編輯控制項中。 它會自動設定的每當使用者變更文字。 其值用來擷取[GetModify](#getmodify)成員函式。

如需詳細資訊，請參閱 < [EM_SETMODIFY](/windows/desktop/Controls/em-setmodify) Windows SDK 中。

### <a name="example"></a>範例

  範例，請參閱[CEdit::GetModify](#getmodify)。

##  <a name="setpasswordchar"></a>  CEdit::SetPasswordChar

呼叫此函式可設定或移除時使用者輸入的文字編輯控制項中顯示的密碼字元。

```
void SetPasswordChar(TCHAR ch);
```

### <a name="parameters"></a>參數

*ch*<br/>
指定要顯示使用者輸入的字元取代的字元。 如果*ch*是 0，則會顯示使用者輸入的實際字元。

### <a name="remarks"></a>備註

設定密碼字元時，該字元會顯示每個字元的使用者類型。

此成員函式已不會影響多行編輯控制項。

當`SetPasswordChar`成員函式呼叫時，`CEdit`將會重新繪製所有可見的字元，使用指定的字元*ch*。

如果編輯控制項以建立[ES_PASSWORD](styles-used-by-mfc.md#edit-styles)樣式，預設密碼字元設為星號 ( <strong>\*</strong>)。 如果移除此樣式`SetPasswordChar`以呼叫*ch*設為 0。

如需詳細資訊，請參閱 < [EM_SETPASSWORDCHAR](/windows/desktop/Controls/em-setpasswordchar) Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#16](../../mfc/reference/codesnippet/cpp/cedit-class_22.cpp)]

##  <a name="setreadonly"></a>  CEdit::SetReadOnly

呼叫此函式可將編輯控制項的唯讀狀態。

```
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```

### <a name="parameters"></a>參數

*bReadOnly*<br/>
指定是否要設定或移除編輯控制項的唯讀狀態。 如果為 true 會將狀態設定為唯讀的;FALSE 值設定為讀取/寫入的狀態。

### <a name="return-value"></a>傳回值

非零值，如果作業成功，則為 0，如果錯誤發生。

### <a name="remarks"></a>備註

目前的設定可以測試所發現[ES_READONLY](styles-used-by-mfc.md#edit-styles)中的傳回值的旗標[CWnd::GetStyle](cwnd-class.md#getstyle)。

如需詳細資訊，請參閱 < [EM_SETREADONLY](/windows/desktop/Controls/em-setreadonly) Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#23](../../mfc/reference/codesnippet/cpp/cedit-class_23.cpp)]

##  <a name="setrect"></a>  CEdit::SetRect

呼叫此函式可設定使用指定的座標是矩形的維度。

```
void SetRect(LPCRECT lpRect);
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向`RECT`結構或`CRect`物件，指定新的格式化矩形的維度。

### <a name="remarks"></a>備註

多行編輯控制項只會處理此成員。

使用`SetRect`設定的格式化矩形的多行編輯控制項。 格式化矩形是大小的文字，也就是大小的獨立的編輯控制項視窗限制的矩形。 編輯控制項最初建立時，格式化矩形是編輯控制項視窗的工作區相同。 使用`SetRect`成員函式，大於或小於編輯控制項視窗的應用程式可以進行格式化的矩形。

如果編輯控制項有沒有捲軸，文字會裁剪，不會包裝，如果格式化矩形超過視窗。 如果編輯控制項包含框線，框線的大小減少格式化矩形。 如果您調整所傳回的矩形`GetRect`成員函式，您必須移除框線的大小，才能傳遞至矩形`SetRect`。

當`SetRect`呼叫時，編輯控制項的文字也重新格式化並重新顯示。

如需詳細資訊，請參閱 < [EM_SETRECT](/windows/desktop/Controls/em-setrect) Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#24](../../mfc/reference/codesnippet/cpp/cedit-class_24.cpp)]

##  <a name="setrectnp"></a>  CEdit::SetRectNP

呼叫此函式來設定多行編輯控制項的格式化矩形。

```
void SetRectNP(LPCRECT lpRect);
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向`RECT`結構或`CRect`物件，指定矩形的新的維度。

### <a name="remarks"></a>備註

格式化矩形是大小的文字，也就是大小的獨立的編輯控制項視窗限制的矩形。

`SetRectNP` 等同於`SetRect`成員函式不同之處在於不會重新繪製編輯控制項的視窗。

編輯控制項最初建立時，格式化矩形是編輯控制項視窗的工作區相同。 藉由呼叫`SetRectNP`成員函式，大於或小於編輯控制項視窗的應用程式可以進行格式化的矩形。

如果編輯控制項有沒有捲軸，文字會裁剪，不會包裝，如果格式化矩形超過視窗。

多行編輯控制項只會處理此成員。

如需詳細資訊，請參閱 < [EM_SETRECTNP](/windows/desktop/Controls/em-setrectnp) Windows SDK 中。

### <a name="example"></a>範例

  範例，請參閱[CEdit::SetRect](#setrect)。

##  <a name="setsel"></a>  CEdit::SetSel

呼叫此函式可編輯控制項中選取的字元範圍。

```
void SetSel(
    DWORD dwSelection,
    BOOL bNoScroll = FALSE);

void SetSel(
    int nStartChar,
    int nEndChar,
    BOOL bNoScroll = FALSE);
```

### <a name="parameters"></a>參數

*dwSelection*<br/>
指定低序位字組中的開始位置和結束的位置中的高序位文字。 如果低序位字組為 0，而高序位字組為-1，則會選取編輯控制項中的所有文字。 如果低序位字組為-1，則會移除任何目前的選取範圍。

*bNoScroll*<br/>
指出是否應該插入號捲動到檢視。 如果為 FALSE，則會將插入號捲動到檢視。 如果為 TRUE，插入號不會捲動到檢視中。

*nStartChar*<br/>
指定的開始位置。 如果*nStartChar*為 0 並*nEndChar*為-1，所有選取的文字編輯控制項中。 如果*nStartChar*為-1，會移除任何目前的選取範圍。

*nEndChar*<br/>
指定的結束位置。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [EM_SETSEL](/windows/desktop/Controls/em-setsel) Windows SDK 中。

### <a name="example"></a>範例

  範例，請參閱[CEdit::GetSel](#getsel)。

##  <a name="settabstops"></a>  CEdit::SetTabStops

呼叫此函式以多行編輯控制項中設定定位停駐點。

```
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>參數

*cxEachStop*<br/>
指定在設定定位停駐點每隔*cxEachStop*對話方塊單位。

*nTabStops*<br/>
指定定位停駐點中包含的數目*rgTabStops*。 此數目必須大於 1。

*rgTabStops*<br/>
對話方塊單位，就會停止指向指定的索引標籤的不帶正負號整數的陣列。 對話方塊單位是水平或垂直距離。 一個水平對話方塊單位等於目前對話方塊基底寬度單位的四分之一，而且 1 個垂直對話方塊單位等於目前對話方塊基底的高度單位的八分之一。 對話方塊基本單位是根據目前系統字型的高度和寬度計算。 `GetDialogBaseUnits` Windows 函式會傳回目前對話方塊基底的單位像素為單位。

### <a name="return-value"></a>傳回值

如果已設定索引標籤，為非零否則為 0。

### <a name="remarks"></a>備註

當文字複製到多行編輯控制項時，任何索引標籤文字中的字元會導致產生到下一個定位停駐點的空間。

若要設定 32 個對話方塊單位的預設大小的定位停駐點，呼叫此成員函式的無參數的版本。 若要設定定位停駐點至 32 以外的大小，呼叫的版本與*cxEachStop*參數。 若要設定定位停駐點陣列的大小，請使用兩個參數使用的版本。

此成員函式只會處理多行編輯控制項。

`SetTabStops` 不會自動重新繪製 [編輯] 視窗。 如果您變更已在編輯控制項中文字的定位停駐點時，呼叫[CWnd::InvalidateRect](cwnd-class.md#invalidaterect)重繪 [編輯] 視窗。

如需詳細資訊，請參閱 < [EM_SETTABSTOPS](/windows/desktop/Controls/em-settabstops)並[GetDialogBaseUnits](/windows/desktop/api/winuser/nf-winuser-getdialogbaseunits) Windows SDK 中。

### <a name="example"></a>範例

  範例，請參閱[CEditView::SetTabStops](ceditview-class.md#settabstops)。

##  <a name="showballoontip"></a>  CEdit::ShowBalloonTip

顯示與目前的編輯控制項相關聯的汽球提示。

```
BOOL ShowBalloonTip(PEDITBALLOONTIP pEditBalloonTip);

BOOL ShowBalloonTip(
    LPCWSTR lpszTitle,
    LPCWSTR lpszText,
    INT ttiIcon = TTI_NONE);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*pEditBalloonTip*|[in]指標[EDITBALLOONTIP](/windows/desktop/api/commctrl/ns-commctrl-_tageditballoontip)該結構描述之氣球提示。|
|*lpszTitle*|[in]包含的汽球提示標題的 Unicode 字串指標。|
|*lpszText*|[in]包含的汽球提示文字的 Unicode 字串指標。|
|*ttiIcon*|[in]**INT**指定類型的相關聯之氣球提示的圖示。 預設值是 TTI_NONE。 如需詳細資訊，請參閱 <<c0> `ttiIcon` 隸屬[EDITBALLOONTIP](/windows/desktop/api/commctrl/ns-commctrl-_tageditballoontip)結構。|

### <a name="return-value"></a>傳回值

如果成功，這個方法，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

此函式會將[EM_SHOWBALLOONTIP](/windows/desktop/Controls/em-showballoontip)訊息，Windows SDK 中所述。 如需詳細資訊，請參閱 < [Edit_ShowBalloonTip](/windows/desktop/api/commctrl/nf-commctrl-edit_showballoontip)巨集。

### <a name="example"></a>範例

下列程式碼範例會定義變數`m_cedit`，也就是用來存取目前的編輯控制項。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CEdit_s1#1](../../mfc/reference/codesnippet/cpp/cedit-class_25.h)]

### <a name="example"></a>範例

下列程式碼範例會顯示編輯控制項的汽球提示。 [CEdit::ShowBalloonTip](#showballoontip)方法指定標題和註解方塊的提示文字。

[!code-cpp[NVC_MFC_CEdit_s1#3](../../mfc/reference/codesnippet/cpp/cedit-class_26.cpp)]

##  <a name="undo"></a>  CEdit::Undo

呼叫此函式可復原上次的編輯控制項作業。

```
BOOL Undo();
```

### <a name="return-value"></a>傳回值

單行編輯控制項，則傳回值永遠為非零值。 對於多行編輯控制項，傳回的值為非零，如果復原作業成功，則為 0，如果復原作業失敗。

### <a name="remarks"></a>備註

復原作業也會復原。 例如，您可以在其中還原刪除的文字，與第一次呼叫`Undo`。 只要沒有任何中介的編輯作業，您可以移除第二個呼叫一次的文字`Undo`。

如需詳細資訊，請參閱 < [EM_UNDO](/windows/desktop/Controls/em-undo) Windows SDK 中。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#25](../../mfc/reference/codesnippet/cpp/cedit-class_27.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[MFC 範例 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 類別](cwnd-class.md)<br/>
[CButton 類別](cbutton-class.md)<br/>
[CComboBox 類別](ccombobox-class.md)<br/>
[CListBox 類別](clistbox-class.md)<br/>
[CScrollBar 類別](cscrollbar-class.md)<br/>
[CStatic 類別](cstatic-class.md)<br/>
[CDialog 類別](cdialog-class.md)
