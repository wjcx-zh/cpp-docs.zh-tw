---
title: CMFCCaptionBar 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar::Create
- AFXCAPTIONBAR/CMFCCaptionBar::DoesAllowDynInsertBefore
- AFXCAPTIONBAR/CMFCCaptionBar::EnableButton
- AFXCAPTIONBAR/CMFCCaptionBar::GetAlignment
- AFXCAPTIONBAR/CMFCCaptionBar::GetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::GetButtonRect
- AFXCAPTIONBAR/CMFCCaptionBar::GetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::IsMessageBarMode
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveButton
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveIcon
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveText
- AFXCAPTIONBAR/CMFCCaptionBar::SetBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::SetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::SetButton
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonPressed
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetFlatBorder
- AFXCAPTIONBAR/CMFCCaptionBar::SetIcon
- AFXCAPTIONBAR/CMFCCaptionBar::SetImageToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::SetText
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBackground
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBorder
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawButton
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawImage
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawText
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBackground
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBorder
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarText
helpviewer_keywords:
- CMFCCaptionBar [MFC], Create
- CMFCCaptionBar [MFC], DoesAllowDynInsertBefore
- CMFCCaptionBar [MFC], EnableButton
- CMFCCaptionBar [MFC], GetAlignment
- CMFCCaptionBar [MFC], GetBorderSize
- CMFCCaptionBar [MFC], GetButtonRect
- CMFCCaptionBar [MFC], GetMargin
- CMFCCaptionBar [MFC], IsMessageBarMode
- CMFCCaptionBar [MFC], RemoveBitmap
- CMFCCaptionBar [MFC], RemoveButton
- CMFCCaptionBar [MFC], RemoveIcon
- CMFCCaptionBar [MFC], RemoveText
- CMFCCaptionBar [MFC], SetBitmap
- CMFCCaptionBar [MFC], SetBorderSize
- CMFCCaptionBar [MFC], SetButton
- CMFCCaptionBar [MFC], SetButtonPressed
- CMFCCaptionBar [MFC], SetButtonToolTip
- CMFCCaptionBar [MFC], SetFlatBorder
- CMFCCaptionBar [MFC], SetIcon
- CMFCCaptionBar [MFC], SetImageToolTip
- CMFCCaptionBar [MFC], SetMargin
- CMFCCaptionBar [MFC], SetText
- CMFCCaptionBar [MFC], OnDrawBackground
- CMFCCaptionBar [MFC], OnDrawBorder
- CMFCCaptionBar [MFC], OnDrawButton
- CMFCCaptionBar [MFC], OnDrawImage
- CMFCCaptionBar [MFC], OnDrawText
- CMFCCaptionBar [MFC], m_clrBarBackground
- CMFCCaptionBar [MFC], m_clrBarBorder
- CMFCCaptionBar [MFC], m_clrBarText
ms.assetid: acb54d5f-14ff-4c96-aeb3-7717cf566d9a
ms.openlocfilehash: c6385cb6bd3eec3ce5fefe0475d771c774777820
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403837"
---
# <a name="cmfccaptionbar-class"></a>CMFCCaptionBar 類別

A`CMFCCaptionBar`物件是一種控制列，可以顯示三個項目： 按鈕、 文字標籤和點陣圖。 它一次只能每個類型各顯示一個項目。 您可以將每個項目對齊控制項的左緣或右緣，或對齊中央。 您也可以將平面或 3D 樣式套用至標題列的上框線和下框線。

## <a name="syntax"></a>語法

