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
ms.openlocfilehash: fdf91549fd1b911de3af82bb940b92fe5e220b92
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365109"
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
|[CToolTipctrl::CToolTipCtrl](#ctooltipctrl)|建構 `CToolTipCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CToolTipCtrl::啟動](#activate)|啟動並停用工具尖端控制項。|
|[CToolTipctrl::新增工具](#addtool)|使用工具尖端控制程式註冊工具。|
|[CToolTipctrl::調整](#adjustrect)|在工具提示控制項的文本顯示矩形及其視窗矩形之間進行轉換。|
|[CToolTipCtrl::建立](#create)|創建工具尖端控制件並將其附加到`CToolTipCtrl`物件。|
|[CToolTipCtrl::創建Ex](#createex)|使用指定的 Windows 擴充樣式創建工具提示控制項並將`CToolTipCtrl`其附加到 物件。|
|[CToolTipCtrl::DelTool](#deltool)|從工具尖端控制項中移除工具。|
|[CToolTipctrl::取得泡泡大小](#getbubblesize)|檢索工具提示的大小。|
|[CToolTipCtrl::取得電流工具](#getcurrenttool)|檢索目前工具提示控制項顯示的工具提示視窗的大小、位置和文字等資訊。|
|[CToolTipCtrl::取得延遲時間](#getdelaytime)|檢索目前為工具提示控制項設定的初始、彈出視窗和重展持續時間。|
|[CToolTipctrl::獲取保證金](#getmargin)|檢索為工具提示視窗設置的上邊、左邊、下和右邊距。|
|[CToolTipctrl::取得最大提示寬度](#getmaxtipwidth)|檢索工具提示視窗的最大寬度。|
|[CToolTipctrl::取得文字](#gettext)|檢索工具尖端控制項為工具維護的文本。|
|[CToolTipCtrl::取得提示BkColor](#gettipbkcolor)|檢索工具提示視窗中的背景顏色。|
|[CToolTipCtrl::取得提示文字顏色](#gettiptextcolor)|檢索工具提示視窗中的文字顏色。|
|[CToolTipCtrl::取得標題](#gettitle)|檢索目前工具提示控件的標題。|
|[CToolTipCtrl::取得工具計數](#gettoolcount)|檢索工具尖端控件維護的工具計數。|
|[CToolTipctrl::取得工具資訊](#gettoolinfo)|檢索工具尖端控件維護的工具的資訊。|
|[CToolTipctrl:hitTest](#hittest)|測試點以確定它是否在給定工具的邊界矩形內。 如果是,則檢索有關該工具的資訊。|
|[CToolTipCtrl::Pop](#pop)|從檢視中刪除顯示的工具提示視窗。|
|[CToolTipCtrl::P](#popup)|使當前 ToolTip 控制件顯示在最後一個滑鼠訊息的座標處。|
|[CToolTipCtrl::接力事件](#relayevent)|將滑鼠訊息傳遞到工具提示控制項進行處理。|
|[CToolTipctrl::設定延遲時間](#setdelaytime)|設定工具提示控制件的初始、彈出視窗和重展持續時間。|
|[CToolTipctrl::設定邊緣](#setmargin)|設置工具尖端視窗的上邊、左邊、下和右邊距。|
|[CToolTipctrl::設定最大提示寬度](#setmaxtipwidth)|設置工具尖端視窗的最大寬度。|
|[CToolTipctrl::SetTipBkColor](#settipbkcolor)|在工具提示視窗中設定背景顏色。|
|[CToolTipctrl::設定提示文字顏色](#settiptextcolor)|在工具提示視窗中設定文字顏色。|
|[CToolTipctrl::設定標題](#settitle)|將標準圖示和標題字串添加到工具提示。|
|[CToolTipctrl::設定工具資訊](#settoolinfo)|設置工具提示為工具維護的資訊。|
|[CToolTipctrl::設定工具重新](#settoolrect)|為工具設置新的邊界矩形。|
|[CToolTipctrl::設定視窗主題](#setwindowtheme)|設置工具提示視窗的視覺樣式。|
|[CToolTipCtrl::更新](#update)|強制重繪當前工具。|
|[CToolTipctrl::更新提示文字](#updatetiptext)|設定工具的工具提示文字。|

## <a name="remarks"></a>備註

工具"是視窗(如子視窗或控制項)或視窗工作區中應用程式定義的矩形區域。 工具提示大部分時間都在隱藏狀態，只有在使用者將游標放置在工具上並停留約二分之一秒時才會顯現。 工具提示顯示在游標附近,當用戶按下滑鼠按鈕或將游標移出工具時,工具提示將消失。

`CToolTipCtrl`提供用於控制工具提示的初始時間和持續時間、刀具尖端文本周圍的邊距寬度、工具提示視窗本身的寬度以及工具提示的背景和文本顏色的功能。 一個工具提示控制項可以提供多個工具的資訊。

`CToolTipCtrl` 類別提供 Windows 通用工具提示控制項的功能。 此控制項(因此類別`CToolTipCtrl`)僅適用於在 Windows 95/98 和 Windows NT 版本 3.51 及更高版本下運行的程式。

有關啟用工具提示的詳細資訊,請參閱[Windows 中的工具提示,而不是從 CFrameWnd 派生](../../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)的 。

有關`CToolTipCtrl`使用的詳細資訊,請參閱[控制項](../../mfc/controls-mfc.md)[和使用 CToolTipCtrl](../../mfc/using-ctooltipctrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CToolTipCtrl`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

## <a name="ctooltipctrlactivate"></a><a name="activate"></a>CToolTipCtrl::啟動

調用此函數以啟動或停用工具尖端控制項。

```
void Activate(BOOL bActivate);
```

### <a name="parameters"></a>參數

*b 啟動*<br/>
指定是啟動還是停用工具尖端控制項。

### <a name="remarks"></a>備註

如果 bActivate 為 TRUE,則該控件將啟動;如果*bActivate*為 TRUE,則該控件將啟動該控件。如果 FALSE,則將其停用。

當工具尖端控件處於活動狀態時,當游標位於與控制項一起註冊的工具上時,將顯示工具提示資訊;當它處於非活動狀態時,即使游標位於工具上,也不會顯示工具提示資訊。

### <a name="example"></a>範例

  請參閱[CPropertySheet 的範例:getTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)。

## <a name="ctooltipctrladdtool"></a><a name="addtool"></a>CToolTipctrl::新增工具

使用工具尖端控制程式註冊工具。

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

*pwnd*<br/>
指向包含工具的視窗的指標。

*nIDText*<br/>
包含工具文字的字串資源的識別碼。

*lpRectTool*<br/>
指向包含工具邊界矩形座標的[RECT](/previous-versions/dd162897\(v=vs.85\))結構的指標。 座標相對於*pWnd*標識的視窗的工作區的左上角。

*nIDTool*<br/>
工具的識別碼。

*lpszText*<br/>
指向工具的文字的指標。 如果此參數包含值LPSTR_TEXTCALLBACK,TTN_NEEDTEXT通知消息將轉到*pwnd*指向的視窗的父級。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

*lpRectTool*和*nIDTool*參數必須都有效,或者如果*lpRectTool*為 NULL,*則 nIDTool*必須為 0。

工具尖端控制項可以與多個工具關聯。 呼叫此函式以使用工具尖端控制程式註冊工具,以便在游標位於工具上時顯示工具提示中儲存的資訊。

> [!NOTE]
> 不能使用`AddTool`將工具提示設置為靜態控制項。

### <a name="example"></a>範例

  請參閱[CPropertySheet 的範例:getTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)。

## <a name="ctooltipctrladjustrect"></a><a name="adjustrect"></a>CToolTipctrl::調整

在工具提示控制項的文本顯示矩形及其視窗矩形之間進行轉換。

```
BOOL AdjustRect(
    LPRECT lprc,
    BOOL bLarger = TRUE);
```

### <a name="parameters"></a>參數

*利赫浦*<br/>
指向保存工具提示視窗矩形或文本顯示矩形的[RECT](/previous-versions/dd162897\(v=vs.85\))結構的指標。

*b 更大*<br/>
如果為 TRUE,*則 lprc*用於指定文本顯示矩形,並接收相應的視窗矩形。 如果 FALSE,*則 lprc*用於指定視窗矩形,並且它接收相應的文本顯示矩形。

### <a name="return-value"></a>傳回值

如果矩形已成功調整,則非零;否則 0。

### <a name="remarks"></a>備註

此成員函數從視窗矩形計算工具提示控件的文本顯示矩形,或顯示指定文本顯示矩形所需的工具尖端視窗矩形。

此成員函數實現 Win32 消息[TTM_ADJUSTRECT](/windows/win32/Controls/ttm-adjustrect)的行為,如 Windows SDK 中所述。

## <a name="ctooltipctrlcreate"></a><a name="create"></a>CToolTipCtrl::建立

創建工具尖端控制件並將其附加到`CToolTipCtrl`物件。

```
virtual BOOL Create(CWnd* pParentWnd, DWORD dwStyle = 0);
```

### <a name="parameters"></a>參數

*pparentwnd*<br/>
指定工具提示控制檔的父視窗(通常為`CDialog`。 它不得為 NULL。

*dwStyle*<br/>
指定工具尖端控制件的樣式。 有關詳細資訊,請參閱**備註**部分。

### <a name="return-value"></a>傳回值

如果成功創建物件`CToolTipCtrl`,則非零;否則 0。

### <a name="remarks"></a>備註

在兩個步驟`CToolTipCtrl`中構造 一個。 首先,調用構造函數構造`CToolTipCtrl`物件,然後調`Create`用 以創建工具提示控件並將其`CToolTipCtrl`附加到 物件。

*dwStyle*參數可以是[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)的任意組合。 此外,工具提示控件具有兩種特定於類的樣式:TTS_ALWAYSTIP和TTS_NOPREFIX。

|Style|意義|
|-----------|-------------|
|TTS_ALWAYSTIP|指定游標位於工具上時將顯示工具提示,而不考慮工具提示控制件的所有者視窗是活動還是非活動。 如果沒有此樣式,工具頭控件在工具的擁有者視窗處於活動狀態時顯示,但在工具處於非活動狀態時不會顯示。|
|TTS_NOPREFIX|此樣式可防止系統從字串中剝離安培(&)字元。 如果工具提示控件沒有TTS_NOPREFIX樣式,系統會自動剝離 ampersand 字元,允許應用程式使用與功能表項和工具提示控制項中的文本相同的字串。|

工具提示控制項具有WS_POPUP和WS_EX_TOOLWINDOW視窗樣式,而不管在創建控制項時是否指定它們。

要建立式延伸視窗樣式的工具提示控制項,請致電[CToolTipCtrl::createEx](#createex)而不是`Create`。

### <a name="example"></a>範例

  請參閱[CPropertySheet 的範例:getTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)。

## <a name="ctooltipctrlcreateex"></a><a name="createex"></a>CToolTipCtrl::創建Ex

創建控制項(子視窗)並將其與`CToolTipCtrl`物件關聯。

```
virtual BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwStyle = 0,
    DWORD dwStyleEx = 0);
```

### <a name="parameters"></a>參數

*pparentwnd*<br/>
指向控件的父視窗的指標。

*dwStyle*<br/>
指定工具尖端控制件的樣式。 有關詳細資訊,請參閱["創建](#create)**"的備註**部分。

*dwStyleEx*<br/>
指定要創建的控制項的擴充樣式。 有關擴展 Windows 樣式的清單,請參閱 Windows SDK 中[創建 WindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*參數。

### <a name="return-value"></a>傳回值

如果成功,則為非零,否則為 0。

### <a name="remarks"></a>備註

使用`CreateEx``Create`而不是應用擴展的 Windows 樣式,由 Windows 擴充樣式前言**WS_EX_** 指定。

## <a name="ctooltipctrlctooltipctrl"></a><a name="ctooltipctrl"></a>CToolTipctrl::CToolTipCtrl

建構 `CToolTipCtrl` 物件。

```
CToolTipCtrl();
```

### <a name="remarks"></a>備註

構造對象`Create`後 必須調用。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#74](../../mfc/codesnippet/cpp/ctooltipctrl-class_1.h)]

## <a name="ctooltipctrldeltool"></a><a name="deltool"></a>CToolTipCtrl::DelTool

從工具尖端控制項支援的工具集合中刪除*pWnd*和*nIDTool*指定的工具。

```
void DelTool(
    CWnd* pWnd,
    UINT_PTR nIDTool = 0);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
指向包含工具的視窗的指標。

*nIDTool*<br/>
工具的識別碼。

## <a name="ctooltipctrlgetbubblesize"></a><a name="getbubblesize"></a>CToolTipctrl::取得泡泡大小

檢索工具提示的大小。

```
CSize GetBubbleSize(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>參數

*lpToolInfo*<br/>
指向工具提示[TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa)結構的指標。

### <a name="return-value"></a>傳回值

工具提示的大小。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[TTM_GETBUBBLESIZE](/windows/win32/Controls/ttm-getbubblesize)的行為,如 Windows SDK 中所述。

## <a name="ctooltipctrlgetcurrenttool"></a><a name="getcurrenttool"></a>CToolTipCtrl::取得電流工具

檢索目前工具提示控制項顯示的工具提示視窗的大小、位置和文字等資訊。

```
BOOL GetCurrentTool(LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*lpToolInfo*|[出]指向接收有關當前工具提示視窗的資訊的[TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa)結構的指標。|

### <a name="return-value"></a>傳回值

如果資訊被成功檢索,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法發送[TTM_GETCURRENTTOOL](/windows/win32/Controls/ttm-getcurrenttool)訊息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

以下代碼示例檢索有關當前工具提示視窗的資訊。

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#6](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_2.cpp)]

## <a name="ctooltipctrlgetdelaytime"></a><a name="getdelaytime"></a>CToolTipCtrl::取得延遲時間

檢索目前為工具提示控制項設定的初始、彈出視窗和重展持續時間。

```
int GetDelayTime(DWORD dwDuration) const;
```

### <a name="parameters"></a>參數

*dwDuration*<br/>
指定將檢索的持續時間值的標誌。 這裡可以是以下值之一:

- TTDT_AUTOPOP 如果指標在工具的邊界矩形內靜止,則檢索工具尖端視窗保持可見的時間長度。

- TTDT_INITIAL 檢索指標必須在工具邊界矩形內保持靜止的時間長度,然後出現工具尖端視窗。

- TTDT_RESHOW檢索後續工具提示視窗在指標從一個工具移動到另一個工具時顯示所需的時間長度。

### <a name="return-value"></a>傳回值

指定的延遲時間 (以毫秒為單位)

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[TTM_GETDELAYTIME](/windows/win32/Controls/ttm-getdelaytime)的行為,如 Windows SDK 中所述。

## <a name="ctooltipctrlgetmargin"></a><a name="getmargin"></a>CToolTipctrl::獲取保證金

檢索為工具提示視窗設置的上邊、左、下和右邊距。

```
void GetMargin(LPRECT lprc) const;
```

### <a name="parameters"></a>參數

*利赫浦*<br/>
將接收保證金`RECT`信息的結構的位址。 [RECT](/previous-versions/dd162897\(v=vs.85\))結構的成員不定義邊界矩形。 對於此消息,結構成員的解釋如下:

|member|表示法|
|------------|--------------------|
|`top`|頂部邊框與工具提示文本頂部之間的距離(以像素為單位)。|
|`left`|提示文字的左邊框和左端之間的距離(以像素為單位)。|
|`bottom`|筆尖文字底部邊框和底部之間的距離(以像素為單位)。|
|`right`|提示文字的右邊框和右端之間的距離(以像素為單位)。|

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[TTM_GETMARGIN](/windows/win32/Controls/ttm-getmargin)的行為,如 Windows SDK 中所述。

## <a name="ctooltipctrlgetmaxtipwidth"></a><a name="getmaxtipwidth"></a>CToolTipctrl::取得最大提示寬度

檢索工具提示視窗的最大寬度。

```
int GetMaxTipWidth() const;
```

### <a name="return-value"></a>傳回值

工具尖端視窗的最大寬度。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[的行為TTM_GETMAXTIPWIDTH](/windows/win32/Controls/ttm-getmaxtipwidth),如 Windows SDK 中所述。

## <a name="ctooltipctrlgettext"></a><a name="gettext"></a>CToolTipctrl::取得文字

檢索工具尖端控制項為工具維護的文本。

```
void GetText(
    CString& str,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>參數

*Str*<br/>
對接收工具`CString`文本的物件的引用。

*pwnd*<br/>
指向包含工具的視窗的指標。

*nIDTool*<br/>
工具的識別碼。

### <a name="remarks"></a>備註

*pWnd*和*nIDTool*參數識別工具。 如果該工具以前已通過以前調用`CToolTipCtrl::AddTool`在工具尖端控制項中註冊,則*str*參數引用的物件將分配該工具的文本。

## <a name="ctooltipctrlgettipbkcolor"></a><a name="gettipbkcolor"></a>CToolTipCtrl::取得提示BkColor

檢索工具提示視窗中的背景顏色。

```
COLORREF GetTipBkColor() const;
```

### <a name="return-value"></a>傳回值

表示背景顏色的[COLORREF](/windows/win32/gdi/colorref)值。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[的行為TTM_GETTIPBKCOLOR,](/windows/win32/Controls/ttm-gettipbkcolor)如 Windows SDK 中所述。

## <a name="ctooltipctrlgettiptextcolor"></a><a name="gettiptextcolor"></a>CToolTipCtrl::取得提示文字顏色

檢索工具提示視窗中的文字顏色。

```
COLORREF GetTipTextColor() const;
```

### <a name="return-value"></a>傳回值

表示文字顏色的[COLORREF](/windows/win32/gdi/colorref)值。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[TTM_GETTIPTEXTCOLOR](/windows/win32/Controls/ttm-gettiptextcolor)的行為,如 Windows SDK 中所述。

## <a name="ctooltipctrlgettitle"></a><a name="gettitle"></a>CToolTipCtrl::取得標題

檢索目前工具提示控件的標題。

```
void GetTitle(PTTGETTITLE pttgt) const;
```

### <a name="parameters"></a>參數

|參數|描述|
|---------------|-----------------|
|*普特格特*|[出]指向包含工具提示控件資訊的[TTGETTITLE](/windows/win32/api/commctrl/ns-commctrl-ttgettitle)結構的指標。 當此方法返回時[,TTGETTITLE](/windows/win32/api/commctrl/ns-commctrl-ttgettitle)結構的*pszTitle*成員指向標題的文本。|

### <a name="remarks"></a>備註

此方法發送[TTM_GETTITLE](/windows/win32/Controls/ttm-gettitle)消息,這在 Windows SDK 中介紹。

## <a name="ctooltipctrlgettoolcount"></a><a name="gettoolcount"></a>CToolTipCtrl::取得工具計數

檢索使用工具尖端控制件註冊的工具的計數。

```
int GetToolCount() const;
```

### <a name="return-value"></a>傳回值

使用工具尖端控制件註冊的工具計數。

## <a name="ctooltipctrlgettoolinfo"></a><a name="gettoolinfo"></a>CToolTipctrl::取得工具資訊

檢索工具尖端控件維護的工具的資訊。

```
BOOL GetToolInfo(
    CToolInfo& ToolInfo,
    CWnd* pWnd,
    UINT_PTR nIDTool = 0) const;
```

### <a name="parameters"></a>參數

*工具資訊*<br/>
對接收工具`TOOLINFO`文本的物件的引用。

*pwnd*<br/>
指向包含工具的視窗的指標。

*nIDTool*<br/>
工具的識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

`hwnd` *CToolInfo*引用的[TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa)結構和`uId`成員標識了該工具。 如果該工具已通過之前對`AddTool`的調用在工具尖端控制項中註冊,`TOOLINFO`則結構將填充有關該工具的資訊。

## <a name="ctooltipctrlhittest"></a><a name="hittest"></a>CToolTipctrl:hitTest

測試點以確定它是否在給定工具的邊界矩形內,如果是,則檢索有關該工具的資訊。

```
BOOL HitTest(
    CWnd* pWnd,
    CPoint pt,
    LPTOOLINFO lpToolInfo) const;
```

### <a name="parameters"></a>參數

*pwnd*<br/>
指向包含工具的視窗的指標。

*pt*<br/>
指向包含`CPoint`要測試的點的座標的物件的指標。

*lpToolInfo*<br/>
指向包含工具資訊的[TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa)結構的指標。

### <a name="return-value"></a>傳回值

如果命中測試資訊指定的點位於工具的邊界矩形內,則非零;否則 0。

### <a name="remarks"></a>備註

如果此函數傳回非零值,*則 lpToolInfo*指向的結構將填充有關其矩形中的刀具的資訊。

結構`TTHITTESTINFO`的定義如下:

```cpp
typedef struct _TT_HITTESTINFO { // tthti
    HWND hwnd;   // handle of tool or window with tool
    POINT pt;    // client coordinates of point to test
    TOOLINFO ti; // receives information about the tool
} TTHITTESTINFO, FAR * LPHITTESTINFO;
```

- `hwnd`

   指定工具的句柄。

- `pt`

   如果點位於工具的邊界矩形中,則指定點的座標。

- `ti`

   有關該工具的資訊。 有關結構的詳細資訊,`TOOLINFO`請參考[CToolTipCtrl::取得 Toolinfo](#gettoolinfo)。

## <a name="ctooltipctrlpop"></a><a name="pop"></a>CToolTipCtrl::Pop

從檢視中刪除顯示的工具提示視窗。

```
void Pop();
```

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[TTM_POP](/windows/win32/Controls/ttm-pop)的行為,如 Windows SDK 中所述。

## <a name="ctooltipctrlpopup"></a><a name="popup"></a>CToolTipCtrl::P

使目前工具提示控制項顯示在最後一個滑鼠訊息的座標處。

```
void Popup();
```

### <a name="remarks"></a>備註

此方法發送[TTM_POPUP](/windows/win32/Controls/ttm-popup)消息,這在 Windows SDK 中介紹。

### <a name="example"></a>範例

以下代碼示例顯示工具提示視窗。

[!code-cpp[NVC_MFC_CToolBarCtrl_s1#7](../../mfc/reference/codesnippet/cpp/ctooltipctrl-class_3.cpp)]

## <a name="ctooltipctrlrelayevent"></a><a name="relayevent"></a>CToolTipCtrl::接力事件

將滑鼠訊息傳遞到工具提示控制項進行處理。

```
void RelayEvent(LPMSG lpMsg);
```

### <a name="parameters"></a>參數

*lpMsg*<br/>
指向包含要中繼的消息的[MSG](/windows/win32/api/winuser/ns-winuser-msg)結構的指標。

### <a name="remarks"></a>備註

工具提示控制項僅處理以下訊息,這些訊息通過`RelayEvent`: 發送給它。

|WM_LBUTTONDOWN|WM_MOUSEMOVE|
|---------------------|-------------------|
|WM_LBUTTONUP|WM_RBUTTONDOWN|
|WM_MBUTTONDOWN|WM_RBUTTONUP|
|WM_MBUTTONUP||

### <a name="example"></a>範例

  請參閱[CPropertySheet 的範例:getTabControl](../../mfc/reference/cpropertysheet-class.md#gettabcontrol)。

## <a name="ctooltipctrlsetdelaytime"></a><a name="setdelaytime"></a>CToolTipctrl::設定延遲時間

設置工具尖端控制的延遲時間。

```
void SetDelayTime(UINT nDelay);

void SetDelayTime(
    DWORD dwDuration,
    int iTime);
```

### <a name="parameters"></a>參數

*nDelay*<br/>
指定新的延遲時間(以毫秒為單位)。

*dwDuration*<br/>
指定將檢索的持續時間值的標誌。 有關有效值的說明,請參閱[CToolTipCtrl:取得延遲時間](#getdelaytime)。

*iTime*<br/>
指定的延遲時間(以毫秒為單位)。

### <a name="remarks"></a>備註

延遲時間是游標在工具尖端視窗出現之前必須保留的時間長度。 默認延遲時間是 500 毫秒。

## <a name="ctooltipctrlsetmargin"></a><a name="setmargin"></a>CToolTipctrl::設定邊緣

設置工具尖端視窗的上邊、左邊、下和右邊距。

```
void SetMargin(LPRECT lprc);
```

### <a name="parameters"></a>參數

*利赫浦*<br/>
包含要設置`RECT`的邊距資訊的結構的位址。 `RECT`結構的成員不定義邊界矩形。 有關保證金資訊的說明,請參閱[CToolTipCtrl:取得保證金](#getmargin)。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[TTM_SETMARGIN](/windows/win32/Controls/ttm-setmargin)的行為,如 Windows SDK 中所述。

## <a name="ctooltipctrlsetmaxtipwidth"></a><a name="setmaxtipwidth"></a>CToolTipctrl::設定最大提示寬度

設置工具尖端視窗的最大寬度。

```
int SetMaxTipWidth(int iWidth);
```

### <a name="parameters"></a>參數

*iWidth*<br/>
要設置的最大工具尖端窗口寬度。

### <a name="return-value"></a>傳回值

上一個最大尖端寬度。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[TTM_SETMAXTIPWIDTH](/windows/win32/Controls/ttm-setmaxtipwidth)的行為,如 Windows SDK 中所述。

## <a name="ctooltipctrlsettipbkcolor"></a><a name="settipbkcolor"></a>CToolTipctrl::SetTipBkColor

在工具提示視窗中設定背景顏色。

```
void SetTipBkColor(COLORREF clr);
```

### <a name="parameters"></a>參數

*Clr*<br/>
新的背景顏色。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[的行為TTM_SETTIPBKCOLOR](/windows/win32/Controls/ttm-settipbkcolor),如 Windows SDK 中所述。

## <a name="ctooltipctrlsettiptextcolor"></a><a name="settiptextcolor"></a>CToolTipctrl::設定提示文字顏色

在工具提示視窗中設定文字顏色。

```
void SetTipTextColor(COLORREF clr);
```

### <a name="parameters"></a>參數

*Clr*<br/>
新的文字顏色。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[TTM_SETTIPTEXTCOLOR](/windows/win32/Controls/ttm-settiptextcolor)的行為,如 Windows SDK 中所述。

## <a name="ctooltipctrlsettitle"></a><a name="settitle"></a>CToolTipctrl::設定標題

將標準圖示和標題字串添加到工具提示。

```
BOOL SetTitle(
    UINT uIcon,
    LPCTSTR lpstrTitle);
```

### <a name="parameters"></a>參數

*uIcon*<br/>
請參考 Windows SDK 中[TTM_SETTITLE](/windows/win32/Controls/ttm-settitle)中的*圖示*。

*lpstrTitle*<br/>
指向標題字串的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

此成員函數實現 Win32 消息[TTM_SETTITLE](/windows/win32/Controls/ttm-settitle)的行為,如 Windows SDK 中所述。

## <a name="ctooltipctrlsettoolinfo"></a><a name="settoolinfo"></a>CToolTipctrl::設定工具資訊

設置工具提示為工具維護的資訊。

```
void SetToolInfo(LPTOOLINFO lpToolInfo);
```

### <a name="parameters"></a>參數

*lpToolInfo*<br/>
指向[TOOLINFO](/windows/win32/api/commctrl/ns-commctrl-tttoolinfoa)結構的指標,用於指定要設置的資訊。

## <a name="ctooltipctrlsettoolrect"></a><a name="settoolrect"></a>CToolTipctrl::設定工具重新

為工具設置新的邊界矩形。

```
void SetToolRect(
    CWnd* pWnd,
    UINT_PTR nIDTool,
    LPCRECT lpRect);
```

### <a name="parameters"></a>參數

*pwnd*<br/>
指向包含工具的視窗的指標。

*nIDTool*<br/>
工具的識別碼。

*lpRect*<br/>
指向指定新邊界矩形的[RECT](/previous-versions/dd162897\(v=vs.85\))結構的指標。

## <a name="ctooltipctrlsetwindowtheme"></a><a name="setwindowtheme"></a>CToolTipctrl::設定視窗主題

設置工具提示視窗的視覺樣式。

```
HRESULT SetWindowTheme(LPCWSTR pszSubAppName);
```

### <a name="parameters"></a>參數

*pssSubApp 名稱*<br/>
指向 Unicode 字串的指標,其中包含要設置的可視樣式。

### <a name="return-value"></a>傳回值

不使用返回值。

### <a name="remarks"></a>備註

此成員函數類比[TTM_SETWINDOWTHEME](/windows/win32/Controls/ttm-setwindowtheme)消息的功能,如 Windows SDK 中所述。

## <a name="ctooltipctrlupdate"></a><a name="update"></a>CToolTipCtrl::更新

強制重繪當前工具。

```
void Update();
```

## <a name="ctooltipctrlupdatetiptext"></a><a name="updatetiptext"></a>CToolTipctrl::更新提示文字

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
指向工具的文字的指標。

*pwnd*<br/>
指向包含工具的視窗的指標。

*nIDTool*<br/>
工具的識別碼。

*nIDText*<br/>
包含工具文字的字串資源的識別碼。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CToolBar 類別](../../mfc/reference/ctoolbar-class.md)
