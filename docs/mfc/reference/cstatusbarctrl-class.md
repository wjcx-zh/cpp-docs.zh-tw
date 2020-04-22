---
title: CStatusBarCtrl 類別
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
- AFXCMN/CStatusBarCtrl
- AFXCMN/CStatusBarCtrl::CStatusBarCtrl
- AFXCMN/CStatusBarCtrl::Create
- AFXCMN/CStatusBarCtrl::CreateEx
- AFXCMN/CStatusBarCtrl::DrawItem
- AFXCMN/CStatusBarCtrl::GetBorders
- AFXCMN/CStatusBarCtrl::GetIcon
- AFXCMN/CStatusBarCtrl::GetParts
- AFXCMN/CStatusBarCtrl::GetRect
- AFXCMN/CStatusBarCtrl::GetText
- AFXCMN/CStatusBarCtrl::GetTextLength
- AFXCMN/CStatusBarCtrl::GetTipText
- AFXCMN/CStatusBarCtrl::IsSimple
- AFXCMN/CStatusBarCtrl::SetBkColor
- AFXCMN/CStatusBarCtrl::SetIcon
- AFXCMN/CStatusBarCtrl::SetMinHeight
- AFXCMN/CStatusBarCtrl::SetParts
- AFXCMN/CStatusBarCtrl::SetSimple
- AFXCMN/CStatusBarCtrl::SetText
- AFXCMN/CStatusBarCtrl::SetTipText
helpviewer_keywords:
- CStatusBarCtrl [MFC], CStatusBarCtrl
- CStatusBarCtrl [MFC], Create
- CStatusBarCtrl [MFC], CreateEx
- CStatusBarCtrl [MFC], DrawItem
- CStatusBarCtrl [MFC], GetBorders
- CStatusBarCtrl [MFC], GetIcon
- CStatusBarCtrl [MFC], GetParts
- CStatusBarCtrl [MFC], GetRect
- CStatusBarCtrl [MFC], GetText
- CStatusBarCtrl [MFC], GetTextLength
- CStatusBarCtrl [MFC], GetTipText
- CStatusBarCtrl [MFC], IsSimple
- CStatusBarCtrl [MFC], SetBkColor
- CStatusBarCtrl [MFC], SetIcon
- CStatusBarCtrl [MFC], SetMinHeight
- CStatusBarCtrl [MFC], SetParts
- CStatusBarCtrl [MFC], SetSimple
- CStatusBarCtrl [MFC], SetText
- CStatusBarCtrl [MFC], SetTipText
ms.assetid: 8504ad38-7b91-4746-aede-ac98886eb47b
ms.openlocfilehash: 57d040a7efd87d384e0aaa6275593bc91f38cc86
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753043"
---
# <a name="cstatusbarctrl-class"></a>CStatusBarCtrl 類別

提供 Windows 通用狀態列控制項的功能。

## <a name="syntax"></a>語法