```
class CMFCCaptionBar : public CPane
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCCaptionBar::Create](#create)|會建立標題列控制項，並將它附加至`CMFCCaptionBar`物件。|
|[CMFCCaptionBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|指出是否可以在標題列和其父框架之間動態插入另一個窗格。 (覆寫[cbasepane:: Doesallowdyninsertbefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore)。)|
|[CMFCCaptionBar::EnableButton](#enablebutton)|啟用或停用在標題列按鈕。|
|[CMFCCaptionBar::GetAlignment](#getalignment)|傳回指定之項目的對齊方式。|
|[CMFCCaptionBar::GetBorderSize](#getbordersize)|傳回的標題列的框線大小。|
|[CMFCCaptionBar::GetButtonRect](#getbuttonrect)|擷取在標題列按鈕的週框矩形。|
|[CMFCCaptionBar::GetMargin](#getmargin)|傳回的標題列項目邊緣和標題列控制項的邊緣之間的距離。|
|[CMFCCaptionBar::IsMessageBarMode](#ismessagebarmode)|指定是否在訊息列模式中的標題列。|
|[CMFCCaptionBar::RemoveBitmap](#removebitmap)|移除的標題列中的點陣圖影像。|
|[CMFCCaptionBar::RemoveButton](#removebutton)|移除的標題列中的按鈕。|
|[CMFCCaptionBar::RemoveIcon](#removeicon)|移除的標題列中的圖示。|
|[CMFCCaptionBar::RemoveText](#removetext)|移除的標題列中的文字標籤。|
|[CMFCCaptionBar::SetBitmap](#setbitmap)|設定標題列的點陣圖影像。|
|[CMFCCaptionBar::SetBorderSize](#setbordersize)|設定標題列的框線大小。|
|[CMFCCaptionBar::SetButton](#setbutton)|設定標題列按鈕。|
|[CMFCCaptionBar::SetButtonPressed](#setbuttonpressed)|指定是否要保持已按下按鈕。|
|[CMFCCaptionBar::SetButtonToolTip](#setbuttontooltip)|設定按鈕的工具提示。|
|[CMFCCaptionBar::SetFlatBorder](#setflatborder)|設定標題列的框線樣式。|
|[CMFCCaptionBar::SetIcon](#seticon)|設定標題列的圖示。|
|[CMFCCaptionBar::SetImageToolTip](#setimagetooltip)|設定標題列的映像的工具提示。|
|[CMFCCaptionBar::SetMargin](#setmargin)|設定標題列項目的邊緣和標題列控制項的邊緣之間的距離。|
|[CMFCCaptionBar::SetText](#settext)|設定標題列的文字標籤。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CMFCCaptionBar::OnDrawBackground](#ondrawbackground)|由架構呼叫以填滿的標題列的背景。|
|[CMFCCaptionBar::OnDrawBorder](#ondrawborder)|由架構呼叫以繪製的標題列的框線。|
|[CMFCCaptionBar::OnDrawButton](#ondrawbutton)|由架構呼叫以繪製標題列按鈕。|
|[CMFCCaptionBar::OnDrawImage](#ondrawimage)|由架構呼叫以繪製的標題列映像。|
|[CMFCCaptionBar::OnDrawText](#ondrawtext)|由架構呼叫以繪製的標題列文字。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMFCCaptionBar::m_clrBarBackground](#m_clrbarbackground)|標題列背景色彩。|
|[CMFCCaptionBar::m_clrBarBorder](#m_clrbarborder)|標題列的框線色彩。|
|[CMFCCaptionBar::m_clrBarText](#m_clrbartext)|標題列文字的色彩。|

## <a name="remarks"></a>備註

若要建立的標題列，請遵循下列步驟：

1. 建構 `CMFCCaptionBar` 物件。 一般而言，您會將標題列加入框架視窗類別。

1. 呼叫[CMFCCaptionBar::Create](#create)方法來建立標題列控制項，並將其附加至`CMFCCaptionBar`物件。

1. 呼叫[CMFCCaptionBar::SetButton](#setbutton)， [CMFCCaptionBar::SetText](#settext)， [CMFCCaptionBar::SetIcon](#seticon)，和[CMFCCaptionBar::SetBitmap](#setbitmap)來設定標題列項目。

當您設定的按鈕項目時，您必須指派至按鈕的命令 ID。 當使用者按一下按鈕時，標題列將路由傳送到父框架視窗有這個 ID 的 WM_COMMAND 訊息。

標題列也可在訊息列模式中，可模擬 Microsoft Office 2007 應用程式中出現的訊息列。 在訊息列模式中，標題列會顯示點陣圖、 訊息和按鈕 （通常會開啟一個對話方塊。）您可以將工具提示指派到點陣圖中。

若要啟用訊息捲軸模式，請呼叫[CMFCCaptionBar::Create](#create)並設定為 TRUE 的第四個參數 (bIsMessageBarMode)。

## <a name="example"></a>範例

下例示範如何在 `CMFCCaptionBar` 類別中使用各種方法。 此範例示範如何建立標題列控制項、 設定標題列的 3D 框線、 設定像素為單位，項目列標題的邊緣和標題列控制項的邊緣之間的距離，、 設定標題列按鈕設定按鈕的工具提示、 標題列的文字標籤設定、 設定標題列中，點陣圖影像以及設定影像的工具提示的標題列中。 此程式碼片段是一部分[MS Office 2007 示範範例](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_MSOffice2007Demo#1](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_1.h)]
[!code-cpp[NVC_MFC_MSOffice2007Demo#2](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCCaptionBar](../../mfc/reference/cmfccaptionbar-class.md)

## <a name="requirements"></a>需求

**標頭：** afxcaptionbar.h

##  <a name="create"></a>  CMFCCaptionBar::Create

會建立標題列控制項，並將它附加至`CMFCCaptionBar`物件。

```
BOOL Create(
    DWORD dwStyle,
    CWnd* pParentWnd,
    UINT uID,
    int nHeight=-1,
    BOOL bIsMessageBarMode=FALSE);
