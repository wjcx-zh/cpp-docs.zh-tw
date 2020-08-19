---
title: CToolTipCtrl Class
ms.date: 11/04/2016
f1_keywords:
- CToolTipCtrl
- AFXCMN/CToolTipCtrl
- AFXCMN/CToolTipCtrl::CToolTipCtrl
- AFXCMN/CToolTipCtrl::Activate
- AFXCMN/CToolTipCtrl::AddTool
- AFXCMN/CToolTipCtrl::AdjustRect
- AFXCMN/CToolTipCtrl::Create
- AFXCMN/CToolTipCtrl::CreateEx
- AFXCMN/CToolTipCtrl::DelTool
- AFXCMN/CToolTipCtrl::GetBubbleSize
- AFXCMN/CToolTipCtrl::GetCurrentTool
- AFXCMN/CToolTipCtrl::GetDelayTime
- AFXCMN/CToolTipCtrl::GetMargin
- AFXCMN/CToolTipCtrl::GetMaxTipWidth
- AFXCMN/CToolTipCtrl::GetText
- AFXCMN/CToolTipCtrl::GetTipBkColor
- AFXCMN/CToolTipCtrl::GetTipTextColor
- AFXCMN/CToolTipCtrl::GetTitle
- AFXCMN/CToolTipCtrl::GetToolCount
- AFXCMN/CToolTipCtrl::GetToolInfo
- AFXCMN/CToolTipCtrl::HitTest
- AFXCMN/CToolTipCtrl::Pop
- AFXCMN/CToolTipCtrl::Popup
- AFXCMN/CToolTipCtrl::RelayEvent
- AFXCMN/CToolTipCtrl::SetDelayTime
- AFXCMN/CToolTipCtrl::SetMargin
- AFXCMN/CToolTipCtrl::SetMaxTipWidth
- AFXCMN/CToolTipCtrl::SetTipBkColor
- AFXCMN/CToolTipCtrl::SetTipTextColor
- AFXCMN/CToolTipCtrl::SetTitle
- AFXCMN/CToolTipCtrl::SetToolInfo
- AFXCMN/CToolTipCtrl::SetToolRect
- AFXCMN/CToolTipCtrl::SetWindowTheme
- AFXCMN/CToolTipCtrl::Update
- AFXCMN/CToolTipCtrl::UpdateTipText
helpviewer_keywords:
- CToolTipCtrl [MFC], CToolTipCtrl
- CToolTipCtrl [MFC], Activate
- CToolTipCtrl [MFC], AddTool
- CToolTipCtrl [MFC], AdjustRect
- CToolTipCtrl [MFC], Create
- CToolTipCtrl [MFC], CreateEx
- CToolTipCtrl [MFC], DelTool
- CToolTipCtrl [MFC], GetBubbleSize
- CToolTipCtrl [MFC], GetCurrentTool
- CToolTipCtrl [MFC], GetDelayTime
- CToolTipCtrl [MFC], GetMargin
- CToolTipCtrl [MFC], GetMaxTipWidth
- CToolTipCtrl [MFC], GetText
- CToolTipCtrl [MFC], GetTipBkColor
- CToolTipCtrl [MFC], GetTipTextColor
- CToolTipCtrl [MFC], GetTitle
- CToolTipCtrl [MFC], GetToolCount
- CToolTipCtrl [MFC], GetToolInfo
- CToolTipCtrl [MFC], HitTest
- CToolTipCtrl [MFC], Pop
- CToolTipCtrl [MFC], Popup
- CToolTipCtrl [MFC], RelayEvent
- CToolTipCtrl [MFC], SetDelayTime
- CToolTipCtrl [MFC], SetMargin
- CToolTipCtrl [MFC], SetMaxTipWidth
- CToolTipCtrl [MFC], SetTipBkColor
- CToolTipCtrl [MFC], SetTipTextColor
- CToolTipCtrl [MFC], SetTitle
- CToolTipCtrl [MFC], SetToolInfo
- CToolTipCtrl [MFC], SetToolRect
- CToolTipCtrl [MFC], SetWindowTheme
- CToolTipCtrl [MFC], Update
- CToolTipCtrl [MFC], UpdateTipText
ms.assetid: 8973f70c-b73a-46c7-908d-758f364b9a97
ms.openlocfilehash: a4c2644ff7a9b2ae60cc166247d27d7a25305b97
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561839"
---
# <a name="ctooltipctrl-class"></a>CToolTipCtrl Class

