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
ms.openlocfilehash: d2440eb05a1367b7d4980494e3d7f5de646d5fd0
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88562645"
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
|[CStatusBarCtrl：： CStatusBarCtrl](#cstatusbarctrl)|建構 `CStatusBarCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CStatusBarCtrl：： Create](#create)|建立狀態列控制項並將其附加至 `CStatusBarCtrl` 物件。|
|[CStatusBarCtrl：： CreateEx](#createex)|使用指定的 Windows 擴充樣式建立狀態列控制項，並將其附加至 `CStatusBarCtrl` 物件。|
|[CStatusBarCtrl：:D rawItem](#drawitem)|當主控描繪狀態列控制項的視覺外觀變更時呼叫。|
|[CStatusBarCtrl：： GetBorders](#getborders)|抓取狀態列控制項之水準和垂直框線的目前寬度。|
|[CStatusBarCtrl：： GetIcon](#geticon)|抓取元件 (的圖示，也稱為目前狀態列控制項中的窗格) 。|
|[CStatusBarCtrl：： GetParts](#getparts)|抓取狀態列控制項中元件的計數。|
|[CStatusBarCtrl：： GetRect](#getrect)|抓取狀態列控制項中某部分的周框。|
|[CStatusBarCtrl：： GetText](#gettext)|從狀態列控制項的指定部分抓取文字。|
|[CStatusBarCtrl：： GetTextLength](#gettextlength)|從狀態列控制項的指定部分，取得文字的長度（以字元為單位）。|
|[CStatusBarCtrl：： GetTipText](#gettiptext)|抓取狀態列中窗格的工具提示文字。|
|[CStatusBarCtrl：： IsSimple](#issimple)|檢查狀態視窗控制項，以判斷其是否為簡單模式。|
|[CStatusBarCtrl：： SetBkColor](#setbkcolor)|設定狀態列中的背景色彩。|
|[CStatusBarCtrl：： SetIcon](#seticon)|設定狀態列中窗格的圖示。|
|[CStatusBarCtrl：： SetMinHeight](#setminheight)|設定狀態列控制項之繪圖區的最小高度。|
|[CStatusBarCtrl：： SetParts](#setparts)|設定狀態列控制項中的部分數目，以及每個元件右邊緣的座標。|
|[CStatusBarCtrl：： SetSimple](#setsimple)|指定狀態列控制項是否顯示簡單文字，或顯示前一次呼叫所設定的所有控制群組件 `SetParts` 。|
|[CStatusBarCtrl：： SetText](#settext)|在狀態列控制項的指定部分設定文字。|
|[CStatusBarCtrl：： SetTipText](#settiptext)|設定狀態列中窗格的工具提示文字。|

## <a name="remarks"></a>備註

「狀態列控制項」是水準視窗，通常會顯示在父視窗的底部，讓應用程式可以顯示各種類型的狀態資訊。 狀態列控制項可以分割成多個部分，以顯示一種以上的資訊。

此控制項 (，因此 `CStatusBarCtrl` 類別) 僅適用于在 Windows 95/98 和 Windows NT 3.51 版和更新版本下執行的程式。

如需使用的詳細資訊 `CStatusBarCtrl` ，請參閱 [控制項](../../mfc/controls-mfc.md) 和 [使用 CStatusBarCtrl](../../mfc/using-cstatusbarctrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatusBarCtrl`

## <a name="requirements"></a>規格需求

**標頭：** afxcmn.h

## <a name="cstatusbarctrlcreate"></a><a name="create"></a> CStatusBarCtrl：： Create

建立狀態列控制項並將其附加至 `CStatusBarCtrl` 物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定狀態列控制項的樣式。 套用 Windows SDK 中 [通用控制項樣式](/windows/win32/Controls/common-control-styles) 所列出的狀態列控制項樣式的任何組合。 這個參數必須包含 WS_CHILD 的樣式。 它也應該包含 WS_VISIBLE 的樣式。

*矩形*<br/>
指定狀態列控制項的大小和位置。 它可以是 [CRect](../../atl-mfc-shared/reference/crect-class.md) 物件或 [RECT](/windows/win32/api/windef/ns-windef-rect) 結構。

*pParentWnd*<br/>
指定狀態列控制項的父視窗，通常是 `CDialog` 。 它不得為 NULL。

*nID*<br/>
指定狀態列控制項的識別碼。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

您可以 `CStatusBarCtrl` 用兩個步驟來建立。 首先，呼叫此函式，然後呼叫 `Create` ，以建立狀態列控制項並將其附加至 `CStatusBarCtrl` 物件。

狀態視窗的預設位置是在父視窗的底部，但您可以指定 CCS_TOP 樣式，讓它出現在父視窗的工作區上方。 您可以指定 SBARS_SIZEGRIP 樣式，在狀態視窗的右端包含調整大小的底框。 不建議結合 CCS_TOP 和 SBARS_SIZEGRIP 樣式，因為即使系統在狀態視窗中繪製它，結果的調整大小底框仍無法運作。

若要建立具有延伸視窗樣式的狀態列，請呼叫 [CStatusBarCtrl：： CreateEx](#createex) 而不是 `Create` 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatusBarCtrl#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_1.cpp)]

## <a name="cstatusbarctrlcreateex"></a><a name="createex"></a> CStatusBarCtrl：： CreateEx

 (子視窗) 建立控制項，並將它與物件產生關聯 `CStatusBarCtrl` 。

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
指定要建立之控制項的延伸樣式。 如需擴充 Windows 樣式的清單，請參閱 Windows SDK 中[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*參數。

*dwStyle*<br/>
指定狀態列控制項的樣式。 套用 Windows SDK 中 [通用控制項樣式](/windows/win32/Controls/common-control-styles) 所列出的狀態列控制項樣式的任何組合。 這個參數必須包含 WS_CHILD 的樣式。 它也應該包含 WS_VISIBLE 的樣式。

*矩形*<br/>
[矩形](/windows/win32/api/windef/ns-windef-rect)結構的參考，描述要建立之視窗的大小和位置（以*pParentWnd*的用戶端座標表示）。

*pParentWnd*<br/>
視窗的指標，該視窗為控制項的父代。

*nID*<br/>
控制項的子視窗識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

使用 `CreateEx` instead Of [Create](#create) 來套用延伸的 windows 樣式（依 Windows 擴充樣式的 "前言 **WS_EX_** 指定）。

## <a name="cstatusbarctrlcstatusbarctrl"></a><a name="cstatusbarctrl"></a> CStatusBarCtrl：： CStatusBarCtrl

建構 `CStatusBarCtrl` 物件。

```
CStatusBarCtrl();
```

## <a name="cstatusbarctrldrawitem"></a><a name="drawitem"></a> CStatusBarCtrl：:D rawItem

當主控描繪狀態列控制項的視覺外觀變更時，由架構呼叫。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>參數

*lpDrawItemStruct*<br/>
[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)結構的長指標，其中包含所需繪圖類型的相關資訊。

### <a name="remarks"></a>備註

`itemAction`結構的成員 `DRAWITEMSTRUCT` 會定義要執行的繪圖動作。

依預設，此成員函式不會執行任何動作。 覆寫這個成員函式，以針對主控描繪物件來執行繪圖 `CStatusBarCtrl` 。

應用程式應該在此成員函式終止之前，還原為 *lpDrawItemStruct* 中提供的顯示內容選取的所有圖形裝置介面 (GDI) 物件。

## <a name="cstatusbarctrlgetborders"></a><a name="getborders"></a> CStatusBarCtrl：： GetBorders

抓取狀態列控制項目前的水準和垂直框線寬度，以及矩形之間的間距。

```
BOOL GetBorders(int* pBorders) const;

BOOL GetBorders(
    int& nHorz,
    int& nVert,
    int& nSpacing) const;
```

### <a name="parameters"></a>參數

*pBorders*<br/>
有三個元素的整數陣列位址。 第一個元素會接收水準框線的寬度，第二個會接收垂直框線的寬度，而第三個專案會接收矩形之間的框線寬度。

*nHorz*<br/>
接收水準框線寬度之整數的參考。

*轉換 n）*<br/>
整數的參考，該整數會接收垂直框線的寬度。

*nSpacing*<br/>
在矩形之間接收框線寬度的整數參考。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

這些框線可決定控制項外緣與包含文字之控制項內的矩形之間的間距。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatusBarCtrl#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_2.cpp)]

## <a name="cstatusbarctrlgeticon"></a><a name="geticon"></a> CStatusBarCtrl：： GetIcon

抓取元件 (的圖示，也稱為目前狀態列控制項中的窗格) 。

```
HICON GetIcon(int iPart) const;
```

### <a name="parameters"></a>參數

*iPart*\
在元件以零為起始的索引，其中包含要取出的圖示。 如果此參數為-1，則會假設狀態列為簡單模式的狀態列。

### <a name="return-value"></a>傳回值

如果方法成功，則為圖示的控制碼;否則為 Null。

### <a name="remarks"></a>備註

這個方法會傳送 [SB_GETICON](/windows/win32/Controls/sb-geticon) 的訊息，如 Windows SDK 中所述。

狀態列控制項是由一列文字輸出窗格所組成，這些窗格也稱為「部分」。 如需狀態列的詳細資訊，請參閱 [MFC 中的狀態列執行](../../mfc/status-bar-implementation-in-mfc.md) 和 [設定 CStatusBarCtrl 物件的模式](../../mfc/setting-the-mode-of-a-cstatusbarctrl-object.md)。

### <a name="example"></a>範例

下列程式碼範例 `m_statusBar` 會定義用來存取目前狀態列控制項的變數。 下一個範例中會使用此變數。

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_3.h)]

### <a name="example"></a>範例

下列程式碼範例會將圖示複製到目前狀態列控制項的兩個窗格。 在程式碼範例的先前章節中，我們建立了具有三個窗格的狀態列控制項，然後將圖示新增至第一個窗格。 此範例會從第一個窗格抓取圖示，然後將它新增至第二個和第三個窗格。

[!code-cpp[NVC_MFC_CStatusBarCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_4.cpp)]

## <a name="cstatusbarctrlgetparts"></a><a name="getparts"></a> CStatusBarCtrl：： GetParts

抓取狀態列控制項中元件的計數。

```
int GetParts(
    int nParts,
    int* pParts) const;
```

### <a name="parameters"></a>參數

*nParts*<br/>
要抓取座標的部分數目。 如果此參數大於控制項中的部分數目，則訊息只會抓取現有元件的座標。

*pParts*<br/>
整數陣列的位址，其專案數與 *nParts*所指定的元件數相同。 陣列中的每個元素都會接收相對應元件右邊緣的用戶端座標。 如果元素設定為-1，則該部分的右邊緣位置會延伸至狀態列的右邊緣。

### <a name="return-value"></a>傳回值

如果成功，則為控制項中的部分數目，否則為零。

### <a name="remarks"></a>備註

此成員函式也會抓取指定部分數目的右邊緣座標。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatusBarCtrl#3](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_5.cpp)]

## <a name="cstatusbarctrlgetrect"></a><a name="getrect"></a> CStatusBarCtrl：： GetRect

抓取狀態列控制項中某部分的周框。

```
BOOL GetRect(
    int nPane,
    LPRECT lpRect) const;
```

### <a name="parameters"></a>參數

*nPane*<br/>
以零為基底的索引，這是要抓取其周框矩形的部分。

*lpRect*<br/>
接收周框矩形的 [RECT](/windows/win32/api/windef/ns-windef-rect) 結構位址。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatusBarCtrl#4](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_6.cpp)]

## <a name="cstatusbarctrlgettext"></a><a name="gettext"></a> CStatusBarCtrl：： GetText

從狀態列控制項的指定部分抓取文字。

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
接收文字之緩衝區的位址。 此參數是以 null 結束的字串。

*nPane*<br/>
以零為基底的索引，這是要從中取得文字的部分。

*pType*<br/>
接收型別資訊之整數的指標。 此類型可以是下列其中一個值：

- **0** 文字以框線繪製，並顯示在狀態列的平面下方。

- SBT_NOBORDERS 不含框線的文字繪製。

- SBT_POPOUT 文字會以框線繪製，並顯示在狀態列的平面上方。

- SBT_OWNERDRAW 如果文字具有 SBT_OWNERDRAW 繪圖類型， *pType* 會接收此訊息並傳回與文字相關聯的32位值，而不是長度和運算類型。

### <a name="return-value"></a>傳回值

文字的長度（以字元為單位），或包含目前文字的 [CString](../../atl-mfc-shared/reference/cstringt-class.md) 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatusBarCtrl#5](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_7.cpp)]

## <a name="cstatusbarctrlgettextlength"></a><a name="gettextlength"></a> CStatusBarCtrl：： GetTextLength

從狀態列控制項的指定部分，取得文字的長度（以字元為單位）。

```
int GetTextLength(
    int nPane,
    int* pType = NULL) const;
```

### <a name="parameters"></a>參數

*nPane*<br/>
以零為基底的索引，這是要從中取得文字的部分。

*pType*<br/>
接收型別資訊之整數的指標。 此類型可以是下列其中一個值：

- **0** 文字以框線繪製，並顯示在狀態列的平面下方。

- SBT_NOBORDERS 不含框線的文字繪製。

- SBT_OWNERDRAW 父視窗繪製文字。

- SBT_POPOUT 文字會以框線繪製，並顯示在狀態列的平面上方。

### <a name="return-value"></a>傳回值

文字的長度（以字元為單位）。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatusBarCtrl#6](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_8.cpp)]

## <a name="cstatusbarctrlgettiptext"></a><a name="gettiptext"></a> CStatusBarCtrl：： GetTipText

抓取狀態列中窗格的工具提示文字。

```
CString GetTipText(int nPane) const;
```

### <a name="parameters"></a>參數

*nPane*<br/>
以零為基底的狀態列索引，用來接收工具提示文字。

### <a name="return-value"></a>傳回值

[CString](../../atl-mfc-shared/reference/cstringt-class.md)物件，其中包含要在工具提示中使用的文字。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [SB_GETTIPTEXT](/windows/win32/Controls/sb-gettiptext)的行為。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatusBarCtrl#7](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_9.cpp)]

## <a name="cstatusbarctrlissimple"></a><a name="issimple"></a> CStatusBarCtrl：： IsSimple

檢查狀態視窗控制項，以判斷其是否為簡單模式。

```
BOOL IsSimple() const;
```

### <a name="return-value"></a>傳回值

如果狀態視窗控制項處於簡單模式，則為非零。否則為零。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [SB_ISSIMPLE](/windows/win32/Controls/sb-issimple)的行為。

## <a name="cstatusbarctrlsetbkcolor"></a><a name="setbkcolor"></a> CStatusBarCtrl：： SetBkColor

設定狀態列中的背景色彩。

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>參數

*鉻*<br/>
COLORRE光圈值，指定新的背景色彩。 指定 CLR_DEFAULT 值，使狀態列使用其預設背景色彩。

### <a name="return-value"></a>傳回值

表示先前預設背景色彩的 [COLORREF](/windows/win32/gdi/colorref) 值。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [SB_SETBKCOLOR](/windows/win32/Controls/sb-setbkcolor)的行為。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatusBarCtrl#8](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_10.cpp)]

## <a name="cstatusbarctrlseticon"></a><a name="seticon"></a> CStatusBarCtrl：： SetIcon

設定狀態列中窗格的圖示。

```
BOOL SetIcon(
    int nPane,
    HICON hIcon);
```

### <a name="parameters"></a>參數

*nPane*<br/>
將接收圖示之窗格的以零為基底的索引。 如果此參數為-1，則會假設狀態列為簡單的狀態列。

*hIcon*<br/>
要設定之圖示的控制碼。 如果這個值為 Null，則會從元件中移除圖示。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [SB_SETICON](/windows/win32/Controls/sb-seticon)的行為。

### <a name="example"></a>範例

  請參閱 [CStatusBarCtrl：： SetBkColor](#setbkcolor)的範例。

## <a name="cstatusbarctrlsetminheight"></a><a name="setminheight"></a> CStatusBarCtrl：： SetMinHeight

設定狀態列控制項之繪圖區的最小高度。

```cpp
void SetMinHeight(int nMin);
```

### <a name="parameters"></a>參數

*N 每天下限*<br/>
控制項的最小高度（以圖元為單位）。

### <a name="remarks"></a>備註

最小高度為狀態列控制項的垂直框線寬度（以圖元為單位）的 *總和（以* 圖元為單位）。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatusBarCtrl#9](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_11.cpp)]

## <a name="cstatusbarctrlsetparts"></a><a name="setparts"></a> CStatusBarCtrl：： SetParts

設定狀態列控制項中的部分數目，以及每個元件右邊緣的座標。

```
BOOL SetParts(
    int nParts,
    int* pWidths);
```

### <a name="parameters"></a>參數

*nParts*<br/>
要設定的部分數目。 部分數目不可大於255。

*pWidths*<br/>
整數陣列的位址，其專案數與 *nParts*所指定的元件相同。 陣列中的每個元素會指定相對應元件右邊緣的位置（以客戶座標為單位）。 如果元素為-1，則該部分的右邊緣位置會延伸至控制項的右邊緣。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatusBarCtrl#10](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_12.cpp)]

## <a name="cstatusbarctrlsetsimple"></a><a name="setsimple"></a> CStatusBarCtrl：： SetSimple

指定狀態列控制項是否顯示簡單文字，或顯示前一次呼叫 [SetParts](#setparts)所設定的所有控制群組件。

```
BOOL SetSimple(BOOL bSimple = TRUE);
```

### <a name="parameters"></a>參數

*bSimple*<br/>
在顯示類型旗標。 如果此參數為 TRUE，控制項會顯示簡單的文字;如果為 FALSE，則會顯示多個部分。

### <a name="return-value"></a>傳回值

永遠傳回 0。

### <a name="remarks"></a>備註

如果您的應用程式將狀態列控制項從非簡單變更為簡單，或反之亦然，系統會立即重新繪製控制項。

## <a name="cstatusbarctrlsettext"></a><a name="settext"></a> CStatusBarCtrl：： SetText

在狀態列控制項的指定部分設定文字。

```
BOOL SetText(
    LPCTSTR lpszText,
    int nPane,
    int nType);
```

### <a name="parameters"></a>參數

*lpszText*<br/>
以 Null 結束的字串位址，其指定要設定的文字。 如果 *nType* 是 SBT_OWNERDRAW， *lpszText* 代表32位的資料。

*nPane*<br/>
要設定之部分的以零為起始的索引。 如果此值為 255，則假設狀態列控制項是只有一個部分的簡單控制項。

*nType*<br/>
繪圖作業的類型。 如需可能值的清單，請參閱 [SB_SETTEXT 訊息](/windows/win32/Controls/sb-settext) 。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

此訊息會使已變更之控制項的部分失效，使其在控制項下一次收到 WM_PAINT 訊息時顯示新的文字。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatusBarCtrl#11](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_13.cpp)]

## <a name="cstatusbarctrlsettiptext"></a><a name="settiptext"></a> CStatusBarCtrl：： SetTipText

設定狀態列中窗格的工具提示文字。

```cpp
void SetTipText(
    int nPane,
    LPCTSTR pszTipText);
```

### <a name="parameters"></a>參數

*nPane*<br/>
以零為基底的狀態列索引，用來接收工具提示文字。

*pszTipText*<br/>
包含工具提示文字之字串的指標。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [SB_SETTIPTEXT](/windows/win32/Controls/sb-settiptext)的行為。

### <a name="example"></a>範例

[!code-cpp[NVC_MFC_CStatusBarCtrl#12](../../mfc/reference/codesnippet/cpp/cstatusbarctrl-class_14.cpp)]

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CToolBarCtrl 類別](../../mfc/reference/ctoolbarctrl-class.md)
