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
ms.openlocfilehash: 651b5775886374f3fcc95ab6b2cb3d892d9d77e8
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87183379"
---
# <a name="canimatectrl-class"></a>CAnimateCtrl 類別

提供 Windows 通用動畫控制項的功能。

## <a name="syntax"></a>語法

```
class CAnimateCtrl : public CWnd
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CAnimateCtrl：： CAnimateCtrl](#canimatectrl)|建構 `CAnimateCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CAnimateCtrl：： Close](#close)|關閉 AVI 剪輯。|
|[CAnimateCtrl：： Create](#create)|建立動畫控制項，並將其附加至 `CAnimateCtrl` 物件。|
|[CAnimateCtrl：： CreateEx](#createex)|建立具有指定之 Windows 擴充樣式的動畫控制項，並將其附加至 `CAnimateCtrl` 物件。|
|[CAnimateCtrl：： IsPlaying](#isplaying)|指出是否現正播放音訊影片交錯（AVI）剪輯。|
|[CAnimateCtrl：： Open](#open)|從檔案或資源開啟 AVI 剪輯，並顯示第一個框架。|
|[CAnimateCtrl：:P 的版面配置](#play)|播放 AVI 剪輯而不音效。|
|[CAnimateCtrl：： Seek](#seek)|顯示已選取的 AVI 剪輯單一框架。|
|[CAnimateCtrl：： Stop](#stop)|停止播放 AVI 剪輯。|

## <a name="remarks"></a>備註

這個控制項（因此 `CAnimateCtrl` 類別）僅適用于在 windows 95、windows 98 和 WINDOWS NT 3.51 版和更新版本下執行的程式。

動畫控制項是一個矩形視窗，會以 AVI （音訊影片交錯）格式顯示剪輯，這是標準的 Windows Video/音訊格式。 AVI 短片是一系列的點陣圖框架，例如電影。

動畫控制項只能播放簡單的 AVI 剪輯。 具體而言，動畫控制項要播放的剪輯必須符合下列需求：

- 必須只有一個影片串流，而且必須至少有一個畫面格。

- 檔案中最多可以有兩個數據流（通常是另一個資料流程（如果有的話）是音訊資料流程，雖然動畫控制項會忽略音訊資訊）。

- 剪輯必須使用 RLE8 壓縮進行解壓縮或壓縮。

- 影片資料流程中不允許任何調色板變更。

您可以將 AVI 剪輯新增至您的應用程式做為 AVI 資源，也可以隨應用程式一起做為個別的 AVI 檔案。

因為在顯示 AVI 剪輯時，您的執行緒會繼續執行，所以動畫控制項的常見用法是在冗長的作業期間指出系統活動。 例如，[檔案瀏覽器] 的 [尋找] 對話方塊會在系統搜尋檔案時，顯示移動的放大鏡。

如果您 `CAnimateCtrl` 使用對話方塊編輯器，在對話方塊中或從對話方塊資源建立物件，則會在使用者關閉對話方塊時自動終結。

如果您在 `CAnimateCtrl` 視窗中建立物件，可能需要將它摧毀。 如果您在 `CAnimateCtrl` 堆疊上建立物件，它會自動終結。 如果您使用函式在 `CAnimateCtrl` 堆積上建立物件 **`new`** ，您必須 **`delete`** 在物件上呼叫來摧毀它。 如果您從衍生新的類別， `CAnimateCtrl` 並在該類別中配置任何記憶體，請覆寫 `CAnimateCtrl` 析構函式來處置配置。

如需使用的詳細資訊 `CAnimateCtrl` ，請參閱[控制項](../../mfc/controls-mfc.md)和[使用 CAnimateCtrl](../../mfc/using-canimatectrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CAnimateCtrl`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

## <a name="canimatectrlcanimatectrl"></a><a name="canimatectrl"></a>CAnimateCtrl：： CAnimateCtrl

建構 `CAnimateCtrl` 物件。

```
CAnimateCtrl();
```

### <a name="remarks"></a>備註

您必須先呼叫[create](#create)成員函式，才能在您所建立的物件上執行任何其他作業。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#56](../../mfc/codesnippet/cpp/canimatectrl-class_1.cpp)]

## <a name="canimatectrlclose"></a><a name="close"></a>CAnimateCtrl：： Close

關閉先前在動畫控制項中開啟的 AVI 剪輯（如果有的話），並從記憶體中移除它。

```
BOOL Close();
```

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="example"></a>範例

  請參閱[CAnimateCtrl：： CAnimateCtrl](#canimatectrl)的範例。

## <a name="canimatectrlcreate"></a><a name="create"></a>CAnimateCtrl：： Create

建立動畫控制項，並將其附加至 `CAnimateCtrl` 物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
指定動畫控制項的樣式。 套用下列「備註」一節所述的任何 windows 樣式組合，以及 Windows SDK 中的[動畫控制樣式](/windows/win32/Controls/animation-control-styles)中所述的動畫控制項樣式。

*各種*<br/>
指定動畫控制項的位置和大小。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](/windows/win32/api/windef/ns-windef-rect)結構。

*pParentWnd*<br/>
指定動畫控制項的父視窗，通常是 `CDialog` 。 它不得為 NULL。

*nID*<br/>
指定動畫控制項的識別碼。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

您可以使用 `CAnimateCtrl` 兩個步驟來建立。 首先，呼叫此函式，然後呼叫 `Create` ，它會建立動畫控制項並將其附加至 `CAnimateCtrl` 物件。

將下列[視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)套用至動畫控制項。

- 一律 WS_CHILD

- WS_VISIBLE 通常

- WS_DISABLED 很少

如果您想要搭配動畫控制項使用擴充的 windows 樣式，請呼叫[CreateEx](#createex) ，而不是 `Create` 。

除了上面所列的視窗樣式，您可能會想要將一或多個動畫控制項樣式套用至動畫控制項。 如需[動畫控制項樣式](/windows/win32/Controls/animation-control-styles)的詳細資訊，請參閱 Windows SDK。

### <a name="example"></a>範例

  請參閱[CAnimateCtrl：： CAnimateCtrl](#canimatectrl)的範例。

## <a name="canimatectrlcreateex"></a><a name="createex"></a>CAnimateCtrl：： CreateEx

建立控制項（子視窗），並將它與物件產生關聯 `CAnimateCtrl` 。

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
指定所要建立之控制項的延伸樣式。 如需擴充 Windows 樣式的清單，請參閱 Windows SDK 中[CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)的*dwExStyle*參數。

*dwStyle*<br/>
指定動畫控制項的樣式。 套用 Windows SDK 中[動畫控制項樣式](/windows/win32/Controls/animation-control-styles)中所述之視窗和動畫控制項樣式的任何組合。

*各種*<br/>
[矩形](/windows/win32/api/windef/ns-windef-rect)結構的參考，描述要建立之視窗的大小和位置，以*pParentWnd*的用戶端座標表示。

*pParentWnd*<br/>
做為控制項父系之視窗的指標。

*nID*<br/>
控制項的子視窗識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

使用 `CreateEx` ，而不是[Create](#create)來套用擴充的 windows 樣式（由 Windows 擴充樣式指定于**WS_EX_** 的前面）。

## <a name="canimatectrlisplaying"></a><a name="isplaying"></a>CAnimateCtrl：： IsPlaying

指出是否現正播放音訊影片交錯（AVI）剪輯。

```
BOOL IsPlaying() const;
```

### <a name="return-value"></a>傳回值

如果現正播放 AVI 剪輯，則為 TRUE;否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[ACM_ISPLAYING](/windows/win32/Controls/acm-isplaying)訊息，如 Windows SDK 所述。

## <a name="canimatectrlopen"></a><a name="open"></a>CAnimateCtrl：： Open

呼叫此函式可開啟 AVI 剪輯，並顯示其第一個框架。

```
BOOL Open(LPCTSTR lpszFileName);
BOOL Open(UINT nID);
```

### <a name="parameters"></a>參數

*lpszFileName*<br/>
`CString`物件或以 null 終止之字串的指標，其中包含 avi 檔案的名稱或 avi 資源的名稱。 如果此參數為 Null，系統會關閉先前為動畫控制項開啟的 AVI 剪輯（如果有的話）。

*nID*<br/>
AVI 資源識別碼。 如果此參數為 Null，系統會關閉先前為動畫控制項開啟的 AVI 剪輯（如果有的話）。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

AVI 資源是從建立動畫控制項的模組載入。

`Open`不支援 AVI 剪輯中的音效;您只能開啟無訊息的 AVI 剪輯。

如果動畫控制項具有 `ACS_AUTOPLAY` 樣式，動畫控制項就會在開啟剪輯之後自動開始播放。 當您的執行緒繼續執行時，它會繼續在背景播放剪輯。 當剪輯完成播放時，它會自動重複。

如果動畫控制項具有 `ACS_CENTER` 樣式，則 AVI 剪輯會在控制項中置中，而且控制項的大小不會變更。 如果動畫控制項沒有 `ACS_CENTER` 樣式，當 avi 剪輯開啟為 avi 剪輯中影像的大小時，控制項會調整大小。 控制項左上角的位置不會變更，只會改變控制項的大小。

如果動畫控制項具有 `ACS_TRANSPARENT` 樣式，則會使用透明背景繪製第一個框架，而不是在動畫剪輯中指定的背景色彩。

### <a name="example"></a>範例

  請參閱[CAnimateCtrl：： CAnimateCtrl](#canimatectrl)的範例。

## <a name="canimatectrlplay"></a><a name="play"></a>CAnimateCtrl：:P 的版面配置

呼叫此函式可在動畫控制項中播放 AVI 剪輯。

```
BOOL Play(
    UINT nFrom,
    UINT nTo,
    UINT nRep);
```

### <a name="parameters"></a>參數

*n*<br/>
播放開始之框架的以零為起始的索引。 值必須小於65536。 值為0表示開頭為 AVI 剪輯中的第一個框架。

*\N\n*<br/>
播放結束之框架的以零為起始的索引。 值必須小於65536。 -1 的值表示結尾為 AVI 剪輯中的最後一個框架。

*nRep*<br/>
重新播放 AVI 剪輯的次數。 -1 的值表示無限期地重新執行檔案。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

當您的執行緒繼續執行時，動畫控制項會在背景播放剪輯。 如果動畫控制項具有 `ACS_TRANSPARENT` 樣式，則會使用透明背景來播放 AVI 剪輯，而不是動畫剪輯中指定的背景色彩。

### <a name="example"></a>範例

  請參閱[CAnimateCtrl：： CAnimateCtrl](#canimatectrl)的範例。

## <a name="canimatectrlseek"></a><a name="seek"></a>CAnimateCtrl：： Seek

呼叫此函式，以靜態方式顯示 AVI 剪輯的單一畫面格。

```
BOOL Seek(UINT nTo);
```

### <a name="parameters"></a>參數

*\N\n*<br/>
要顯示之框架的以零為基底的索引。 值必須小於65536。 值為0表示顯示 AVI 剪輯中的第一個框架。 值為-1 表示顯示 AVI 剪輯中的最後一個框架。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

如果動畫控制項具有 `ACS_TRANSPARENT` 樣式，則會使用透明背景繪製 AVI 剪輯，而不是在動畫剪輯中指定的背景色彩。

### <a name="example"></a>範例

請參閱[CAnimateCtrl：： CAnimateCtrl](#canimatectrl)的範例。

## <a name="canimatectrlstop"></a><a name="stop"></a>CAnimateCtrl：： Stop

呼叫此函式可停止播放動畫控制項中的 AVI 剪輯。

```
BOOL Stop();
```

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="example"></a>範例

  請參閱[CAnimateCtrl：： CAnimateCtrl](#canimatectrl)的範例。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CAnimateCtrl：： Create](#create)<br/>
[ON_CONTROL](message-map-macros-mfc.md#on_control)
