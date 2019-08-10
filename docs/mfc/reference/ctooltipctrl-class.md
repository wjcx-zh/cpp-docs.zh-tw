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
ms.openlocfilehash: bbd369d282df1cac59e6966a2d832e23b8ff6da0
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916732"
---
# <a name="ctooltipctrl-class"></a>CToolTipCtrl Class

封裝「工具提示控制項」的功能，這個小型快顯視窗顯示說明應用程式中工具用途的單行文字。

## <a name="syntax"></a>語法

```
class CToolTipCtrl : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CToolTipCtrl::CToolTipCtrl](#ctooltipctrl)|建構 `CToolTipCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CToolTipCtrl::Activate](#activate)|啟用和停用工具提示控制項。|
|[CToolTipCtrl::AddTool](#addtool)|向工具提示控制項註冊工具。|
|[CToolTipCtrl::AdjustRect](#adjustrect)|在工具提示控制項的文字顯示矩形和其視窗矩形之間轉換。|
|[CToolTipCtrl::Create](#create)|建立工具提示控制項, 並將它附加至`CToolTipCtrl`物件。|
|[CToolTipCtrl::CreateEx](#createex)|使用指定的 Windows 擴充樣式建立工具提示控制項, 並將其附加至`CToolTipCtrl`物件。|
|[CToolTipCtrl::DelTool](#deltool)|從工具提示控制項移除工具。|
|[CToolTipCtrl::GetBubbleSize](#getbubblesize)|抓取工具提示的大小。|
|[CToolTipCtrl::GetCurrentTool](#getcurrenttool)|抓取目前工具提示控制項顯示之工具提示視窗的大小、位置和文字等資訊。|
|[CToolTipCtrl::GetDelayTime](#getdelaytime)|抓取目前為工具提示控制項所設定的初始、快顯視窗和 reshow 持續時間。|
|[CToolTipCtrl::GetMargin](#getmargin)|抓取工具提示視窗所設定的上、左、下和右邊界。|
|[CToolTipCtrl::GetMaxTipWidth](#getmaxtipwidth)|抓取工具提示視窗的最大寬度。|
|[CToolTipCtrl::GetText](#gettext)|抓取工具提示控制項為工具維護的文字。|
|[CToolTipCtrl::GetTipBkColor](#gettipbkcolor)|抓取工具提示視窗中的背景色彩。|
|[CToolTipCtrl::GetTipTextColor](#gettiptextcolor)|抓取工具提示視窗中的文字色彩。|
|[CToolTipCtrl::GetTitle](#gettitle)|抓取目前工具提示控制項的標題。|
|[CToolTipCtrl::GetToolCount](#gettoolcount)|抓取工具提示控制項所維護的工具計數。|
|[CToolTipCtrl::GetToolInfo](#gettoolinfo)|抓取工具提示控制項針對工具所維護的資訊。|
|[CToolTipCtrl::HitTest](#hittest)|測試點, 判斷它是否在指定之工具的周框內。 若是如此, 則會抓取工具的相關資訊。|
|[CToolTipCtrl::Pop](#pop)|從 view 中移除顯示的工具提示視窗。|
|[CToolTipCtrl::Popup](#popup)|使目前的工具提示控制項顯示在最後一個滑鼠訊息的座標上。|
|[CToolTipCtrl::RelayEvent](#relayevent)|將滑鼠訊息傳遞至工具提示控制項以進行處理。|
|[CToolTipCtrl::SetDelayTime](#setdelaytime)|設定工具提示控制項的初始、快顯和 reshow 持續時間。|
|[CToolTipCtrl::SetMargin](#setmargin)|設定工具提示視窗的上、左、下和右邊界。|
|[CToolTipCtrl::SetMaxTipWidth](#setmaxtipwidth)|設定工具提示視窗的最大寬度。|
|[CToolTipCtrl::SetTipBkColor](#settipbkcolor)|設定工具提示視窗中的背景色彩。|
|[CToolTipCtrl::SetTipTextColor](#settiptextcolor)|設定工具提示視窗中的文字色彩。|
|[CToolTipCtrl::SetTitle](#settitle)|將標準圖示和標題字串加入工具提示中。|
|[CToolTipCtrl::SetToolInfo](#settoolinfo)|設定工具提示為工具維護的資訊。|
|[CToolTipCtrl::SetToolRect](#settoolrect)|設定工具的新周框。|
|[CToolTipCtrl::SetWindowTheme](#setwindowtheme)|設定工具提示視窗的視覺化樣式。|
|[CToolTipCtrl::Update](#update)|強制重新繪製目前的工具。|
|[CToolTipCtrl::UpdateTipText](#updatetiptext)|設定工具的工具提示文字。|

## <a name="remarks"></a>備註

「工具」是視窗 (例如子視窗或控制項), 或是視窗工作區中的應用程式定義的矩形區域。 工具提示大部分時間都在隱藏狀態，只有在使用者將游標放置在工具上並停留約二分之一秒時才會顯現。 工具提示會出現在游標附近, 而且當使用者按一下滑鼠按鍵或將游標移出工具時, 就會消失。

`CToolTipCtrl`提供的功能可控制工具提示的初始時間和持續時間、工具提示文字周圍的邊界寬度、工具提示視窗本身的寬度, 以及工具提示的背景和文字色彩。 一個工具提示控制項可以提供多個工具的資訊。

`CToolTipCtrl` 類別提供 Windows 通用工具提示控制項的功能。 這個控制項 (因此`CToolTipCtrl`類別) 僅適用于在 windows 95/98 和 windows NT 3.51 版和更新版本下執行的程式。

如需啟用工具提示的詳細資訊, 請參閱[Windows 中的工具提示不是衍生自 CFrameWnd](../../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)。

如需使用`CToolTipCtrl`的詳細資訊, 請參閱[控制項](../../mfc/controls-mfc.md)和[使用 CToolTipCtrl](../../mfc/using-ctooltipctrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CToolTipCtrl`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

##  <a name="activate"></a>CToolTipCtrl:: Activate

呼叫此函式可啟動或停用工具提示控制項。

```
void Activate(BOOL bActivate);
```

### <a name="parameters"></a>參數

*bActivate*<br/>
指定是否要啟用或停用工具提示控制項。

### <a name="remarks"></a>備註

如果*bActivate*為 TRUE, 則會啟用控制項;如果為 FALSE, 則會停用。

當工具提示控制項為作用中時, 當游標位於已向控制項註冊的工具上時, 就會出現工具提示資訊。處於非作用中狀態時, 即使游標位於工具上, 工具提示資訊也不會出現。

### <a name="example"></a>範例

  請參閱[CPropertySheet:: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)的範例。

##  <a name="addtool"></a>CToolTipCtrl:: AddTool

向工具提示控制項註冊工具。

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
包含工具文字的字串資源識別碼。

*lpRectTool*<br/>
[矩形](/previous-versions/dd162897\(v=vs.85\))結構的指標, 其中包含工具周框的座標。 座標相對於*pWnd*所識別之視窗的工作區左上角。

*nIDTool*<br/>
工具的識別碼。

*lpszText*<br/>
工具文字的指標。 如果此參數包含 LPSTR_TEXTCALLBACK 值, TTN_NEEDTEXT 通知訊息會移至*pWnd*指向之視窗的父系。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

*LpRectTool*和*nIDTool*參數必須是有效的, 或如果*LpRectTool*是 Null, 則*nIDTool*必須是0。

工具提示控制項可以與一個以上的工具相關聯。 呼叫這個函式以向工具提示控制項註冊工具, 如此一來, 當游標位於工具上時, 就會顯示儲存在工具提示中的資訊。

> [!NOTE]
>  您無法使用`AddTool`將工具提示設定為靜態控制項。

### <a name="example"></a>範例

  請參閱[CPropertySheet:: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)的範例。

##  <a name="adjustrect"></a>CToolTipCtrl:: AdjustRect

在工具提示控制項的文字顯示矩形和其視窗矩形之間轉換。

```
BOOL AdjustRect(
    LPRECT lprc,
    BOOL bLarger = TRUE);
```

### <a name="parameters"></a>參數

*lprc*<br/>
[矩形](/previous-versions/dd162897\(v=vs.85\))結構的指標, 其中包含工具提示視窗矩形或文字顯示矩形。

*bLarger*<br/>
若為 TRUE, 則會使用*lprc*指定文字顯示矩形, 並接收對應的視窗矩形。 如果為 FALSE, 則會使用*lprc*來指定視窗矩形, 並接收對應的文字顯示矩形。

### <a name="return-value"></a>傳回值

如果矩形已成功調整, 則為非零值;否則為0。

### <a name="remarks"></a>備註

此成員函式會從視窗矩形中計算工具提示控制項的文字顯示矩形, 或在顯示指定之文字顯示矩形時所需的工具提示視窗矩形。

此成員函式會執行 Win32 message [TTM_ADJUSTRECT](/windows/desktop/Controls/ttm-adjustrect)的行為, 如 Windows SDK 中所述。

##  <a name="create"></a>CToolTipCtrl:: Create

建立工具提示控制項, 並將它附加至`CToolTipCtrl`物件。

```
virtual BOOL Create(CWnd* pParentWnd, DWORD dwStyle = 0);
```

### <a name="parameters"></a>參數

*pParentWnd*<br/>
指定工具提示控制項的父視窗, 通常是`CDialog`。 不得為 Null。

*dwStyle*<br/>
指定工具提示控制項的樣式。 如需詳細資訊, 請參閱**備註**一節。

### <a name="return-value"></a>傳回值

如果成功建立`CToolTipCtrl`物件, 則為非零, 否則為0。

### <a name="remarks"></a>備註

您可以使用`CToolTipCtrl`兩個步驟來建立。 首先, 呼叫函式來建立`CToolTipCtrl`物件, 然後呼叫`Create`來建立工具提示控制項, `CToolTipCtrl`並將它附加至物件。

*DwStyle*參數可以是[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)的任意組合。 此外, 工具提示控制項有兩個類別特定的樣式:TTS_ALWAYSTIP 和 TTS_NOPREFIX。

|樣式|意義|
|-----------|-------------|
|TTS_ALWAYSTIP|指定當游標位於工具上時, 工具提示就會出現, 不論工具提示控制項的擁有者視窗是作用中或非使用中。 如果沒有此樣式, 則工具提示控制項會在工具的擁有者視窗作用中時出現, 但不會在非使用中時顯示。|
|TTS_NOPREFIX|此樣式可防止系統從字串中去除連字號 (&)。 如果工具提示控制項沒有 TTS_NOPREFIX 樣式, 系統就會自動去除符號字元, 讓應用程式使用與功能表項目相同的字串, 以及工具提示控制項中的文字。|

工具提示控制項具有 [WS_POPUP] 和 [WS_EX_TOOLWINDOW] 視窗樣式, 不論您是否在建立控制項時指定它們。

若要建立具有擴充 windows 樣式的工具提示控制項, 請呼叫[CToolTipCtrl:: CreateEx](#createex) , 而不是`Create`。

### <a name="example"></a>範例

  請參閱[CPropertySheet:: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)的範例。

##  <a name="createex"></a>CToolTipCtrl:: CreateEx

建立控制項 (子視窗), 並將它與`CToolTipCtrl`物件產生關聯。

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwStyle = 0,
    DWORD dwStyleEx = 0);
```

### <a name="parameters"></a>參數

*pParentWnd*<br/>
做為控制項父系之視窗的指標。

*dwStyle*<br/>
指定工具提示控制項的樣式。 如需詳細資訊, 請參閱[建立](#create)的「**備註**」一節。

*dwStyleEx*<br/>
指定所要建立之控制項的延伸樣式。 如需擴充 Windows 樣式的清單, 請參閱 Windows SDK 中[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa)的*dwExStyle*參數。

### <a name="return-value"></a>傳回值

如果成功, 則為非零, 否則為0。

### <a name="remarks"></a>備註

使用`CreateEx`而非來套用擴充的 windows 樣式 (由 Windows 擴充樣式指定于 WS_EX_ 的前面) `Create` 。

##  <a name="ctooltipctrl"></a>CToolTipCtrl:: CToolTipCtrl

建構 `CToolTipCtrl` 物件。

```
CToolTipCtrl();
```

### <a name="remarks"></a>備註

您必須在`Create`建立物件之後呼叫。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#74](../../mfc/codesnippet/cpp/ctooltipctrl-class_1.h)]

##  <a name="deltool"></a>CToolTipCtrl::D elTool

從工具提示控制項支援的工具集合中, 移除*pWnd*和*nIDTool*所指定的工具。

```
void DelTool(
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
包含工具之視窗的指標。

*nIDTool*<br/>
工具的識別碼。

##  <a name="getbubblesize"></a>CToolTipCtrl:: GetBubbleSize

抓取工具提示的大小。

```
CSize GetBubbleSize(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>參數

*lpToolInfo*<br/>
工具提示之[TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa)結構的指標。

### <a name="return-value"></a>傳回值

工具提示的大小。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [TTM_GETBUBBLESIZE](/windows/desktop/Controls/ttm-getbubblesize)的行為, 如 Windows SDK 中所述。

##  <a name="getcurrenttool"></a>CToolTipCtrl:: GetCurrentTool

抓取目前工具提示控制項所顯示之工具提示視窗的大小、位置和文字等資訊。

```
BOOL GetCurrentTool(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*lpToolInfo*|脫銷[TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa)結構的指標, 它會接收目前工具提示視窗的相關資訊。|

### <a name="return-value"></a>傳回值

如果成功取出資訊, 則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[TTM_GETCURRENTTOOL](/windows/desktop/Controls/ttm-getcurrenttool)訊息, 如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會抓取目前工具提示視窗的相關資訊。

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#6](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_2.cpp)]

##  <a name="getdelaytime"></a>CToolTipCtrl:: GetDelayTime

抓取目前為工具提示控制項設定的初始、快顯視窗和 reshow 持續時間。

```
int GetDelayTime(DWORD dwDuration) const;
```

### <a name="parameters"></a>參數

*dwDuration*<br/>
指定將會抓取哪一個 duration 值的旗標。 這個參數可以是下列其中一個值:

- 如果指標在工具的周框中是固定的, TTDT_AUTOPOP 會抓取工具提示視窗保持可見的時間長度。

- TTDT_INITIAL 會在工具提示視窗出現之前, 抓取指標在工具周框中必須保持靜止的時間長度。

- TTDT_RESHOW 會抓取當指標從一個工具移到另一個時, 後續工具提示視窗所需的時間長度。

### <a name="return-value"></a>傳回值

指定的延遲時間 (以毫秒為單位)

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [TTM_GETDELAYTIME](/windows/desktop/Controls/ttm-getdelaytime)的行為, 如 Windows SDK 中所述。

##  <a name="getmargin"></a>CToolTipCtrl:: GetMargin

抓取工具提示視窗的上、左、下和右邊邊界設定。

```
void GetMargin(LPRECT lprc) const;
```

### <a name="parameters"></a>參數

*lprc*<br/>
將接收邊界資訊的結構位址。`RECT` [RECT](/previous-versions/dd162897\(v=vs.85\))結構的成員不會定義周框。 基於此訊息的目的, 結構成員的解讀方式如下:

|成員|表示|
|------------|--------------------|
|`top`|上框線與工具提示文字頂端之間的距離, 以圖元為單位。|
|`left`|左框線和尖端文字左邊端之間的距離, 以圖元為單位。|
|`bottom`|下框線和尖端文字底部之間的距離 (以圖元為單位)。|
|`right`|右框線和尖端文字右端之間的距離 (以圖元為單位)。|

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [TTM_GETMARGIN](/windows/desktop/Controls/ttm-getmargin)的行為, 如 Windows SDK 中所述。

##  <a name="getmaxtipwidth"></a>CToolTipCtrl:: GetMaxTipWidth

抓取工具提示視窗的最大寬度。

```
int GetMaxTipWidth() const;
```

### <a name="return-value"></a>傳回值

工具提示視窗的最大寬度。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [TTM_GETMAXTIPWIDTH](/windows/desktop/Controls/ttm-getmaxtipwidth)的行為, 如 Windows SDK 中所述。

##  <a name="gettext"></a>CToolTipCtrl:: GetText

抓取工具提示控制項為工具維護的文字。

```
void GetText(
    CString& str,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>參數

*str*<br/>
接收工具文字之物件的參考。`CString`

*pWnd*<br/>
包含工具之視窗的指標。

*nIDTool*<br/>
工具的識別碼。

### <a name="remarks"></a>備註

*PWnd*和*nIDTool*參數會識別工具。 如果先前的呼叫`CToolTipCtrl::AddTool`已透過工具提示控制項註冊該工具, 則*str*參數所參考的物件會被指派工具的文字。

##  <a name="gettipbkcolor"></a>CToolTipCtrl:: GetTipBkColor

抓取工具提示視窗中的背景色彩。

```
COLORREF GetTipBkColor() const;
```

### <a name="return-value"></a>傳回值

代表背景色彩的[COLORREF](/windows/desktop/gdi/colorref)值。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [TTM_GETTIPBKCOLOR](/windows/desktop/Controls/ttm-gettipbkcolor)的行為, 如 Windows SDK 中所述。

##  <a name="gettiptextcolor"></a>CToolTipCtrl:: GetTipTextColor

抓取工具提示視窗中的文字色彩。

```
COLORREF GetTipTextColor() const;
```

### <a name="return-value"></a>傳回值

代表文字色彩的[COLORREF](/windows/desktop/gdi/colorref)值。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [TTM_GETTIPTEXTCOLOR](/windows/desktop/Controls/ttm-gettiptextcolor)的行為, 如 Windows SDK 中所述。

##  <a name="gettitle"></a>CToolTipCtrl:: GetTitle

抓取目前工具提示控制項的標題。

```
void GetTitle(PTTGETTITLE pttgt) const;
```

### <a name="parameters"></a>參數

|參數|說明|
|---------------|-----------------|
|*pttgt*|脫銷[TTGETTITLE](/windows/desktop/api/commctrl/ns-commctrl-ttgettitle)結構的指標, 其中包含工具提示控制項的相關資訊。 當這個方法傳回時, [TTGETTITLE](/windows/desktop/api/commctrl/ns-commctrl-ttgettitle)結構的*pszTitle*成員會指向標題的文字。|

### <a name="remarks"></a>備註

這個方法會傳送[TTM_GETTITLE](/windows/desktop/Controls/ttm-gettitle)訊息, 如 Windows SDK 中所述。

##  <a name="gettoolcount"></a>CToolTipCtrl:: GetToolCount

抓取以工具提示控制項註冊的工具計數。

```
int GetToolCount() const;
```

### <a name="return-value"></a>傳回值

使用工具提示控制項註冊的工具計數。

##  <a name="gettoolinfo"></a>CToolTipCtrl:: GetToolInfo

抓取工具提示控制項針對工具所維護的資訊。

```
BOOL GetToolInfo(
    CToolInfo& ToolInfo,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>參數

*ToolInfo*<br/>
接收工具文字之物件的參考。`TOOLINFO`

*pWnd*<br/>
包含工具之視窗的指標。

*nIDTool*<br/>
工具的識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

CToolInfo 所`uId`參考之[TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa)結構的 和成員可識別此工具。`hwnd` 如果已透過先前的呼叫向`AddTool`工具提示控制項註冊該工具, 此`TOOLINFO`結構會填入工具的相關資訊。

##  <a name="hittest"></a>CToolTipCtrl:: HitTest

測試點, 判斷它是否在指定之工具的周框中, 如果是的話, 則抓取工具的相關資訊。

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
`CPoint`物件的指標, 包含要測試之點的座標。

*lpToolInfo*<br/>
[TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa)結構的指標, 其中包含工具的相關資訊。

### <a name="return-value"></a>傳回值

如果點擊測試資訊所指定的點在工具的周框矩形內, 則為非零值;否則為0。

### <a name="remarks"></a>備註

如果此函式傳回非零值, *lpToolInfo*所指向的結構就會填入其所在矩形內的工具資訊。

`TTHITTESTINFO`結構定義如下:

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

   如果點位於工具的周框中, 則指定點的座標。

- `ti`

   此工具的相關資訊。 如需`TOOLINFO`結構的詳細資訊, 請參閱[CToolTipCtrl:: GetToolInfo](#gettoolinfo)。

##  <a name="pop"></a>CToolTipCtrl::P op

從視圖中移除顯示的工具提示視窗。

```
void Pop();
```

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [TTM_POP](/windows/desktop/Controls/ttm-pop)的行為, 如 Windows SDK 中所述。

##  <a name="popup"></a>CToolTipCtrl::P opup

使目前的工具提示控制項顯示在最後一個滑鼠訊息的座標上。

```
void Popup();
```

### <a name="remarks"></a>備註

這個方法會傳送[TTM_POPUP](/windows/desktop/Controls/ttm-popup)訊息, 如 Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會顯示工具提示視窗。

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#7](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_3.cpp)]

##  <a name="relayevent"></a>CToolTipCtrl:: RelayEvent

將滑鼠訊息傳遞至工具提示控制項以進行處理。

```
void RelayEvent(LPMSG lpMsg);
```

### <a name="parameters"></a>參數

*lpMsg*<br/>
包含要轉送之訊息的[MSG](/windows/desktop/api/winuser/ns-winuser-msg)結構的指標。

### <a name="remarks"></a>備註

工具提示控制項只會處理下列訊息, 其會透過以下方式`RelayEvent`傳送給它:

|WM_LBUTTONDOWN|WM_MOUSEMOVE|
|---------------------|-------------------|
|WM_LBUTTONUP|WM_RBUTTONDOWN|
|WM_MBUTTONDOWN|WM_RBUTTONUP|
|WM_MBUTTONUP||

### <a name="example"></a>範例

  請參閱[CPropertySheet:: GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)的範例。

##  <a name="setdelaytime"></a>CToolTipCtrl:: SetDelayTime

設定工具提示控制項的延遲時間。

```
void SetDelayTime(UINT nDelay);

void SetDelayTime(
    DWORD dwDuration,
    int iTime);
```

### <a name="parameters"></a>參數

*nDelay*<br/>
指定新的延遲時間 (以毫秒為單位)。

*dwDuration*<br/>
指定將會抓取哪一個 duration 值的旗標。 如需有效值的描述, 請參閱[CToolTipCtrl:: GetDelayTime](#getdelaytime) 。

*iTime*<br/>
指定的延遲時間 (以毫秒為單位)。

### <a name="remarks"></a>備註

延遲時間是在工具提示視窗出現之前, 游標必須留在工具上的時間長度。 預設的延遲時間為500毫秒。

##  <a name="setmargin"></a>CToolTipCtrl:: Setmargin:

設定工具提示視窗的上、左、下和右邊界。

```
void SetMargin(LPRECT lprc);
```

### <a name="parameters"></a>參數

*lprc*<br/>
包含要設定之邊界資訊的結構位址。`RECT` `RECT`結構的成員不會定義周框。 如需邊界資訊的描述, 請參閱[CToolTipCtrl:: GetMargin](#getmargin) 。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [TTM_SETMARGIN](/windows/desktop/Controls/ttm-setmargin)的行為, 如 Windows SDK 中所述。

##  <a name="setmaxtipwidth"></a>CToolTipCtrl:: Setmaxtipwidth:

設定工具提示視窗的最大寬度。

```
int SetMaxTipWidth(int iWidth);
```

### <a name="parameters"></a>參數

*iWidth*<br/>
要設定的工具提示視窗寬度上限。

### <a name="return-value"></a>傳回值

先前的最大提示寬度。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [TTM_SETMAXTIPWIDTH](/windows/desktop/Controls/ttm-setmaxtipwidth)的行為, 如 Windows SDK 中所述。

##  <a name="settipbkcolor"></a>CToolTipCtrl:: Settipbkcolor:

設定工具提示視窗中的背景色彩。

```
void SetTipBkColor(COLORREF clr);
```

### <a name="parameters"></a>參數

*clr*<br/>
新的背景色彩。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [TTM_SETTIPBKCOLOR](/windows/desktop/Controls/ttm-settipbkcolor)的行為, 如 Windows SDK 中所述。

##  <a name="settiptextcolor"></a>CToolTipCtrl:: Settiptextcolor:

設定工具提示視窗中的文字色彩。

```
void SetTipTextColor(COLORREF clr);
```

### <a name="parameters"></a>參數

*clr*<br/>
新的文字色彩。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [TTM_SETTIPTEXTCOLOR](/windows/desktop/Controls/ttm-settiptextcolor)的行為, 如 Windows SDK 中所述。

##  <a name="settitle"></a>CToolTipCtrl:: SetTitle

將標準圖示和標題字串加入工具提示中。

```
BOOL SetTitle(
    UINT uIcon,
    LPCTSTR lpstrTitle);
```

### <a name="parameters"></a>參數

*uIcon*<br/>
請參閱 *圖示* 中[TTM_SETTITLE](/windows/desktop/Controls/ttm-settitle) Windows SDK 中。

*lpstrTitle*<br/>
標題字串的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式會執行 Win32 message [TTM_SETTITLE](/windows/desktop/Controls/ttm-settitle)的行為, 如 Windows SDK 中所述。

##  <a name="settoolinfo"></a>CToolTipCtrl:: SetToolInfo

設定工具提示為工具維護的資訊。

```
void SetToolInfo(LPTOOLINFO lpToolInfo);
```

### <a name="parameters"></a>參數

*lpToolInfo*<br/>
[TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa)結構的指標, 指定要設定的資訊。

##  <a name="settoolrect"></a>CToolTipCtrl:: SetToolRect

設定工具的新周框。

```
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
[矩形](/previous-versions/dd162897\(v=vs.85\))結構的指標, 指定新的周框。

##  <a name="setwindowtheme"></a>CToolTipCtrl:: SetWindowTheme

設定工具提示視窗的視覺化樣式。

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>參數

*pszSubAppName*<br/>
Unicode 字串的指標, 其中包含要設定的視覺化樣式。

### <a name="return-value"></a>傳回值

不使用傳回值。

### <a name="remarks"></a>備註

此成員函式會模擬[TTM_SETWINDOWTHEME](/windows/desktop/Controls/ttm-setwindowtheme)訊息的功能, 如 Windows SDK 中所述。

##  <a name="update"></a>CToolTipCtrl:: Update

強制重新繪製目前的工具。

```
void Update();
```

##  <a name="updatetiptext"></a>CToolTipCtrl:: UpdateTipText

更新此控制項工具的工具提示文字。

```
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
工具文字的指標。

*pWnd*<br/>
包含工具之視窗的指標。

*nIDTool*<br/>
工具的識別碼。

*nIDText*<br/>
包含工具文字的字串資源識別碼。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CToolBar 類別](../../mfc/reference/ctoolbar-class.md)