```

### <a name="parameters"></a>參數

*dwStyle*<br/>
邏輯 OR 運算子組合的標題列的樣式。

*pParentWnd*<br/>
標題列控制項的父視窗。

*uID*<br/>
標題列控制項的 ID。

*nHeight*<br/>
像素為單位，標題列控制項的高度。 如果是-1，則會根據圖示、 文字和標題列控制項顯示的按鈕的高度計算高度。

*bIsMessageBarMode*<br/>
標題列中訊息捲軸模式; 如果為 TRUEFALSE 否則。

### <a name="return-value"></a>傳回值

如果成功，建立標題列控制項，則為 TRUE。FALSE 否則。

### <a name="remarks"></a>備註

您建構`CMFCCaptionBar`兩個步驟中的物件。 您第一次呼叫建構函式，然後再呼叫`Create`方法，它會建立 Windows 控制項，並將它附加至`CMFCCaptionBar`物件。

##  <a name="doesallowdyninsertbefore"></a>  CMFCCaptionBar::DoesAllowDynInsertBefore

指出是否可以在標題列和其父框架之間動態插入另一個窗格。

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>傳回值

除非覆寫，則傳回 FALSE。

### <a name="remarks"></a>備註

##  <a name="enablebutton"></a>  CMFCCaptionBar::EnableButton

啟用或停用在標題列按鈕。

```
void EnableButton(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>參數

*bEnable*<br/>
[in]True 以啟用按鈕，FALSE 以停用按鈕。

##  <a name="getalignment"></a>  CMFCCaptionBar::GetAlignment

傳回指定之項目的對齊方式。

```
BarElementAlignment GetAlignment(BarElement elem);
```

### <a name="parameters"></a>參數

*elem*<br/>
[in]要擷取對齊標題列項目。

### <a name="return-value"></a>傳回值

項目，例如按鈕、 點陣圖、 文字或圖示的對齊方式。

### <a name="remarks"></a>備註

項目的對齊方式可以是下列值之一：

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

##  <a name="getbordersize"></a>  CMFCCaptionBar::GetBorderSize

傳回的標題列的框線大小。

```
int GetBorderSize() const;
```

### <a name="return-value"></a>傳回值

單位為像素框線的大小。

##  <a name="getbuttonrect"></a>  CMFCCaptionBar::GetButtonRect

擷取在標題列按鈕的週框矩形。

```
CRect GetButtonRect() const;
```

### <a name="return-value"></a>傳回值

A`CRect`物件，其中包含在標題列按鈕的週框矩形的座標。

##  <a name="getmargin"></a>  CMFCCaptionBar::GetMargin

傳回的標題列項目邊緣和標題列控制項的邊緣之間的距離。

```
int GetMargin() const;
```

### <a name="return-value"></a>傳回值

距離，單位為像素的標題列項目邊緣的標題列控制項邊緣之間。

##  <a name="ismessagebarmode"></a>  CMFCCaptionBar::IsMessageBarMode

指定是否在訊息列模式中的標題列。

```
BOOL IsMessageBarMode() const;
```

### <a name="return-value"></a>傳回值

標題列中訊息捲軸模式; 如果為 TRUEFALSE 否則。

### <a name="remarks"></a>備註

在訊息列模式中，標題列會顯示工具提示、 訊息文字與按鈕影像。

##  <a name="m_clrbarbackground"></a>  CMFCCaptionBar::m_clrBarBackground

標題列背景色彩。

```
COLORREF m_clrBarBackground
```

##  <a name="m_clrbarborder"></a>  CMFCCaptionBar::m_clrBarBorder

標題列的框線色彩。

```
COLORREF m_clrBarBorder
```

##  <a name="m_clrbartext"></a>  CMFCCaptionBar::m_clrBarText

標題列文字的色彩。

```
COLORREF m_clrBarText
```

##  <a name="ondrawbackground"></a>  CMFCCaptionBar::OnDrawBackground

由架構呼叫以填滿的標題列的背景。

```
virtual void OnDrawBackground(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]裝置內容的標題列的指標。

*rect*<br/>
[in]要填滿的週框矩形。

### <a name="remarks"></a>備註

`OnDrawBackground`填滿的標題列的背景時，會呼叫方法。 使用的預設實作填滿的背景[CMFCCaptionBar::m_clrBarBackground](#m_clrbarbackground)色彩。

覆寫這個方法在`CMFCCaptionBar`衍生類別，以自訂的標題列的外觀。

##  <a name="ondrawborder"></a>  CMFCCaptionBar::OnDrawBorder

由架構呼叫以繪製的標題列的框線。

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]裝置內容，用來顯示框線。

*rect*<br/>
[in]週框的矩形。

### <a name="remarks"></a>備註

根據預設，框線會有一般的樣式。

覆寫這個方法在`CMFCCaptionBar`衍生類別，以自訂的標題列的框線外觀。

##  <a name="ondrawbutton"></a>  CMFCCaptionBar::OnDrawButton

由架構呼叫以繪製標題列按鈕。

```
virtual void OnDrawButton(
    CDC* pDC,
    CRect rect,
    const CString& strButton,
    BOOL bEnabled);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]用來顯示按鈕的裝置內容指標。

