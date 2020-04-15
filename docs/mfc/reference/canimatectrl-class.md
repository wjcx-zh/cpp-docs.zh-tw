---
title: CAnimateCtrl 類別
ms.date: 11/04/2016
f1_keywords:
- CAnimateCtrl
- AFXCMN/CAnimateCtrl
- AFXCMN/CAnimateCtrl::CAnimateCtrl
- AFXCMN/CAnimateCtrl::Close
- AFXCMN/CAnimateCtrl::Create
- AFXCMN/CAnimateCtrl::CreateEx
- AFXCMN/CAnimateCtrl::IsPlaying
- AFXCMN/CAnimateCtrl::Open
- AFXCMN/CAnimateCtrl::Play
- AFXCMN/CAnimateCtrl::Seek
- AFXCMN/CAnimateCtrl::Stop
helpviewer_keywords:
- CAnimateCtrl [MFC], CAnimateCtrl
- CAnimateCtrl [MFC], Close
- CAnimateCtrl [MFC], Create
- CAnimateCtrl [MFC], CreateEx
- CAnimateCtrl [MFC], IsPlaying
- CAnimateCtrl [MFC], Open
- CAnimateCtrl [MFC], Play
- CAnimateCtrl [MFC], Seek
- CAnimateCtrl [MFC], Stop
ms.assetid: 5e8eb1bd-96b7-47b8-8de2-6bcbb3cc299b
ms.openlocfilehash: fcee569659d732c26e274c8ca189042a16f13557
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371052"
---
# <a name="canimatectrl-class"></a>CAnimateCtrl 類別

提供 Windows 通用動畫控制項的功能。

## <a name="syntax"></a>語法

