---
title: CBitmapButton 類別
ms.date: 11/04/2016
f1_keywords:
- CBitmapButton
- AFXEXT/CBitmapButton
- AFXEXT/CBitmapButton::CBitmapButton
- AFXEXT/CBitmapButton::AutoLoad
- AFXEXT/CBitmapButton::LoadBitmaps
- AFXEXT/CBitmapButton::SizeToContent
helpviewer_keywords:
- CBitmapButton [MFC], CBitmapButton
- CBitmapButton [MFC], AutoLoad
- CBitmapButton [MFC], LoadBitmaps
- CBitmapButton [MFC], SizeToContent
ms.assetid: 9ad6cb45-c3c4-4fb1-96d3-1fe3df7bbcfc
ms.openlocfilehash: 0cf4554f86f4a9275e4d96b3db519fde7fb05b22
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231867"
---
# <a name="cbitmapbutton-class"></a>CBitmapButton 類別

建立以點陣圖影像 (而非文字) 標記的按鈕控制項。

## <a name="syntax"></a>語法

```
class CBitmapButton : public CButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|說明|
|----------|-----------------|
|[CBitmapButton：： CBitmapButton](#cbitmapbutton)|建構 `CBitmapButton` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CBitmapButton：： AutoLoad](#autoload)|將對話方塊中的按鈕與類別的物件產生關聯 `CBitmapButton` 、依名稱載入點陣圖，然後調整按鈕大小以符合點陣圖。|
|[CBitmapButton：： LoadBitmaps](#loadbitmaps)|從應用程式的資源檔載入一或多個名為點陣圖資源，並將點陣圖附加至物件，以初始化物件。|
|[CBitmapButton：： System.windows.window.sizetocontent](#sizetocontent)|調整按鈕大小以配合點陣圖。|

## <a name="remarks"></a>備註

`CBitmapButton`物件最多包含四個位圖，其中包含按鈕可假設的各種不同狀態影像：向上（或正常）、向下（或選取）、焦點和停用。 只需要第一個點陣圖;其他則是選擇性的。

點陣圖按鈕影像包括影像周圍的框線，以及影像本身。 框線通常會在顯示按鈕狀態的部分中播放。 例如，焦點狀態的點陣圖通常類似于 [啟動] 狀態，但有一個虛線矩形是從框線或框線的粗實線。 停用狀態的點陣圖通常類似于啟動狀態，但對比度較低（例如暗灰色或灰色的功能表選取專案）。

這些點陣圖可以是任何大小，但全都會被視為與 up 狀態點陣圖的大小相同。

各種應用程式需要不同的點陣圖影像組合：

|Up|Down|已取得焦點|停用|應用程式|
|--------|----------|-------------|--------------|-----------------|
|×||||點陣圖|
|×|×|||沒有 WS_TABSTOP 樣式的按鈕|
|×|×|×|×|包含所有狀態的對話方塊按鈕|
|×|×|×||具有 WS_TABSTOP 樣式的對話方塊按鈕|

建立點陣圖按鈕控制項時，請將 BS_OWNERDRAW 樣式設定為指定按鈕為主控描繪。 這會導致 Windows 傳送按鈕的 WM_MEASUREITEM 和 WM_DRAWITEM 訊息;架構會處理這些訊息，並為您管理按鈕的外觀。

### <a name="to-create-a-bitmap-button-control-in-a-windows-client-area"></a>在視窗的工作區中建立點陣圖按鈕控制項

1. 為按鈕建立一到四個位圖影像。

1. 建立[CBitmapButton](#cbitmapbutton)物件。

1. 呼叫[create](../../mfc/reference/cbutton-class.md#create)函式來建立 Windows 按鈕控制項，並將它附加至 `CBitmapButton` 物件。

1. 呼叫[LoadBitmaps](#loadbitmaps)成員函式，以在結構化按鈕建立之後載入點陣圖資源。

### <a name="to-include-a-bitmap-button-control-in-a-dialog-box"></a>在對話方塊中包含點陣圖按鈕控制項

1. 為按鈕建立一到四個位圖影像。

1. 建立具有 [主控描繪] 按鈕的對話方塊範本，而您想要在其中放置點陣圖按鈕。 範本中的按鈕大小並不重要。

1. 將按鈕的標題設定為值（例如 "MYIMAGE"），並定義按鈕的符號，例如 IDC_MYIMAGE。

1. 在應用程式的資源腳本中，為按鈕所建立的每個影像提供一個識別碼，方法是將其中一個字母 "U"、"D"、"F" 或 "X" （針對向上、向下、已停用）附加至步驟3中用於按鈕標題的字串。 例如，針對按鈕標題 "MYIMAGE"，識別碼會是 "MYIMAGEU"、"MYIMAGED"、"MYIMAGEF" 和 "MYIMAGEX"。 您**必須**在雙引號內指定點陣圖的識別碼。 否則，資源編輯器會將整數指派給資源，而 MFC 會在載入影像時失敗。

1. 在應用程式的對話方塊類別（衍生自 `CDialog` ）中，加入 `CBitmapButton` 成員物件。

1. 在 `CDialog` 物件的[OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog)常式中，呼叫 `CBitmapButton` 物件的[AutoLoad](#autoload)函式，並使用按鈕的控制項 ID 和 `CDialog` 物件的指標，做為參數 **`this`** 。

如果您想要處理 Windows 通知訊息，例如 BN_CLICKED，由點陣圖按鈕控制項傳送至其父系（通常是衍生自的類別 `CDialog` ），請將 `CDialog` 每個訊息的訊息對應專案和訊息處理常式成員函式新增至衍生物件。 物件所傳送的通知與 `CBitmapButton` [CButton](../../mfc/reference/cbutton-class.md)物件所傳送的通知相同。

[類別[CToolBar](../../mfc/reference/ctoolbar-class.md) ] 會採用不同的方式來點陣圖按鈕。

如需的詳細資訊 `CBitmapButton` ，請參閱[控制項](../../mfc/controls-mfc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CBitmapButton`

