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
ms.openlocfilehash: c052f913f68d1890a470ed8a6aae2882ed181863
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352722"
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
|[C 位地圖按鈕::C 位地圖按鈕](#cbitmapbutton)|建構 `CBitmapButton` 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CBitmap 按鈕:自動載入](#autoload)|對話框中的按鈕與`CBitmapButton`類的物件關聯,按名稱載入點陣圖,並調整按鈕的大小以適合位圖。|
|[C 位地圖按鈕::載入點映射](#loadbitmaps)|通過從應用程式的資源檔載入一個或多個命名點陣圖資源並將點陣圖附加到物件來初始化物件。|
|[CBitmap 按鈕::大小到內容](#sizetocontent)|調整按鈕的大小以適應位圖。|

## <a name="remarks"></a>備註

`CBitmapButton`物件最多包含四個位圖,其中包含按鈕可以假定的不同狀態的圖像:向上(或正常)、向下(或選中)、聚焦和禁用。 只需要第一個位圖;其他是可選的。

位圖按鈕圖像包括圖像周圍的邊框以及圖像本身。 邊框通常在顯示按鈕的狀態時發揮作用。 例如,焦點狀態的位圖通常類似於向上狀態的位圖,但從邊框中設置虛線矩形或邊框處的粗實線。 禁用狀態的位圖通常類似於向上狀態的位圖,但對比度較低(如灰色或灰色菜單選擇)。

這些位圖的大小可以是任意大小的,但所有位圖都被視為與上狀態的位圖大小相同。

各種應用程式需要點陣圖影像的不同組合:

|上移|向下|已取得焦點|已停用|Application|
|--------|----------|-------------|--------------|-----------------|
|×||||點陣圖|
|×|×|||無WS_TABSTOP樣式的按鈕|
|×|×|×|×|具有所有狀態的對話框按鍵|
|×|×|×||具有WS_TABSTOP樣式的對話框按鈕|

創建點陣圖按鈕控制件時,請設置BS_OWNERDRAW樣式以指定按鈕是所有者繪製的。 這將導致 Windows 發送按鈕的WM_MEASUREITEM和WM_DRAWITEM消息;因此,Windows 會為按鈕發送WM_MEASUREITEM消息,然後WM_DRAWITEM消息。框架處理這些消息,並為您管理按鈕的外觀。

### <a name="to-create-a-bitmap-button-control-in-a-windows-client-area"></a>在視窗的工作區中建立點陣圖按鍵控制項

1. 為按鈕創建一到四個位圖圖像。

1. 構造[CBitmapButton](#cbitmapbutton)物件。

1. 呼叫["創建"](../../mfc/reference/cbutton-class.md#create)函數以建立 Windows 按鈕控制項`CBitmapButton`並將其附加到 物件。

1. 調用[LoadBitmap](#loadbitmaps)成員函數,在建構位圖按鈕後載入位圖資源。

### <a name="to-include-a-bitmap-button-control-in-a-dialog-box"></a>在對話框包含點陣圖按鈕控制項

1. 為按鈕創建一到四個位圖圖像。

1. 創建一個對話方塊範本,其中包含所有者繪製按鈕,該按鈕位於所需的位圖按鈕的位置。 範本中按鈕的大小並不重要。

1. 將按鈕的標題設置為"MYIMAGE"等值,並為按鈕定義符號,如IDC_MYIMAGE。

1. 在應用程式的資源腳本中,為為按鈕創建的每個圖像提供一個 ID,該 ID 通過將其中一個字母"U"、"D"、"F"或"X"(用於向上、向下、焦點和禁用)添加到步驟 3 中用於按鈕標題的字串中。 例如,對於按鈕標題"MYIMAGE",ID將是"MYIMAGEU"、"MYIMAGED"、"MYIMAGEF"和"MYIMAGEX"。 **您必須**在雙引號中指定位圖的 ID。 否則,資源編輯器將為資源分配整數,並且 MFC 在載入映射時將失敗。

1. 在應用程式的對話方塊類中(派生`CDialog`自 ),添加`CBitmapButton`成員物件。

1. `CDialog`在物件的[OnInitDialog](../../mfc/reference/cdialog-class.md#oninitdialog)程式程`CBitmapButton`中, 呼叫物件的[自動載入](#autoload)函數,將按鈕`CDialog`的控制 ID 和物件的**此**指標用作參數。

如果要處理由位圖按鈕控制件發送到其父級(通常是派生自`CDialog`的類)發送到其父級(通常從`CDialog`派生 物件的 Windows 通知訊息,如BN_CLICKED。 `CBitmapButton`物件發送的通知與[CButton](../../mfc/reference/cbutton-class.md)物件發送的通知相同。

類[CToolBar](../../mfc/reference/ctoolbar-class.md)對位圖按鈕採取了不同的方法。

有關 的詳細`CBitmapButton`資訊 ,請參閱[控制項](../../mfc/controls-mfc.md)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

`CBitmapButton`

## <a name="requirements"></a>需求

**標題:** afxext.h

## <a name="cbitmapbuttonautoload"></a><a name="autoload"></a>CBitmap 按鈕:自動載入

對話框中的按鈕與`CBitmapButton`類的物件關聯,按名稱載入點陣圖,並調整按鈕的大小以適合位圖。

```
BOOL AutoLoad(
    UINT nID,
    CWnd* pParent);
```

### <a name="parameters"></a>參數

*nID*<br/>
按鈕的控制識別碼。

*pParent*<br/>
指向擁有按鈕的物件的指標。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="remarks"></a>備註

使用`AutoLoad`函數將對話方塊中的所有者繪製按鈕初始化為位圖按鈕。 有關使用此函式的說明在類別的備註中`CBitmapButton`。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#75](../../mfc/codesnippet/cpp/cbitmapbutton-class_1.cpp)]

## <a name="cbitmapbuttoncbitmapbutton"></a><a name="cbitmapbutton"></a>C 位地圖按鈕::C 位地圖按鈕

建立 `CBitmapButton` 物件。

```
CBitmapButton();
```

### <a name="remarks"></a>備註

創建C++`CBitmapButton`物件後,調用[CButton::創建](../../mfc/reference/cbutton-class.md#create)以創建 Windows 按鈕控制`CBitmapButton`項並將其附加到 物件。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#57](../../mfc/codesnippet/cpp/cbitmapbutton-class_2.cpp)]

## <a name="cbitmapbuttonloadbitmaps"></a><a name="loadbitmaps"></a>C 位地圖按鈕::載入點映射

如果要載入由其資源名稱或 ID 號識別的位貼圖影像,或者由於創建不是對話框一`AutoLoad`部分的點陣圖按鈕而無法使用該函數時,請使用此功能。

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

*lpszBitmap資源*<br/>
包含點陣圖按鈕正常或「向上」狀態的點陣圖名稱的 null 連接端的字串。 必要。

*lpszBitmap 資源塞爾*<br/>
指向包含點陣圖按鈕所選或「向下」狀態的位圖名稱的 null 連接端字串。 可能是 NULL。

*lpszBitmap 資源焦點*<br/>
包含點陣圖按鍵焦點狀態的點陣圖名稱的 null 連接字串。 可能是 NULL。

*lpszBitmap 資源已關閉*<br/>
包含點陣圖鍵關閉狀態的點陣圖名稱的 null 的字串。 可能是 NULL。

*nIDBitmap資源*<br/>
指定點陣圖按鈕的正常或「向上」狀態的位圖資源的資源 ID 號。 必要。

*nIDBitmap 資源塞爾*<br/>
指定點陣圖按鈕的選定或「向下」狀態的位圖資源的資源 ID 號。 可能為 0。

*nIDBitmap 資源焦點*<br/>
指定點陣圖按鈕的聚焦狀態點陣圖資源的資源 ID 號。 可能為 0。

*nIDBitmap 資源已關閉*<br/>
指定點陣圖按鈕關閉狀態的圖資源的資源 ID 號。 可能為 0。

### <a name="return-value"></a>傳回值

如果成功則為非零；否則為 0。

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#58](../../mfc/codesnippet/cpp/cbitmapbutton-class_3.cpp)]

## <a name="cbitmapbuttonsizetocontent"></a><a name="sizetocontent"></a>CBitmap 按鈕::大小到內容

呼叫此函數以將點陣圖按鈕的大小調整到位圖的大小。

```
void SizeToContent();
```

### <a name="example"></a>範例

[!code-cpp[NVC_MFCControlLadenDialog#59](../../mfc/codesnippet/cpp/cbitmapbutton-class_4.cpp)]

## <a name="see-also"></a>另請參閱

[MFC 樣品 CTRLTEST](../../overview/visual-cpp-samples.md)<br/>
[CButton 類別](../../mfc/reference/cbutton-class.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)
