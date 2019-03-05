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
ms.openlocfilehash: c800b40fcf2bb3008b35614390e4aafcb43a54f5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296757"
---
# <a name="cbitmapbutton-class"></a>CBitmapButton 類別

建立以點陣圖影像 (而非文字) 標記的按鈕控制項。

## <a name="syntax"></a>語法

```
class CBitmapButton : public CButton
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CBitmapButton::CBitmapButton](#cbitmapbutton)|建構 `CBitmapButton` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CBitmapButton::AutoLoad](#autoload)|在對話方塊中的按鈕關聯的物件`CBitmapButton`類別名稱，以載入 bitmap(s) 和調整大小以符合點陣圖按鈕。|
|[CBitmapButton::LoadBitmaps](#loadbitmaps)|從應用程式的資源檔載入一或多個具名的點陣圖資源，並附加至物件的點陣圖，初始化物件。|
|[CBitmapButton::SizeToContent](#sizetocontent)|調整大小以容納點陣圖按鈕。|

## <a name="remarks"></a>備註

`CBitmapButton` 物件包含最多四個點陣圖，其中包含一個按鈕可以假設的不同狀態的映像： 最新 （或標準），向下 （或選取），已取得焦點，且停用。 只有第一個點陣圖是必要項有些則是選擇性的。

點陣圖按鈕映像包含映像，以及映像本身周圍的框線。 框線通常扮演一個角色中顯示按鈕的狀態。 例如，焦點狀態的點陣圖通常是類似的最新狀態，但與虛線的矩形內凹框線或邊界的粗實線。 點陣圖已停用狀態通常類似於其中的最新狀態，但具有較低對比 （例如呈現暗灰色或灰色的功能表選取項目）。

這些點陣圖可以是任何規模大小，但是會視為如同它們是相同的大小維持在最新狀態的點陣圖。

各種應用程式會要求點陣圖影像的不同組合：

|上移|下移|已取得焦點|已停用|應用程式|
|--------|----------|-------------|--------------|-----------------|
|×||||Bitmap|
|×|×|||按鈕不會 WS_TABSTOP 樣式|
|×|×|×|×|所有狀態，[對話方塊] 按鈕|
|×|×|×||WS_TABSTOP 樣式的 [對話方塊] 按鈕|

在建立點陣圖按鈕控制項時，設定 BS_OWNERDRAW 樣式以指定的是主控描繪按鈕。 這會使 Windows 傳送按鈕; 的 WM_MEASUREITEM 和 WM_DRAWITEM 訊息架構會處理這些訊息，並管理為您按鈕的外觀。

### <a name="to-create-a-bitmap-button-control-in-a-windows-client-area"></a>若要在視窗的工作區中建立的點陣圖按鈕控制項

1. 建立一到四個點陣圖影像的按鈕。

1. 建構[CBitmapButton](#cbitmapbutton)物件。

1. 呼叫[Create](../../mfc/reference/cbutton-class.md#create)函式來建立 Windows 按鈕控制項，並將其附加至`CBitmapButton`物件。

1. 呼叫[LoadBitmaps](#loadbitmaps)成員函式來建構點陣圖按鈕後，請載入點陣圖資源。

### <a name="to-include-a-bitmap-button-control-in-a-dialog-box"></a>若要在對話方塊中包含的點陣圖按鈕控制項

1. 建立一到四個點陣圖影像的按鈕。

1. 建立包含主控描繪按鈕位於您想要的點陣圖按鈕的對話方塊範本。 在範本中按鈕的大小並不重要。

1. 將按鈕的標題設為值，例如"MYIMAGE 」，並定義的符號，例如 IDC_MYIMAGE 按鈕。

1. 在您的應用程式資源指令碼，讓每個按鈕建立識別碼建構所附加的字母"U，""D，""F，"其中一個映像或者"X"（適用於、 關閉、 已取得焦點，且停用） 按鈕標題中所使用的字串到步驟 3。 按鈕標題"MYIMAGE 」 中，例如，識別碼會是"MYIMAGEU"，"MYIMAGED，""MYIMAGEF，"和"MYIMAGEX。 」 您**必須**指定您的點陣圖，雙引號括住的識別碼。 否則資源編輯器會將整數指派給資源，並載入影像時，MFC 將會失敗。

1. 在您的應用程式的對話方塊類別 (衍生自`CDialog`)，新增`CBitmapButton`成員物件。

1. 在 `CDialog`物件的[OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog)常式，呼叫`CBitmapButton`物件的[AutoLoad](#autoload)函式，做為參數使用按鈕的控制項 ID 和`CDialog`物件的**這**指標。

如果您想要處理 Windows 通知訊息，例如 BN_CLICKED，傳送至其父代的點陣圖按鈕控制項 (通常是從衍生的類別`CDialog`)，將新增至`CDialog`-衍生的物件的訊息對應項目和訊息處理常式成員每個訊息的函式。 所傳送的通知`CBitmapButton`物件是所傳送的相同[CButton](../../mfc/reference/cbutton-class.md)物件。

此類別[CToolBar](../../mfc/reference/ctoolbar-class.md)點陣圖按鈕來採取不同的方法。

如需詳細資訊`CBitmapButton`，請參閱 <<c2> [ 控制項](../../mfc/controls-mfc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CBitmapButton`

