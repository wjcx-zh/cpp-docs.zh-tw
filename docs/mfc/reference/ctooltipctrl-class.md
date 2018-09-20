---
title: CToolTipCtrl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bfb50c707f0e9055d80a91581696981b6a4d6606
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399518"
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
|[CToolTipCtrl::CToolTipCtrl](#ctooltipctrl)|建構 `CToolTipCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CToolTipCtrl::Activate](#activate)|啟用和停用工具提示控制項。|
|[CToolTipCtrl::AddTool](#addtool)|工具提示控制項註冊工具。|
|[CToolTipCtrl::AdjustRect](#adjustrect)|矩形和其視窗矩形，就會顯示工具提示控制項的文字之間的轉換。|
|[CToolTipCtrl::Create](#create)|建立工具提示控制項，並將它附加至`CToolTipCtrl`物件。|
|[CToolTipCtrl::CreateEx](#createex)|使用指定的 Windows 延伸樣式中建立工具提示控制項，並將它附加至`CToolTipCtrl`物件。|
|[CToolTipCtrl::DelTool](#deltool)|從工具提示控制項移除的工具。|
|[CToolTipCtrl::GetBubbleSize](#getbubblesize)|擷取的工具提示的大小。|
|[CToolTipCtrl::GetCurrentTool](#getcurrenttool)|擷取資訊，例如大小、 位置和目前的工具提示控制項顯示之工具提示視窗的文字。|
|[CToolTipCtrl::GetDelayTime](#getdelaytime)|擷取初始、 快顯視窗，以及重新顯示持續時間，目前所設定的工具提示控制項。|
|[CToolTipCtrl::GetMargin](#getmargin)|擷取頂端、 左邊、 底部、 與已為工具提示視窗的左右邊界。|
|[CToolTipCtrl::GetMaxTipWidth](#getmaxtipwidth)|擷取工具提示視窗的最大寬度。|
|[CToolTipCtrl::GetText](#gettext)|擷取維護工具的工具提示控制項的文字。|
|[CToolTipCtrl::GetTipBkColor](#gettipbkcolor)|擷取工具提示視窗中的背景色彩。|
|[CToolTipCtrl::GetTipTextColor](#gettiptextcolor)|擷取工具提示視窗中的文字色彩。|
|[CToolTipCtrl::GetTitle](#gettitle)|擷取目前的工具提示控制項的標題。|
|[CToolTipCtrl::GetToolCount](#gettoolcount)|擷取工具提示控制項所維護的工具的計數。|
|[CToolTipCtrl::GetToolInfo](#gettoolinfo)|擷取工具提示控制項維護工具的相關資訊。|
|[CToolTipCtrl::HitTest](#hittest)|測試點，以判斷它是否在指定之工具的週框矩形內。 如果是的話，擷取工具的相關資訊。|
|[CToolTipCtrl::Pop](#pop)|移除檢視中顯示的工具提示視窗。|
|[CToolTipCtrl::Popup](#popup)|使目前的工具提示控制項顯示在最後一個滑鼠訊息的座標。|
|[Relayevent](#relayevent)|將滑鼠訊息傳遞至 工具提示控制項進行處理。|
|[CToolTipCtrl::SetDelayTime](#setdelaytime)|設定初始、 快顯視窗，並重新顯示工具提示控制項的持續時間。|
|[CToolTipCtrl::SetMargin](#setmargin)|頂端、 左邊、 底部、 與工具提示視窗的左右邊界設定。|
|[CToolTipCtrl::SetMaxTipWidth](#setmaxtipwidth)|設定工具提示視窗的最大寬度。|
|[CToolTipCtrl::SetTipBkColor](#settipbkcolor)|在工具提示視窗中設定的背景色彩。|
|[CToolTipCtrl::SetTipTextColor](#settiptextcolor)|在工具提示視窗中設定的文字色彩。|
|[CToolTipCtrl::SetTitle](#settitle)|將工具提示中的標準圖示和標題的字串。|
|[CToolTipCtrl::SetToolInfo](#settoolinfo)|設定工具提示會維護工具的資訊。|
|[CToolTipCtrl::SetToolRect](#settoolrect)|設定工具的新週框矩形。|
|[CToolTipCtrl::SetWindowTheme](#setwindowtheme)|設定工具提示視窗的視覺化樣式。|
|[CToolTipCtrl::Update](#update)|強制重新繪製目前的工具。|
|[CToolTipCtrl::UpdateTipText](#updatetiptext)|設定工具的工具提示文字。|

## <a name="remarks"></a>備註

「 工具 」 也可以是視窗，例如子視窗或控制項或在視窗的工作區中，應用程式定義的矩形區域。 工具提示大部分時間都在隱藏狀態，只有在使用者將游標放置在工具上並停留約二分之一秒時才會顯現。 工具提示會出現在接近資料指標，並在使用者按下滑鼠按鈕，或移動資料指標關閉此工具時，就會消失。

`CToolTipCtrl` 提供控制項的初始時間和持續時間的工具提示中，功能的工具提示文字、 本身，工具提示視窗的寬度和工具提示的背景和文字色彩的邊界寬度。 一個工具提示控制項可以提供多個工具的資訊。

`CToolTipCtrl` 類別提供 Windows 通用工具提示控制項的功能。 這個控制項 (並因此`CToolTipCtrl`類別) 僅適用於 Windows 95/98 和 Windows NT 的版本 3.51 下執行的程式和更新版本。

如需啟用工具提示的詳細資訊，請參閱[在 Windows 中的工具提示不會衍生自 cframewnd 之](../../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)。

如需有關使用`CToolTipCtrl`，請參閱 <<c2> [ 控制項](../../mfc/controls-mfc.md)並[使用 CToolTipCtrl](../../mfc/using-ctooltipctrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CToolTipCtrl`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

##  <a name="activate"></a>  CToolTipCtrl::Activate

呼叫此函式可啟用或停用工具提示控制項。

```
void Activate(BOOL bActivate);
```

### <a name="parameters"></a>參數

*bActivate*<br/>
指定要啟用或停用工具提示控制項。

### <a name="remarks"></a>備註

如果*bActivate*為 TRUE 時，在啟動控制項; 如果為 FALSE，它會停用。

在游標位於工具註冊與控制項上時，工具提示控制項使用中時，會出現工具提示資訊非使用中時，工具提示資訊沒有出現，即使當游標位於工具上。

### <a name="example"></a>範例

  範例，請參閱[CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)。

##  <a name="addtool"></a>  CToolTipCtrl::AddTool

工具提示控制項註冊工具。

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
包含此工具視窗的指標。

*nIDText*<br/>
包含此工具的文字的字串資源的識別碼。

*lpRectTool*<br/>
指標[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構，其中包含工具的座標的週框矩形。 座標是相對於視窗所識別的工作區的左上角*pWnd*。

*nIDTool*<br/>
此工具的識別碼。

*lpszText*<br/>
此工具的文字指標。 如果這個參數會包含值 LPSTR_TEXTCALLBACK，TTN_NEEDTEXT 通知訊息請移至 視窗的父代的*pWnd*指向。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

*LpRectTool*並*nIDTool*參數必須是有效的或者如果*lpRectTool*是 NULL， *nIDTool*必須是 0。

工具提示控制項可以與一個以上的工具相關聯。 呼叫此函式可使用工具提示控制項，註冊工具，因此在游標位於工具上時，會顯示工具提示中所儲存的資訊。

> [!NOTE]
>  您無法將工具提示設定為靜態控制項，使用`AddTool`。

### <a name="example"></a>範例

  範例，請參閱[CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)。

##  <a name="adjustrect"></a>  CToolTipCtrl::AdjustRect

矩形和其視窗矩形，就會顯示工具提示控制項的文字之間的轉換。

```
BOOL AdjustRect(
    LPRECT lprc,
    BOOL bLarger = TRUE);
```

### <a name="parameters"></a>參數

*lprc*<br/>
指標[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構，其中包含工具提示視窗矩形或文字的顯示矩形。

*bLarger*<br/>
如果為 TRUE， *lprc*用來指定文字顯示矩形，並且會收到對應的視窗矩形。 如果為 FALSE， *lprc*用來指定視窗的矩形中，並且會收到對應的文字顯示矩形。

### <a name="return-value"></a>傳回值

如果已成功調整矩形; 時，非零值。否則為 0。

### <a name="remarks"></a>備註

此成員函式會計算從其視窗矩形或顯示指定的文字顯示矩形所需的工具提示視窗矩形的工具提示控制項的文字顯示矩形。

此成員函式實作的 Win32 訊息的行為[TTM_ADJUSTRECT](/windows/desktop/Controls/ttm-adjustrect)、 Windows SDK 中所述。

##  <a name="create"></a>  CToolTipCtrl::Create

建立工具提示控制項，並將它附加至`CToolTipCtrl`物件。

```
virtual BOOL Create(CWnd* pParentWnd, DWORD dwStyle = 0);
```

### <a name="parameters"></a>參數

*pParentWnd*<br/>
指定工具提示控制項的父視窗，通常`CDialog`。 它必須不是 NULL。

*cheaderctrl:: Create*<br/>
指定工具提示控制項的樣式。 請參閱**備註**節的詳細資訊。

### <a name="return-value"></a>傳回值

非零`CToolTipCtrl`物件已成功建立，否則為 0。

### <a name="remarks"></a>備註

您建構`CToolTipCtrl`兩個步驟。 首先，呼叫建構函式來建構`CToolTipCtrl`物件，然後再呼叫`Create`建立工具提示控制項，並將其附加至`CToolTipCtrl`物件。

*Cheaderctrl:: Create*參數可以是任何組合[的視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)。 此外，工具提示控制項有兩種類別的特定樣式： TTS_ALWAYSTIP 和 TTS_NOPREFIX。

|樣式|意義|
|-----------|-------------|
|TTS_ALWAYSTIP|指定資料指標上的工具，無論工具提示控制項的主控視窗是作用中或非作用中時，會出現工具提示。 沒有這個樣式，當工具的擁有者視窗是作用中，但不是當它為非作用中，會出現工具提示控制項。|
|TTS_NOPREFIX|此樣式會防止系統移除連字號 (&) 字元從字串。 如果工具提示控制項並沒有 TTS_NOPREFIX 樣式，系統會自動移除連字號字元，可讓應用程式使用相同的字串，為這兩個功能表項目，以及在工具提示控制項的文字。|

工具提示控制項有 WS_POPUP 和 WS_EX_TOOLWINDOW 視窗樣式，無論您是否指定它們建立控制項時。

若要建立擴充的 windows 樣式工具提示控制項，呼叫[CToolTipCtrl::CreateEx](#createex)而不是`Create`。

### <a name="example"></a>範例

  範例，請參閱[CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)。

##  <a name="createex"></a>  CToolTipCtrl::CreateEx

建立控制項 （子視窗） 和其關聯`CToolTipCtrl`物件。

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwStyle = 0,
    DWORD dwStyleEx = 0);
```

### <a name="parameters"></a>參數

*pParentWnd*<br/>
是控制項的父視窗的指標。

*cheaderctrl:: Create*<br/>
指定工具提示控制項的樣式。 請參閱**備註**一節[建立](#create)如需詳細資訊。

*dwStyleEx*<br/>
指定正在建立之控制項的延伸的樣式。 如需延伸的 Windows 樣式的清單，請參閱 < *dwExStyle*參數[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) Windows SDK 中。

### <a name="return-value"></a>傳回值

非零值，如果成功則為 0。

### <a name="remarks"></a>備註

使用`CreateEx`而非`Create`套用延伸的 Windows 樣式，由 Windows 延伸的樣式前置詞**WS_EX_**。

##  <a name="ctooltipctrl"></a>  CToolTipCtrl::CToolTipCtrl

建構 `CToolTipCtrl` 物件。

```
CToolTipCtrl();
```

### <a name="remarks"></a>備註

您必須呼叫`Create`之後建構的物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#74](../../mfc/codesnippet/cpp/ctooltipctrl-class_1.h)]

##  <a name="deltool"></a>  CToolTipCtrl::DelTool

移除所指定的工具*pWnd*並*nIDTool*從支援的工具提示控制項的工具集合。

```
void DelTool(
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
包含此工具視窗的指標。

*nIDTool*<br/>
此工具的識別碼。

##  <a name="getbubblesize"></a>  CToolTipCtrl::GetBubbleSize

擷取的工具提示的大小。

```
CSize GetBubbleSize(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>參數

*lpToolInfo*<br/>
指標的工具提示[TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa)結構。

### <a name="return-value"></a>傳回值

工具提示的大小。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[TTM_GETBUBBLESIZE](/windows/desktop/Controls/ttm-getbubblesize)、 Windows SDK 中所述。

##  <a name="getcurrenttool"></a>  CToolTipCtrl::GetCurrentTool

擷取資訊，例如大小、 位置和目前的工具提示控制項所顯示的工具提示視窗的文字。

```
BOOL GetCurrentTool(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*lpToolInfo*|[out]指標[TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa)接收目前的工具提示視窗的相關資訊的結構。|

### <a name="return-value"></a>傳回值

如果已成功; 擷取的資訊，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[TTM_GETCURRENTTOOL](/windows/desktop/Controls/ttm-getcurrenttool)訊息，Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會擷取目前的工具提示視窗的相關資訊。

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#6](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_2.cpp)]

##  <a name="getdelaytime"></a>  CToolTipCtrl::GetDelayTime

擷取初始、 快顯視窗，並重新顯示工具提示控制項的目前設定的期間。

```
int GetDelayTime(DWORD dwDuration) const;
```

### <a name="parameters"></a>參數

*dwDuration*<br/>
會擷取指定的持續時間值的旗標。 這個參數可以是下列值之一：

- TTDT_AUTOPOP 擷取的工具提示視窗的時間長度仍會顯示如果指標位於靜態工具的週框矩形內。

- TTDT_INITIAL 擷取顯示的指標必須保持靜止在工具提示視窗之前的工具的週框矩形內的時間長度。

- TTDT_RESHOW 擷取的後續工具提示視窗，顯示為指標所花費的時間長度移動兩種工具到另一個。

### <a name="return-value"></a>傳回值

指定的延遲時間 （毫秒）

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[TTM_GETDELAYTIME](/windows/desktop/Controls/ttm-getdelaytime)、 Windows SDK 中所述。

##  <a name="getmargin"></a>  CToolTipCtrl::GetMargin

擷取頂端、 左邊、 底部、 與設定工具提示視窗的左右邊界。

```
void GetMargin(LPRECT lprc) const;
```

### <a name="parameters"></a>參數

*lprc*<br/>
位址`RECT`結構，將會收到邊界資訊。 成員[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構未定義的周框。 此訊息，請以結構成員解譯，如下所示：

|成員|表示法|
|------------|--------------------|
|`top`|上框線和工具提示文字，像素為單位的頂端之間的距離。|
|`left`|左的框線和左的提示文字，像素為單位的結尾之間的距離。|
|`bottom`|下框線和像素為單位的提示文字的底部之間的距離。|
|`right`|右框線和右端的像素為單位的提示文字之間的距離。|

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[TTM_GETMARGIN](/windows/desktop/Controls/ttm-getmargin)、 Windows SDK 中所述。

##  <a name="getmaxtipwidth"></a>  CToolTipCtrl::GetMaxTipWidth

擷取工具提示視窗的最大寬度。

```
int GetMaxTipWidth() const;
```

### <a name="return-value"></a>傳回值

工具提示 視窗的最大寬度。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[TTM_GETMAXTIPWIDTH](/windows/desktop/Controls/ttm-getmaxtipwidth)、 Windows SDK 中所述。

##  <a name="gettext"></a>  CToolTipCtrl::GetText

擷取維護工具的工具提示控制項的文字。

```
void GetText(
    CString& str,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>參數

*str*<br/>
若要參考`CString`接收工具的文字物件。

*pWnd*<br/>
包含此工具視窗的指標。

*nIDTool*<br/>
此工具的識別碼。

### <a name="remarks"></a>備註

*PWnd*並*nIDTool*參數識別的工具。 如果該工具先前註冊與前一個呼叫透過工具提示控制項`CToolTipCtrl::AddTool`，所參考的物件*str*參數被指派為工具的文字。

##  <a name="gettipbkcolor"></a>  CToolTipCtrl::GetTipBkColor

擷取工具提示視窗中的背景色彩。

```
COLORREF GetTipBkColor() const;
```

### <a name="return-value"></a>傳回值

A [COLORREF](/windows/desktop/gdi/colorref)值，表示背景色彩。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[TTM_GETTIPBKCOLOR](/windows/desktop/Controls/ttm-gettipbkcolor)、 Windows SDK 中所述。

##  <a name="gettiptextcolor"></a>  CToolTipCtrl::GetTipTextColor

擷取工具提示視窗中的文字色彩。

```
COLORREF GetTipTextColor() const;
```

### <a name="return-value"></a>傳回值

A [COLORREF](/windows/desktop/gdi/colorref)值，表示文字色彩。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[TTM_GETTIPTEXTCOLOR](/windows/desktop/Controls/ttm-gettiptextcolor)、 Windows SDK 中所述。

##  <a name="gettitle"></a>  CToolTipCtrl::GetTitle

擷取目前的工具提示控制項的標題。

```
void GetTitle(PTTGETTITLE pttgt) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*pttgt*|[out]指標[TTGETTITLE](/windows/desktop/api/commctrl/ns-commctrl-_ttgettitle)結構，其中包含工具提示控制項的相關資訊。 當這個方法傳回時， *pszTitle*隸屬[TTGETTITLE](/windows/desktop/api/commctrl/ns-commctrl-_ttgettitle)結構標題的文字點。|

### <a name="remarks"></a>備註

這個方法會傳送[TTM_GETTITLE](/windows/desktop/Controls/ttm-gettitle)訊息，Windows SDK 中所述。

##  <a name="gettoolcount"></a>  CToolTipCtrl::GetToolCount

擷取工具提示控制項註冊工具的計數。

```
int GetToolCount() const;
```

### <a name="return-value"></a>傳回值

工具提示控制項註冊工具的計數。

##  <a name="gettoolinfo"></a>  CToolTipCtrl::GetToolInfo

擷取工具提示控制項維護工具的相關資訊。

```
BOOL GetToolInfo(
    CToolInfo& ToolInfo,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>參數

*ToolInfo*<br/>
若要參考`TOOLINFO`接收工具的文字物件。

*pWnd*<br/>
包含此工具視窗的指標。

*nIDTool*<br/>
此工具的識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

`hwnd`並`uId`的成員[TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa)所參考的結構*CToolInfo*識別的工具。 如果工具提示控制項，透過由先前呼叫尚未註冊，此工具`AddTool`，則`TOOLINFO`結構填滿工具的相關資訊。

##  <a name="hittest"></a>  CToolTipCtrl::HitTest

測試點，以判斷它是否在指定之工具的週框矩形內，並可能的話，擷取工具的相關資訊。

```
BOOL HitTest(
    CWnd* pWnd,
    CPoint pt,
    LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>參數

*pWnd*<br/>
包含此工具視窗的指標。

*太平洋時間*<br/>
指標`CPoint`物件，其中包含要測試點的座標。

*lpToolInfo*<br/>
指標[TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa)結構，其中包含工具的相關資訊。

### <a name="return-value"></a>傳回值

如果指定的點擊測試資訊的點工具的週框矩形內，非零值。否則為 0。

### <a name="remarks"></a>備註

如果此函式會傳回非零值，結構所指*lpToolInfo*填滿的矩形內的這個點位於工具 上的資訊。

`TTHITTESTINFO`結構定義，如下所示：

```cpp
typedef struct _TT_HITTESTINFO { // tthti
    HWND hwnd;   // handle of tool or window with tool
    POINT pt;    // client coordinates of point to test
    TOOLINFO ti; // receives information about the tool
} TTHITTESTINFO, FAR * LPHITTESTINFO;
```

- `hwnd`

   指定工具的控制代碼。

- `pt`

   指定點的座標，如果端點在工具中的週框矩形。

- `ti`

   此工具的相關資訊。 如需詳細資訊`TOOLINFO`結構，請參閱[CToolTipCtrl::GetToolInfo](#gettoolinfo)。

##  <a name="pop"></a>  CToolTipCtrl::Pop

移除檢視中顯示的工具提示視窗。

```
void Pop();
```

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[TTM_POP](/windows/desktop/Controls/ttm-pop)、 Windows SDK 中所述。

##  <a name="popup"></a>  CToolTipCtrl::Popup

使目前的工具提示控制項顯示在最後一個滑鼠訊息的座標。

```
void Popup();
```

### <a name="remarks"></a>備註

這個方法會傳送[TTM_POPUP](/windows/desktop/Controls/ttm-popup)訊息，Windows SDK 中所述。

### <a name="example"></a>範例

下列程式碼範例會顯示工具提示視窗。

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#7](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_3.cpp)]

##  <a name="relayevent"></a>  Relayevent

將滑鼠訊息傳遞至 工具提示控制項進行處理。

```
void RelayEvent(LPMSG lpMsg);
```

### <a name="parameters"></a>參數

*lpMsg*<br/>
指標[MSG](https://msdn.microsoft.com/library/windows/desktop/ms644958)結構，其中包含要轉送的訊息。

### <a name="remarks"></a>備註

工具提示控制項只會處理下列訊息，傳送給它的`RelayEvent`:

|WM_LBUTTONDOWN|WM_MOUSEMOVE|
|---------------------|-------------------|
|WM_LBUTTONUP|WM_RBUTTONDOWN|
|WM_MBUTTONDOWN|WM_RBUTTONUP|
|WM_MBUTTONUP||

### <a name="example"></a>範例

  範例，請參閱[CPropertySheet::GetTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)。

##  <a name="setdelaytime"></a>  CToolTipCtrl::SetDelayTime

設定工具提示控制項的延遲時間。

```
void SetDelayTime(UINT nDelay);


void SetDelayTime(
    DWORD dwDuration,
    int iTime);
```

### <a name="parameters"></a>參數

*nDelay*<br/>
指定新的延遲時間，以毫秒為單位。

*dwDuration*<br/>
會擷取指定的持續時間值的旗標。 請參閱[CToolTipCtrl::GetDelayTime](#getdelaytime)如需有效值的描述。

*iTime*<br/>
指定的延遲時間 （毫秒）。

### <a name="remarks"></a>備註

延遲時的工具提示視窗出現之前，將必須保留工具的資料指標的時間長度。 預設的延遲時間為 500 毫秒。

##  <a name="setmargin"></a>  CToolTipCtrl::SetMargin

頂端、 左邊、 底部、 與工具提示視窗的左右邊界設定。

```
void SetMargin(LPRECT lprc);
```

### <a name="parameters"></a>參數

*lprc*<br/>
位址`RECT`結構，其中包含要設定邊界資訊。 成員`RECT`結構未定義的周框。 請參閱[CToolTipCtrl::GetMargin](#getmargin)邊界資訊的說明。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[TTM_SETMARGIN](/windows/desktop/Controls/ttm-setmargin)、 Windows SDK 中所述。

##  <a name="setmaxtipwidth"></a>  CToolTipCtrl::SetMaxTipWidth

設定工具提示視窗的最大寬度。

```
int SetMaxTipWidth(int iWidth);
```

### <a name="parameters"></a>參數

*iWidth*<br/>
若要設定最大的工具提示視窗寬度。

### <a name="return-value"></a>傳回值

先前的最大秘訣寬度。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[TTM_SETMAXTIPWIDTH](/windows/desktop/Controls/ttm-setmaxtipwidth)、 Windows SDK 中所述。

##  <a name="settipbkcolor"></a>  CToolTipCtrl::SetTipBkColor

在工具提示視窗中設定的背景色彩。

```
void SetTipBkColor(COLORREF clr);
```

### <a name="parameters"></a>參數

*clr*<br/>
新的背景色彩。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[TTM_SETTIPBKCOLOR](/windows/desktop/Controls/ttm-settipbkcolor)、 Windows SDK 中所述。

##  <a name="settiptextcolor"></a>  CToolTipCtrl::SetTipTextColor

在工具提示視窗中設定的文字色彩。

```
void SetTipTextColor(COLORREF clr);
```

### <a name="parameters"></a>參數

*clr*<br/>
新的文字色彩。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[TTM_SETTIPTEXTCOLOR](/windows/desktop/Controls/ttm-settiptextcolor)、 Windows SDK 中所述。

##  <a name="settitle"></a>  CToolTipCtrl::SetTitle

將工具提示中的標準圖示和標題的字串。

```
BOOL SetTitle(
    UINT uIcon,
    LPCTSTR lpstrTitle);
```

### <a name="parameters"></a>參數

*uIcon*<br/>
請參閱* 圖示*中[TTM_SETTITLE](/windows/desktop/Controls/ttm-settitle) Windows SDK 中。

*lpstrTitle*<br/>
標題字串的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函式實作的 Win32 訊息的行為[TTM_SETTITLE](/windows/desktop/Controls/ttm-settitle)、 Windows SDK 中所述。

##  <a name="settoolinfo"></a>  CToolTipCtrl::SetToolInfo

設定工具提示會維護工具的資訊。

```
void SetToolInfo(LPTOOLINFO lpToolInfo);
```

### <a name="parameters"></a>參數

*lpToolInfo*<br/>
指標[TOOLINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtoolinfoa)結構，指定要設定的資訊。

##  <a name="settoolrect"></a>  CToolTipCtrl::SetToolRect

設定工具的新週框矩形。

```
void SetToolRect(
    CWnd* pWnd,
    UINT_PTR nIDTool,
    LPCRECT lpRect);
```

### <a name="parameters"></a>參數

*pWnd*<br/>
包含此工具視窗的指標。

*nIDTool*<br/>
此工具的識別碼。

*lpRect*<br/>
指標[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構，指定新的週框矩形。

##  <a name="setwindowtheme"></a>  CToolTipCtrl::SetWindowTheme

設定工具提示視窗的視覺化樣式。

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>參數

*pszSubAppName*<br/>
包含要設定的視覺化樣式的 Unicode 字串指標。

### <a name="return-value"></a>傳回值

不會使用傳回的值。

### <a name="remarks"></a>備註

此成員函式會模擬[TTM_SETWINDOWTHEME](/windows/desktop/Controls/ttm-setwindowtheme)訊息、 Windows SDK 中所述。

##  <a name="update"></a>  CToolTipCtrl::Update

強制重新繪製目前的工具。

```
void Update();
```

##  <a name="updatetiptext"></a>  CToolTipCtrl::UpdateTipText

更新這個控制項工具的工具提示文字。

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
此工具的文字指標。

*pWnd*<br/>
包含此工具視窗的指標。

*nIDTool*<br/>
此工具的識別碼。

*nIDText*<br/>
包含此工具的文字的字串資源的識別碼。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CToolBar 類別](../../mfc/reference/ctoolbar-class.md)
