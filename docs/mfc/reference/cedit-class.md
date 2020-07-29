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
ms.openlocfilehash: 1cf195401f74261d3e67d5e8e945d1278ff2f90b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212497"
---
# <a name="cedit-class"></a>CEdit Class

提供 Windows 編輯控制項的功能。

## <a name="syntax"></a>語法

```
class CEdit : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CEdit：： CEdit](#cedit)|結構 `CEdit` 控制物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CEdit：： CanUndo](#canundo)|決定編輯控制作業是否可以復原。|
|[CEdit：： CharFromPos](#charfrompos)|抓取最接近指定位置之字元的行和字元索引。|
|[CEdit：： Clear](#clear)|刪除（清除）編輯控制項中目前的選取範圍（如果有的話）。|
|[CEdit：： Copy](#copy)|將編輯控制項中的目前選取範圍（如果有的話）複製到剪貼簿，格式為 CF_TEXT。|
|[CEdit：： Create](#create)|建立 Windows 編輯控制項，並將它附加至 `CEdit` 物件。|
|[CEdit：： Cut](#cut)|刪除（剪下）編輯控制項中目前的選取範圍（如果有的話），並以 CF_TEXT 格式將已刪除的文字複製到剪貼簿。|
|[CEdit：： EmptyUndoBuffer](#emptyundobuffer)|重設（清除）編輯控制項的復原旗標。|
|[CEdit：： FmtLines](#fmtlines)|設定在多行編輯控制項內包含或關閉虛分行字元。|
|[CEdit：： GetCueBanner](#getcuebanner)|當控制項為空白且沒有焦點時，抓取在編輯控制項中顯示為文字提示或提示的文字。|
|[CEdit：： GetFirstVisibleLine](#getfirstvisibleline)|決定編輯控制項中最上層的可見線。|
|[CEdit：： GetHandle](#gethandle)|抓取目前配置給多行編輯控制項之記憶體的控制碼。|
|[CEdit：： GetHighlight](#gethighlight)|取得在目前編輯控制項中反白顯示的文字範圍中，開頭和結尾字元的索引。|
|[CEdit：： GetLimitText](#getlimittext)|取得此可包含的最大文字量 `CEdit` 。|
|[CEdit：： GetLine](#getline)|從編輯控制項抓取一行文字。|
|[CEdit：： GetLineCount](#getlinecount)|抓取多行編輯控制項中的行數。|
|[CEdit：： GetMargins](#getmargins)|取得這個的左邊和右邊邊界 `CEdit` 。|
|[CEdit：： GetModify](#getmodify)|決定編輯控制項的內容是否已修改。|
|[CEdit：： GetPasswordChar](#getpasswordchar)|當使用者輸入文字時，抓取編輯控制項中顯示的密碼字元。|
|[CEdit：： GetRect](#getrect)|取得編輯控制項的格式化矩形。|
|[CEdit：： GetSel](#getsel)|取得編輯控制項中目前選取範圍的第一個和最後一個字元位置。|
|[CEdit：： HideBalloonTip](#hideballoontip)|隱藏與目前編輯控制項相關聯的任何球形氣球提示。|
|[CEdit：： LimitText](#limittext)|限制使用者可以在編輯控制項中輸入的文字長度。|
|[CEdit：： LineFromChar](#linefromchar)|抓取包含指定字元索引之行的行號。|
|[CEdit：： LineIndex](#lineindex)|抓取多行編輯控制項內一行的字元索引。|
|[CEdit：： LineLength](#linelength)|抓取編輯控制項中的行長度。|
|[CEdit：： LineScroll](#linescroll)|滾動多行編輯控制項的文字。|
|[CEdit：:P aste](#paste)|將剪貼簿中的資料插入目前游標位置的編輯控制項。 只有當剪貼簿包含 CF_TEXT 格式的資料時，才會插入資料。|
|[CEdit：:P osFromChar](#posfromchar)|抓取指定字元索引左上角的座標。|
|[CEdit：： ReplaceSel](#replacesel)|以指定的文字取代編輯控制項中目前的選取範圍。|
|[CEdit：： SetCueBanner](#setcuebanner)|設定當控制項為空白且沒有焦點時，在編輯控制項中顯示為文字提示或提示的文字。|
|[CEdit：： SetHandle](#sethandle)|將控制碼設定為將由多行編輯控制項使用的本機記憶體。|
|[CEdit：： SetHighlight](#sethighlight)|反白顯示目前編輯控制項中顯示的文字範圍。|
|[CEdit：： SetLimitText](#setlimittext)|設定此可包含的最大文字量 `CEdit` 。|
|[CEdit：： SetMargins](#setmargins)|設定這個的左邊和右邊邊界 `CEdit` 。|
|[CEdit：： SetModify](#setmodify)|設定或清除編輯控制項的修改旗標。|
|[CEdit：： SetPasswordChar](#setpasswordchar)|設定或移除使用者輸入文字時，編輯控制項中所顯示的密碼字元。|
|[CEdit：： SetReadOnly](#setreadonly)|設定編輯控制項的唯讀狀態。|
|[CEdit：： SetRect](#setrect)|設定多行編輯控制項的格式化矩形，並更新控制項。|
|[CEdit：： SetRectNP](#setrectnp)|設定多行編輯控制項的格式化矩形，而不重新繪製控制項視窗。|
|[CEdit：： SetSel](#setsel)|選取編輯控制項中的字元範圍。|
|[CEdit：： SetTabStops](#settabstops)|設定多行編輯控制項中的定位停駐點。|
|[CEdit：： ShowBalloonTip](#showballoontip)|顯示與目前編輯控制項相關聯的氣球提示。|
|[CEdit：： Undo](#undo)|反轉上次編輯控制作業。|

## <a name="remarks"></a>備註

編輯控制項是一個矩形子視窗，使用者可以在其中輸入文字。

您可以從對話方塊範本或直接在程式碼中建立編輯控制項。 在這兩種情況下，請先呼叫函式 `CEdit` 來建立 `CEdit` 物件，然後呼叫[create](#create)成員函式來建立 Windows 編輯控制項，並將它附加至 `CEdit` 物件。

在衍生自的類別中，結構可以是一個步驟的處理常式 `CEdit` 。 撰寫衍生類別的函式，並從函式 `Create` 內呼叫。

`CEdit`從繼承重要的功能 `CWnd` 。 若要設定和抓取物件中的文字 `CEdit` ，請使用成員函式 `CWnd` [SetWindowText](cwnd-class.md#setwindowtext)和[GetWindowText](cwnd-class.md#getwindowtext)，這會設定或取得編輯控制項的完整內容，即使它是多行控制項也一樣。 多行控制項中的文字會以 ' \r\n ' 字元序列分隔。 此外，如果編輯控制項是多行，請藉由呼叫成員函式 `CEdit` [GetLine](#getline)、 [SetSel](#setsel)、 [GetSel](#getsel)和[ReplaceSel](#replacesel)，取得並設定部分的控制項文字。

如果您想要處理編輯控制項傳送給其父系的 Windows 通知訊息（通常是衍生自的類別 `CDialog` ），請將訊息對應專案和訊息處理常式成員函式新增至每個訊息的父類別。

每個訊息對應專案會採用下列格式：

  **ON_**_通知_**（** _識別碼_**、** _memberFxn_ **）**

其中 `id` 指定要傳送通知之編輯控制項的子視窗識別碼，而 `memberFxn` 則是您已撰寫來處理通知之父成員函式的名稱。

父系的函數原型如下所示：

**afx_msg** void memberFxn **（）;**

以下是可能的訊息對應專案清單，以及其會傳送至父系的案例描述：

- ON_EN_CHANGE 使用者採取的動作可能已更改編輯控制項中的文字。 不同于 EN_UPDATE 通知訊息，此通知訊息會在 Windows 更新顯示後傳送。

- ON_EN_ERRSPACE 編輯控制項無法配置足夠的記憶體來符合特定的要求。

- ON_EN_HSCROLL 使用者按一下編輯控制項的水準捲軸。 在更新螢幕之前，會通知父視窗。

- ON_EN_KILLFOCUS 編輯控制項失去輸入焦點。

- ON_EN_MAXTEXT 目前的插入已超過編輯控制項指定的字元數，而且已被截斷。 當編輯控制項沒有 ES_AUTOHSCROLL 樣式，而且要插入的字元數超過編輯控制項的寬度時，也會傳送。 當編輯控制項沒有 ES_AUTOVSCROLL 樣式，而且文字插入所產生的總行數超過編輯控制項的高度時，也會一併傳送。

- 當編輯控制項收到輸入焦點時，ON_EN_SETFOCUS 傳送。

- ON_EN_UPDATE 編輯控制項即將顯示改變的文字。 在控制項已格式化文字之後，但在螢幕上會先傳送，以便在必要時變更視窗大小。

- ON_EN_VSCROLL 使用者按一下編輯控制項的垂直捲動條。 在更新螢幕之前，會通知父視窗。

如果您在 `CEdit` 對話方塊中建立物件， `CEdit` 當使用者關閉對話方塊時，就會自動終結物件。

如果您 `CEdit` 使用對話方塊編輯器從對話方塊資源建立物件， `CEdit` 當使用者關閉對話方塊時，會自動終結物件。

如果您在 `CEdit` 視窗中建立物件，您可能也需要將它摧毀。 如果您在 `CEdit` 堆疊上建立物件，它會自動終結。 如果您使用函式在 `CEdit` 堆積上建立物件 **`new`** ，您必須 **`delete`** 在物件上呼叫，以便在使用者終止 Windows 編輯控制項時終結它。 如果您在物件中配置任何記憶體 `CEdit` ，請覆寫 `CEdit` 析構函式以處置配置。

若要修改編輯控制項（例如 ES_READONLY）中的特定樣式，您必須將特定訊息傳送至控制項，而不是使用[ModifyStyle](cwnd-class.md#modifystyle)。 請參閱 Windows SDK 中的[編輯控制項樣式](/windows/win32/Controls/edit-control-styles)。

如需的詳細資訊 `CEdit` ，請參閱[控制項](../../mfc/controls-mfc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

`CEdit`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="ceditcanundo"></a><a name="canundo"></a>CEdit：： CanUndo

呼叫此函式，以判斷是否可以復原最後的編輯作業。

```
BOOL CanUndo() const;
```

### <a name="return-value"></a>傳回值

如果可以透過成員函式的呼叫來復原最後一個編輯作業，則為非零， `Undo` 如果無法復原，則為0。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 Windows SDK 中的[EM_CANUNDO](/windows/win32/Controls/em-canundo) 。

### <a name="example"></a>範例

  請參閱[CEdit：： Undo](#undo)的範例。

## <a name="ceditcedit"></a><a name="cedit"></a>CEdit：： CEdit

建構 `CEdit` 物件。

```
CEdit();
```

### <a name="remarks"></a>備註

使用 [[建立](#create)] 來建立 Windows 編輯控制項。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#1](../../mfc/reference/codesnippet/cpp/cedit-class_1.cpp)]

## <a name="ceditcharfrompos"></a><a name="charfrompos"></a>CEdit：： CharFromPos

呼叫此函式可抓取最接近此控制項中指定點的字元之以零為起始的行和字元索引 `CEdit`

```
int CharFromPos(CPoint pt) const;
```

### <a name="parameters"></a>參數

*pt*<br/>
這個物件的工作區中某個點的座標 `CEdit` 。

### <a name="return-value"></a>傳回值

低序位字組中的字元索引，以及高序位單字中的行索引。

### <a name="remarks"></a>備註

> [!NOTE]
> 從 Windows 95 和 Windows NT 4.0 開始提供此成員函式。

如需詳細資訊，請參閱 Windows SDK 中的[EM_CHARFROMPOS](/windows/win32/Controls/em-charfrompos) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#3](../../mfc/reference/codesnippet/cpp/cedit-class_2.cpp)]

## <a name="ceditclear"></a><a name="clear"></a>CEdit：： Clear

呼叫此函式可刪除（清除）編輯控制項中目前的選取範圍（如果有的話）。

```cpp
void Clear();
```

### <a name="remarks"></a>備註

您 `Clear` 可以藉由呼叫[Undo](#undo)成員函式來復原所執行的刪除作業。

若要刪除目前的選取範圍，並將已刪除的內容放入剪貼簿中，請呼叫[剪](#cut)下成員函式。

如需詳細資訊，請參閱 Windows SDK 中的[WM_CLEAR](/windows/win32/dataxchg/wm-clear) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#4](../../mfc/reference/codesnippet/cpp/cedit-class_3.cpp)]

## <a name="ceditcopy"></a><a name="copy"></a>CEdit：： Copy

呼叫此函式可將編輯控制項中的目前選取範圍（如果有的話）下列方式複製為 CF_TEXT 格式的剪貼簿。

```cpp
void Copy();
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 Windows SDK 中的[WM_COPY](/windows/win32/dataxchg/wm-copy) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#5](../../mfc/reference/codesnippet/cpp/cedit-class_4.cpp)]