## <a name="requirements"></a>需求

**標頭：** afxext.h

##  <a name="autoload"></a>  CBitmapButton::AutoLoad

在對話方塊中的按鈕關聯的物件`CBitmapButton`類別名稱，以載入 bitmap(s) 和調整大小以符合點陣圖按鈕。

```
BOOL AutoLoad(
    UINT nID,
    CWnd* pParent);
```

### <a name="parameters"></a>參數

*nID*<br/>
按鈕的控制項 id。

*pParent*<br/>
擁有按鈕的物件指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

使用`AutoLoad`函式來初始化為點陣圖按鈕的對話方塊中的主控描繪按鈕。 中的 < 備註 > 中的指示使用此函式`CBitmapButton`類別。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#75](../../mfc/codesnippet/cpp/cbitmapbutton-class_1.cpp)]

##  <a name="cbitmapbutton"></a>  CBitmapButton::CBitmapButton

建立 `CBitmapButton` 物件。

```
CBitmapButton();
```

### <a name="remarks"></a>備註

建立 c + + 之後`CBitmapButton`物件，請呼叫[CButton::Create](../../mfc/reference/cbutton-class.md#create)來建立 Windows 按鈕控制項，並將其附加至`CBitmapButton`物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#57](../../mfc/codesnippet/cpp/cbitmapbutton-class_2.cpp)]

##  <a name="loadbitmaps"></a>  CBitmapButton::LoadBitmaps

使用此函式，當您想要載入識別依資源名稱或身分證號碼，或您不能使用的點陣圖影像`AutoLoad`函式，因為，比方說，您要建立不是對話方塊中的點陣圖按鈕。

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
指向以 null 結束的字串，其中包含點陣圖按鈕的標準模式或 「 向上 」 狀態的點陣圖名稱。 必要項。

*lpszBitmapResourceSel*<br/>
以 null 終止的字串，其中包含點陣圖的名稱的點陣圖按鈕的選取，或 「 關機 」 狀態的點。 可以是 NULL。

*lpszBitmapResourceFocus*<br/>
指向以 null 結束的字串，其中包含點陣圖的名稱的點陣圖按鈕的焦點狀態。 可以是 NULL。

*lpszBitmapResourceDisabled*<br/>
指向以 null 結束的字串，其中包含的點陣圖按鈕已停用狀態的點陣圖的名稱。 可以是 NULL。

*nIDBitmapResource*<br/>
指定的點陣圖按鈕的標準模式或 「 向上 」 狀態的點陣圖資源的資源識別碼。 必要項。

*nIDBitmapResourceSel*<br/>
點陣圖按鈕的選取，或 「 關機 」 狀態，請指定點陣圖資源的資源識別碼。 可能是 0。

*nIDBitmapResourceFocus*<br/>
指定點陣圖按鈕的焦點狀態的點陣圖資源的資源識別碼。 可能是 0。

*nIDBitmapResourceDisabled*<br/>
指定的點陣圖按鈕已停用狀態的點陣圖資源的資源識別碼。 可能是 0。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#58](../../mfc/codesnippet/cpp/cbitmapbutton-class_3.cpp)]

##  <a name="sizetocontent"></a>  CBitmapButton::SizeToContent

呼叫此函式可調整大小的點陣圖大小的點陣圖按鈕。

```
void SizeToContent();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#59](../../mfc/codesnippet/cpp/cbitmapbutton-class_4.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 範例 CTRLTEST](../../visual-cpp-samples.md)<br/>
[CButton 類別](../../mfc/reference/cbutton-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
