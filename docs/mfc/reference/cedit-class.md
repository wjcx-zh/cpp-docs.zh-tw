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
ms.openlocfilehash: 3ca2fe4486ae0751f37d046ef28ed11e60e776ac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373977"
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
|[編輯:編輯](#cedit)|構造`CEdit`控件物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[編輯::CanUndo](#canundo)|確定是否可以撤銷編輯控制操作。|
|[編輯::查里波斯](#charfrompos)|檢索最接近指定位置的字元的行和字元索引。|
|[編輯:清除](#clear)|刪除(清除)編輯控制項中的當前選擇(如果有)。|
|[編輯::複製](#copy)|以CF_TEXT格式將編輯控制件中的當前選擇(如果有)複製到剪貼簿。|
|[編輯::建立](#create)|創建 Windows 編輯控制件並將其`CEdit`附加到 物件。|
|[編輯::切割](#cut)|刪除(剪切)編輯控制項中的目前選擇(如果有),並將刪除的文本以CF_TEXT格式複製到剪貼簿。|
|[編輯::空UndoBuffer](#emptyundobuffer)|重置(清除)編輯控制項的復原標誌。|
|[編輯::Fmtlines](#fmtlines)|設置多行編輯控制項中軟換行字元的包含。|
|[編輯::GetCueBanner](#getcuebanner)|當控制項為空且沒有焦點時,檢索在編輯控制項中顯示為文本提示或提示的文本。|
|[編輯:取得第一可見線](#getfirstvisibleline)|確定編輯控制項中最上面可見的行。|
|[編輯::取得手柄](#gethandle)|檢索當前為多行編輯控制件分配的記憶體的句柄。|
|[編輯:取得高光](#gethighlight)|獲取目前編輯控制項中突出顯示的文本範圍內的起始字元和結束字元的索引。|
|[編輯::取得限制文字](#getlimittext)|獲取可以`CEdit`包含的最大文本量。|
|[編輯:抓取線](#getline)|從編輯控制項檢索一行文本。|
|[編輯::取得線計數](#getlinecount)|檢索多行編輯控制件中的行數。|
|[編輯::取得邊緣](#getmargins)|獲取此`CEdit`的左右邊距。|
|[編輯::取得修改](#getmodify)|確定編輯控制件的內容是否已修改。|
|[編輯::抓取密碼字元](#getpasswordchar)|當使用者輸入文本時,檢索編輯控件中顯示的密碼字元。|
|[編輯::取得 Rect](#getrect)|取得編輯控制項的格式矩形。|
|[編輯::GetSel](#getsel)|在編輯控制項中獲取當前所選內容的第一個和最後一個字元位置。|
|[編輯::隱藏氣球提示](#hideballoontip)|隱藏與當前編輯控制件關聯的任何氣球提示。|
|[編輯::限制文字](#limittext)|限制用戶可以在編輯控制項中輸入的文本長度。|
|[編輯::線從查爾](#linefromchar)|檢索包含指定字元索引的行號的行號。|
|[編輯:串列引](#lineindex)|檢索多行編輯控制件中的行的字元索引。|
|[編輯:線長](#linelength)|檢索編輯控制件中的行的長度。|
|[編輯::線捲動](#linescroll)|捲動多行編輯控制項的文字。|
|[編輯::Paste](#paste)|將剪輯簿中的資料插入到目前游標位置的編輯控制項中。 僅當剪貼簿以CF_TEXT格式包含數據時,才會插入數據。|
|[編輯::P從查爾](#posfromchar)|檢索指定字元索引左上角的座標。|
|[編輯::取代氏](#replacesel)|將編輯控制項中的目前選擇取代為指定的文本。|
|[編輯::設定庫班](#setcuebanner)|設置當控制項為空且沒有焦點時,在編輯控制項中顯示為文本提示或提示的文本。|
|[編輯::設定手](#sethandle)|將句柄設置到多行編輯控制項將使用的本地記憶體。|
|[編輯:設定高光](#sethighlight)|突顯目前編輯控制項中顯示的文字範圍。|
|[編輯::設定限制文字](#setlimittext)|設置可以`CEdit`包含的最大文本量。|
|[編輯::設定邊界](#setmargins)|設定左邊距`CEdit`。|
|[編輯::設定修改](#setmodify)|設置或清除編輯控制件的修改標誌。|
|[編輯::設定密碼字元](#setpasswordchar)|設定或刪除使用者輸入文本時在編輯控制項中顯示的密碼字元。|
|[編輯:僅設定 Read](#setreadonly)|設置編輯控制項的唯讀狀態。|
|[編輯::設定重新](#setrect)|設定多行編輯控制項的格式矩形並更新該控制項。|
|[編輯::設定RectNP](#setrectnp)|設置多行編輯控制件的格式矩形,而無需重新繪製控制件視窗。|
|[編輯::SetSel](#setsel)|在編輯控制項中選擇一系列字元。|
|[編輯::設定標籤](#settabstops)|在多行編輯控制項中設置製表符停止。|
|[編輯::顯示氣球提示](#showballoontip)|顯示與當前編輯控制件關聯的氣球提示。|
|[編輯:復原](#undo)|反轉上次編輯控制操作。|

## <a name="remarks"></a>備註

編輯控制項是一個矩形子視窗,用戶可以在其中輸入文本。

可以從對話框範本或直接在代碼中創建編輯控制項。 在這兩種情況下,首先調用構造`CEdit`函數構`CEdit`造 物件,然後調用[Create](#create)成員函數以創建 Windows 編輯`CEdit`控件並將其附加到 物件。

構造可以是派生自`CEdit`的類中的一個步驟。 為派生類編寫一個構造函數,並從`Create`構造函數內部調用。

`CEdit`從 繼承重要`CWnd`功能 。 若要從`CEdit`物件設置和檢索文本,請`CWnd`使用成員函數[SetWindowText](cwnd-class.md#setwindowtext)和[GetWindowText](cwnd-class.md#getwindowtext),它們設置或獲取編輯控制項的全部內容,即使它是多行控制件。 多行控制項中的文字行由「\r\n」字串序列分隔。 此外,如果編輯控件是多行的,則通過`CEdit`調用成員函數[GetLine、SetSel、GetSel](#getline)和[ReplaceSel](#replacesel)獲取[GetSel](#getsel)和設置控制件文本[SetSel](#setsel)的一部分。

如果要處理由編輯控制件發送到其父級(通常是派生自`CDialog`的類)的 Windows 通知訊息,請為每個消息向父類添加消息映射條目和消息處理程式成員函數。

每個訊息對應項目以以下的檔案:

  **ON_**_通知_**(ID** _ _ **,** _成員Fxn_ **)**

其中`id`指定傳送通知的編輯控制項的子視窗`memberFxn`ID,以及 您為處理通知而編寫的父成員函數的名稱。

父函數原型如下所示:

**afx_msg**無效成員Fxn **( ;**

以下是潛在訊息對應項目的清單,以及將它們傳送到父項目的說明:

- ON_EN_CHANGE使用者已執行的操作可能更改了編輯控制項中的文本。 與EN_UPDATE通知消息不同,此通知消息是在Windows更新顯示後發送的。

- ON_EN_ERRSPACE 編輯控制件無法分配足夠的記憶體以滿足特定請求。

- ON_EN_HSCROLL用戶按一下編輯控制件的水準滾動條。 在更新螢幕之前,將通知父視窗。

- ON_EN_KILLFOCUS 編輯控制件失去輸入焦點。

- ON_EN_MAXTEXT當前插入已超過編輯控制項的指定字元數,並且已被截斷。 當編輯控制項沒有ES_AUTOHSCROLL樣式且要插入的字元數超過編輯控制項的寬度時,也會發送。 當編輯控制項沒有ES_AUTOVSCROLL樣式,並且文本插入產生的行總數將超過編輯控制項的高度時,也會發送。

- ON_EN_SETFOCUS編輯控制件接收輸入焦點時已發送。

- ON_EN_UPDATE 編輯控制項即將顯示更改的文字。 控制項在控制檔格式化文本後傳送,但在它篩選文本之前,以便在必要時可以更改視窗大小。

- ON_EN_VSCROLL用戶按一下編輯控制件的垂直滾動條。 在更新螢幕之前,將通知父視窗。

如果在對話框中創建`CEdit`物件,則當使用者關閉對話方`CEdit`塊時 ,該物件將自動銷毀。

如果使用對話框編輯器從`CEdit`對話方塊資源創建物件,則當使用者關閉對話方`CEdit`塊時, 該物件將自動銷毀。

如果在視窗中創建`CEdit`物件,則可能需要銷毀它。 如果在堆疊上`CEdit`創建物件,則會自動銷毀該物件。 如果使用**新**函數在`CEdit`堆上創建物件,**則必須調用刪除**物件以在使用者終止 Windows 編輯控制件時銷毀該物件。 如果在`CEdit`物件中分配任何記憶體,請重寫`CEdit`析構函數以釋放分配。

要修改編輯控制檔中的某些樣式(如ES_READONLY),必須向控制件傳送特定訊息,而不是使用[ModifyStyle](cwnd-class.md#modifystyle)。 請參考 Windows SDK 的[編輯控制項樣式](/windows/win32/Controls/edit-control-styles)。

有關 的詳細`CEdit`資訊 ,請參閱[控制項](../../mfc/controls-mfc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

`CEdit`

## <a name="requirements"></a>需求

**標題:** afxwin.h

## <a name="ceditcanundo"></a><a name="canundo"></a>編輯::CanUndo

呼叫此函數以確定是否可以撤銷最後一個編輯操作。

```
BOOL CanUndo() const;
```

### <a name="return-value"></a>傳回值

如果最後一個編輯操作可以通過調`Undo`用 成員函數撤銷,則非零;0,如果它不能撤銷。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱 Windows SDK 中的[EM_CANUNDO。](/windows/win32/Controls/em-canundo)

### <a name="example"></a>範例

  請參考[CEdit::復原的範例](#undo)。

## <a name="ceditcedit"></a><a name="cedit"></a>編輯:編輯

建構 `CEdit` 物件。

```
CEdit();
```

### <a name="remarks"></a>備註

使用[「建立](#create)」建構 Windows 編輯控制件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#1](../../mfc/reference/codesnippet/cpp/cedit-class_1.cpp)]

## <a name="ceditcharfrompos"></a><a name="charfrompos"></a>編輯::查里波斯

呼叫此函式以檢索離此`CEdit`控制項中指定點的字元的零基線和字元索引

```
int CharFromPos(CPoint pt) const;
```

### <a name="parameters"></a>參數

*pt*<br/>
此`CEdit`物件工作區中點的座標。

### <a name="return-value"></a>傳回值

低階 WORD 中的字元索引和高階 WORD 中的線索引。

### <a name="remarks"></a>備註

> [!NOTE]
> 此成員功能從 Windows 95 和 Windows NT 4.0 開始可用。

有關詳細資訊,請參閱 Windows SDK 中的[EM_CHARFROMPOS。](/windows/win32/Controls/em-charfrompos)

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#3](../../mfc/reference/codesnippet/cpp/cedit-class_2.cpp)]

## <a name="ceditclear"></a><a name="clear"></a>編輯:清除

呼叫此函數以刪除(清除)編輯控制項中的當前選擇(如果有)。

```
void Clear();
```

### <a name="remarks"></a>備註

可以通過調用[復原](#undo)成員`Clear`函數撤銷執行的刪除。

要刪除當前選擇並將已刪除的內容放入剪貼簿,請呼叫[「剪切](#cut)」成員函數。

有關詳細資訊,請參閱 Windows SDK 中的[WM_CLEAR。](/windows/win32/dataxchg/wm-clear)

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#4](../../mfc/reference/codesnippet/cpp/cedit-class_3.cpp)]

## <a name="ceditcopy"></a><a name="copy"></a>編輯::複製

呼叫此函數以CF_TEXT格式將編輯控制項中的當前選擇(如果有)與剪貼簿進行配合。

```
void Copy();
```

### <a name="remarks"></a>備註

有關詳細資訊,請參閱 Windows SDK 中的[WM_COPY。](/windows/win32/dataxchg/wm-copy)

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#5](../../mfc/reference/codesnippet/cpp/cedit-class_4.cpp)]

## <a name="ceditcreate"></a><a name="create"></a>編輯::建立

創建 Windows 編輯控制件並將其`CEdit`附加到 物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定編輯控制項樣式。 將[編輯樣式](styles-used-by-mfc.md#edit-styles)的任意組合應用於控制項。

*矩形*<br/>
指定編輯控制項大小和位置。 可以是`CRect`對`RECT`象或結構。

*pparentwnd*<br/>
指定編輯控制檔的父視窗(通常為`CDialog`。 它不得為 NULL。

*nID*<br/>
指定編輯控制項的識別碼。

### <a name="return-value"></a>傳回值

初始化成功時非零;否則 0。

### <a name="remarks"></a>備註

分兩步`CEdit`構造物件。 首先調用`CEdit`建構函數,然後調`Create`用 ,這將創建 Windows 編輯控件`CEdit`並將其附加到 物件。

執行`Create`時,Windows[WM_NCCREATE](/windows/win32/winmsg/wm-nccreate)會將WM_NCCREATE、WM_NCCALCSIZE、WM_CREATE和[WM_GETMINMAXINFO消息發送到](/windows/win32/winmsg/wm-getminmaxinfo)編輯[WM_NCCALCSIZE](/windows/win32/winmsg/wm-nccalcsize)[WM_CREATE](/windows/win32/winmsg/wm-create)控制項。

默認情況下,這些消息由`CWnd`基類中的[OnNcCreate、OnNcCalcsize、OnCreate](cwnd-class.md#onnccreate)和[OnGetMinMaxInfo](cwnd-class.md#ongetminmaxinfo)成員[OnNcCalcSize](cwnd-class.md#onnccalcsize)[OnCreate](cwnd-class.md#oncreate)函數處理。 要擴展預設消息處理,從`CEdit`派生類,向新類添加消息映射,並重寫上述消息處理程式成員函數。 例如`OnCreate`,重寫以執行新類所需的初始化。

將以下[視窗樣式](styles-used-by-mfc.md#window-styles)應用於編輯控制項。

- WS_CHILD始終

- WS_VISIBLE 通常

- WS_DISABLED很少

- WS_GROUP元件

- WS_TABSTOP在制表順序包含編輯控制項

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#2](../../mfc/reference/codesnippet/cpp/cedit-class_5.cpp)]

## <a name="ceditcut"></a><a name="cut"></a>編輯::切割

呼叫此函數以刪除(剪切)編輯控制項中的當前選擇(如果有),並將刪除的文本以CF_TEXT格式複製到剪貼簿。

```
void Cut();
```

### <a name="remarks"></a>備註

可以通過調用[復原](#undo)成員`Cut`函數撤銷執行的刪除。

要刪除當前選擇而不將刪除的文本放入剪貼簿,請呼叫[「清除](#clear)」成員函數。

有關詳細資訊,請參閱 Windows SDK 中的[WM_CUT。](/windows/win32/dataxchg/wm-cut)

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#6](../../mfc/reference/codesnippet/cpp/cedit-class_6.cpp)]

## <a name="ceditemptyundobuffer"></a><a name="emptyundobuffer"></a>編輯::空UndoBuffer

呼叫此函數以重置(清除)編輯控制項的撤消標誌。

```
void EmptyUndoBuffer();
```

### <a name="remarks"></a>備註

編輯控制項現在將無法撤銷最後一個操作。 每當可以撤銷編輯控制件中的操作時,都會設置撤消標誌。

每當調用[SetWindowText](../../mfc/reference/cwnd-class.md#setwindowtext)或[SetHandle](#sethandle)`CWnd`成員函數時,將自動清除復原標誌。

有關詳細資訊,請參閱 Windows SDK 中的[EM_EMPTYUNDOBUFFER。](/windows/win32/Controls/em-emptyundobuffer)

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#7](../../mfc/reference/codesnippet/cpp/cedit-class_7.cpp)]

## <a name="ceditfmtlines"></a><a name="fmtlines"></a>編輯::Fmtlines

呼叫此函數可設置在多行編輯控制項中包含軟換行字元。

```
BOOL FmtLines(BOOL bAddEOL);
```

### <a name="parameters"></a>參數

*bAddEOL*<br/>
指定是否要插入軟換行符號。 TRUE 的值插入字元;如果 "TRUE"值插入字元。FALSE 的值刪除它們。

### <a name="return-value"></a>傳回值

如果發生任何格式,則非零;否則 0。

### <a name="remarks"></a>備註

軟換行符由兩個回車和插入行尾的換行符組成,該換行由於文字包裝而斷開。 硬線中斷由一個回車和一條換行件組成。 以硬線中斷結尾的行不受`FmtLines`的影響 。

僅當物件是多行編輯`CEdit`控件時,Windows 才會回應。

`FmtLines`僅影響[GetHandle](#gethandle)返回的緩衝區和[WM_GETTEXT](/windows/win32/winmsg/wm-gettext)返回的文本。 它不會影響編輯控制件中文本的顯示。

有關詳細資訊,請參閱 Windows SDK 中的[EM_FMTLINES。](/windows/win32/Controls/em-fmtlines)

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#8](../../mfc/reference/codesnippet/cpp/cedit-class_8.cpp)]

## <a name="ceditgetcuebanner"></a><a name="getcuebanner"></a>編輯::GetCueBanner

檢索當控制項為空時,在編輯控制項中顯示為文本提示或提示的文本。

```
BOOL GetCueBanner(
    LPWSTR lpszText,
    int cchText) const;

CString GetCueBanner() const;
```

### <a name="parameters"></a>參數

*lpszText*<br/>
[出]指向包含提示文本的字串的指標。

*cchText*<br/>
[在]可以接收的字元數。 此數位包括終止 NULL 字元。

### <a name="return-value"></a>傳回值

對於第一個重載,如果方法成功,則為 TRUE;否則 FALSE。

對於第二個重載,如果方法成功,則包含提示文本的[CString;](../../atl-mfc-shared/using-cstring.md)否則,空字串 ("")。

### <a name="remarks"></a>備註

此方法發送[EM_GETCUEBANNER](/windows/win32/Controls/em-getcuebanner)消息,這在 Windows SDK 中介紹。 有關詳細資訊,請參閱[Edit_GetCueBannerText](/windows/win32/api/commctrl/nf-commctrl-edit_getcuebannertext)宏。

## <a name="ceditgetfirstvisibleline"></a><a name="getfirstvisibleline"></a>編輯:取得第一可見線

呼叫此函數以確定編輯控制項中最上面可見的行。

```
int GetFirstVisibleLine() const;
```

### <a name="return-value"></a>傳回值

最上面可見線的零基索引。 對於單行編輯控件,返回值為 0。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱 Windows SDK 中的[EM_GETFIRSTVISIBLELINE。](/windows/win32/Controls/em-getfirstvisibleline)

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#9](../../mfc/reference/codesnippet/cpp/cedit-class_9.cpp)]

## <a name="ceditgethandle"></a><a name="gethandle"></a>編輯::取得手柄

呼叫此函數以檢索當前為多行編輯控制件分配的記憶體的句柄。

```
HLOCAL GetHandle() const;
```

### <a name="return-value"></a>傳回值

標識保存編輯控制件內容的緩衝區的本地記憶體句柄。 如果發生錯誤(如將消息發送到單行編輯控件),則返回值為 0。

### <a name="remarks"></a>備註

該句柄是本地記憶體句柄,可用於任何將本地記憶體句柄作為參數的**本地**Windows 記憶體函數。

`GetHandle`僅由多行編輯控件處理。

僅當`GetHandle`對話框使用DS_LOCALEDIT樣式標誌集創建時,才在對話框中調用多行編輯控制件。 如果未設置DS_LOCALEDIT樣式,您仍將獲得非零返回值,但您將無法使用返回的值。

> [!NOTE]
> `GetHandle`不適用於 Windows 95/98。 如果您在 Windows `GetHandle` 95/98 中呼叫,它將傳回 NULL。 `GetHandle`將工作在 Windows NT,版本 3.51 和更高版本中記錄。

有關詳細資訊,請參閱 windows SDK 中的[EM_GETHANDLE。](/windows/win32/Controls/em-gethandle)

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#10](../../mfc/reference/codesnippet/cpp/cedit-class_10.cpp)]

## <a name="ceditgethighlight"></a><a name="gethighlight"></a>編輯:取得高光

獲取當前編輯控制項中突出顯示的文本範圍內第一個字元和最後一個字元的索引。

```
BOOL GetHighlight(
    int* pichStart,
    int* pichEnd) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*pich 開始*|[出]突出顯示的文本範圍內第一個字元的基於零的索引。|
|*pichEnd*|[出]突出顯示的文本範圍內最後一個字元的基於零的索引。|

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法發送[EM_GETHILITE](/windows/win32/Controls/em-gethilite)消息,這在 Windows SDK 中介紹。 和`SetHighlight``GetHighlight`當前都只為 UNICODE 產生啟用。

## <a name="ceditgetlimittext"></a><a name="getlimittext"></a>編輯::取得限制文字

呼叫此成員函數以獲取此`CEdit`物件的文本限制。

```
UINT GetLimitText() const;
```

### <a name="return-value"></a>傳回值

此`CEdit`物件的當前文本限制(在 TCHA 中)。

### <a name="remarks"></a>備註

文本限制是編輯控制項可以接受的最大文本量(在 TCHA 中)。

> [!NOTE]
> 此成員功能從 Windows 95 和 Windows NT 4.0 開始可用。

有關詳細資訊,請參閱在 Windows SDK 中的[EM_GETLIMITTEXT。](/windows/win32/Controls/em-getlimittext)

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#11](../../mfc/reference/codesnippet/cpp/cedit-class_11.cpp)]

## <a name="ceditgetline"></a><a name="getline"></a>編輯:抓取線

呼叫此函數從編輯控制項檢索文本行並將其置於*lpszBuffer*中。

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
指定要從多行編輯控制項檢索的行號。 行號為零;值 0 指定第一行。 單行編輯控制件將忽略此參數。

*lpszBuffer*<br/>
指向接收行副本的緩衝區。 緩衝區的第一個單詞必須指定可複製到緩衝區的最大 TCHAR 數。

*nMaxLength*<br/>
指定可複製到緩衝區的最大 TCHAR 字元數。 `GetLine`在調用 Windows 之前,將此值放在*lpszBuffer*的第一個單詞中。

### <a name="return-value"></a>傳回值

實際複製的字元數。 如果*nIndex*指定的行號大於編輯控制件中的行數,則返回值為 0。

### <a name="remarks"></a>備註

複製的行不包含空終止字元。

有關詳細資訊,請參閱 windows SDK 中的[EM_GETLINE。](/windows/win32/Controls/em-getline)

### <a name="example"></a>範例

  請參考[CEdit::取得線計數的範例](#getlinecount)。

## <a name="ceditgetlinecount"></a><a name="getlinecount"></a>編輯::取得線計數

呼叫此函數以檢索多行編輯控制件中的行數。

```
int GetLineCount() const;
```

### <a name="return-value"></a>傳回值

包含多行編輯控制件中的行數的整數。 如果編輯控制項中未輸入文本,則返回值為1。

### <a name="remarks"></a>備註

`GetLineCount`僅由多行編輯控件處理。

有關詳細資訊,請參閱 Windows SDK 中的[EM_GETLINECOUNT。](/windows/win32/Controls/em-getlinecount)

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#12](../../mfc/reference/codesnippet/cpp/cedit-class_12.cpp)]

## <a name="ceditgetmargins"></a><a name="getmargins"></a>編輯::取得邊緣

呼叫此成員函數以檢索此編輯控件的左右邊距。

```
DWORD GetMargins() const;
```

### <a name="return-value"></a>傳回值

低階 WORD 中左邊距的寬度和高階 WORD 中右邊距的寬度。

### <a name="remarks"></a>備註

邊距以像素為單位進行測量。

> [!NOTE]
> 此成員功能從 Windows 95 和 Windows NT 4.0 開始可用。

有關詳細資訊,請參閱 Windows SDK 中的[EM_GETMARGINS。](/windows/win32/Controls/em-getmargins)

### <a name="example"></a>範例

  請參考[CEditView 的範例:取得編輯Ctrl](ceditview-class.md#geteditctrl)。

## <a name="ceditgetmodify"></a><a name="getmodify"></a>編輯::取得修改

呼叫此函數以確定編輯控制件的內容是否已修改。

```
BOOL GetModify() const;
```

### <a name="return-value"></a>傳回值

如果編輯控制內容已修改,則非零;0,如果他們保持不變。

### <a name="remarks"></a>備註

Windows 維護一個內部標誌,指示編輯控件的內容是否已更改。 首次創建編輯控制件時,將清除此標誌,也可以通過調用[SetModify](#setmodify)成員函數清除。

有關詳細資訊,請參閱 Windows SDK 中的[EM_GETMODIFY。](/windows/win32/Controls/em-getmodify)

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#13](../../mfc/reference/codesnippet/cpp/cedit-class_13.cpp)]

## <a name="ceditgetpasswordchar"></a><a name="getpasswordchar"></a>編輯::抓取密碼字元

呼叫此函數以檢索使用者輸入文本時在編輯控制項中顯示的密碼字元。

```
TCHAR GetPasswordChar() const;
```

### <a name="return-value"></a>傳回值

指定要顯示的字元,而不是使用者鍵入的字元。 如果沒有密碼字元,則返回值為 NULL。

### <a name="remarks"></a>備註

如果使用ES_PASSWORD樣式創建編輯控制項,則支援該控制項的 DLL 將確定預設密碼字元。 清單或[Init 公共控制 Ex](/windows/win32/api/commctrl/nf-commctrl-initcommoncontrolsex)方法確定哪個 DLL 支援編輯控制件。 如果使用者32.dll支援編輯控制項,則預設密碼字元為ASTERISK ('*, U+002A)。 如果 comctl32.dll 版本 6 支援編輯控制件,則預設字元為「黑色 CIRCLE」(「*」,U+25CF)。 有關哪些 DLL 與版本支援常見控制項的詳細資訊,請參閱[指令程式版本和通用控制項版本](/previous-versions/windows/desktop/legacy/bb776779\(v=vs.85\))。

此方法發送[EM_GETPASSWORDCHAR](/windows/win32/Controls/em-getpasswordchar)訊息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#14](../../mfc/reference/codesnippet/cpp/cedit-class_14.cpp)]

## <a name="ceditgetrect"></a><a name="getrect"></a>編輯::取得 Rect

呼叫此函數以獲取編輯控制項的格式矩形。

```
void GetRect(LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向接收格式`RECT`矩形的結構。

### <a name="remarks"></a>備註

格式矩形是文字的限制矩形,與編輯控制視窗的大小無關。

多行編輯控制項的格式矩形可以由[SetRect 和 SetRectNP](#setrect)成員[SetRectNP](#setrectnp)函數修改。

有關詳細資訊,請參閱 Windows SDK 中的[EM_GETRECT。](/windows/win32/Controls/em-getrect)

### <a name="example"></a>範例

  請參考[CEdit::限制文字的範例](#limittext)。

## <a name="ceditgetsel"></a><a name="getsel"></a>編輯::GetSel

呼叫此函數,使用返回值或參數獲取編輯控制件中當前所選內容(如果有)的起始和結束字元位置。

```
DWORD GetSel() const;

void GetSel(
    int& nStartChar,
    int& nEndChar) const;
```

### <a name="parameters"></a>參數

*nStartChar*<br/>
引用將接收當前所選內容中第一個字元位置的整數。

*nEndChar*<br/>
引用一個整數,該整數將接收當前所選內容末尾的第一個未選擇字元的位置。

### <a name="return-value"></a>傳回值

返回 DWORD 的版本傳回值,該值包含低階單詞中的起始位置,以及高階單詞中所選內容結束後第一個未選中字元的位置。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱 Windows SDK 中的[EM_GETSEL。](/windows/win32/Controls/em-getsel)

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#15](../../mfc/reference/codesnippet/cpp/cedit-class_15.cpp)]

## <a name="cedithideballoontip"></a><a name="hideballoontip"></a>編輯::隱藏氣球提示

隱藏與當前編輯控制件關聯的任何氣球提示。

```
BOOL HideBalloonTip();
```

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此功能發送[EM_HIDEBALLOONTIP](/windows/win32/Controls/em-hideballoontip)消息,這在 Windows SDK 中介紹。

## <a name="ceditlimittext"></a><a name="limittext"></a>編輯::限制文字

呼叫此函數以限制使用者可以輸入到編輯控制項的文本長度。

```
void LimitText(int nChars = 0);
```

### <a name="parameters"></a>參數

*n查理斯*<br/>
指定使用者可以輸入的文本的長度(在 TCHA 中)。 如果此參數為 0,則文本長度設置為UINT_MAX位元組。 此為預設行為。

### <a name="remarks"></a>備註

變更文字限制僅限制使用者可以輸入的文本。 它對編輯控制件中已有的任何文本沒有影響,也不會影響 在`CWnd`中[SetWindowText](cwnd-class.md#setwindowtext)成員函數複製到編輯控制項的文本的長度。 如果應用程式使用 函`SetWindowText`數將更多的文本放入編輯控制項中,而不是調用`LimitText`中 指定的文本,則使用者可以刪除編輯控制項中的任何文本。 但是,文本限制將阻止使用者用新文本替換現有文本,除非刪除當前選擇會導致文本低於文本限制。

> [!NOTE]
> 在 Win32(Windows NT 和 Windows 95/98)中[,SetLimitText](#setlimittext)將替換此功能。

有關詳細資訊,請參閱 Windows SDK 中的[EM_LIMITTEXT。](/windows/win32/Controls/em-limittext)

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#17](../../mfc/reference/codesnippet/cpp/cedit-class_16.cpp)]

## <a name="ceditlinefromchar"></a><a name="linefromchar"></a>編輯::線從查爾

呼叫此函數以檢索包含指定字元索引的行號的行號。

```
int LineFromChar(int nIndex = -1) const;
```

### <a name="parameters"></a>參數

*nIndex*<br/>
在編輯控制項的文本中包含所需字元的零基索引值,或包含 -1。 如果*nIndex*為 -1,則指定當前線,即包含 caret 的行。

### <a name="return-value"></a>傳回值

包含*nIndex*指定的字元索引的行的零基行號。 如果*nIndex*為 -1,則傳回包含所選內容的第一個字元的行數。 如果沒有選擇,則返回當前行號。

### <a name="remarks"></a>備註

字元索引是編輯控制項開頭的字元數。

此成員函數僅由多行編輯控制件使用。

有關詳細資訊,請參閱 Windows SDK 中的[EM_LINEFROMCHAR。](/windows/win32/Controls/em-linefromchar)

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#18](../../mfc/reference/codesnippet/cpp/cedit-class_17.cpp)]

## <a name="ceditlineindex"></a><a name="lineindex"></a>編輯:串列引

呼叫此函數以檢索多行編輯控制件中的行的字元索引。

```
int LineIndex(int nLine = -1) const;
```

### <a name="parameters"></a>參數

*n 線*<br/>
在編輯控制項的文本中包含所需行的索引值,或包含 -1。 如果*nLine*為 -1,則指定當前線,即包含 caret 的行。

### <a name="return-value"></a>傳回值

如果指定的行號大於編輯控制項中的行數,則以*nLine*或 -1 指定的行的字元索引。

### <a name="remarks"></a>備註

字元索引是從編輯控制項的開頭到指定行的字元數。

此成員函數僅由多行編輯控件處理。

有關詳細資訊,請參閱 Windows SDK 中的[EM_LINEINDEX。](/windows/win32/controls/em-lineindex)

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#19](../../mfc/reference/codesnippet/cpp/cedit-class_18.cpp)]

## <a name="ceditlinelength"></a><a name="linelength"></a>編輯:線長

檢索編輯控制件中的行的長度。

```
int LineLength(int nLine = -1) const;
```

### <a name="parameters"></a>參數

*n 線*<br/>
要檢索長度的行中字元的零基索引。 預設值為 -1。

### <a name="return-value"></a>傳回值

對於單行編輯控制件,返回值是編輯控制項中文本的長度(在 TCHA 中)。

對於多行編輯控件,返回值是*nLine*參數指定的行的長度(在 TCHAR 中)。 對於 ANSI 文字,長度是行中的位元組數;對於 Unicode 文本,長度是行中的字元數。 長度不包括行尾的回車字元。

如果*nLine*參數大於控制項中的字元數,則返回值為零。

如果*nLine*參數為 -1,則傳回值是包含選定字元的行中未選擇的字元數。 例如,如果所選內容從一行的第四個字元延伸到下一行末尾的第八個字元,則返回值為 10。 也就是說,第一行有三個字元,下一行有七個字元。

有關 TCHAR 類型的詳細資訊,請參閱[Windows 數據類型](/windows/win32/WinProg/windows-data-types)表中的 TCHAR 行。

### <a name="remarks"></a>備註

此方法受[EM_LINELENGTH](/windows/win32/Controls/em-linelength)消息的支援,該消息在 Windows SDK 中介紹。

### <a name="example"></a>範例

  請參考[CEdit::lineIndex 的範例](#lineindex)。

## <a name="ceditlinescroll"></a><a name="linescroll"></a>編輯::線捲動

呼叫此函數滾動多行編輯控制項的文字。

```
void LineScroll(
    int nLines,
    int nChars = 0);
```

### <a name="parameters"></a>參數

*n線*<br/>
指定要垂直滾動的行數。

*n查理斯*<br/>
指定要水平滾動的字元位置數。 如果編輯控制項具有ES_RIGHT或ES_CENTER樣式,則忽略此值。

### <a name="remarks"></a>備註

此成員函數僅由多行編輯控件處理。

編輯控制項不會垂直捲動超過編輯控制項中的最後一行文本。 如果當前行加上*nLines*指定的行數超過編輯控制件中的行總數,則調整該值,以便編輯控制項的最後一行滾動到編輯控制視窗的頂部。

`LineScroll`可用於水準滾動超過任何行的最後一個字元。

有關詳細資訊,請參閱 Windows SDK 中的[EM_LINESCROLL。](/windows/win32/Controls/em-linescroll)

### <a name="example"></a>範例

  請參考[CEdit::取得第一個可見線的範例](#getfirstvisibleline)。

## <a name="ceditpaste"></a><a name="paste"></a>編輯::Paste

呼叫此功能以將數據從剪貼簿插入到插入`CEdit`點。

```
void Paste();
```

### <a name="remarks"></a>備註

僅當剪貼簿以CF_TEXT格式包含數據時,才會插入數據。

有關詳細資訊,請參閱 Windows SDK 中的[WM_PASTE。](/windows/win32/dataxchg/wm-paste)

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#20](../../mfc/reference/codesnippet/cpp/cedit-class_19.cpp)]

## <a name="ceditposfromchar"></a><a name="posfromchar"></a>編輯::P從查爾

呼叫此函數以獲取此`CEdit`物件中給定字元的位置(左上角)。

```
CPoint PosFromChar(UINT nChar) const;
```

### <a name="parameters"></a>參數

*n查爾*<br/>
指定字元的零基索引。

### <a name="return-value"></a>傳回值

*nChar*指定的字元的左上角的座標。

### <a name="remarks"></a>備註

該字元通過給出其零基索引值來指定。 如果*nChar*大`CEdit`於此 物件中最後一個字元的索引,則返回值將指定`CEdit`剛剛經過此 物件中最後一個字元的字元位置的座標。

> [!NOTE]
> 此成員功能從 Windows 95 和 Windows NT 4.0 開始可用。

有關詳細資訊,請參閱 Windows SDK 中的[EM_POSFROMCHAR。](/windows/win32/Controls/em-posfromchar)

### <a name="example"></a>範例

  請參閱[CEdit::LineFromChar](#linefromchar)的範例。

## <a name="ceditreplacesel"></a><a name="replacesel"></a>編輯::取代氏

呼叫此函數以將編輯控制項中的目前選擇替換為*lpszNewText*指定的文字。

```
void ReplaceSel(LPCTSTR lpszNewText, BOOL bCanUndo = FALSE);
```

### <a name="parameters"></a>參數

*lpsz 新文字*<br/>
包含取代文字的 null 連接字串。

*bCanUndo*<br/>
要指定可以復原此函數,請選擇參數的值設定為 TRUE 。 預設值為 FALSE。

### <a name="remarks"></a>備註

僅替換編輯控制件中文字的一部分。 如果要替換所有文本,請使用[CWnd:setWindowText](cwnd-class.md#setwindowtext)成員函數。

如果沒有當前選擇,則替換文本將插入到當前游標位置。

有關詳細資訊,請參閱 Windows SDK 中的[EM_REPLACESEL。](/windows/win32/Controls/em-replacesel)

### <a name="example"></a>範例

  請參考[CEdit::lineIndex 的範例](#lineindex)。

## <a name="ceditsetcuebanner"></a><a name="setcuebanner"></a>編輯::設定庫班

設置當控制項為空時,在編輯控制項中顯示為文本提示或提示的文本。

```
BOOL SetCueBanner(LPCWSTR lpszText);

BOOL SetCueBanner(
    LPCWSTR lpszText,
    BOOL fDrawWhenFocused = FALSE);
```

### <a name="parameters"></a>參數

*lpszText*<br/>
[在]包含要編輯控制檔中顯示的提示的字串的指標。

*fDraw 時聚焦*<br/>
[在]如果 FALSE,則當使用者單擊編輯控制件並給出控制項焦點時,不會繪製提示橫幅。

如果為 TRUE,則即使控件具有焦點,也會繪製提示橫幅。 當用戶開始鍵入控件時,提示橫幅將消失。

預設值為 FALSE。

### <a name="return-value"></a>傳回值

如果方法成功,則為 TRUE;否則 FALSE。

### <a name="remarks"></a>備註

此方法發送[EM_SETCUEBANNER](/windows/win32/Controls/em-setcuebanner)訊息,這在 Windows SDK 中介紹。 有關詳細資訊,請參閱[Edit_SetCueBannerTextFocused](/windows/win32/api/commctrl/nf-commctrl-edit_setcuebannertextfocused)宏。

### <a name="example"></a>範例

下面的範例演示了[CEdit:setCueBanner](#setcuebanner)方法。

[!code-cpp[NVC_MFC_CEdit_s1#2](../../mfc/reference/codesnippet/cpp/cedit-class_20.cpp)]

## <a name="ceditsethandle"></a><a name="sethandle"></a>編輯::設定手

呼叫此函數以將句柄設置為多行編輯控制件將使用的本地記憶體。

```
void SetHandle(HLOCAL hBuffer);
```

### <a name="parameters"></a>參數

*hBuffer*<br/>
包含本地記憶體的句柄。 此句柄必須由以前使用 LMEM_MOVEABLE 標誌對[LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc) Windows 函數的調用創建。 假定記憶體包含 null 終止的字串。 如果不是這樣,則分配的記憶體的第一個字節應設置為 0。

### <a name="remarks"></a>備註

然後,編輯控制項將使用此緩衝區儲存當前顯示的文本,而不是分配自己的緩衝區。

此成員函數僅由多行編輯控件處理。

在應用程式設置新的記憶體句柄之前,它應該使用[GetHandle](#gethandle)成員函數將句柄獲取到當前記憶體緩衝區,並使用`LocalFree`Windows 函數釋放該記憶體。

`SetHandle`清除撤銷緩衝區(然後傳回 0[的 CanUndo](#canundo)成員函數)和內部修改標誌[(GetModify](#getmodify)成員函數則返回 0)。 重新繪製編輯控制視窗。

僅當已創建帶有DS_LOCALEDIT樣式標誌集的對話方塊時,才能在對話方塊中的多行編輯控制項中使用此成員函數。

> [!NOTE]
> `GetHandle`不適用於 Windows 95/98。 如果您在 Windows `GetHandle` 95/98 中呼叫,它將傳回 NULL。 `GetHandle`將工作在 Windows NT,版本 3.51 和更高版本中記錄。

有關詳細資訊,請參閱 windows SDK 中的[EM_SETHANDLE、](/windows/win32/Controls/em-sethandle)[本地 Alloc](/windows/win32/api/winbase/nf-winbase-localalloc)和[本地自由](/windows/win32/api/winbase/nf-winbase-localfree)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#22](../../mfc/reference/codesnippet/cpp/cedit-class_21.cpp)]

## <a name="ceditsethighlight"></a><a name="sethighlight"></a>編輯:設定高光

突顯目前編輯控制項中顯示的文字範圍。

```
void SetHighlight(
    int ichStart,
    int ichEnd);
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*ichStart*|[在]要突出顯示的文本範圍內第一個字元的基於零的索引。|
|*ichEnd*|[在]要突出顯示的文本範圍內最後一個字元的零索引。|

### <a name="remarks"></a>備註

此方法發送[EM_SETHILITE](/windows/win32/Controls/em-sethilite)消息,這在Windows SDK中介紹。  此方法發送[EM_SETHILITE](/windows/win32/Controls/em-sethilite)消息,這在Windows SDK中介紹。 和`SetHighlight``GetHighlight`都僅為 UNICODE 生成啟用。

## <a name="ceditsetlimittext"></a><a name="setlimittext"></a>編輯::設定限制文字

呼叫此成員函數以設定此`CEdit`物件的文本限制。

```
void SetLimitText(UINT nMax);
```

### <a name="parameters"></a>參數

*nMax*<br/>
新的文本限制,以字元表示。

### <a name="remarks"></a>備註

文本限制是編輯控制項可以接受的最大文本量(以字元表示)。

變更文字限制僅限制使用者可以輸入的文本。 它對編輯控制件中已有的任何文本沒有影響,也不會影響 在`CWnd`中[SetWindowText](cwnd-class.md#setwindowtext)成員函數複製到編輯控制項的文本的長度。 如果應用程式使用 函`SetWindowText`數將更多的文本放入編輯控制項中,而不是調用`LimitText`中 指定的文本,則使用者可以刪除編輯控制項中的任何文本。 但是,文本限制將阻止使用者用新文本替換現有文本,除非刪除當前選擇會導致文本低於文本限制。

此功能取代 Win32 中的[「限制文本](#limittext)」。

有關詳細資訊,請參閱 Windows SDK 中的[EM_SETLIMITTEXT。](/windows/win32/Controls/em-setlimittext)

### <a name="example"></a>範例

  請參考[CEditView 的範例:取得編輯Ctrl](ceditview-class.md#geteditctrl)。

## <a name="ceditsetmargins"></a><a name="setmargins"></a>編輯::設定邊界

呼叫此方法以設定此編輯控制項的左右邊距。

```
void SetMargins(
    UINT nLeft,
    UINT nRight);
```

### <a name="parameters"></a>參數

*N 左*<br/>
新左邊距的寬度(以像素為單位)。

*nRight*<br/>
新右邊距的寬度(以像素為單位)。

### <a name="remarks"></a>備註

> [!NOTE]
> 此成員功能從 Windows 95 和 Windows NT 4.0 開始可用。

有關詳細資訊,請參閱 Windows SDK 中的[EM_SETMARGINS。](/windows/win32/Controls/em-setmargins)

### <a name="example"></a>範例

  請參考[CEditView 的範例:取得編輯Ctrl](ceditview-class.md#geteditctrl)。

## <a name="ceditsetmodify"></a><a name="setmodify"></a>編輯::設定修改

呼叫此函數以設置或清除編輯控制項的修改標誌。

```
void SetModify(BOOL bModified = TRUE);
```

### <a name="parameters"></a>參數

*b 修改*<br/>
TRUE 的值表示文本已被修改,FALSE 值表示未修改。 默認情況下,將設置修改後的標誌。

### <a name="remarks"></a>備註

修改後的標誌指示編輯控制件中的文本是否已修改。 每當使用者更改文本時,都會自動設置它。 可以使用[GetModify](#getmodify)成員函數檢索其值。

有關詳細資訊,請參閱 Windows SDK 中的[EM_SETMODIFY。](/windows/win32/Controls/em-setmodify)

### <a name="example"></a>範例

  請參考[CEdit::取得修改的範例](#getmodify)。

## <a name="ceditsetpasswordchar"></a><a name="setpasswordchar"></a>編輯::設定密碼字元

呼叫此函數以設定或刪除使用者鍵入文本時在編輯控制項中顯示的密碼字元。

```
void SetPasswordChar(TCHAR ch);
```

### <a name="parameters"></a>參數

*ch*<br/>
指定要顯示的字元,以代替使用者鍵入的字元。 如果*ch*為 0,將顯示用戶鍵入的實際字元。

### <a name="remarks"></a>備註

設置密碼字元時,該字元將針對用戶鍵入的每個字元顯示。

此成員函數對多行編輯控件沒有影響。

呼叫`SetPasswordChar`成員函數時,`CEdit`將使用*ch*指定的字元重新繪製所有可見字元。

如果使用[ES_PASSWORD](styles-used-by-mfc.md#edit-styles)樣式創建編輯控制項,則默認密碼字元將設置為星號<strong>\*</strong>()。 如果`SetPasswordChar`使用*ch*設定為 0 調用此樣式,則將刪除此樣式。

有關詳細資訊,請參閱 Windows SDK 中的[EM_SETPASSWORDCHAR。](/windows/win32/Controls/em-setpasswordchar)

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#16](../../mfc/reference/codesnippet/cpp/cedit-class_22.cpp)]

## <a name="ceditsetreadonly"></a><a name="setreadonly"></a>編輯:僅設定 Read

呼叫此函數以設置編輯控制項的唯讀狀態。

```
BOOL SetReadOnly(BOOL bReadOnly = TRUE);
```

### <a name="parameters"></a>參數

*b 唯讀*<br/>
指定是設定還是刪除編輯控制項的唯讀狀態。 TRUE 的值將狀態設為唯讀狀態;如果 「TRUE」值將狀態設為唯讀狀態。FALSE 的值將狀態設置為讀/寫。

### <a name="return-value"></a>傳回值

如果操作成功,則為非零;如果發生錯誤,則為 0。

### <a name="remarks"></a>備註

可以通過測試[CWnd::getStyle](cwnd-class.md#getstyle)返回值中的[ES_READONLY](styles-used-by-mfc.md#edit-styles)標誌來找到當前設置。

有關詳細資訊,請參閱 Windows SDK 中的[EM_SETREADONLY。](/windows/win32/Controls/em-setreadonly)

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#23](../../mfc/reference/codesnippet/cpp/cedit-class_23.cpp)]

## <a name="ceditsetrect"></a><a name="setrect"></a>編輯::設定重新

呼叫此函數以使用指定的座標設定矩形的尺寸。

```
void SetRect(LPCRECT lpRect);
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向指定格式`RECT`矩形`CRect`的新 尺寸的結構或物件。

### <a name="remarks"></a>備註

此成員僅由多行編輯控件處理。

用於`SetRect`設定多行編輯控制項的格式矩形。 格式矩形是文字的限制矩形,與編輯控制視窗的大小無關。 首次創建編輯控制件時,格式矩形與編輯控制視窗的工作區相同。 通過使用`SetRect`成員函數,應用程式可以使格式矩形大於或小於編輯控制視窗。

如果編輯控制項沒有滾動條,則如果格式矩形大於視窗,則文本將被剪切,而不是換行。 如果編輯控制件包含邊框,則格式矩形將減小為邊框的大小。 如果調整成員函數返回的`GetRect`矩形,則必須在將矩形傳遞`SetRect`給 之前刪除邊框的大小。

呼叫`SetRect`時,編輯控制項的文本也會重新格式化並重新顯示。

有關詳細資訊,請參閱 Windows SDK 中的[EM_SETRECT。](/windows/win32/Controls/em-setrect)

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#24](../../mfc/reference/codesnippet/cpp/cedit-class_24.cpp)]

## <a name="ceditsetrectnp"></a><a name="setrectnp"></a>編輯::設定RectNP

呼叫此函數以設定多行編輯控制項的格式矩形。

```
void SetRectNP(LPCRECT lpRect);
```

### <a name="parameters"></a>參數

*lpRect*<br/>
指向指定矩形`RECT`新`CRect`尺寸的結構或物件。

### <a name="remarks"></a>備註

格式矩形是文字的限制矩形,與編輯控制視窗的大小無關。

`SetRectNP`與`SetRect`成員函數相同,只不過編輯控制視窗不重繪。

首次創建編輯控制件時,格式矩形與編輯控制視窗的工作區相同。 通過調用`SetRectNP`成員函數,應用程式可以使格式矩形大於或小於編輯控制視窗。

如果編輯控制項沒有滾動條,則如果格式矩形大於視窗,則文本將被剪切,而不是換行。

此成員僅由多行編輯控件處理。

有關詳細資訊,請參閱 Windows SDK 中的[EM_SETRECTNP。](/windows/win32/Controls/em-setrectnp)

### <a name="example"></a>範例

  請參閱[CEdit::SetRect](#setrect)的範例。

## <a name="ceditsetsel"></a><a name="setsel"></a>編輯::SetSel

呼叫此函數以選擇編輯控制件中的字元範圍。

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

*dw 選擇*<br/>
指定低階單詞中的起始位置和高階單詞的結束位置。 如果低階單詞為 0,高階單詞為 -1,則選擇編輯控制項中的所有文本。 如果低階單詞為 -1,則刪除任何當前選擇。

*bNoScroll*<br/>
指示是否應將插入者滾動到視圖中。 如果 FALSE,則 care 將滾動到視圖中。 如果為 TRUE,則不會滾動到視圖中。

*nStartChar*<br/>
指定起始位置。 如果*nStartChar*為*0,nEndChar*為 -1,則選擇編輯控制項中的文字。 如果*nStartChar*為 -1,則刪除任何當前選擇。

*nEndChar*<br/>
指定結束位置。

### <a name="remarks"></a>備註

有關詳細資訊,請參閱 Windows SDK 中的[EM_SETSEL。](/windows/win32/Controls/em-setsel)

### <a name="example"></a>範例

  請參閱[CEdit::GetSel](#getsel)的範例。

## <a name="ceditsettabstops"></a><a name="settabstops"></a>編輯::設定標籤

呼叫此函數以在多行編輯控制項中設置製表位。

```
void SetTabStops();
BOOL SetTabStops(const int& cxEachStop);

BOOL SetTabStops(
    int nTabStops,
    LPINT rgTabStops);
```

### <a name="parameters"></a>參數

*cxEachStop*<br/>
指定在每個*cxEachStop*對話框單元上設置製表符止動器。

*NTabStops*<br/>
指定*rgTabStops*中包含的制表位數。 此數字必須大於 1。

*rgTabStops*<br/>
指向指定在對話框儲存格中指定的制表符止動器的無符號整數陣列。 對話框單位是水準或垂直距離。 一個水平對話框單位等於當前對話框基本寬度單位的四分之一,1 個垂直對話框單位等於當前對話框基本高度單位的八分之一。 對話方塊基本單位是根據目前系統字型的高度和寬度計算。 Windows`GetDialogBaseUnits`函數返回當前以像素為單位的當前對話框基本單位。

### <a name="return-value"></a>傳回值

設置選項卡時非零;否則 0。

### <a name="remarks"></a>備註

將文字複製到多行編輯控制項時,文本中的任何選項卡字元都將導致將空間生成到下一個制表位。

要將制表符停止設置為 32 個對話方塊單位的預設大小,請調用此成員函數的無參數版本。 要將製表符停止設置為大小小於 32,請使用*cxEachStop*參數調用版本。 要將製表符停止設置為大小陣列,請使用具有兩個參數的版本。

此成員函數僅由多行編輯控件處理。

`SetTabStops`不會自動重繪編輯視窗。 如果更改編輯控制件中已有文本的制表位,請致電[CWnd::ininrect](cwnd-class.md#invalidaterect)以重新繪製編輯視窗。

有關詳細資訊,請參閱 windows SDK 中的[EM_SETTABSTOPS](/windows/win32/Controls/em-settabstops)和[GetDialogBase 單位](/windows/win32/api/winuser/nf-winuser-getdialogbaseunits)。

### <a name="example"></a>範例

  請參閱[CEditView 示例::設置 TabStop。](ceditview-class.md#settabstops)

## <a name="ceditshowballoontip"></a><a name="showballoontip"></a>編輯::顯示氣球提示

顯示與當前編輯控制件關聯的氣球提示。

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
|*pEdit氣球提示*|[在]指向描述氣球尖端的[EDITBALLTIP](/windows/win32/api/commctrl/ns-commctrl-editballoontip)結構的指標。|
|*lpszTitle*|[在]指向包含氣球提示標題的 Unicode 字串的指標。|
|*lpszText*|[在]指向包含氣球提示文本的 Unicode 字串的指標。|
|*蒂圖示*|[在]指定要與氣球提示關聯的圖示類型的**INT。** 默認值為TTI_NONE。 有關詳細資訊,請參閱`ttiIcon`[EDITBALLTIP](/windows/win32/api/commctrl/ns-commctrl-editballoontip)結構的成員。|

### <a name="return-value"></a>傳回值

如果此方法成功,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此功能發送[EM_SHOWBALLOONTIP](/windows/win32/Controls/em-showballoontip)消息,這在 Windows SDK 中介紹。 有關詳細資訊,請參閱[Edit_ShowBalloonTip](/windows/win32/api/commctrl/nf-commctrl-edit_showballoontip)宏。

### <a name="example"></a>範例

以下代碼範例定義用於存取目前編輯控制`m_cedit`項 的變數 。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CEdit_s1#1](../../mfc/reference/codesnippet/cpp/cedit-class_25.h)]

### <a name="example"></a>範例

以下代碼示例顯示編輯控制項的氣球提示。 [CEdit::Show氣球提示](#showballoontip)方法指定標題和氣球提示文本。

[!code-cpp[NVC_MFC_CEdit_s1#3](../../mfc/reference/codesnippet/cpp/cedit-class_26.cpp)]

## <a name="ceditundo"></a><a name="undo"></a>編輯:復原

呼叫此函數以復原上次編輯控制操作。

```
BOOL Undo();
```

### <a name="return-value"></a>傳回值

對於單行編輯控件,返回值始終為非零。 對於多行編輯控件,如果撤銷操作成功,返回值為非零;如果撤銷操作失敗,則返回值為 0。

### <a name="remarks"></a>備註

撤銷操作也可以撤銷。 例如, 可以使用第一次呼叫 回復已移除的`Undo`文字 。 只要沒有干預編輯操作,就可以使用第二個調用`Undo`再次刪除文本。

有關詳細資訊,請參閱 Windows SDK 中的[EM_UNDO。](/windows/win32/Controls/em-undo)

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CEdit#25](../../mfc/reference/codesnippet/cpp/cedit-class_27.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 樣品 CALCDRIV](../../overview/visual-cpp-samples.md)<br/>
[MFC 樣品 CMNCTRL2](../../overview/visual-cpp-samples.md)<br/>
[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CWnd 類別](cwnd-class.md)<br/>
[CButton 類別](cbutton-class.md)<br/>
[CComboBox 類別](ccombobox-class.md)<br/>
[CListBox 類別](clistbox-class.md)<br/>
[CScrollBar 類別](cscrollbar-class.md)<br/>
[CStatic 類別](cstatic-class.md)<br/>
[CDialog 類別](cdialog-class.md)