```
class CAnimateCtrl : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[克拉萬克::克拉萬克Ctrl](#canimatectrl)|建構 `CAnimateCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAnimateCtrl:關閉](#close)|關閉 AVI 剪輯。|
|[CAnimateCtrl::創建](#create)|創建動畫控制項並將其附加到`CAnimateCtrl`物件。|
|[創刊::創建Ex](#createex)|使用指定的 Windows 擴充樣式創建動畫控制項並將`CAnimateCtrl`其附加到 物件。|
|[CAnimateCtrl:播放](#isplaying)|指示是否正在播放音訊視頻交錯 (AVI) 剪輯。|
|[CAnimateCtrl::打開](#open)|從檔或資源打開 AVI 剪輯並顯示第一個幀。|
|[克拉萬克克::P萊](#play)|播放沒有聲音的 AVI 剪輯。|
|[CAnimateCtrl::尋找](#seek)|顯示 AVI 剪輯的選定單幀。|
|[克拉萬克::停止](#stop)|停止播放 AVI 剪輯。|

## <a name="remarks"></a>備註

此控制項(因此該`CAnimateCtrl`類別)僅適用於在 Windows 95、Windows 98 和 Windows NT 版本 3.51 及更高版本下運行的程式。

動畫控項是一個矩形視窗,以 AVI(音訊視訊交錯)格式顯示剪輯 — 標準 Windows 視頻/音訊格式。 AVI 短片是一系列的點陣圖框架，例如電影。

動畫控件只能播放簡單的 AVI 剪輯。 具體而言,動畫控件要播放的剪輯必須滿足以下要求:

- 必須正好有一個視頻流,並且必須至少有一個幀。

- 檔中最多只能有兩個流(如果存在,通常另一個流是音訊流,儘管動畫控件忽略音訊資訊)。

- 剪輯必須解壓縮或使用 RLE8 壓縮進行壓縮。

- 視頻流中不允許更改調色板。

您可以將 AVI 剪輯作為 AVI 資源添加到您的應用程式中,也可以作為單獨的 AVI 檔隨同應用程式。

由於線程在顯示 AVI 剪輯時繼續執行,因此動畫控件的一個常見用途是指示長時間操作期間的系統活動。 例如,在系統搜索檔時,「查找檔案資源管理器」對話框將顯示移動的放大鏡。

如果在對話框中或使用`CAnimateCtrl`對話框編輯器從對話方塊資源創建物件,則當使用者關閉對話方塊時,該物件將自動銷毀。

如果在視窗中創建`CAnimateCtrl`物件,則可能需要銷毀它。 如果在堆疊上`CAnimateCtrl`創建物件,則會自動銷毀該物件。 如果使用新函數在`CAnimateCtrl`堆上創建物件,則必須調**new**用 物件上的**delete**以銷毀它。 如果從`CAnimateCtrl`該類派生新類並分配該類中的任何記憶體,請重寫`CAnimateCtrl`析構函數以釋放分配。

有關`CAnimateCtrl`使用的詳細資訊,請參閱[控制項](../../mfc/controls-mfc.md)[和使用 CAnimateCtrl](../../mfc/using-canimatectrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CAnimateCtrl`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

## <a name="canimatectrlcanimatectrl"></a><a name="canimatectrl"></a>克拉萬克::克拉萬克Ctrl

建構 `CAnimateCtrl` 物件。

```
CAnimateCtrl();
```

### <a name="remarks"></a>備註

必須先調用[Create](#create)成員函數,然後才能對創建的物件執行任何其他操作。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#56](../../mfc/codesnippet/cpp/canimatectrl-class_1.cpp)]

## <a name="canimatectrlclose"></a><a name="close"></a>CAnimateCtrl:關閉

關閉以前在動畫控制項中打開的 AVI 剪輯(如果有),並將其從記憶體中刪除。

```
BOOL Close();
```

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="example"></a>範例

  請參閱[CAnimateCtrl 的範例::CAnimateCtrl](#canimatectrl)。

## <a name="canimatectrlcreate"></a><a name="create"></a>CAnimateCtrl::創建

創建動畫控制項並將其附加到`CAnimateCtrl`物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定動畫控制項樣式。 套用下面「備註」 部份中描述的視窗樣式的任意組合, 以及 Windows SDK 中的[動畫控制元件樣式中描述的動畫控制元件樣式](/windows/win32/Controls/animation-control-styles)。

*矩形*<br/>
指定動畫控制項的位置和大小。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](/windows/win32/api/windef/ns-windef-rect)結構。

*pparentwnd*<br/>
指定動畫控制的檔的父視窗,通常`CDialog`為 。 它不得為 NULL。

*nID*<br/>
指定動畫控制項的識別碼。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

在兩個步驟`CAnimateCtrl`中構造 一個。 首先調用構造函數,然後調用`Create`,這將創建動畫控制項並將其附加`CAnimateCtrl`到 物件。

將以下[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)應用於動畫控制項。

- WS_CHILD始終

- WS_VISIBLE 通常

- WS_DISABLED很少

如果要將延伸視窗樣式與動畫控制項一起使用,請呼叫[CreateEx](#createex)`Create`而不是 。

除了上面列出的視窗樣式外,您可能還希望將一個或多個動畫控制項樣式應用於動畫控制項。 有關[動畫控件樣式](/windows/win32/Controls/animation-control-styles)的詳細資訊,請參閱 Windows SDK。

### <a name="example"></a>範例

  請參閱[CAnimateCtrl 的範例::CAnimateCtrl](#canimatectrl)。

## <a name="canimatectrlcreateex"></a><a name="createex"></a>創刊::創建Ex

創建控制項(子視窗),並將其與`CAnimateCtrl`物件關聯。

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
指定動畫控制項樣式。 應用 Windows SDK 中的[動畫控制樣式](/windows/win32/Controls/animation-control-styles)中描述的視窗和動畫控制項樣式的任意組合。

*矩形*<br/>
對[RECT](/previous-versions/dd162897\(v=vs.85\))結構的引用,描述要創建的視窗的大小和位置,在*pParentWnd*的用戶端座標中。

*pparentwnd*<br/>
指向控件的父視窗的指標。

*nID*<br/>
控制項的子視窗 ID。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

使用`CreateEx`而不是[「創建](#create)」來應用擴展的 Windows 樣式,該樣式由 Windows 擴充樣式前言**WS_EX_** 指定。

## <a name="canimatectrlisplaying"></a><a name="isplaying"></a>CAnimateCtrl:播放

指示是否正在播放音訊視頻交錯 (AVI) 剪輯。

```
BOOL IsPlaying() const;
```

### <a name="return-value"></a>傳回值

如果正在播放 AVI 剪輯,則為 TRUE;否則,FALSE。

### <a name="remarks"></a>備註

此方法發送[ACM_ISPLAYING](/windows/win32/Controls/acm-isplaying)消息,這在 Windows SDK 中介紹。

## <a name="canimatectrlopen"></a><a name="open"></a>CAnimateCtrl::打開

呼叫此功能以打開 AVI 剪輯並顯示其第一個幀。

```
BOOL Open(LPCTSTR lpszFileName);
BOOL Open(UINT nID);
```

### <a name="parameters"></a>參數

*lpszFile 名稱*<br/>
`CString`包含 AVI 檔名稱或 AVI 資源名稱的物件或指向 null 終止字串的指標。 如果此參數為 NULL,系統將關閉以前為動畫控制件打開的 AVI 剪輯(如果有)。

*nID*<br/>
AVI 資源標識碼。 如果此參數為 NULL,系統將關閉以前為動畫控制件打開的 AVI 剪輯(如果有)。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

AVI 資源從創建動畫控制項的模組載入。

`Open`不支援 AVI 剪輯中的聲音;您只能打開靜默的 AVI 剪輯。

如果動畫控制項具有`ACS_AUTOPLAY`樣式,動畫控制項將在剪輯打開後立即開始播放。 當線程繼續執行時,它將繼續在後台播放剪輯。 播放完剪輯后,將自動重複剪輯。

如果動畫控制項具有`ACS_CENTER`樣式,則 AVI 剪輯將居中於控制項中,並且控制項大小不會更改。 如果動畫控制項沒有`ACS_CENTER`樣式,則當 AVI 剪輯打開到 AVI 剪輯中圖像的大小時,控制項將調整大小。 控制元件左上角的位置不會更改,只有控制項大小。

如果動畫控制項具有`ACS_TRANSPARENT`樣式,則將使用透明背景而不是動畫剪輯中指定的背景顏色繪製第一個幀。

### <a name="example"></a>範例

  請參閱[CAnimateCtrl 的範例::CAnimateCtrl](#canimatectrl)。

## <a name="canimatectrlplay"></a><a name="play"></a>克拉萬克克::P萊

調用此函數以在動畫控制項中播放 AVI 剪輯。

```
BOOL Play(
    UINT nFrom,
    UINT nTo,
    UINT nRep);
```

### <a name="parameters"></a>參數

*n 從*<br/>
播放開始的框架的從零開始的索引。 值必須小於 65,536。 值 0 表示從 AVI 剪輯中的第一幀開始。

*nto*<br/>
播放結束幀的基於零的索引。 值必須小於 65,536。 值 - 1 表示以 AVI 剪輯中的最後一幀結尾。

*NRep*<br/>
重播 AVI 剪輯的次數。 值 - 1 表示無限期重播檔。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

動畫控件將在線程繼續執行時在後台播放剪輯。 如果動畫控制項具有`ACS_TRANSPARENT`樣式,則使用透明背景而不是動畫剪輯中指定的背景顏色播放 AVI 剪輯。

### <a name="example"></a>範例

  請參閱[CAnimateCtrl 的範例::CAnimateCtrl](#canimatectrl)。

## <a name="canimatectrlseek"></a><a name="seek"></a>CAnimateCtrl::尋找

調用此功能以靜態顯示 AVI 剪輯的單個幀。

```
BOOL Seek(UINT nTo);
```

### <a name="parameters"></a>參數

*nto*<br/>
要顯示的幀的從零開始索引。 值必須小於 65,536。 值 0 表示在 AVI 剪輯中顯示第一個幀。 值 -1 表示在 AVI 剪輯中顯示最後一個幀。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

如果動畫控制項具有`ACS_TRANSPARENT`樣式,則 AVI 剪輯將使用透明背景而不是動畫剪輯中指定的背景顏色進行繪製。

### <a name="example"></a>範例

請參閱[CAnimateCtrl 的範例::CAnimateCtrl](#canimatectrl)。

## <a name="canimatectrlstop"></a><a name="stop"></a>克拉萬克::停止

調用此函數停止在動畫控制項中播放 AVI 剪輯。

```
BOOL Stop();
```

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="example"></a>範例

  請參閱[CAnimateCtrl 的範例::CAnimateCtrl](#canimatectrl)。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CAnimateCtrl::創建](#create)<br/>
[ON_CONTROL](message-map-macros-mfc.md#on_control)