*rect*<br/>
[in]按鈕的週框。

*strButton*<br/>
[in]按鈕的文字標籤。

*bEnabled*<br/>
[in]如果已啟用按鈕，則為 TRUE。FALSE 否則。

### <a name="remarks"></a>備註

覆寫這個方法在`CMFCCaptionBar`衍生類別，來自訂標題列按鈕的外觀。

##  <a name="ondrawimage"></a>  CMFCCaptionBar::OnDrawImage

由架構呼叫以繪製的標題列映像。

```
virtual void OnDrawImage(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]用來顯示影像的裝置內容指標。

*rect*<br/>
[in]指定影像的週框矩形。

### <a name="remarks"></a>備註

覆寫這個方法在`CMFCCaptionBar`衍生類別，以自訂映像的外觀。

##  <a name="ondrawtext"></a>  CMFCCaptionBar::OnDrawText

由架構呼叫以繪製的標題列文字。

```
virtual void OnDrawText(
    CDC* pDC,
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[in]用來顯示按鈕的裝置內容指標。

*rect*<br/>
[in]文字的週框。

*strText*<br/>
[in]要顯示的文字字串。

### <a name="remarks"></a>備註

使用的預設實作會顯示的文字`CDC::DrawText`並[CMFCCaptionBar::m_clrBarText](#m_clrbartext)色彩。

覆寫這個方法在`CMFCCaptionBar`衍生類別，以自訂的標題列的文字外觀。

##  <a name="removebitmap"></a>  CMFCCaptionBar::RemoveBitmap

移除的標題列中的點陣圖影像。

```
void RemoveBitmap();
```

##  <a name="removebutton"></a>  CMFCCaptionBar::RemoveButton

移除的標題列中的按鈕。

```
void RemoveButton();
```

### <a name="remarks"></a>備註

會自動調整的標題列項目配置。

##  <a name="removeicon"></a>  CMFCCaptionBar::RemoveIcon

移除的標題列中的圖示。

```
void RemoveIcon();
```

##  <a name="removetext"></a>  CMFCCaptionBar::RemoveText

移除的標題列中的文字標籤。

```
void RemoveText();
```

##  <a name="setbitmap"></a>  CMFCCaptionBar::SetBitmap

設定標題列的點陣圖影像。

```
void SetBitmap(
    HBITMAP hBitmap,
    COLORREF clrTransparent,
    BOOL bStretch=FALSE,
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);

void SetBitmap(
    UINT uiBmpResID,
    COLORREF clrTransparent,
    BOOL bStretch=FALSE,
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>參數

*hBitmap*<br/>
[in]若要設定點陣圖控制代碼。

*clrTransparent*<br/>
[in]指定點陣圖的透明色彩的 RGB 值。

*bStretch*<br/>
[in]如果為 TRUE，如果它不符合影像週框矩形，會自動縮放點陣圖。 否則點陣圖不會自動縮放。

*bmpAlignment*<br/>
[in]點陣圖的對齊方式。

### <a name="remarks"></a>備註

這個方法可用於設定在標題列上的點陣圖。

先前的點陣圖，會自動終結。 如果標題列顯示的圖示，因為您呼叫[CMFCCaptionBar::SetIcon](#seticon)方法，將不會顯示點陣圖，除非您移除圖示，藉由呼叫[CMFCCaptionBar::RemoveIcon](#removeicon)。

點陣圖會對齊依照*bmpAlignment*參數。  這個參數可以是下列其中一個 `BarElementAlignment` 值：

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

##  <a name="setbordersize"></a>  CMFCCaptionBar::SetBorderSize

設定標題列的框線大小。

```
void SetBorderSize(int nSize);
```

### <a name="parameters"></a>參數

*nSize*<br/>
[in]新的大小，單位為像素的標題列框線。

##  <a name="setbutton"></a>  CMFCCaptionBar::SetButton

設定標題列按鈕。

```
void SetButton(
    LPCTSTR lpszLabel,
    UINT uiCmdUI,
    BarElementAlignment btnAlignmnet=ALIGN_LEFT,
    BOOL bHasDropDownArrow=TRUE);
```

### <a name="parameters"></a>參數

*lpszLabel*<br/>
按鈕的命令的標籤。

*uiCmdUI*<br/>
按鈕的命令識別碼。

*btnAlignmnet*<br/>
按鈕的對齊方式。

*bHasDropDownArrow*<br/>
按鈕會顯示下拉式箭號，FALSE 否則，其值為 TRUE。

##  <a name="setbuttonpressed"></a>  CMFCCaptionBar::SetButtonPressed

指定是否要保持已按下按鈕。

```
void SetButtonPressed(BOOL bPresed=TRUE);
```

### <a name="parameters"></a>參數

*bPresed*<br/>
如果按鈕已按下的狀態，FALSE 否則，則為 TRUE。

##  <a name="setbuttontooltip"></a>  CMFCCaptionBar::SetButtonToolTip

設定按鈕的工具提示。

```
void SetButtonToolTip(
    LPCTSTR lpszToolTip,
    LPCTSTR lpszDescription=NULL);
```

### <a name="parameters"></a>參數

*lpszToolTip*<br/>
[in]工具提示的標題。

*lpszDescription*<br/>
[in]工具提示描述。

##  <a name="setflatborder"></a>  CMFCCaptionBar::SetFlatBorder

設定標題列的框線樣式。

```
void SetFlatBorder(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>參數

*bFlat*<br/>
[in]標題列的框線是平面的其值為 TRUE。 如果框線是 3D，則為 FALSE。

##  <a name="seticon"></a>  CMFCCaptionBar::SetIcon

設定標題列的圖示。

```
void SetIcon(
    HICON hIcon,
    BarElementAlignment iconAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>參數

*hIcon*<br/>
[in]若要設定圖示的控制代碼。

*iconAlignment*<br/>
[in]圖示的對齊方式。

### <a name="remarks"></a>備註

標題列可以顯示圖示或點陣圖。 請參閱[CMFCCaptionBar::SetBitmap](#setbitmap)若要了解如何顯示點陣圖。 如果您設定圖示和點陣圖，一律會顯示圖示。 呼叫[CMFCCaptionBar::RemoveIcon](#removeicon)若要移除的標題列中的圖示。

圖示靠根據*iconAlignment*參數。 它可以是下列其中一種`BarElementAlignment`值：

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

##  <a name="setimagetooltip"></a>  CMFCCaptionBar::SetImageToolTip

設定影像的工具提示的標題列中。

```
void SetImageToolTip(
    LPCTSTR lpszToolTip,
    LPCTSTR lpszDescription=NULL);
```

### <a name="parameters"></a>參數

*lpszToolTip*<br/>
[in]工具提示文字。

*lpszDescription*<br/>
[in]工具提示描述。

##  <a name="setmargin"></a>  CMFCCaptionBar::SetMargin

設定標題列項目的邊緣和標題列控制項的邊緣之間的距離。

```
void SetMargin(int nMargin);
```

### <a name="parameters"></a>參數

*nMargin*<br/>
[in]距離，單位為像素的標題列項目邊緣的標題列控制項邊緣之間。

##  <a name="settext"></a>  CMFCCaptionBar::SetText

設定標題列的文字標籤。

```
void SetText(
    const CString& strText,
    BarElementAlignment textAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>參數

*strText*<br/>
[in]若要設定文字字串。

*textAlignment*<br/>
[in]文字的對齊方式。

### <a name="remarks"></a>備註

對齊的文字標籤所指定*textAlignment*參數。 它可以是下列其中一種`BarElementAlignment`值：

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