封裝「工具提示控制項」的功能，這個小型快顯視窗顯示說明應用程式中工具用途的單行文字。

## <a name="syntax"></a>語法

```
class CToolTipCtrl : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CToolTipCtrl：： CToolTipCtrl](#ctooltipctrl)|建構 `CToolTipCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CToolTipCtrl：： Activate](#activate)|啟用並停用工具提示控制項。|
|[CToolTipCtrl：： AddTool](#addtool)|使用工具提示控制項註冊工具。|
|[CToolTipCtrl：： AdjustRect](#adjustrect)|在工具提示控制項的文字顯示矩形與其視窗矩形之間進行轉換。|
|[CToolTipCtrl：： Create](#create)|建立工具提示控制項，並將其附加至 `CToolTipCtrl` 物件。|
|[CToolTipCtrl：： CreateEx](#createex)|使用指定的 Windows 擴充樣式建立工具提示控制項，並將其附加至 `CToolTipCtrl` 物件。|
|[CToolTipCtrl：:D elTool](#deltool)|從工具提示控制項移除工具。|
|[CToolTipCtrl：： GetBubbleSize](#getbubblesize)|捕獲工具提示的大小。|
|[CToolTipCtrl：： GetCurrentTool](#getcurrenttool)|抓取目前工具提示控制項所顯示之工具提示視窗的大小、位置和文字等資訊。|
|[CToolTipCtrl：： GetDelayTime](#getdelaytime)|抓取目前針對工具提示控制項設定的初始、快顯和 reshow 持續時間。|
|[CToolTipCtrl：： GetMargin](#getmargin)|抓取為工具提示視窗設定的上方、左方、下邊界和右邊界。|
|[CToolTipCtrl：： GetMaxTipWidth](#getmaxtipwidth)|抓取工具提示視窗的最大寬度。|
|[CToolTipCtrl：： GetText](#gettext)|抓取工具提示控制項為工具維護的文字。|
|[CToolTipCtrl：： GetTipBkColor](#gettipbkcolor)|抓取工具提示視窗中的背景色彩。|
|[CToolTipCtrl：： GetTipTextColor](#gettiptextcolor)|抓取工具提示視窗中的文字色彩。|
|[CToolTipCtrl：： GetTitle](#gettitle)|抓取目前工具提示控制項的標題。|
|[CToolTipCtrl：： GetToolCount](#gettoolcount)|捕獲工具提示控制項所維護的工具計數。|
|[CToolTipCtrl：： GetToolInfo](#gettoolinfo)|抓取工具提示控制項維護的工具相關資訊。|
|[CToolTipCtrl：： System.windows.media.visualtreehelper.hittest](#hittest)|測試點以判斷它是否在指定之工具的周框中。 如果是，則會抓取工具的相關資訊。|
|[CToolTipCtrl：:P op](#pop)|從 view 中移除顯示的工具提示視窗。|
|[CToolTipCtrl：:P opup](#popup)|使目前的工具提示控制項顯示于最後一個滑鼠訊息的座標上。|
|[CToolTipCtrl：： RelayEvent](#relayevent)|將滑鼠訊息傳遞至工具提示控制項以進行處理。|
|[CToolTipCtrl：： SetDelayTime](#setdelaytime)|設定工具提示控制項的初始、彈出和 reshow 持續時間。|
|[CToolTipCtrl：： SetMargin](#setmargin)|設定工具提示視窗的頂端、左方、下邊界和右邊界。|
|[CToolTipCtrl：： SetMaxTipWidth](#setmaxtipwidth)|設定工具提示視窗的最大寬度。|
|[CToolTipCtrl：： SetTipBkColor](#settipbkcolor)|設定工具提示視窗中的背景色彩。|
|[CToolTipCtrl：： SetTipTextColor](#settiptextcolor)|設定工具提示視窗中的文字色彩。|
|[CToolTipCtrl：： SetTitle](#settitle)|將標準圖示和標題字串新增至工具提示。|
|[CToolTipCtrl：： SetToolInfo](#settoolinfo)|設定工具提示為工具維護的資訊。|
|[CToolTipCtrl：： SetToolRect](#settoolrect)|設定工具的新周框矩形。|
|[CToolTipCtrl：： SetWindowTheme](#setwindowtheme)|設定工具提示視窗的視覺化樣式。|
|[CToolTipCtrl：： Update](#update)|強制重新繪製目前的工具。|
|[CToolTipCtrl：： UpdateTipText](#updatetiptext)|設定工具的工具提示文字。|

## <a name="remarks"></a>備註

「工具」是視窗，例如子視窗或控制項，或是視窗工作區中應用程式定義的矩形區域。 工具提示大部分時間都在隱藏狀態，只有在使用者將游標放置在工具上並停留約二分之一秒時才會顯現。 工具提示會出現在游標附近，並在使用者按一下滑鼠按鍵或將游標移出工具時消失。

`CToolTipCtrl` 提供的功能可控制工具提示的初始時間和持續時間、工具提示文字周圍的邊界寬度、工具提示視窗本身的寬度，以及工具提示的背景和文字色彩。 一個工具提示控制項可以提供多個工具的資訊。

`CToolTipCtrl` 類別提供 Windows 通用工具提示控制項的功能。 此控制項 (，因此 `CToolTipCtrl` 類別) 僅適用于在 Windows 95/98 和 Windows NT 3.51 版和更新版本下執行的程式。

如需啟用工具提示的詳細資訊，請參閱 [Windows 中的工具提示，而不是衍生自 CFrameWnd](../../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)。

如需使用的詳細資訊 `CToolTipCtrl` ，請參閱 [控制項](../../mfc/controls-mfc.md) 和 [使用 CToolTipCtrl](../../mfc/using-ctooltipctrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CToolTipCtrl`

## <a name="requirements"></a>規格需求

**標頭：** afxcmn.h

## <a name="ctooltipctrlactivate"></a><a name="activate"></a> CToolTipCtrl：： Activate

呼叫此函式來啟用或停用工具提示控制項。

```cpp
void Activate(BOOL bActivate);
```

### <a name="parameters"></a>參數

*bActivate*<br/>
指定是否要啟用或停用工具提示控制項。

### <a name="remarks"></a>備註

如果 *bActivate* 為 TRUE，則會啟用控制項;如果為 FALSE，則會停用它。

當工具提示控制項處於作用中狀態時，當游標位於已向控制項註冊的工具上時，就會出現工具提示資訊。當它處於非使用中狀態時，即使游標位於工具上，也不會出現工具提示資訊。

### <a name="example"></a>範例

  請參閱 [CPropertySheet：： GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)的範例。

## <a name="ctooltipctrladdtool"></a><a name="addtool"></a> CToolTipCtrl：： AddTool

使用工具提示控制項註冊工具。

```
BOOL AddTool(
    CWnd* pWnd,
    UINT nIDText,
    LPCRECT lpRectTool = NULL,
    UINT_PTR nIDTool = 0);

BOOL AddTool(
    CWnd* pWnd,
    LPCTSTR lpszText = LPSTR_TEXTCALLBACK,
    LPCRECT lpRectTool = NULL,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
包含工具之視窗的指標。

*nIDText*<br/>
包含工具文字之字串資源的識別碼。

*lpRectTool*<br/>
[矩形](/windows/win32/api/windef/ns-windef-rect)結構的指標，其中包含工具周框的座標。 座標相對於 *pWnd*所識別之視窗工作區的左上角。

*nIDTool*<br/>
工具的識別碼。

*lpszText*<br/>
工具的文字指標。 如果這個參數包含 LPSTR_TEXTCALLBACK 的值，TTN_NEEDTEXT 通知訊息會移至 *pWnd* 指向的視窗父代。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

*LpRectTool*和*nIDTool*參數必須是有效的，或如果*LpRectTool*為 Null，則*nIDTool*必須為0。

工具提示控制項可以與一個以上的工具相關聯。 呼叫此函式可向工具提示控制項註冊工具，如此一來，當游標位於工具上時，就會顯示工具提示中儲存的資訊。

> [!NOTE]
> 您無法使用將工具提示設定為靜態控制項 `AddTool` 。

### <a name="example"></a>範例

  請參閱 [CPropertySheet：： GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)的範例。

## <a name="ctooltipctrladjustrect"></a><a name="adjustrect"></a> CToolTipCtrl：： AdjustRect

在工具提示控制項的文字顯示矩形與其視窗矩形之間進行轉換。

```
BOOL AdjustRect(
    LPRECT lprc,
    BOOL bLarger = TRUE);
```

### <a name="parameters"></a>參數

*lprc*<br/>
[矩形](/windows/win32/api/windef/ns-windef-rect)結構的指標，該結構會保存工具提示視窗矩形或文字顯示矩形。

*bLarger*<br/>
若為 TRUE，則會使用 *lprc* 來指定文字顯示矩形，並接收對應的視窗矩形。 如果為 FALSE，則會使用 *lprc* 來指定視窗矩形，並接收對應的文字顯示矩形。

### <a name="return-value"></a>傳回值

如果已成功調整矩形，則為非零;否則為0。

### <a name="remarks"></a>備註

此成員函式會從視窗矩形計算工具提示控制項的文字顯示矩形，或從顯示指定的文字顯示矩形所需的工具提示視窗矩形計算。

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [TTM_ADJUSTRECT](/windows/win32/Controls/ttm-adjustrect)的行為。

## <a name="ctooltipctrlcreate"></a><a name="create"></a> CToolTipCtrl：： Create

建立工具提示控制項，並將其附加至 `CToolTipCtrl` 物件。

```
virtual BOOL Create(CWnd* pParentWnd, DWORD dwStyle = 0);
```

### <a name="parameters"></a>參數

*pParentWnd*<br/>
指定工具提示控制項的父視窗，通常是 `CDialog` 。 它不得為 NULL。

*dwStyle*<br/>
指定工具提示控制項的樣式。 如需詳細資訊，請參閱「 **備註** 」一節。

### <a name="return-value"></a>傳回值

如果成功建立物件，則為非零， `CToolTipCtrl` 否則為0。

### <a name="remarks"></a>備註

您可以 `CToolTipCtrl` 用兩個步驟來建立。 首先，呼叫此函式來建立 `CToolTipCtrl` 物件，然後呼叫 `Create` 以建立工具提示控制項，並將它附加至 `CToolTipCtrl` 物件。

*DwStyle*參數可以是[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)的任何組合。 此外，工具提示控制項有兩個類別特定樣式： TTS_ALWAYSTIP 和 TTS_NOPREFIX。

|樣式|意義|
|-----------|-------------|
|TTS_ALWAYSTIP|指定當游標位於工具上時，無論工具提示控制項的主控視窗是否為作用中或非作用中，都會出現工具提示。 如果沒有這個樣式，工具提示控制項會在工具的擁有者視窗為使用中時出現，但不會在非使用中時出現。|
|TTS_NOPREFIX|此樣式可防止系統從字串中移除連字號 ( # A0) 字元。 如果工具提示控制項沒有 TTS_NOPREFIX 樣式，則系統會自動移除連字號字元，讓應用程式可以使用與功能表項目相同的字串，也可以使用工具提示控制項中的文字。|

無論您是在建立控制項時指定它們，工具提示控制項都有 WS_POPUP 和 WS_EX_TOOLWINDOW 視窗樣式。

若要建立具有擴充 windows 樣式的工具提示控制項，請呼叫 [CToolTipCtrl：： CreateEx](#createex) 而不是 `Create` 。

### <a name="example"></a>範例

  請參閱 [CPropertySheet：： GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)的範例。

## <a name="ctooltipctrlcreateex"></a><a name="createex"></a> CToolTipCtrl：： CreateEx

 (子視窗) 建立控制項，並將它與物件產生關聯 `CToolTipCtrl` 。

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwStyle = 0,
    DWORD dwStyleEx = 0);
```

### <a name="parameters"></a>參數

*pParentWnd*<br/>
視窗的指標，該視窗為控制項的父代。

*dwStyle*<br/>
指定工具提示控制項的樣式。 如需詳細資訊，請參閱「[建立](#create)」的「**備註**」一節。

*dwStyleEx*<br/>
指定要建立之控制項的延伸樣式。 如需擴充 Windows 樣式的清單，請參閱 Windows SDK 中[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*參數。

### <a name="return-value"></a>傳回值

如果成功則為非零，否則為0。

### <a name="remarks"></a>備註

使用 `CreateEx` 而不是套用 `Create` 延伸的 windows 樣式（由 windows 擴充樣式指定的，在 **WS_EX_** 前面。

## <a name="ctooltipctrlctooltipctrl"></a><a name="ctooltipctrl"></a> CToolTipCtrl：： CToolTipCtrl

建構 `CToolTipCtrl` 物件。

```
CToolTipCtrl();
```

### <a name="remarks"></a>備註

您必須 `Create` 在建立物件之後呼叫。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#74](../../mfc/codesnippet/cpp/ctooltipctrl-class_1.h)]

## <a name="ctooltipctrldeltool"></a><a name="deltool"></a> CToolTipCtrl：:D elTool

從工具提示控制項所支援的工具集合中，移除 *pWnd* 和 *nIDTool* 指定的工具。

```cpp
void DelTool(
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
包含工具之視窗的指標。

*nIDTool*<br/>
工具的識別碼。

## <a name="ctooltipctrlgetbubblesize"></a><a name="getbubblesize"></a> CToolTipCtrl：： GetBubbleSize

捕獲工具提示的大小。

```
CSize GetBubbleSize(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>參數

*lpToolInfo*<br/>
工具提示 [TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) 結構的指標。

### <a name="return-value"></a>傳回值

工具提示的大小。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [TTM_GETBUBBLESIZE](/windows/win32/Controls/ttm-getbubblesize)的行為。

## <a name="ctooltipctrlgetcurrenttool"></a><a name="getcurrenttool"></a> CToolTipCtrl：： GetCurrentTool

抓取目前工具提示控制項所顯示之工具提示視窗的大小、位置和文字等資訊。

```
BOOL GetCurrentTool(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>參數

*lpToolInfo*\
擴展 [TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa) 結構的指標，此結構會接收目前工具提示視窗的相關資訊。

### <a name="return-value"></a>傳回值

如果成功取出資訊，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送 [TTM_GETCURRENTTOOL](/windows/win32/Controls/ttm-getcurrenttool) 的訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會抓取目前工具提示視窗的相關資訊。

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#6](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_2.cpp)]

## <a name="ctooltipctrlgetdelaytime"></a><a name="getdelaytime"></a> CToolTipCtrl：： GetDelayTime

抓取目前為工具提示控制項設定的初始、快顯和 reshow 持續時間。

```
int GetDelayTime(DWORD dwDuration) const;
```

### <a name="parameters"></a>參數

*dwDuration*<br/>
旗標，指定將取出的持續時間值。 這個參數可以是下列其中一個值：

- 如果指標在工具的周框內是固定的，TTDT_AUTOPOP 取得工具提示視窗維持可見的時間長度。

- TTDT_INITIAL 取出在工具提示視窗出現之前，指標必須保持在工具周框內的靜止時間長度。

- TTDT_RESHOW 取出在指標從一個工具移至另一個工具時，後續工具提示視窗出現的時間長度。

### <a name="return-value"></a>傳回值

指定的延遲時間（以毫秒為單位）

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [TTM_GETDELAYTIME](/windows/win32/Controls/ttm-getdelaytime)的行為。

## <a name="ctooltipctrlgetmargin"></a><a name="getmargin"></a> CToolTipCtrl：： GetMargin

抓取工具提示視窗的頂端、左方、底端和右邊界設定。

```cpp
void GetMargin(LPRECT lprc) const;
```

### <a name="parameters"></a>參數

*lprc*<br/>
`RECT`將接收邊界資訊之結構的位址。 [矩形](/windows/win32/api/windef/ns-windef-rect)結構的成員不會定義周框。 針對此訊息的目的，結構成員會以下面方式解讀：

|member|表示法|
|------------|--------------------|
|`top`|頂端框線和工具提示文字頂端之間的距離（以圖元為單位）。|
|`left`|提示文字的左邊框線和左邊緣之間的距離（以圖元為單位）。|
|`bottom`|下框線和尖端文字底部之間的距離（以圖元為單位）。|
|`right`|右邊框線和右邊的提示文字之間的距離（以圖元為單位）。|

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [TTM_GETMARGIN](/windows/win32/Controls/ttm-getmargin)的行為。

## <a name="ctooltipctrlgetmaxtipwidth"></a><a name="getmaxtipwidth"></a> CToolTipCtrl：： GetMaxTipWidth

抓取工具提示視窗的最大寬度。

```
int GetMaxTipWidth() const;
```

### <a name="return-value"></a>傳回值

工具提示視窗的最大寬度。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [TTM_GETMAXTIPWIDTH](/windows/win32/Controls/ttm-getmaxtipwidth)的行為。

## <a name="ctooltipctrlgettext"></a><a name="gettext"></a> CToolTipCtrl：： GetText

抓取工具提示控制項為工具維護的文字。

```cpp
void GetText(
    CString& str,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>參數

*Str*<br/>
`CString`物件的參考，該物件會接收工具的文字。

*pWnd*<br/>
包含工具之視窗的指標。

*nIDTool*<br/>
工具的識別碼。

### <a name="remarks"></a>備註

*PWnd*和*nIDTool*參數會識別工具。 如果該工具先前已透過先前的呼叫向工具提示控制項註冊 `CToolTipCtrl::AddTool` ，則 *str* 參數所參考的物件會被指派工具的文字。

## <a name="ctooltipctrlgettipbkcolor"></a><a name="gettipbkcolor"></a> CToolTipCtrl：： GetTipBkColor

抓取工具提示視窗中的背景色彩。

```
COLORREF GetTipBkColor() const;
```

### <a name="return-value"></a>傳回值

表示背景色彩的 [COLORREF](/windows/win32/gdi/colorref) 值。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [TTM_GETTIPBKCOLOR](/windows/win32/Controls/ttm-gettipbkcolor)的行為。

## <a name="ctooltipctrlgettiptextcolor"></a><a name="gettiptextcolor"></a> CToolTipCtrl：： GetTipTextColor

抓取工具提示視窗中的文字色彩。

```
COLORREF GetTipTextColor() const;
```

### <a name="return-value"></a>傳回值

表示文字色彩的 [COLORREF](/windows/win32/gdi/colorref) 值。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [TTM_GETTIPTEXTCOLOR](/windows/win32/Controls/ttm-gettiptextcolor)的行為。

## <a name="ctooltipctrlgettitle"></a><a name="gettitle"></a> CToolTipCtrl：： GetTitle

抓取目前工具提示控制項的標題。

```cpp
void GetTitle(PTTGETTITLE pttgt) const;
```

### <a name="parameters"></a>參數

*pttgt*\
擴展 [TTGETTITLE](/windows/win32/api/commctrl/ns-commctrl-ttgettitle) 結構的指標，其中包含工具提示控制項的相關資訊。 當此方法傳回時， [TTGETTITLE](/windows/win32/api/commctrl/ns-commctrl-ttgettitle)結構的*pszTitle*成員會指向標題的文字。

### <a name="remarks"></a>備註

這個方法會傳送 [TTM_GETTITLE](/windows/win32/Controls/ttm-gettitle) 的訊息，如 Windows SDK 中所述。

## <a name="ctooltipctrlgettoolcount"></a><a name="gettoolcount"></a> CToolTipCtrl：： GetToolCount

抓取以工具提示控制項註冊的工具計數。

```
int GetToolCount() const;
```

### <a name="return-value"></a>傳回值

使用工具提示控制項註冊的工具計數。

## <a name="ctooltipctrlgettoolinfo"></a><a name="gettoolinfo"></a> CToolTipCtrl：： GetToolInfo

抓取工具提示控制項維護的工具相關資訊。

```
BOOL GetToolInfo(
    CToolInfo& ToolInfo,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>參數

*ToolInfo*<br/>
`TOOLINFO`物件的參考，該物件會接收工具的文字。

*pWnd*<br/>
包含工具之視窗的指標。

*nIDTool*<br/>
工具的識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

`hwnd`CToolInfo 所 `uId` 參考之[TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa)結構的和成員*CToolInfo*會識別該工具。 如果該工具已透過先前的呼叫向工具提示控制項註冊 `AddTool` ，該 `TOOLINFO` 結構就會填入工具的相關資訊。

## <a name="ctooltipctrlhittest"></a><a name="hittest"></a> CToolTipCtrl：： System.windows.media.visualtreehelper.hittest

測試點以判斷它是否在指定之工具的周框矩形內，如果是的話，則會取出工具的相關資訊。

```
BOOL HitTest(
    CWnd* pWnd,
    CPoint pt,
    LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>參數

*pWnd*<br/>
包含工具之視窗的指標。

*pt*<br/>
物件的指標， `CPoint` 其中包含要測試之點的座標。

*lpToolInfo*<br/>
[TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa)結構的指標，其中包含工具的相關資訊。

### <a name="return-value"></a>傳回值

如果點擊測試資訊指定的點位於工具的周框矩形內，則為非零。否則為0。

### <a name="remarks"></a>備註

如果此函式傳回非零值，則 *lpToolInfo* 所指向的結構會填入該工具在其矩形內的資訊。

`TTHITTESTINFO`結構的定義如下：

```cpp
typedef struct _TT_HITTESTINFO { // tthti
    HWND hwnd;   // handle of tool or window with tool
    POINT pt;    // client coordinates of point to test
    TOOLINFO ti; // receives information about the tool
} TTHITTESTINFO, FAR * LPHITTESTINFO;
```

- `hwnd`

   指定工具的控制碼。

- `pt`

   指定點是否在工具周框中的座標。

- `ti`

   工具的相關資訊。 如需結構的詳細資訊 `TOOLINFO` ，請參閱 [CToolTipCtrl：： GetToolInfo](#gettoolinfo)。

## <a name="ctooltipctrlpop"></a><a name="pop"></a> CToolTipCtrl：:P op

從視圖中移除顯示的工具提示視窗。

```cpp
void Pop();
```

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [TTM_POP](/windows/win32/Controls/ttm-pop)的行為。

## <a name="ctooltipctrlpopup"></a><a name="popup"></a> CToolTipCtrl：:P opup

使目前的工具提示控制項顯示于最後一個滑鼠訊息的座標上。

```cpp
void Popup();
```

### <a name="remarks"></a>備註

這個方法會傳送 [TTM_POPUP](/windows/win32/Controls/ttm-popup) 的訊息，如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會顯示工具提示視窗。

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#7](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_3.cpp)]

## <a name="ctooltipctrlrelayevent"></a><a name="relayevent"></a> CToolTipCtrl：： RelayEvent

將滑鼠訊息傳遞至工具提示控制項以進行處理。

```cpp
void RelayEvent(LPMSG lpMsg);
```

### <a name="parameters"></a>參數

*lpMsg*<br/>
訊息結構的指標，其中包含要 [轉送的訊息](/windows/win32/api/winuser/ns-winuser-msg) 。

### <a name="remarks"></a>備註

工具提示控制項只會處理下列訊息，這些訊息會透過下列方式傳送給它 `RelayEvent` ：

|WM_LBUTTONDOWN|WM_MOUSEMOVE|
|---------------------|-------------------|
|WM_LBUTTONUP|WM_RBUTTONDOWN|
|WM_MBUTTONDOWN|WM_RBUTTONUP|
|WM_MBUTTONUP||

### <a name="example"></a>範例

  請參閱 [CPropertySheet：： GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)的範例。

## <a name="ctooltipctrlsetdelaytime"></a><a name="setdelaytime"></a> CToolTipCtrl：： SetDelayTime

設定工具提示控制項的延遲時間。

```cpp
void SetDelayTime(UINT nDelay);

void SetDelayTime(
    DWORD dwDuration,
    int iTime);
```

### <a name="parameters"></a>參數

*nDelay*<br/>
指定新的延遲時間（以毫秒為單位）。

*dwDuration*<br/>
旗標，指定將取出的持續時間值。 如需有效值的描述，請參閱 [CToolTipCtrl：： GetDelayTime](#getdelaytime) 。

*iTime*<br/>
指定的延遲時間（以毫秒為單位）。

### <a name="remarks"></a>備註

延遲時間是在工具提示視窗出現之前，游標必須保留在工具上的時間長度。 預設的延遲時間是500毫秒。

## <a name="ctooltipctrlsetmargin"></a><a name="setmargin"></a> CToolTipCtrl：： SetMargin

設定工具提示視窗的頂端、左方、下邊界和右邊界。

```cpp
void SetMargin(LPRECT lprc);
```

### <a name="parameters"></a>參數

*lprc*<br/>
結構的位址 `RECT` ，其中包含要設定的邊界資訊。 結構的成員 `RECT` 不會定義周框。 請參閱 [CToolTipCtrl：： GetMargin](#getmargin) ，以取得邊際資訊的描述。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [TTM_SETMARGIN](/windows/win32/Controls/ttm-setmargin)的行為。

## <a name="ctooltipctrlsetmaxtipwidth"></a><a name="setmaxtipwidth"></a> CToolTipCtrl：： SetMaxTipWidth

設定工具提示視窗的最大寬度。

```
int SetMaxTipWidth(int iWidth);
```

### <a name="parameters"></a>參數

*iWidth*<br/>
要設定的最大工具提示視窗寬度。

### <a name="return-value"></a>傳回值

先前的提示寬度上限。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [TTM_SETMAXTIPWIDTH](/windows/win32/Controls/ttm-setmaxtipwidth)的行為。

## <a name="ctooltipctrlsettipbkcolor"></a><a name="settipbkcolor"></a> CToolTipCtrl：： SetTipBkColor

設定工具提示視窗中的背景色彩。

```cpp
void SetTipBkColor(COLORREF clr);
```

### <a name="parameters"></a>參數

*Clr*<br/>
新的背景色彩。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [TTM_SETTIPBKCOLOR](/windows/win32/Controls/ttm-settipbkcolor)的行為。

## <a name="ctooltipctrlsettiptextcolor"></a><a name="settiptextcolor"></a> CToolTipCtrl：： SetTipTextColor

設定工具提示視窗中的文字色彩。

```cpp
void SetTipTextColor(COLORREF clr);
```

### <a name="parameters"></a>參數

*Clr*<br/>
新的文字色彩。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [TTM_SETTIPTEXTCOLOR](/windows/win32/Controls/ttm-settiptextcolor)的行為。

## <a name="ctooltipctrlsettitle"></a><a name="settitle"></a> CToolTipCtrl：： SetTitle

將標準圖示和標題字串新增至工具提示。

```
BOOL SetTitle(
    UINT uIcon,
    LPCTSTR lpstrTitle);
```

### <a name="parameters"></a>參數

*uIcon*<br/>
請參閱 Windows SDK [TTM_SETTITLE](/windows/win32/Controls/ttm-settitle)中的*圖示*。

*lpstrTitle*<br/>
標題字串的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式會依照 Windows SDK 所述，執行 Win32 訊息 [TTM_SETTITLE](/windows/win32/Controls/ttm-settitle)的行為。

## <a name="ctooltipctrlsettoolinfo"></a><a name="settoolinfo"></a> CToolTipCtrl：： SetToolInfo

設定工具提示為工具維護的資訊。

```cpp
void SetToolInfo(LPTOOLINFO lpToolInfo);
```

### <a name="parameters"></a>參數

*lpToolInfo*<br/>
[TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa)結構的指標，指定要設定的資訊。

## <a name="ctooltipctrlsettoolrect"></a><a name="settoolrect"></a> CToolTipCtrl：： SetToolRect

設定工具的新周框矩形。

```cpp
void SetToolRect(
    CWnd* pWnd,
    UINT_PTR nIDTool,
    LPCRECT lpRect);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
包含工具之視窗的指標。

*nIDTool*<br/>
工具的識別碼。

*lpRect*<br/>
指定新周 [框的矩形結構指標](/windows/win32/api/windef/ns-windef-rect) 。

## <a name="ctooltipctrlsetwindowtheme"></a><a name="setwindowtheme"></a> CToolTipCtrl：： SetWindowTheme

設定工具提示視窗的視覺化樣式。

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>參數

*pszSubAppName*<br/>
Unicode 字串的指標，其中包含要設定的視覺化樣式。

### <a name="return-value"></a>傳回值

未使用傳回值。

### <a name="remarks"></a>備註

此成員函式會模擬 [TTM_SETWINDOWTHEME](/windows/win32/Controls/ttm-setwindowtheme) 訊息的功能，如 Windows SDK 中所述。

## <a name="ctooltipctrlupdate"></a><a name="update"></a> CToolTipCtrl：： Update

強制重新繪製目前的工具。

```cpp
void Update();
```

## <a name="ctooltipctrlupdatetiptext"></a><a name="updatetiptext"></a> CToolTipCtrl：： UpdateTipText

更新此控制項工具的工具提示文字。

```cpp
void UpdateTipText(
    LPCTSTR lpszText,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);

void UpdateTipText(
    UINT nIDText,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>參數

*lpszText*<br/>
工具的文字指標。

*pWnd*<br/>
包含工具之視窗的指標。

*nIDTool*<br/>
工具的識別碼。

*nIDText*<br/>
包含工具文字之字串資源的識別碼。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CToolBar 類別](../../mfc/reference/ctoolbar-class.md)