## <a name="ceditcreate"></a><a name="create"></a>CEdit：： Create

建立 Windows 編輯控制項，並將它附加至 `CEdit` 物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定編輯控制項的樣式。 將[編輯樣式](styles-used-by-mfc.md#edit-styles)的任何組合套用至控制項。

*各種*<br/>
指定編輯控制項的大小和位置。 可以是 `CRect` 物件或 `RECT` 結構。

*pParentWnd*<br/>
指定編輯控制項的父視窗（通常是 `CDialog` ）。 它不得為 NULL。

*nID*<br/>
指定編輯控制項的識別碼。

### <a name="return-value"></a>傳回值

如果初始化成功，則為非零;否則為0。

### <a name="remarks"></a>備註

您可以使用 `CEdit` 兩個步驟來建立物件。 首先，呼叫此函式， `CEdit` 然後呼叫 `Create` ，它會建立 Windows 編輯控制項並將其附加至 `CEdit` 物件。

當 `Create` 執行時，Windows 會將[WM_NCCREATE](/windows/win32/winmsg/wm-nccreate)、 [WM_NCCALCSIZE](/windows/win32/winmsg/wm-nccalcsize)、 [WM_CREATE](/windows/win32/winmsg/wm-create)和[WM_GETMINMAXINFO](/windows/win32/winmsg/wm-getminmaxinfo)訊息傳送至編輯控制項。

根據預設，這些訊息會由基類中的[OnNcCreate](cwnd-class.md#onnccreate)、 [OnNcCalcSize](cwnd-class.md#onnccalcsize)、 [OnCreate](cwnd-class.md#oncreate)和[OnGetMinMaxInfo](cwnd-class.md#ongetminmaxinfo)成員函式來處理 `CWnd` 。 若要擴充預設訊息處理，請從衍生類別 `CEdit` ，將訊息對應加入至新的類別，並覆寫上述的訊息處理常式成員函式。 `OnCreate`例如，覆寫以執行新類別所需的初始化。

將下列[視窗樣式](styles-used-by-mfc.md#window-styles)套用至編輯控制項。

- 一律 WS_CHILD

- WS_VISIBLE 通常

- WS_DISABLED 很少

- WS_GROUP 至群組控制項

- WS_TABSTOP 以 tab 鍵順序加入編輯控制項

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#2](../../mfc/reference/codesnippet/cpp/cedit-class_5.cpp)]

## <a name="ceditcut"></a><a name="cut"></a>CEdit：： Cut

呼叫此函式可在編輯控制項中刪除（剪下）目前的選取範圍（如果有的話），並以 CF_TEXT 格式將已刪除的文字複製到剪貼簿。

```cpp
void Cut();
```

### <a name="remarks"></a>備註

您 `Cut` 可以藉由呼叫[Undo](#undo)成員函式來復原所執行的刪除作業。

若要刪除目前的選取範圍，而不將已刪除的文字放入剪貼簿中，請呼叫[Clear](#clear)成員函式。

如需詳細資訊，請參閱 Windows SDK 中的[WM_CUT](/windows/win32/dataxchg/wm-cut) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#6](../../mfc/reference/codesnippet/cpp/cedit-class_6.cpp)]

## <a name="ceditemptyundobuffer"></a><a name="emptyundobuffer"></a>CEdit：： EmptyUndoBuffer

呼叫此函式以重設（清除）編輯控制項的復原旗標。

```cpp
void EmptyUndoBuffer();
```

### <a name="remarks"></a>備註

編輯控制項現在將無法復原最後一個作業。 每當編輯控制項內的作業可以復原時，就會設定「復原」旗標。

每當呼叫[SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)或[SetHandle](#sethandle)成員函式時，就會自動清除復原旗標 `CWnd` 。

如需詳細資訊，請參閱 Windows SDK 中的[EM_EMPTYUNDOBUFFER](/windows/win32/Controls/em-emptyundobuffer) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#7](../../mfc/reference/codesnippet/cpp/cedit-class_7.cpp)]

## <a name="ceditfmtlines"></a><a name="fmtlines"></a>CEdit：： FmtLines

呼叫此函式可在多行編輯控制項內設定包含虛分行符號字元的功能。

```
BOOL FmtLines(BOOL bAddEOL);
```

### <a name="parameters"></a>參數

*bAddEOL*<br/>
指定是否要插入軟換行字元。 TRUE 的值會插入字元;值為 FALSE 時，會將其移除。

### <a name="return-value"></a>傳回值

如果發生任何格式，則為非零值;否則為0。

### <a name="remarks"></a>備註

軟換行是由兩個回車傳回，而且在行尾插入的換行是因為斷字而中斷。 硬式分行符號包含一個回車和一個換行字元。 以硬式分行符號結尾的行不會受到的影響 `FmtLines` 。

只有當 `CEdit` 物件為多行編輯控制項時，Windows 才會回應。

`FmtLines`只會影響[GetHandle](#gethandle)所傳回的緩衝區，以及[WM_GETTEXT](/windows/win32/winmsg/wm-gettext)所傳回的文字。 它對編輯控制項內的文字顯示不會有任何影響。

如需詳細資訊，請參閱 Windows SDK 中的[EM_FMTLINES](/windows/win32/Controls/em-fmtlines) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#8](../../mfc/reference/codesnippet/cpp/cedit-class_8.cpp)]

## <a name="ceditgetcuebanner"></a><a name="getcuebanner"></a>CEdit：： GetCueBanner

當控制項為空白時，抓取編輯控制項中顯示為文字提示或提示的文字。

```
BOOL GetCueBanner(
    LPWSTR lpszText,
    int cchText) const;

CString GetCueBanner() const;
```

### <a name="parameters"></a>參數

*lpszText*<br/>
脫銷包含提示文字之字串的指標。

*cchText*<br/>
在可以接收的字元數。 這個數位包含結束的 Null 字元。

### <a name="return-value"></a>傳回值

針對第一個多載，如果方法成功，則為 TRUE;否則為 FALSE。

針對第二個多載，如果方法成功，則為包含提示文字的[CString](../../atl-mfc-shared/using-cstring.md) ;否則為空字串（""）。

### <a name="remarks"></a>備註

這個方法會傳送[EM_GETCUEBANNER](/windows/win32/Controls/em-getcuebanner)訊息，如 Windows SDK 所述。 如需詳細資訊，請參閱[Edit_GetCueBannerText](/windows/win32/api/commctrl/nf-commctrl-edit_getcuebannertext)宏。

## <a name="ceditgetfirstvisibleline"></a><a name="getfirstvisibleline"></a>CEdit：： GetFirstVisibleLine

呼叫此函式可判斷編輯控制項中最上層的可見線。

```
int GetFirstVisibleLine() const;
```

### <a name="return-value"></a>傳回值

最上層可見行之以零為起始的索引。 若為單行編輯控制項，則傳回值為0。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 Windows SDK 中的[EM_GETFIRSTVISIBLELINE](/windows/win32/Controls/em-getfirstvisibleline) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#9](../../mfc/reference/codesnippet/cpp/cedit-class_9.cpp)]

## <a name="ceditgethandle"></a><a name="gethandle"></a>CEdit：： GetHandle

呼叫此函式可抓取目前配置給多行編輯控制項的記憶體控制碼。

```
HLOCAL GetHandle() const;
```

### <a name="return-value"></a>傳回值

本機記憶體控制碼，可識別保存編輯控制項內容的緩衝區。 如果發生錯誤，例如將訊息傳送至單行編輯控制項，則傳回值為0。

### <a name="remarks"></a>備註

控制碼是本機記憶體控制碼，可供接受本機記憶體控制碼做為參數的任何**本機**Windows 記憶體函數使用。

`GetHandle`只由多行編輯控制項處理。

`GetHandle`只有在已設定 DS_LOCALEDIT 樣式旗標的對話方塊建立時，才會在對話方塊中呼叫多行編輯控制項。 如果未設定 DS_LOCALEDIT 樣式，您仍然會得到非零的傳回值，但您將無法使用傳回的值。

> [!NOTE]
> `GetHandle`將無法用於 Windows 95/98。 如果您 `GetHandle` 在 Windows 95/98 中呼叫，它會傳回 Null。 `GetHandle`會如 Windows NT 3.51 版和更新版本中所記載的方式工作。

如需詳細資訊，請參閱 Windows SDK 中的[EM_GETHANDLE](/windows/win32/Controls/em-gethandle) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#10](../../mfc/reference/codesnippet/cpp/cedit-class_10.cpp)]

## <a name="ceditgethighlight"></a><a name="gethighlight"></a>CEdit：： GetHighlight

取得文字範圍中的第一個和最後一個字元的索引，在目前的編輯控制項中反白顯示。

```
BOOL GetHighlight(
    int* pichStart,
    int* pichEnd) const;
```

### <a name="parameters"></a>參數

|參數|說明|
|---------------|-----------------|
|*pichStart*|脫銷反白顯示的文字範圍中第一個字元之以零為起始的索引。|
|*pichEnd*|脫銷反白顯示的文字範圍中，最後一個字元的索引（以零為基底）。|

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[EM_GETHILITE](/windows/win32/Controls/em-gethilite)訊息，如 Windows SDK 所述。 `SetHighlight`和 `GetHighlight` 目前僅針對 UNICODE 組建啟用。

## <a name="ceditgetlimittext"></a><a name="getlimittext"></a>CEdit：： GetLimitText

呼叫這個成員函式以取得此物件的文字限制 `CEdit` 。

```
UINT GetLimitText() const;
```

### <a name="return-value"></a>傳回值

這個物件目前的文字限制（以 TCHARs 為限） `CEdit` 。

### <a name="remarks"></a>備註

文字限制是編輯控制項可以接受的最大文字量（以 TCHARs 為限）。

> [!NOTE]
> 從 Windows 95 和 Windows NT 4.0 開始提供此成員函式。

如需詳細資訊，請參閱 Windows SDK 中的[EM_GETLIMITTEXT](/windows/win32/Controls/em-getlimittext) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#11](../../mfc/reference/codesnippet/cpp/cedit-class_11.cpp)]

## <a name="ceditgetline"></a><a name="getline"></a>CEdit：： GetLine

呼叫此函式可從編輯控制項取出一行文字，並將它放在*lpszBuffer*中。

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
指定要從多行編輯控制項取出的行號。 行號是以零為基底;值為0會指定第一行。 單一行編輯控制項會忽略這個參數。

*lpszBuffer*<br/>
指向接收一行複本的緩衝區。 緩衝區的第一個字必須指定可複製到緩衝區的最大 TCHARs 數目。

*nMaxLength*<br/>
指定可以複製到緩衝區的 TCHAR 字元數目上限。 `GetLine`在呼叫 Windows 之前，將此值放在*lpszBuffer*的第一個字組中。

### <a name="return-value"></a>傳回值

實際複製的字元數。 如果*nIndex*所指定的行號大於編輯控制項中的行數，則傳回值為0。

### <a name="remarks"></a>備註

複製的行不包含 null 終止字元。

如需詳細資訊，請參閱 Windows SDK 中的[EM_GETLINE](/windows/win32/Controls/em-getline) 。

### <a name="example"></a>範例

  請參閱[CEdit：： GetLineCount](#getlinecount)的範例。

## <a name="ceditgetlinecount"></a><a name="getlinecount"></a>CEdit：： GetLineCount

呼叫此函式可取出多行編輯控制項中的行數。

```
int GetLineCount() const;
```

### <a name="return-value"></a>傳回值

整數，包含多行編輯控制項中的行數。 如果編輯控制項中未輸入任何文字，則傳回值為1。

### <a name="remarks"></a>備註

`GetLineCount`只由多行編輯控制項處理。

如需詳細資訊，請參閱 Windows SDK 中的[EM_GETLINECOUNT](/windows/win32/Controls/em-getlinecount) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#12](../../mfc/reference/codesnippet/cpp/cedit-class_12.cpp)]

## <a name="ceditgetmargins"></a><a name="getmargins"></a>CEdit：： GetMargins

呼叫這個成員函式，以抓取此編輯控制項的左邊和右邊邊界。

```
DWORD GetMargins() const;
```

### <a name="return-value"></a>傳回值

低序位單字中左邊界的寬度，以及高序位單字中右邊界的寬度。

### <a name="remarks"></a>備註

邊界是以圖元為單位。

> [!NOTE]
> 從 Windows 95 和 Windows NT 4.0 開始提供此成員函式。

如需詳細資訊，請參閱 Windows SDK 中的[EM_GETMARGINS](/windows/win32/Controls/em-getmargins) 。

### <a name="example"></a>範例

  請參閱[CEditView：： GetEditCtrl](ceditview-class.md#geteditctrl)的範例。

## <a name="ceditgetmodify"></a><a name="getmodify"></a>CEdit：： GetModify

呼叫此函式可判斷編輯控制項的內容是否已修改。

```
BOOL GetModify() const;
```

### <a name="return-value"></a>傳回值

如果編輯控制項內容已修改，則為非零值;如果保持不變，則為0。

### <a name="remarks"></a>備註

Windows 會維護一個內部旗標，指出編輯控制項的內容是否已經變更。 第一次建立編輯控制項時，會清除此旗標，而且也可以藉由呼叫[SetModify](#setmodify)成員函式來清除。

如需詳細資訊，請參閱 Windows SDK 中的[EM_GETMODIFY](/windows/win32/Controls/em-getmodify) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#13](../../mfc/reference/codesnippet/cpp/cedit-class_13.cpp)]

## <a name="ceditgetpasswordchar"></a><a name="getpasswordchar"></a>CEdit：： GetPasswordChar

呼叫此函式可在使用者輸入文字時，取得編輯控制項中顯示的密碼字元。

```
TCHAR GetPasswordChar() const;
```

### <a name="return-value"></a>傳回值

指定要顯示的字元，而不是使用者輸入的字元。 如果不存在任何密碼字元，則傳回值為 Null。

### <a name="remarks"></a>備註

如果您使用 ES_PASSWORD 樣式建立編輯控制項，則支援控制項的 DLL 會決定預設密碼字元。 資訊清單或[InitCommonControlsEx](/windows/win32/api/commctrl/nf-commctrl-initcommoncontrolsex)方法會決定哪一個 DLL 支援編輯控制項。 如果 user32.dll 支援編輯控制項，則預設的密碼字元為星號（' * '、U + 002A）。 如果 comctl32.dll 版本6支援編輯控制項，則預設字元為黑色圓圈（' ● '，U + 25CF）。 如需哪些 DLL 和版本支援通用控制項的詳細資訊，請參閱[Shell 和通用控制項版本](/previous-versions/windows/desktop/legacy/bb776779\(v=vs.85\))。

這個方法會傳送[EM_GETPASSWORDCHAR](/windows/win32/Controls/em-getpasswordchar)訊息，如 Windows SDK 所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#14](../../mfc/reference/codesnippet/cpp/cedit-class_14.cpp)]

## <a name="ceditgetrect"></a><a name="getrect"></a>CEdit：： GetRect

呼叫此函式可取得編輯控制項的格式化矩形。

```cpp
void GetRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向 `RECT` 接收格式化矩形的結構。

### <a name="remarks"></a>備註

格式化矩形是文字的限制矩形，與編輯控制視窗的大小無關。

多行編輯控制項的格式化矩形可以由[SetRect](#setrect)和[SetRectNP](#setrectnp)成員函式進行修改。

如需詳細資訊，請參閱 Windows SDK 中的[EM_GETRECT](/windows/win32/Controls/em-getrect) 。

### <a name="example"></a>範例

  請參閱[CEdit：： LimitText](#limittext)的範例。

## <a name="ceditgetsel"></a><a name="getsel"></a>CEdit：： GetSel

呼叫此函式，以使用傳回值或參數，取得編輯控制項中目前選取範圍的開始和結束字元位置（如果有的話）。

```
DWORD GetSel() const;

void GetSel(
    int& nStartChar,
    int& nEndChar) const;
```

### <a name="parameters"></a>參數

*nStartChar*<br/>
參考會接收目前選取範圍中第一個字元位置的整數。

*nEndChar*<br/>
整數的參考，將會在目前選取範圍結束之後接收第一個 nonselected 字元的位置。

### <a name="return-value"></a>傳回值

傳回 DWORD 的版本會傳回一個值，其中包含低序位單字中的開始位置，以及在高序位單字選取範圍結尾之後第一個 nonselected 字元的位置。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 Windows SDK 中的[EM_GETSEL](/windows/win32/Controls/em-getsel) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#15](../../mfc/reference/codesnippet/cpp/cedit-class_15.cpp)]

## <a name="cedithideballoontip"></a><a name="hideballoontip"></a>CEdit：： HideBalloonTip

隱藏與目前編輯控制項相關聯的任何球形氣球提示。

```
BOOL HideBalloonTip();
```

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

此函式會傳送[EM_HIDEBALLOONTIP](/windows/win32/Controls/em-hideballoontip)訊息，如 Windows SDK 所述。

## <a name="ceditlimittext"></a><a name="limittext"></a>CEdit：： LimitText

呼叫此函式可限制使用者可以在編輯控制項中輸入的文字長度。

```cpp
void LimitText(int nChars = 0);
```

### <a name="parameters"></a>參數

*nChars*<br/>
指定使用者可以輸入文字的長度（以 TCHARs）。 如果此參數為0，則文字長度會設定為 UINT_MAX 個位元組。 此為預設行為。

### <a name="remarks"></a>備註

變更文字限制只會限制使用者可以輸入的文字。 它不會影響任何已經在編輯控制項中的文字，也不會影響中的[SetWindowText](cwnd-class.md#setwindowtext)成員函式複製到編輯控制項的文字長度 `CWnd` 。 如果應用程式使用函 `SetWindowText` 式將更多文字放入編輯控制項中，而不是呼叫中指定的 `LimitText` ，則使用者可以刪除編輯控制項中的任何文字。 不過，文字限制會讓使用者無法以新的文字取代現有的文字，除非刪除目前的選取範圍會導致文字低於文字限制。

> [!NOTE]
> 在 Win32 （Windows NT 和 Windows 95/98）中， [SetLimitText](#setlimittext)會取代此功能。

如需詳細資訊，請參閱 Windows SDK 中的[EM_LIMITTEXT](/windows/win32/Controls/em-limittext) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#17](../../mfc/reference/codesnippet/cpp/cedit-class_16.cpp)]

## <a name="ceditlinefromchar"></a><a name="linefromchar"></a>CEdit：： LineFromChar

呼叫此函式可取出包含指定字元索引之行的行號。

```
int LineFromChar(int nIndex = -1) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
包含編輯控制項文字中所需字元的以零為基底的索引值，或包含-1。 如果*nIndex*為-1，則會指定目前的行，也就是包含插入號的行。

### <a name="return-value"></a>傳回值

包含*nIndex*所指定之字元索引的行之以零為起始的行號。 如果*nIndex*為-1，則會傳回包含選取範圍之第一個字元的行號。 如果沒有選取專案，則會傳回目前的行號。

### <a name="remarks"></a>備註

字元索引是編輯控制項開頭的字元數。

這個成員函式僅供多行編輯控制項使用。

如需詳細資訊，請參閱 Windows SDK 中的[EM_LINEFROMCHAR](/windows/win32/Controls/em-linefromchar) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#18](../../mfc/reference/codesnippet/cpp/cedit-class_17.cpp)]

## <a name="ceditlineindex"></a><a name="lineindex"></a>CEdit：： LineIndex

呼叫此函式可抓取多行編輯控制項內一行的字元索引。

```
int LineIndex(int nLine = -1) const;
```

### <a name="parameters"></a>參數

*N 行*<br/>
在編輯控制項的文字中包含所需行的索引值，或包含-1。 如果*n 行*為-1，則會指定目前的行，也就是包含插入號的行。

### <a name="return-value"></a>傳回值

*N 行*中指定之行的字元索引，如果指定的行號大於編輯控制項中的行數，則為-1。

### <a name="remarks"></a>備註

字元索引是從編輯控制項開頭到指定行的字元數。

這個成員函式只會由多行編輯控制項處理。

如需詳細資訊，請參閱 Windows SDK 中的[EM_LINEINDEX](/windows/win32/controls/em-lineindex) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#19](../../mfc/reference/codesnippet/cpp/cedit-class_18.cpp)]

## <a name="ceditlinelength"></a><a name="linelength"></a>CEdit：： LineLength

抓取編輯控制項中的行長度。

```
int LineLength(int nLine = -1) const;
```

### <a name="parameters"></a>參數

*N 行*<br/>
要抓取其長度之行中的字元之以零為基底的索引。 預設值為 -1。

### <a name="return-value"></a>傳回值

對於單行編輯控制項，傳回值是編輯控制項中文字的長度（以 TCHARs 為單位）。

針對多行編輯控制項，傳回值是*n 行*參數所指定之行的長度（以 TCHARs）。 若為 ANSI 文字，長度為行中的位元組數目;若為 Unicode 文字，長度為行中的字元數。 長度不包含行尾的回車符。

如果*n 行*參數超過控制項中的字元數，則傳回值會是零。

如果*n 行*參數為-1，則傳回值為包含所選取字元之行中未選取的字元數。 例如，如果選取範圍從一行的第四個字元延伸到下一行結尾的第八個字元，則傳回值會是10。 也就是第一行有三個字元，而下一個則是七個字元。

如需 TCHAR 類型的詳細資訊，請參閱[Windows 資料類型](/windows/win32/WinProg/windows-data-types)中資料表的 TCHAR 一列。

### <a name="remarks"></a>備註

[EM_LINELENGTH](/windows/win32/Controls/em-linelength)訊息支援此方法，如 Windows SDK 所述。

### <a name="example"></a>範例

  請參閱[CEdit：： LineIndex](#lineindex)的範例。

## <a name="ceditlinescroll"></a><a name="linescroll"></a>CEdit：： LineScroll

呼叫此函式可滾動多行編輯控制項的文字。

```cpp
void LineScroll(
    int nLines,
    int nChars = 0);
```

### <a name="parameters"></a>參數

*nLines*<br/>
指定要垂直捲動的行數。

*nChars*<br/>
指定要水準滾動的字元位置數目。 如果編輯控制項具有 ES_RIGHT 或 ES_CENTER 樣式，則會忽略這個值。

### <a name="remarks"></a>備註

這個成員函式只會由多行編輯控制項處理。

編輯控制項不會垂直捲動超過編輯控制項中的最後一行文字。 如果目前的行加上*nLines*所指定的行數超過編輯控制項中的總行數，則會調整值，使編輯控制項的最後一行滾動到編輯控制項視窗的頂端。

`LineScroll`可以用來水準滾動到任何一行的最後一個字元之後。

如需詳細資訊，請參閱 Windows SDK 中的[EM_LINESCROLL](/windows/win32/Controls/em-linescroll) 。

### <a name="example"></a>範例

  請參閱[CEdit：： GetFirstVisibleLine](#getfirstvisibleline)的範例。

## <a name="ceditpaste"></a><a name="paste"></a>CEdit：:P aste

呼叫此函式可將剪貼簿中的資料插入至 `CEdit` 插入點。

```cpp
void Paste();
```

### <a name="remarks"></a>備註

只有當剪貼簿包含 CF_TEXT 格式的資料時，才會插入資料。

如需詳細資訊，請參閱 Windows SDK 中的[WM_PASTE](/windows/win32/dataxchg/wm-paste) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#20](../../mfc/reference/codesnippet/cpp/cedit-class_19.cpp)]

## <a name="ceditposfromchar"></a><a name="posfromchar"></a>CEdit：:P osFromChar

呼叫此函式可取得此物件內指定字元的位置（左上角） `CEdit` 。

```
CPoint PosFromChar(UINT nChar) const;
```

### <a name="parameters"></a>參數

*nChar*<br/>
指定字元之以零為基底的索引。

### <a name="return-value"></a>傳回值

*NChar*所指定之字元左上角的座標。

### <a name="remarks"></a>備註

字元是藉由提供其以零為基底的索引值來指定。 如果*nChar*大於這個物件中最後一個字元的索引 `CEdit` ，則傳回值會指定緊接在這個物件中最後一個字元之後的字元位置座標 `CEdit` 。

> [!NOTE]
> 從 Windows 95 和 Windows NT 4.0 開始提供此成員函式。

如需詳細資訊，請參閱 Windows SDK 中的[EM_POSFROMCHAR](/windows/win32/Controls/em-posfromchar) 。

### <a name="example"></a>範例

  請參閱[CEdit：： LineFromChar](#linefromchar)的範例。

## <a name="ceditreplacesel"></a><a name="replacesel"></a>CEdit：： ReplaceSel

呼叫此函式可將編輯控制項中目前的選取範圍取代為*lpszNewText*所指定的文字。

```cpp
void ReplaceSel(LPCTSTR lpszNewText, BOOL bCanUndo = FALSE);
```

### <a name="parameters"></a>參數

*lpszNewText*<br/>
指向以 null 終止的字串，其中包含取代文字。

*bCanUndo*<br/>
若要指定此函數可以復原，請將此參數的值設定為 TRUE。 預設值為 FALSE。

### <a name="remarks"></a>備註

只取代編輯控制項中的部分文字。 如果您想要取代所有的文字，請使用[CWnd：： SetWindowText](cwnd-class.md#setwindowtext)成員函式。

如果沒有目前的選取範圍，則會在目前的游標位置插入取代文字。

如需詳細資訊，請參閱 Windows SDK 中的[EM_REPLACESEL](/windows/win32/Controls/em-replacesel) 。

### <a name="example"></a>範例

  請參閱[CEdit：： LineIndex](#lineindex)的範例。

## <a name="ceditsetcuebanner"></a><a name="setcuebanner"></a>CEdit：： SetCueBanner

設定當控制項為空白時，在編輯控制項中顯示為文字提示或提示的文字。

```
BOOL SetCueBanner(LPCWSTR lpszText);

BOOL SetCueBanner(
    LPCWSTR lpszText,
    BOOL fDrawWhenFocused = FALSE);
```

### <a name="parameters"></a>參數

*lpszText*<br/>
在字串的指標，其中包含要顯示在編輯控制項中的提示。

*fDrawWhenFocused*<br/>
在若為 FALSE，當使用者在編輯控制項中按一下並提供焦點給控制項時，不會繪製提示橫幅。

若為 TRUE，則即使控制項有焦點，也會繪製提示橫幅。 當使用者開始鍵入控制項時，提示橫幅就會消失。

預設值為 FALSE。

### <a name="return-value"></a>傳回值

如果方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[EM_SETCUEBANNER](/windows/win32/Controls/em-setcuebanner)訊息，如 Windows SDK 所述。 如需詳細資訊，請參閱[Edit_SetCueBannerTextFocused](/windows/win32/api/commctrl/nf-commctrl-edit_setcuebannertextfocused)宏。

### <a name="example"></a>範例

下列範例示範[CEdit：： SetCueBanner](#setcuebanner)方法。

[!code-cpp[NVC_MFC_CEdit_s1#2](../../mfc/reference/codesnippet/cpp/cedit-class_20.cpp)]

## <a name="ceditsethandle"></a><a name="sethandle"></a>CEdit：： SetHandle

呼叫此函式可將控制碼設定為將由多行編輯控制項使用的本機記憶體。

```cpp
void SetHandle(HLOCAL hBuffer);
```

### <a name="parameters"></a>參數

*hBuffer*<br/>
包含本機記憶體的控制碼。 這個控制碼必須是先前使用 LMEM_MOVEABLE 旗標呼叫[LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc) Windows 函數所建立的。 記憶體會假設為包含以 null 終止的字串。 如果不是這種情況，則配置記憶體的第一個位元組應該設定為0。

### <a name="remarks"></a>備註

編輯控制項接著會使用這個緩衝區來儲存目前顯示的文字，而不是配置自己的緩衝區。

這個成員函式只會由多行編輯控制項處理。

在應用程式設定新的記憶體控制碼之前，它應該使用[GetHandle](#gethandle)成員函式來取得目前記憶體緩衝區的控制碼，並使用 Windows 函數釋放該記憶體 `LocalFree` 。

`SetHandle`清除復原緩衝區（ [CanUndo](#canundo)成員函式會傳回0）和內部修改旗標（ [GetModify](#getmodify)成員函式會傳回0）。 [編輯控制] 視窗會重新繪製。

只有在已建立已設定 DS_LOCALEDIT 樣式旗標的對話方塊時，您才可以在對話方塊的多行編輯控制項中使用這個成員函式。

> [!NOTE]
> `GetHandle`將無法用於 Windows 95/98。 如果您 `GetHandle` 在 Windows 95/98 中呼叫，它會傳回 Null。 `GetHandle`會如 Windows NT 3.51 版和更新版本中所記載的方式工作。

如需詳細資訊，請參閱 Windows SDK 中的[EM_SETHANDLE](/windows/win32/Controls/em-sethandle)、 [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc)和[LocalFree](/windows/win32/api/winbase/nf-winbase-localfree) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#22](../../mfc/reference/codesnippet/cpp/cedit-class_21.cpp)]

## <a name="ceditsethighlight"></a><a name="sethighlight"></a>CEdit：： SetHighlight

反白顯示目前編輯控制項中顯示的文字範圍。

```cpp
void SetHighlight(
    int ichStart,
    int ichEnd);
```

### <a name="parameters"></a>參數

|參數|說明|
|---------------|-----------------|
|*ichStart*|在要反白顯示的文字範圍中第一個字元之以零為起始的索引。|
|*ichEnd*|在要反白顯示的文字範圍中，最後一個字元的索引（以零為基底）。|

### <a name="remarks"></a>備註

這個方法會傳送[EM_SETHILITE](/windows/win32/Controls/em-sethilite)訊息，如 Windows SDK 所述。  這個方法會傳送[EM_SETHILITE](/windows/win32/Controls/em-sethilite)訊息，如 Windows SDK 所述。 `SetHighlight`和 `GetHighlight` 都僅針對 UNICODE 組建啟用。

## <a name="ceditsetlimittext"></a><a name="setlimittext"></a>CEdit：： SetLimitText

呼叫這個成員函式可設定這個物件的文字限制 `CEdit` 。

```cpp
void SetLimitText(UINT nMax);
```

### <a name="parameters"></a>參數

*N 上限*<br/>
新的文字限制（以字元為單位）。

### <a name="remarks"></a>備註

文字限制是編輯控制項可以接受的文字數量上限（以字元為單位）。

變更文字限制只會限制使用者可以輸入的文字。 它不會影響任何已經在編輯控制項中的文字，也不會影響中的[SetWindowText](cwnd-class.md#setwindowtext)成員函式複製到編輯控制項的文字長度 `CWnd` 。 如果應用程式使用函 `SetWindowText` 式將更多文字放入編輯控制項中，而不是呼叫中指定的 `LimitText` ，則使用者可以刪除編輯控制項中的任何文字。 不過，文字限制會讓使用者無法以新的文字取代現有的文字，除非刪除目前的選取範圍會導致文字低於文字限制。

此函式會取代 Win32 中的[LimitText](#limittext) 。

如需詳細資訊，請參閱 Windows SDK 中的[EM_SETLIMITTEXT](/windows/win32/Controls/em-setlimittext) 。

### <a name="example"></a>範例

  請參閱[CEditView：： GetEditCtrl](ceditview-class.md#geteditctrl)的範例。

## <a name="ceditsetmargins"></a><a name="setmargins"></a>CEdit：： SetMargins

呼叫這個方法，以設定此編輯控制項的左右邊界。

```cpp
void SetMargins(
    UINT nLeft,
    UINT nRight);
```

### <a name="parameters"></a>參數

*nLeft*<br/>
新左邊界的寬度（以圖元為單位）。

*nRight*<br/>
新右邊界的寬度（以圖元為單位）。

### <a name="remarks"></a>備註

> [!NOTE]
> 從 Windows 95 和 Windows NT 4.0 開始提供此成員函式。

如需詳細資訊，請參閱 Windows SDK 中的[EM_SETMARGINS](/windows/win32/Controls/em-setmargins) 。

### <a name="example"></a>範例

  請參閱[CEditView：： GetEditCtrl](ceditview-class.md#geteditctrl)的範例。

## <a name="ceditsetmodify"></a><a name="setmodify"></a>CEdit：： SetModify

呼叫此函式可設定或清除編輯控制項的修改旗標。

```cpp
void SetModify(BOOL bModified = TRUE);
```

### <a name="parameters"></a>參數

*bModified*<br/>
值為 TRUE 時，表示已修改文字，而值為 FALSE 則表示未修改。 根據預設，已修改的旗標已設定。

### <a name="remarks"></a>備註

修改過的旗標會指出是否已修改編輯控制項內的文字。 每當使用者變更文字時，就會自動設定它。 它的值可以使用[GetModify](#getmodify)成員函式來抓取。

如需詳細資訊，請參閱 Windows SDK 中的[EM_SETMODIFY](/windows/win32/Controls/em-setmodify) 。

### <a name="example"></a>範例

  請參閱[CEdit：： GetModify](#getmodify)的範例。

## <a name="ceditsetpasswordchar"></a><a name="setpasswordchar"></a>CEdit：： SetPasswordChar

呼叫此函式可在使用者輸入文字時，設定或移除編輯控制項中顯示的密碼字元。

```cpp
void SetPasswordChar(TCHAR ch);
```

### <a name="parameters"></a>參數

*頻道*<br/>
指定要顯示的字元，以取代使用者所輸入的字元。 如果*ch*為0，則會顯示使用者輸入的實際字元。

### <a name="remarks"></a>備註

設定密碼字元時，會針對使用者所輸入的每個字元顯示該字元。

這個成員函式對多行編輯控制項沒有任何作用。

呼叫成員函式時 `SetPasswordChar` ， `CEdit` 會使用*ch*指定的字元來重繪所有可見字元。

如果使用[ES_PASSWORD](styles-used-by-mfc.md#edit-styles)樣式建立編輯控制項，則預設密碼字元會設定為星號（ <strong>\*</strong> ）。 如果 `SetPasswordChar` 使用設定為0的*ch*呼叫，則會移除此樣式。

如需詳細資訊，請參閱 Windows SDK 中的[EM_SETPASSWORDCHAR](/windows/win32/Controls/em-setpasswordchar) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#16](../../mfc/reference/codesnippet/cpp/cedit-class_22.cpp)]

## <a name="ceditsetreadonly"></a><a name="setreadonly"></a>CEdit：： SetReadOnly

會呼叫這個函式來設定編輯控制項的唯讀狀態。

```
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```

### <a name="parameters"></a>參數

*bReadOnly*<br/>
指定是否要設定或移除編輯控制項的唯讀狀態。 TRUE 值會將狀態設定為唯讀;值為 FALSE 時，會將狀態設定為讀取/寫入。

### <a name="return-value"></a>傳回值

如果作業成功，則為非零，如果發生錯誤，則為0。

### <a name="remarks"></a>備註

藉由測試[CWnd：： GetStyle](cwnd-class.md#getstyle)的傳回值中的[ES_READONLY](styles-used-by-mfc.md#edit-styles)旗標，即可找到目前的設定。

如需詳細資訊，請參閱 Windows SDK 中的[EM_SETREADONLY](/windows/win32/Controls/em-setreadonly) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#23](../../mfc/reference/codesnippet/cpp/cedit-class_23.cpp)]

## <a name="ceditsetrect"></a><a name="setrect"></a>CEdit：： SetRect

呼叫此函式可使用指定的座標來設定矩形的維度。

```cpp
void SetRect(LPCRECT lpRect);
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向 `RECT` 結構或 `CRect` 物件，指定格式化矩形的新維度。

### <a name="remarks"></a>備註

這個成員只會由多行編輯控制項處理。

用 `SetRect` 來設定多行編輯控制項的格式化矩形。 格式化矩形是文字的限制矩形，與編輯控制視窗的大小無關。 第一次建立編輯控制項時，[格式化] 矩形會與 [編輯控制] 視窗的工作區相同。 藉由使用 `SetRect` 成員函式，應用程式可以讓格式化矩形大於或小於編輯控制視窗。

如果編輯控制項沒有捲軸，則如果格式化矩形的設定大於視窗，則會裁剪文字，而不會換行。 如果編輯控制項包含框線，則格式化矩形會縮小框線的大小。 如果您調整成員函式所傳回的矩形 `GetRect` ，就必須先移除框線的大小，然後再將矩形傳遞給 `SetRect` 。

當 `SetRect` 呼叫時，編輯控制項的文字也會重新格式化並重新顯示。

如需詳細資訊，請參閱 Windows SDK 中的[EM_SETRECT](/windows/win32/Controls/em-setrect) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#24](../../mfc/reference/codesnippet/cpp/cedit-class_24.cpp)]

## <a name="ceditsetrectnp"></a><a name="setrectnp"></a>CEdit：： SetRectNP

呼叫此函式可設定多行編輯控制項的格式化矩形。

```cpp
void SetRectNP(LPCRECT lpRect);
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向 `RECT` `CRect` 指定矩形新維度的結構或物件。

### <a name="remarks"></a>備註

格式化矩形是文字的限制矩形，與編輯控制視窗的大小無關。

`SetRectNP`與 `SetRect` 成員函式相同，不同之處在于編輯控制視窗不會重新繪製。

第一次建立編輯控制項時，[格式化] 矩形會與 [編輯控制] 視窗的工作區相同。 藉由呼叫 `SetRectNP` 成員函式，應用程式可以讓格式化矩形大於或小於編輯控制視窗。

如果編輯控制項沒有捲軸，則如果格式化矩形的設定大於視窗，則會裁剪文字，而不會換行。

這個成員只會由多行編輯控制項處理。

如需詳細資訊，請參閱 Windows SDK 中的[EM_SETRECTNP](/windows/win32/Controls/em-setrectnp) 。

### <a name="example"></a>範例

  請參閱[CEdit：： SetRect](#setrect)的範例。

## <a name="ceditsetsel"></a><a name="setsel"></a>CEdit：： SetSel

呼叫此函式可選取編輯控制項中的字元範圍。

```cpp
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
指定低序位字組中的開始位置，以及高序位單字中的結束位置。 如果低序位字組為0，且高序位單字為-1，則會選取編輯控制項中的所有文字。 如果低序位字組為-1，則會移除任何目前的選取範圍。

*bNoScroll*<br/>
指出插入號是否應滾動到 view。 若為 FALSE，則會將插入號滾動到 view。 若為 TRUE，則插入號不會滾動到 view。

*nStartChar*<br/>
指定開始位置。 如果*nStartChar*為0，而*nEndChar*為-1，則會選取編輯控制項中的所有文字。 如果*nStartChar*為-1，則會移除任何目前的選取範圍。

*nEndChar*<br/>
指定結束位置。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 Windows SDK 中的[EM_SETSEL](/windows/win32/Controls/em-setsel) 。

### <a name="example"></a>範例

  請參閱[CEdit：： GetSel](#getsel)的範例。

## <a name="ceditsettabstops"></a><a name="settabstops"></a>CEdit：： SetTabStops

呼叫此函式可在多行編輯控制項中設定制表位。

```cpp
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>參數

*cxEachStop*<br/>
指定要在每個*cxEachStop*對話單位上設定制表位。

*nTabStops*<br/>
指定*rgTabStops*中包含的定位停駐點數目。 這個數位必須大於1。

*rgTabStops*<br/>
指向不帶正負號整數的陣列，指定對話方塊單位中的定位停駐點。 對話單位是水準或垂直距離。 一個水準對話單位等於目前對話基底寬度單位的四分之一，而1個垂直對話方塊單位等於目前對話基底高度單位的八分之一。 對話方塊基本單位是根據目前系統字型的高度和寬度計算。 Windows 函式會傳回 `GetDialogBaseUnits` 目前的對話方塊基底單位（以圖元為單位）。

### <a name="return-value"></a>傳回值

如果已設定索引標籤，則為非零值;否則為0。

### <a name="remarks"></a>備註

當文字複製到多行編輯控制項時，文字中的任何定位字元都會產生下一個定位停駐點的空間。

若要將 tab 鍵停駐于預設大小的32對話單位，請呼叫此成員函式的無參數版本。 若要將 tab 鍵停駐于32以外的大小，請使用*cxEachStop*參數呼叫版本。 若要將 tab 鍵停駐于大小陣列，請使用具有兩個參數的版本。

這個成員函式只會由多行編輯控制項處理。

`SetTabStops`不會自動重繪 [編輯] 視窗。 如果您變更已在編輯控制項中之文字的定位停駐點，請呼叫[CWnd：： InvalidateRect](cwnd-class.md#invalidaterect)來重繪 [編輯] 視窗。

如需詳細資訊，請參閱 Windows SDK 中的[EM_SETTABSTOPS](/windows/win32/Controls/em-settabstops)和[GetDialogBaseUnits](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits) 。

### <a name="example"></a>範例

  請參閱[CEditView：： SetTabStops](ceditview-class.md#settabstops)的範例。

## <a name="ceditshowballoontip"></a><a name="showballoontip"></a>CEdit：： ShowBalloonTip

顯示與目前編輯控制項相關聯的氣球提示。

```
BOOL ShowBalloonTip(PEDITBALLOONTIP pEditBalloonTip);

BOOL ShowBalloonTip(
    LPCWSTR lpszTitle,
    LPCWSTR lpszText,
    INT ttiIcon = TTI_NONE);
```

### <a name="parameters"></a>參數

|參數|說明|
|---------------|-----------------|
|*pEditBalloonTip*|在描述氣球提示之[EDITBALLOONTIP](/windows/win32/api/commctrl/ns-commctrl-editballoontip)結構的指標。|
|*lpszTitle*|在Unicode 字串的指標，其中包含氣球提示的標題。|
|*lpszText*|在包含氣球提示文字之 Unicode 字串的指標。|
|*ttiIcon*|在**INT** ，指定要與氣球提示相關聯的圖示類型。 預設值為 TTI_NONE。 如需詳細資訊，請參閱 `ttiIcon` [EDITBALLOONTIP](/windows/win32/api/commctrl/ns-commctrl-editballoontip)結構的成員。|

### <a name="return-value"></a>傳回值

如果此方法成功，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

此函式會傳送[EM_SHOWBALLOONTIP](/windows/win32/Controls/em-showballoontip)訊息，如 Windows SDK 所述。 如需詳細資訊，請參閱[Edit_ShowBalloonTip](/windows/win32/api/commctrl/nf-commctrl-edit_showballoontip)宏。

### <a name="example"></a>範例

下列程式碼範例 `m_cedit` 會定義用來存取目前編輯控制項的變數。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CEdit_s1#1](../../mfc/reference/codesnippet/cpp/cedit-class_25.h)]

### <a name="example"></a>範例

下列程式碼範例會顯示編輯控制項的氣球提示。 [CEdit：： ShowBalloonTip](#showballoontip)方法會指定標題和氣球提示文字。

[!code-cpp[NVC_MFC_CEdit_s1#3](../../mfc/reference/codesnippet/cpp/cedit-class_26.cpp)]

## <a name="ceditundo"></a><a name="undo"></a>CEdit：： Undo

呼叫此函式可復原上次編輯控制作業。

```
BOOL Undo();
```

### <a name="return-value"></a>傳回值

針對單行編輯控制項，傳回值一律為非零。 若為多行編輯控制項，如果復原作業成功，傳回值為非零，如果復原作業失敗，則傳回0。

### <a name="remarks"></a>備註

復原作業也可以復原。 例如，您可以在第一次呼叫時還原已刪除的文字 `Undo` 。 只要沒有中間的編輯作業，您就可以在第二次呼叫時，再次移除文字 `Undo` 。

如需詳細資訊，請參閱 Windows SDK 中的[EM_UNDO](/windows/win32/Controls/em-undo) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#25](../../mfc/reference/codesnippet/cpp/cedit-class_27.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 CALCDRIV:](../../overview/visual-cpp-samples.md)<br/>
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