```
class CStatusBarCtrl : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CStatusBarCtrl:CStatusBarCtrl](#cstatusbarctrl)|建構 `CStatusBarCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CStatusBarCtrl:建立](#create)|創建狀態列控制器並將其附加到`CStatusBarCtrl`物件。|
|[CStatusBarCtrl::創建Ex](#createex)|使用指定的 Windows 擴充樣式創建狀態列控制項,並將`CStatusBarCtrl`其附加到 物件。|
|[CStatusBarCtrl::D原始專案](#drawitem)|當所有者繪製狀態欄控件的可視方面發生更改時調用。|
|[CStatusBarctrl:取得Borders](#getborders)|檢索狀態列控件的水準和垂直邊框的當前寬度。|
|[CStatusBarctrl::GetIcon](#geticon)|檢索當前狀態列控件中部件(也稱為窗格)的圖示。|
|[CStatusBarctrl:取得元件](#getparts)|檢索狀態列控件中的零件計數。|
|[CStatusBarctrl::取得 Rect](#getrect)|檢索狀態列控件中零件的邊界矩形。|
|[CStatusBarctrl:取得文字](#gettext)|從狀態列控件的給定部分檢索文本。|
|[CStatusBarctrl:取得文字長度](#gettextlength)|從狀態列控件的給定部分檢索文本的長度(以字元表示)。|
|[CStatusBarctrl::取得提示文字](#gettiptext)|檢索狀態列中窗格的工具提示文本。|
|[CStatusBarctrl::簡單](#issimple)|檢查狀態視窗控制項以確定它是否處於簡單模式。|
|[CStatusBarctrl:SetBkColor](#setbkcolor)|在狀態列中設置背景顏色。|
|[CStatusBarctrl::SetIcon](#seticon)|設置狀態列中窗格的圖示。|
|[CStatusBarctrl:setMinHeight](#setminheight)|設置狀態條控制的繪圖區域的最小高度。|
|[CStatusBarctrl::設定元件](#setparts)|設置狀態條控制項中的零件數和每個零件右邊緣的座標。|
|[CStatusBarctrl:設定簡單](#setsimple)|指定狀態列控制項是顯示簡單文本還是顯示以前調用`SetParts`設置的所有控制元件元件。|
|[CStatusBarctrl::設定文字](#settext)|在狀態列控制項的指定部分設定文字。|
|[CStatusBarctrl::SetTipText](#settiptext)|設定狀態列中窗格的工具提示文本。|

## <a name="remarks"></a>備註

"狀態列控制件"是一個水準視窗,通常顯示在父視窗的底部,應用程式可以在其中顯示各種狀態資訊。 狀態列控制項可以劃分為多個部分以顯示多種類型的資訊。

此控制項(因此該`CStatusBarCtrl`類別)僅適用於在 Windows 95/98 和 Windows NT 版本 3.51 及更高版本下運行的程式。

有關`CStatusBarCtrl`使用的詳細資訊,請參閱[控制項](../../mfc/controls-mfc.md)[和使用 CStatusBarCtrl](../../mfc/using-cstatusbarctrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatusBarCtrl`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

## <a name="cstatusbarctrlcreate"></a><a name="create"></a>CStatusBarCtrl:建立

創建狀態列控制器並將其附加到`CStatusBarCtrl`物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定狀態列控制件的樣式。 應用 Windows SDK 中[「通用控制樣式](/windows/win32/Controls/common-control-styles)」中列出的狀態欄控件樣式的任意組合。 此參數必須包括WS_CHILD樣式。 它還應包括WS_VISIBLE樣式。

*矩形*<br/>
指定狀態列控制的大小和位置。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](/windows/win32/api/windef/ns-windef-rect)結構。

*pparentwnd*<br/>
指定狀態列控制的父視窗,通常為`CDialog`。 它不得為 NULL。

*nID*<br/>
指定狀態列控制項的識別碼。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

在兩個步驟`CStatusBarCtrl`中構造 一個。 首先調用構造函數,然後調用`Create`,這將創建狀態列控件並將其附加`CStatusBarCtrl`到 物件。

狀態視窗的預設位置位於父視窗的底部,但您可以指定CCS_TOP樣式,使其顯示在父視窗的工作區的頂部。 您可以指定SBARS_SIZEGRIP樣式,以在狀態視窗的右端包括大小調整夾。 不建議組合CCS_TOP和SBARS_SIZEGRIP樣式,因為即使系統在狀態視窗中繪製了大小調整夾點,也不起作用。

要建立式建立式視窗樣式的狀態列,請呼叫[CStatusBarCtrl::createEx](#createex)`Create`而不是 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatusBarCtrl#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_1.cpp)]

## <a name="cstatusbarctrlcreateex"></a><a name="createex"></a>CStatusBarCtrl::創建Ex

創建控制項(子視窗),並將其與`CStatusBarCtrl`物件關聯。

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwExStyle*<br/>
指定要創建的控制項的擴充樣式。 有關擴展 Windows 樣式的清單,請參閱 Windows SDK 中[創建 WindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*參數。

*dwStyle*<br/>
指定狀態列控制件的樣式。 應用 Windows SDK 中[「通用控制樣式](/windows/win32/Controls/common-control-styles)」中列出的狀態欄控件樣式的任意組合。 此參數必須包括WS_CHILD樣式。 它還應包括WS_VISIBLE樣式。

*矩形*<br/>
對[RECT](/windows/win32/api/windef/ns-windef-rect)結構的引用,描述要創建的視窗的大小和位置,在*pParentWnd*的用戶端座標中。

*pparentwnd*<br/>
指向控件的父視窗的指標。

*nID*<br/>
控制項的子視窗 ID。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

使用`CreateEx`而不是[「創建](#create)」來應用擴展的 Windows 樣式,該樣式由 Windows 擴充樣式前言**WS_EX_** 指定。

## <a name="cstatusbarctrlcstatusbarctrl"></a><a name="cstatusbarctrl"></a>CStatusBarCtrl:CStatusBarCtrl

建構 `CStatusBarCtrl` 物件。

```
CStatusBarCtrl();
```

## <a name="cstatusbarctrldrawitem"></a><a name="drawitem"></a>CStatusBarCtrl::D原始專案

當所有者繪製狀態欄控件的可視方面發生更改時,由框架調用。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>參數

*lpDraw 專案已結*<br/>
指向[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)結構的長指標,其中包含有關所需繪圖類型的資訊。

### <a name="remarks"></a>備註

`DRAWITEMSTRUCT`結構`itemAction`的成員定義要執行的繪圖操作。

默認情況下,此成員函數不執行任何操作。 重寫此成員函數以擁有擁有者繪製物件的繪圖`CStatusBarCtrl`。

應用程式應還原在此成員函數終止之前為*lpDrawItemStruct*中提供的顯示上下文選擇的所有圖形設備介面 (GDI) 物件。

## <a name="cstatusbarctrlgetborders"></a><a name="getborders"></a>CStatusBarctrl:取得Borders

檢索狀態列控制元件的水準和垂直邊框以及矩形之間的空間的當前寬度。

```
BOOL GetBorders(int* pBorders) const;

BOOL GetBorders(
    int& nHorz,
    int& nVert,
    int& nSpacing) const;
```

### <a name="parameters"></a>參數

*pBorders*<br/>
包含三個元素的整陣列的位址。 第一個元素接收水平邊框的寬度,第二個元素接收垂直邊框的寬度,第三個元素接收矩形之間的邊框寬度。

*恩霍茲*<br/>
引用接收水平邊框寬度的整數。

*nVert*<br/>
引用接收垂直邊框寬度的整數。

*N間距*<br/>
引用接收矩形之間邊框寬度的整數。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

這些邊框確定控制元件外邊緣與控制項中包含文本的矩形之間的間距。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatusBarCtrl#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_2.cpp)]

## <a name="cstatusbarctrlgeticon"></a><a name="geticon"></a>CStatusBarctrl::GetIcon

檢索當前狀態列控件中部件(也稱為窗格)的圖示。

```
HICON GetIcon(int iPart) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*iPart*|[在]包含要檢索的圖示的零點索引。 如果此參數為 -1,則假定狀態列為簡單模式狀態列。|

### <a name="return-value"></a>傳回值

如果方法成功,則圖示的句柄;否則,NULL。

### <a name="remarks"></a>備註

此方法發送[SB_GETICON](/windows/win32/Controls/sb-geticon)消息,這在 Windows SDK 中介紹。

狀態列控制項由一行文本輸出窗格組成,這些窗格也稱為部件。 關於狀態列的詳細資訊,請參閱[MFC 中的狀態列, 並](../../mfc/status-bar-implementation-in-mfc.md)[設定 CStatusBarCtrl 物件的模式](../../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md)。

### <a name="example"></a>範例

以下代碼範例定義用於存取目前狀態`m_statusBar`列 控制項的變數 。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_3.h)]

### <a name="example"></a>範例

以下代碼示例將圖示複製到當前狀態列控制項的兩個窗格中。 在代碼示例的早期版本中,我們創建了一個包含三個窗格的狀態欄控件,然後將圖示添加到第一個窗格中。 本示例從第一個窗格中檢索圖示,然後將其添加到第二個和第三個窗格中。

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_4.cpp)]

## <a name="cstatusbarctrlgetparts"></a><a name="getparts"></a>CStatusBarctrl:取得元件

檢索狀態列控件中的零件計數。

```
int GetParts(
    int nParts,
    int* pParts) const;
```

### <a name="parameters"></a>參數

*n 元件*<br/>
要為其檢索座標的零件數。 如果此參數大於控制項中的零件數,則消息僅檢索現有零件的座標。

*p 組件*<br/>
整數陣列的位址具有與*nParts*指定的零件數相同的元素數。 陣列中的每個元素都接收相應零件右邊緣的客戶端座標。 如果元素設定為 - 1,則該零件的右邊緣位置將延伸到狀態列的右邊緣。

### <a name="return-value"></a>傳回值

控件中的零件數(如果成功)或零。

### <a name="remarks"></a>備註

此成員函數還檢索給定零件數右邊緣的座標。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatusBarCtrl#3](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_5.cpp)]

## <a name="cstatusbarctrlgetrect"></a><a name="getrect"></a>CStatusBarctrl::取得 Rect

檢索狀態列控件中零件的邊界矩形。

```
BOOL GetRect(
    int nPane,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

*nPane*<br/>
要檢索其邊界矩形的零點的零索引。

*lpRect*<br/>
接收邊界矩形的[RECT](/windows/win32/api/windef/ns-windef-rect)結構的位址。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatusBarCtrl#4](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_6.cpp)]

## <a name="cstatusbarctrlgettext"></a><a name="gettext"></a>CStatusBarctrl:取得文字

從狀態列控件的給定部分檢索文本。

```
CString GetText(
    int nPane,
    int* pType = NULL) const;

int GetText(
    LPCTSTR lpszText,
    int nPane,
    int* pType = NULL) const;
```

### <a name="parameters"></a>參數

*lpszText*<br/>
接收文本的緩衝區的位址。 這裡是一個 null 連接字串。

*nPane*<br/>
從中檢索文本的零索引。

*p 型態*<br/>
指向接收類型資訊的整數的指標。 類型可以是以下值之一:

- **0**用邊框繪製文本以顯示低於狀態列的平面。

- SBT_NOBORDERS文本繪製時沒有邊框。

- SBT_POPOUT使用邊框繪製文本以顯示高於狀態列的平面。

- SBT_OWNERDRAW如果文本具有SBT_OWNERDRAW繪圖類型 *,pType*將收到此消息並返回與文本關聯的 32 位值,而不是長度和操作類型。

### <a name="return-value"></a>傳回值

包含當前文本的文本或[CString](../../atl-mfc-shared/reference/cstringt-class.md)的長度(以字元表示)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatusBarCtrl#5](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_7.cpp)]

## <a name="cstatusbarctrlgettextlength"></a><a name="gettextlength"></a>CStatusBarctrl:取得文字長度

從狀態列控件的給定部分檢索文本的長度(以字元表示)。

```
int GetTextLength(
    int nPane,
    int* pType = NULL) const;
```

### <a name="parameters"></a>參數

*nPane*<br/>
從中檢索文本的零索引。

*p 型態*<br/>
指向接收類型資訊的整數的指標。 類型可以是以下值之一:

- **0**用邊框繪製文本以顯示低於狀態列的平面。

- SBT_NOBORDERS文本繪製時沒有邊框。

- SBT_OWNERDRAW文本由父窗口繪製。

- SBT_POPOUT使用邊框繪製文本以顯示高於狀態列的平面。

### <a name="return-value"></a>傳回值

文本的長度(以字元表示)。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatusBarCtrl#6](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_8.cpp)]

## <a name="cstatusbarctrlgettiptext"></a><a name="gettiptext"></a>CStatusBarctrl::取得提示文字

檢索狀態列中窗格的工具提示文本。

```
CString GetTipText(int nPane) const;
```

### <a name="parameters"></a>參數

*nPane*<br/>
用於接收工具提示文本的狀態列窗格的零索引。

### <a name="return-value"></a>傳回值

包含要在工具提示中使用的文本的[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件。

### <a name="remarks"></a>備註

此成員函數實現 win32 消息[SB_GETTIPTEXT](/windows/win32/Controls/sb-gettiptext)的行為,如Windows SDK中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatusBarCtrl#7](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_9.cpp)]

## <a name="cstatusbarctrlissimple"></a><a name="issimple"></a>CStatusBarctrl::簡單

檢查狀態視窗控制項以確定它是否處於簡單模式。

```
BOOL IsSimple() const;
```

### <a name="return-value"></a>傳回值

如果狀態視窗控件處於簡單模式,則非零;否則為零。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[的行為SB_ISSIMPLE](/windows/win32/Controls/sb-issimple),如 Windows SDK 中所述。

## <a name="cstatusbarctrlsetbkcolor"></a><a name="setbkcolor"></a>CStatusBarctrl:SetBkColor

在狀態列中設置背景顏色。

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>參數

*鉻*<br/>
指定新背景顏色的 COLORREF 值。 指定CLR_DEFAULT值,使狀態列使用其預設背景顏色。

### <a name="return-value"></a>傳回值

表示上一個預設背景顏色的[COLORREF](/windows/win32/gdi/colorref)值。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[SB_SETBKCOLOR](/windows/win32/Controls/sb-setbkcolor)的行為,如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatusBarCtrl#8](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_10.cpp)]

## <a name="cstatusbarctrlseticon"></a><a name="seticon"></a>CStatusBarctrl::SetIcon

設置狀態列中窗格的圖示。

```
BOOL SetIcon(
    int nPane,
    HICON hIcon);
```

### <a name="parameters"></a>參數

*nPane*<br/>
將接收圖示的窗格的零基索引。 如果此參數為 -1,則假定狀態列為簡單狀態列。

*hIcon*<br/>
句柄到要設置的圖示。 如果此值為 NULL,則圖示將從零件中刪除。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[SB_SETICON](/windows/win32/Controls/sb-seticon)的行為,如 Windows SDK 中所述。

### <a name="example"></a>範例

  請參考[CStatusBarCtrl 的範例:setBkColor](#setbkcolor)。

## <a name="cstatusbarctrlsetminheight"></a><a name="setminheight"></a>CStatusBarctrl:setMinHeight

設置狀態條控制的繪圖區域的最小高度。

```cpp
void SetMinHeight(int nMin);
```

### <a name="parameters"></a>參數

*nMin*<br/>
控件的最小高度(以像素為單位)。

### <a name="remarks"></a>備註

最小高度是*nMin*和兩倍的寬度(以像素為單位)的狀態欄控件的垂直邊框的總和。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatusBarCtrl#9](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_11.cpp)]

## <a name="cstatusbarctrlsetparts"></a><a name="setparts"></a>CStatusBarctrl::設定元件

設置狀態條控制項中的零件數和每個零件右邊緣的座標。

```
BOOL SetParts(
    int nParts,
    int* pWidths);
```

### <a name="parameters"></a>參數

*n 元件*<br/>
要設置的零件數。 零件數不能大於 255。

*pWidths*<br/>
整數陣列的位址具有與*nParts*指定的零件相同的元素數。 陣列中的每個元素指定相應零件右邊緣的位置(在用戶端座標中)。 如果元素為 - 1,則該零件的右邊緣位置將延伸到控制項的右邊緣。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatusBarCtrl#10](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_12.cpp)]

## <a name="cstatusbarctrlsetsimple"></a><a name="setsimple"></a>CStatusBarctrl:設定簡單

指定狀態列控制項是顯示簡單文本還是顯示以前調用[SetParts](#setparts)設置的所有控制元件元件。

```
BOOL SetSimple(BOOL bSimple = TRUE);
```

### <a name="parameters"></a>參數

*b 簡單*<br/>
[在]顯示類型標誌。 如果此參數為 TRUE,則控制項將顯示簡單文本;如果此參數為 TRUE,則控制項將顯示簡單文本。如果是 FALSE,則顯示多個部件。

### <a name="return-value"></a>傳回值

永遠傳回 0。

### <a name="remarks"></a>備註

如果應用程式將狀態列控件從非簡單更改為簡單,反之亦然,系統將立即重繪該控制項。

## <a name="cstatusbarctrlsettext"></a><a name="settext"></a>CStatusBarctrl::設定文字

在狀態列控制項的指定部分設定文字。

```
BOOL SetText(
    LPCTSTR lpszText,
    int nPane,
    int nType);
```

### <a name="parameters"></a>參數

*lpszText*<br/>
以 Null 結束的字串位址，其指定要設定的文字。 如果*nType*是SBT_OWNERDRAW,*則 lpszText*表示 32 位元資料。

*nPane*<br/>
要設定之部分的以零為起始的索引。 如果此值為 255，則假設狀態列控制項是只有一個部分的簡單控制項。

*nType*<br/>
繪圖作業的類型。 有關可能值的清單,請參閱[SB_SETTEXT訊息](/windows/win32/Controls/sb-settext)。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

該消息使控制項部分已更改無效,從而導致在控制件下次收到WM_PAINT消息時顯示新文本。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatusBarCtrl#11](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_13.cpp)]

## <a name="cstatusbarctrlsettiptext"></a><a name="settiptext"></a>CStatusBarctrl::SetTipText

設定狀態列中窗格的工具提示文本。

```cpp
void SetTipText(
    int nPane,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>參數

*nPane*<br/>
用於接收工具提示文本的狀態列窗格的零索引。

*pssTip文字*<br/>
指向包含工具提示文字的字串的指標。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[SB_SETTIPTEXT](/windows/win32/Controls/sb-settiptext)的行為,如 Windows SDK 中所述。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatusBarCtrl#12](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_14.cpp)]

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CToolBarCtrl 類別](../../mfc/reference/ctoolbarctrl-class.md)