## <a name="requirements"></a>需求

**標頭：** afxext.h。h

## <a name="cbitmapbuttonautoload"></a><a name="autoload"></a>CBitmapButton：： AutoLoad

將對話方塊中的按鈕與類別的物件產生關聯 `CBitmapButton` 、依名稱載入點陣圖，然後調整按鈕大小以符合點陣圖。

```
BOOL AutoLoad(
    UINT nID,
    CWnd* pParent);
```

### <a name="parameters"></a>參數

*nID*<br/>
按鈕的控制項 ID。

*pParent*<br/>
擁有按鈕之物件的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

使用函 `AutoLoad` 式，將對話方塊中的主控描繪按鈕初始化為點陣圖按鈕。 使用此函式的指示位於類別的備註中 `CBitmapButton` 。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#75](../../mfc/codesnippet/cpp/cbitmapbutton-class_1.cpp)]

## <a name="cbitmapbuttoncbitmapbutton"></a><a name="cbitmapbutton"></a>CBitmapButton：： CBitmapButton

建立 `CBitmapButton` 物件。

```
CBitmapButton();
```

### <a name="remarks"></a>備註

建立 c + + `CBitmapButton` 物件之後，請呼叫[CButton：： create](../../mfc/reference/cbutton-class.md#create)來建立 Windows 按鈕控制項，並將它附加至 `CBitmapButton` 物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#57](../../mfc/codesnippet/cpp/cbitmapbutton-class_2.cpp)]

## <a name="cbitmapbuttonloadbitmaps"></a><a name="loadbitmaps"></a>CBitmapButton：： LoadBitmaps

當您想要載入以資源名稱或識別碼編號識別的點陣圖影像，或無法使用函式時，請使用此函式， `AutoLoad` 因為您正在建立不屬於對話方塊的點陣圖按鈕。

```
BOOL LoadBitmaps(
    LPCTSTR lpszBitmapResource,
    LPCTSTR lpszBitmapResourceSel = NULL,
    LPCTSTR lpszBitmapResourceFocus = NULL,
    LPCTSTR lpszBitmapResourceDisabled = NULL);

BOOL LoadBitmaps(
    UINT nIDBitmapResource,
    UINT nIDBitmapResourceSel = 0,
    UINT nIDBitmapResourceFocus = 0,
    UINT nIDBitmapResourceDisabled = 0);
```

### <a name="parameters"></a>參數

*lpszBitmapResource*<br/>
指向以 null 終止的字串，其中包含點陣圖按鈕之法線或 "up" 狀態的點陣圖名稱。 必要。

*lpszBitmapResourceSel*<br/>
指向以 null 終止的字串，其中包含點陣圖按鈕已選取或「向下」狀態的點陣圖名稱。 可能是 NULL。

*lpszBitmapResourceFocus*<br/>
指向以 null 終止的字串，其中包含點陣圖按鈕焦點狀態的點陣圖名稱。 可能是 NULL。

*lpszBitmapResourceDisabled*<br/>
指向以 null 終止的字串，其中包含點陣圖按鈕已停用狀態的點陣圖名稱。 可能是 NULL。

*nIDBitmapResource*<br/>
為點陣圖按鈕的一般或「上」狀態指定點陣圖資源的資源識別碼。 必要。

*nIDBitmapResourceSel*<br/>
針對點陣圖按鈕的已選取或「向下」狀態，指定點陣圖資源的資源識別碼。 可能是0。

*nIDBitmapResourceFocus*<br/>
為點陣圖按鈕的焦點狀態指定點陣圖資源的資源識別碼。 可能是0。

*nIDBitmapResourceDisabled*<br/>
為點陣圖按鈕的停用狀態指定點陣圖資源的資源識別碼。 可能是0。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#58](../../mfc/codesnippet/cpp/cbitmapbutton-class_3.cpp)]

## <a name="cbitmapbuttonsizetocontent"></a><a name="sizetocontent"></a>CBitmapButton：： System.windows.window.sizetocontent

呼叫此函式可將點陣圖按鈕的大小調整為點陣圖的大小。

```cpp
void SizeToContent();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#59](../../mfc/codesnippet/cpp/cbitmapbutton-class_4.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[CButton 類別](../../mfc/reference/cbutton-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
