---
title: CAnimateCtrl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4e52ff062f8ba22eddc7a87e182b267b006f3094
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402404"
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
|[CAnimateCtrl::CAnimateCtrl](#canimatectrl)|建構 `CAnimateCtrl` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CAnimateCtrl::Close](#close)|關閉 AVI 短片。|
|[CAnimateCtrl::Create](#create)|建立動畫控制項，並將它附加至`CAnimateCtrl`物件。|
|[CAnimateCtrl::CreateEx](#createex)|使用指定的 Windows 延伸樣式中建立動畫控制項，並將它附加至`CAnimateCtrl`物件。|
|[CAnimateCtrl::IsPlaying](#isplaying)|指出是否要播放的音訊視訊交錯格式 (AVI) 剪輯。|
|[CAnimateCtrl::Open](#open)|從檔案或資源開啟 AVI 短片，並顯示第一個畫面格。|
|[CAnimateCtrl::Play](#play)|播放 AVI 短片，而不需要音效。|
|[CAnimateCtrl::Seek](#seek)|顯示選取的單一框架的 AVI 短片。|
|[CAnimateCtrl::Stop](#stop)|停止播放 AVI 短片。|

## <a name="remarks"></a>備註

這個控制項 (並因此`CAnimateCtrl`類別) 僅適用於 Windows 95、 Windows 98 和 Windows NT 版 3.51 下執行的程式和更新版本。

動畫控制項是一個矩形的視窗，AVI （音訊視訊交錯格式） 格式來顯示剪輯，標準的 Windows 視訊與音訊格式。 AVI 短片是一系列的點陣圖框架，例如電影。

動畫控制項可以播放只有簡單的 AVI 短片。 具體來說，動畫控制項所要播放的剪輯必須符合下列需求：

- 必須有正好一個視訊串流，而且必須至少一個框架。

- 中可以有最多兩個資料流的檔案 （通常為其他資料流，如果有的話，是一個音訊資料流、 雖然動畫控制項會忽略音訊資訊）。

- 美工圖案必須是未壓縮或形式 RLE8 壓縮。

- 視訊資料流中不允許任何調色盤變更。

您可以在播放 AVI 短片加入為 AVI 資源之後，您的應用程式或其可隨附於您的應用程式，做為個別的 AVI 檔案。

因為您的執行緒會繼續執行時顯示在播放 AVI 短片，動畫控制項的常見用途之一就是在長時間作業期間表示系統的活動。 比方說，檔案總管 的 尋找 對話方塊會顯示移動的放大鏡，隨著系統搜尋檔案。

如果您建立`CAnimateCtrl`物件 對話方塊中，方塊中，或從對話方塊資源，使用對話方塊編輯器，它將會自動終結當使用者關閉對話方塊。

如果您建立`CAnimateCtrl`物件內的視窗中，您可能需要終結它。 如果您建立`CAnimateCtrl`物件在堆疊上，它會自動終結。 如果您建立`CAnimateCtrl`物件上使用堆積**新**函式，您必須呼叫**刪除**終結它在物件上。 如果您衍生新的類別，從`CAnimateCtrl`，會配置任何記憶體，該類別中的覆寫`CAnimateCtrl`解構函式來進行處置的配置。

如需有關使用`CAnimateCtrl`，請參閱 <<c2> [ 控制項](../../mfc/controls-mfc.md)並[使用 CAnimateCtrl](../../mfc/using-canimatectrl.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CAnimateCtrl`

## <a name="requirements"></a>需求

**標頭：** afxcmn.h

##  <a name="canimatectrl"></a>  CAnimateCtrl::CAnimateCtrl

建構 `CAnimateCtrl` 物件。

```
CAnimateCtrl();
```

### <a name="remarks"></a>備註

您必須呼叫[建立](#create)成員函式才能執行您所建立的物件上的任何其他作業。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#56](../../mfc/codesnippet/cpp/canimatectrl-class_1.cpp)]

##  <a name="close"></a>  CAnimateCtrl::Close

關閉先前動畫控制項 （如果有的話） 中開啟 AVI 短片，並將它從記憶體移除。

```
BOOL Close();
```

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="example"></a>範例

  範例，請參閱[CAnimateCtrl::CAnimateCtrl](#canimatectrl)。

##  <a name="create"></a>  CAnimateCtrl::Create

建立動畫控制項，並將它附加至`CAnimateCtrl`物件。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>參數

*cheaderctrl:: Create*<br/>
指定動畫控制項的樣式。 適用於的 windows 中的 < 備註 > 一節和動畫控制項的樣式中所述的樣式所述的任何組合[動畫控制項的樣式](/windows/desktop/Controls/animation-control-styles)Windows SDK 中。

*rect*<br/>
指定動畫控制項的位置和大小。 它可以是[CRect](../../atl-mfc-shared/reference/crect-class.md)物件或[RECT](../../mfc/reference/rect-structure1.md)結構。

*pParentWnd*<br/>
指定動畫控制項的父視窗，通常`CDialog`。 它必須不是 NULL。

*nID*<br/>
指定動畫控制項的識別碼。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

您建構`CAnimateCtrl`兩個步驟。 首先，呼叫建構函式，並接著呼叫`Create`，這會建立動畫控制項，並將它附加至`CAnimateCtrl`物件。

套用下列[的視窗樣式](../../mfc/reference/styles-used-by-mfc.md#window-styles)動畫控制項。

- WS_CHILD 一律

- WS_VISIBLE 通常

- WS_DISABLED 很少

如果您想要使用擴充的 windows 樣式和動畫控制項，呼叫[CreateEx](#createex)而不是`Create`。

除了上面所列的視窗樣式，您可能想要套用至動畫控制項的一或多個動畫控制項的樣式。 請參閱 Windows SDK，如需詳細資訊[動畫控制項的樣式](/windows/desktop/Controls/animation-control-styles)。

### <a name="example"></a>範例

  範例，請參閱[CAnimateCtrl::CAnimateCtrl](#canimatectrl)。

##  <a name="createex"></a>  CAnimateCtrl::CreateEx

建立控制項 （子視窗），並將它與關聯`CAnimateCtrl`物件。

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
指定正在建立之控制項的延伸的樣式。 如需延伸的 Windows 樣式的清單，請參閱 < *dwExStyle*參數[CreateWindowEx](/windows/desktop/api/winuser/nf-winuser-createwindowexa) Windows SDK 中。

*cheaderctrl:: Create*<br/>
指定動畫控制項的樣式。 套用視窗的任意組合和動畫控制項的樣式中所述[動畫控制項的樣式](/windows/desktop/Controls/animation-control-styles)Windows SDK 中。

*rect*<br/>
參考[RECT](https://msdn.microsoft.com/library/windows/desktop/dd162897)結構描述的大小和位置，在中建立工作區座標中的視窗*pParentWnd*。

*pParentWnd*<br/>
是控制項的父視窗的指標。

*nID*<br/>
控制項的子視窗識別碼。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

使用`CreateEx`而非[建立](#create)套用延伸的 Windows 樣式，由 Windows 延伸的樣式前置詞**WS_EX_**。

##  <a name="isplaying"></a>  CAnimateCtrl::IsPlaying

指出是否要播放的音訊視訊交錯格式 (AVI) 剪輯。

```
BOOL IsPlaying() const;
```

### <a name="return-value"></a>傳回值

如果正在播放 AVI 短片就;，則為 TRUE。否則為 FALSE。

### <a name="remarks"></a>備註

這個方法會傳送[ACM_ISPLAYING](/windows/desktop/Controls/acm-isplaying)訊息，Windows SDK 中所述。

##  <a name="open"></a>  CAnimateCtrl::Open

呼叫此函式可開啟 AVI 短片，並顯示其第一個畫面格。

```
BOOL Open(LPCTSTR lpszFileName);
BOOL Open(UINT nID);
```

### <a name="parameters"></a>參數

*lpszFileName*<br/>
A`CString`物件或資料指標，以 null 終止的字串，包含 AVI 檔案的名稱或 AVI 資源的名稱。 如果此參數為 NULL，系統會關閉先前開啟動畫控制項，在播放 AVI 短片，如果有的話。

*nID*<br/>
AVI 資源識別項。 如果此參數為 NULL，系統會關閉先前開啟動畫控制項，在播放 AVI 短片，如果有的話。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

AVI 資源會從模組建立動畫控制項載入。

`Open` 不支援 AVI 短片; 中的音效您可以開啟僅無訊息的 AVI 短片。

如果動畫控制項`ACS_AUTOPLAY`樣式，動畫控制項將自動開始播放短片，它會開啟之後，立即。 它會繼續在背景中播放剪輯，而您的執行緒會繼續執行。 剪輯完成播放時，它會自動重複。

如果動畫控制項`ACS_CENTER`樣式，在播放 AVI 短片會置中對齊控制項中，並不會變更控制項的大小。 如果動畫控制項並沒有`ACS_CENTER`樣式時開啟 AVI 短片就 AVI 短片中的映像的大小會調整大小的控制項。 控制項的左上角的位置不會變更，該控制項的大小。

如果動畫控制項`ACS_TRANSPARENT`樣式，將會使用透明背景繪製第一個畫面格，而非中指定的背景色彩的動畫剪輯。

### <a name="example"></a>範例

  範例，請參閱[CAnimateCtrl::CAnimateCtrl](#canimatectrl)。

##  <a name="play"></a>  CAnimateCtrl::Play

呼叫此函式可播放 AVI 短片中動畫控制項。

```
BOOL Play(
    UINT nFrom,
    UINT nTo,
    UINT nRep);
```

### <a name="parameters"></a>參數

*nFrom*<br/>
框架播放開始處的以零為起始的索引。 值必須小於 65536。 值為 0 表示開頭為 AVI 短片中的第一個框架。

*若要*<br/>
畫面格的以零為起始的索引位置播放結束。 值必須小於 65536。 值為-1 表示結尾為 AVI 短片中的最後一個畫面格。

*nRep*<br/>
若要重新執行在播放 AVI 短片次數。 值為-1 表示無限期地重新執行檔案。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

動畫控制項將會在背景中播放剪輯，而您的執行緒會繼續執行。 如果動畫控制項`ACS_TRANSPARENT`樣式，在播放 AVI 短片就會播放使用透明背景，而不是指定動畫剪輯中的背景色彩。

### <a name="example"></a>範例

  範例，請參閱[CAnimateCtrl::CAnimateCtrl](#canimatectrl)。

##  <a name="seek"></a>  CAnimateCtrl::Seek

呼叫此函數會以靜態方式顯示 AVI 短片的單一框架。

```
BOOL Seek(UINT nTo);
```

### <a name="parameters"></a>參數

*若要*<br/>
要顯示的框架的以零為起始索引。 值必須小於 65536。 值為 0 表示顯示在播放 AVI 短片中的第一個畫面格。 -1 值表示顯示在播放 AVI 短片中的最後一個畫面格。

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="remarks"></a>備註

如果動畫控制項`ACS_TRANSPARENT`樣式，將會使用透明背景繪製 AVI 短片，而非中指定的背景色彩的動畫剪輯。

### <a name="example"></a>範例

  範例，請參閱[CAnimateCtrl::CAnimateCtrl](#canimatectrl)。

##  <a name="stop"></a>  CAnimateCtrl::Stop

呼叫此函式來停止播放 AVI 短片中動畫控制項。

```
BOOL Stop();
```

### <a name="return-value"></a>傳回值

如果成功則不為零，否則為 0。

### <a name="example"></a>範例

  範例，請參閱[CAnimateCtrl::CAnimateCtrl](#canimatectrl)。

## <a name="see-also"></a>另請參閱

[CWnd 類別](../../mfc/reference/cwnd-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[CAnimateCtrl::Create](#create)<br/>
[ON_CONTROL](message-map-macros-mfc.md#on_control)

