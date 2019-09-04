---
title: CMFCToolTipCtrl 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCToolTipCtrl
- AFXTOOLTIPCTRL/CMFCToolTipCtrl
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::GetIconSize
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::GetParams
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawBorder
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawDescription
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawIcon
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawLabel
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnDrawSeparator
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::OnFillBackground
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetDescription
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetFixedWidth
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetHotRibbonButton
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetLocation
- AFXTOOLTIPCTRL/CMFCToolTipCtrl::SetParams
helpviewer_keywords:
- CMFCToolTipCtrl [MFC], GetIconSize
- CMFCToolTipCtrl [MFC], GetParams
- CMFCToolTipCtrl [MFC], OnDrawBorder
- CMFCToolTipCtrl [MFC], OnDrawDescription
- CMFCToolTipCtrl [MFC], OnDrawIcon
- CMFCToolTipCtrl [MFC], OnDrawLabel
- CMFCToolTipCtrl [MFC], OnDrawSeparator
- CMFCToolTipCtrl [MFC], OnFillBackground
- CMFCToolTipCtrl [MFC], SetDescription
- CMFCToolTipCtrl [MFC], SetFixedWidth
- CMFCToolTipCtrl [MFC], SetHotRibbonButton
- CMFCToolTipCtrl [MFC], SetLocation
- CMFCToolTipCtrl [MFC], SetParams
ms.assetid: 9fbfcfb1-a8ab-417f-ae29-9a9ca85ee58f
ms.openlocfilehash: 5376fd21f84411c86ade564d7c76d073ccb909a6
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273684"
---
# <a name="cmfctooltipctrl-class"></a>CMFCToolTipCtrl 類別

根據 [CToolTipCtrl Class](../../mfc/reference/ctooltipctrl-class.md)的擴充工具提示實作。 根據 `CMFCToolTipCtrl` 類別的工具提示可以顯示圖示、標籤和描述。 您可以使用漸層填滿、自訂文字和框線色彩、粗體文字、圓角或氣球樣式，自訂其視覺外觀。

如需詳細資訊, 請參閱位於 Visual Studio 安裝**的\\VC\\atlmfc\\src mfc**資料夾中的原始程式碼。

## <a name="syntax"></a>語法

```
class CMFCToolTipCtrl : public CToolTipCtrl
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|`CMFCToolTipCtrl::CMFCToolTipCtrl`|預設建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CMFCToolTipCtrl::GetIconSize](#geticonsize)|傳回工具提示中的圖示大小。|
|[CMFCToolTipCtrl::GetParams](#getparams)|傳回工具提示的顯示設定。|
|[CMFCToolTipCtrl::OnDrawBorder](#ondrawborder)|繪製工具提示的框線。|
|[CMFCToolTipCtrl::OnDrawDescription](#ondrawdescription)||
|[CMFCToolTipCtrl::OnDrawIcon](#ondrawicon)|在工具提示中顯示圖示。|
|[CMFCToolTipCtrl::OnDrawLabel](#ondrawlabel)|繪製工具提示的標籤，或計算標籤的大小。|
|[CMFCToolTipCtrl::OnDrawSeparator](#ondrawseparator)|工具提示中的標籤和描述之間繪製分隔符號。|
|[CMFCToolTipCtrl::OnFillBackground](#onfillbackground)|填滿工具提示背景。|
|[CMFCToolTipCtrl::SetDescription](#setdescription)|設定要由工具提示顯示的描述。|
|[CMFCToolTipCtrl::SetFixedWidth](#setfixedwidth)||
|[CMFCToolTipCtrl::SetHotRibbonButton](#sethotribbonbutton)||
|[CMFCToolTipCtrl::SetLocation](#setlocation)||
|[CMFCToolTipCtrl::SetParams](#setparams)|使用 `CMFCToolTipInfo` 物件指定工具提示的視覺外觀。|

## <a name="remarks"></a>備註

使用`CMFCToolTipCtrl` 、`CMFCToolTipInfo`和[CTooltipManager 類別](../../mfc/reference/ctooltipmanager-class.md)物件, 在您的應用程式中執行自訂的工具提示。

例如，若要使用氣球樣式工具提示，請依照下列步驟：

1. 使用[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)方法, 初始化應用程式中的工具提示管理員。

2. 建立 `CMFCToolTipInfo` 結構來指定您想要的視覺樣式：

```
CMFCToolTipInfo params;
params.m_bBoldLabel = FALSE;
params.m_bDrawDescription = FALSE;
params.m_bDrawIcon = FALSE;
params.m_bRoundedCorners = TRUE;
params.m_bDrawSeparator = FALSE;
if (m_bCustomColors)
{
    params.m_clrFill = RGB (255, 255, 255);
    params.m_clrFillGradient = RGB (228, 228, 240);
    params.m_clrText = RGB (61, 83, 80);
    params.m_clrBorder = RGB (144, 149, 168);

}
```
3. 使用[CTooltipManager:: SetTooltipParams](../../mfc/reference/ctooltipmanager-class.md#settooltipparams)方法, 即可使用`CMFCToolTipInfo`物件中定義的樣式, 為應用程式中的所有工具提示設定視覺化樣式:

```
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    RUNTIME_CLASS (CMFCToolTipCtrl), &params);
```
您也可以從 `CMFCToolTipCtrl` 衍生新的類別，以控制工具提示的行為和呈現。 若要指定新的工具提示控制項類別，請使用 `CTooltipManager::SetTooltipParams` 方法：

```
myApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    RUNTIME_CLASS (CMyToolTipCtrl))
```
若要還原預設工具提示控制類別，並將工具提示外觀重設為預設狀態，請在 `SetTooltipParams` 的執行階段類別和工具提示資訊參數中指定 NULL：

```
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    NULL,
    NULL);
```

## <a name="example"></a>範例

下列範例示範如何建構 `CMFCToolTipCtrl` 物件、設定工具提示顯示的描述，以及設定工具提示控制項的寬度。

[!code-cpp[NVC_MFC_RibbonApp#41](../../mfc/reference/codesnippet/cpp/cmfctooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)

[CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)

## <a name="requirements"></a>需求

**標頭:** afxtooltipctrl。h

##  <a name="cmfctooltipctrl"></a>CMFCToolTipCtrl:: CMFCToolTipCtrl

```
CMFCToolTipCtrl(CMFCToolTipInfo* pParams = NULL);
```

### <a name="parameters"></a>參數

在*pParams*<br/>

### <a name="remarks"></a>備註

##  <a name="geticonsize"></a>CMFCToolTipCtrl:: GetIconSize

傳回工具提示中的圖示大小。

```
virtual CSize GetIconSize();
```

### <a name="return-value"></a>傳回值

圖示的大小 (以圖元為單位)。

##  <a name="getparams"></a>CMFCToolTipCtrl:: GetParams

傳回工具提示的顯示設定。

```
const CMFCToolTipInfo& GetParams() const;
```

### <a name="return-value"></a>傳回值

目前的工具提示顯示設定, 儲存在[CMFCToolTipInfo 類別](../../mfc/reference/cmfctooltipinfo-class.md)物件中。

##  <a name="ondrawborder"></a>CMFCToolTipCtrl:: OnDrawBorder

繪製工具提示的框線。

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rect,
    COLORREF clrLine);
```

### <a name="parameters"></a>參數

*pDC*<br/>
在裝置內容的指標。

*rect*<br/>
在工具提示的周框。

*clrLine*<br/>
在框線色彩。

### <a name="remarks"></a>備註

覆寫衍生類別中的這個方法, 以自訂工具提示框線的外觀。

##  <a name="ondrawdescription"></a>  CMFCToolTipCtrl::OnDrawDescription

```
virtual CSize OnDrawDescription(
    CDC* pDC,
    CRect rect,
    BOOL bCalcOnly);
```

### <a name="parameters"></a>參數

[in] *pDC*<br/>
在*rect*<br/>
在*bCalcOnly*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

##  <a name="ondrawicon"></a>  CMFCToolTipCtrl::OnDrawIcon

在工具提示中顯示圖示。

```
virtual BOOL OnDrawIcon(
    CDC* pDC,
    CRect rectImage);
```

### <a name="parameters"></a>參數

*pDC*<br/>
在裝置內容的指標。

*rectImage*<br/>
在圖示的座標。

### <a name="return-value"></a>傳回值

如果已繪製圖示, 則為 TRUE。 否則為 FALSE。

### <a name="remarks"></a>備註

覆寫衍生類別中的這個方法, 以顯示自訂圖示。 您也必須覆寫[CMFCToolTipCtrl:: GetIconSize](#geticonsize) , 讓工具提示能夠正確地計算文字和描述的版面配置。

##  <a name="ondrawlabel"></a>  CMFCToolTipCtrl::OnDrawLabel

繪製工具提示的標籤，或計算標籤的大小。

```
virtual CSize OnDrawLabel(
    CDC* pDC,
    CRect rect,
    BOOL bCalcOnly);
```

### <a name="parameters"></a>參數

*pDC*<br/>
在裝置內容的指標。

*rect*<br/>
在標籤區域的周框。

*bCalcOnly*<br/>
在若為 TRUE, 則不會繪製標籤。

### <a name="return-value"></a>傳回值

標籤的大小 (以圖元為單位)。

### <a name="remarks"></a>備註

如果您想要自訂工具提示標籤的外觀, 請在衍生類別中覆寫這個方法。

##  <a name="ondrawseparator"></a>  CMFCToolTipCtrl::OnDrawSeparator

工具提示中的標籤和描述之間繪製分隔符號。

```
virtual void OnDrawSeparator(
    CDC* pDC,
    int x1,
    int x2,
    int y);
```

### <a name="parameters"></a>參數

*pDC*<br/>
在裝置內容的指標。

*x1*<br/>
在分隔符號左邊端的水準座標。

*x2*<br/>
在分隔符號右端的水準座標。

*Y*<br/>
在分隔符號的垂直座標。

### <a name="remarks"></a>備註

預設的執行會從點 (x1, y) 繪製一條線到點 (x2, y)。

覆寫衍生類別中的這個方法, 以自訂分隔符號的外觀。

##  <a name="onfillbackground"></a>  CMFCToolTipCtrl::OnFillBackground

填滿工具提示背景。

```
virtual void OnFillBackground(
    CDC* pDC,
    CRect rect,
    COLORREF& clrText,
    COLORREF& clrLine);
```

### <a name="parameters"></a>參數

*pDC*<br/>
在裝置內容的指標。

*rect*<br/>
在指定要填滿之區域的周框。

*clrText*<br/>
在工具提示前景色彩。

*clrLine*<br/>
在標籤和描述之間的框線色彩和分隔線。

### <a name="remarks"></a>備註

預設的執行會以最新的[CMFCToolTipCtrl:: SetParams](#setparams)呼叫所指定的色彩或模式, 填滿矩形所指定的矩形。

如果您想要自訂工具提示的外觀, 請在衍生類別中覆寫這個方法。

##  <a name="setdescription"></a>  CMFCToolTipCtrl::SetDescription

設定要由工具提示顯示的描述。

```
virtual void SetDescription(const CString strDesrciption);
```

### <a name="parameters"></a>參數

*strDesrciption*<br/>
在描述文字。

### <a name="remarks"></a>備註

[描述] 文字會顯示在 [工具提示] 下的分隔符號底下。

##  <a name="setfixedwidth"></a>CMFCToolTipCtrl:: SetFixedWidth

```
void SetFixedWidth(
    int nWidthRegular,
    int nWidthLargeImage);
```

### <a name="parameters"></a>參數

[in] *nWidthRegular*<br/>
[in] *nWidthLargeImage*<br/>

### <a name="remarks"></a>備註

##  <a name="sethotribbonbutton"></a>CMFCToolTipCtrl:: SetHotRibbonButton

```
void SetHotRibbonButton(CMFCRibbonButton* pRibbonButton);
```

### <a name="parameters"></a>參數

在*pRibbonButton*<br/>

### <a name="remarks"></a>備註

##  <a name="setlocation"></a>  CMFCToolTipCtrl::SetLocation

```
void SetLocation(CPoint pt);
```

### <a name="parameters"></a>參數

[in] *pt*<br/>

### <a name="remarks"></a>備註

##  <a name="setparams"></a>  CMFCToolTipCtrl::SetParams

使用[CMFCToolTipInfo 類別](../../mfc/reference/cmfctooltipinfo-class.md)物件, 指定工具提示的視覺外觀。

```
void SetParams(CMFCToolTipInfo* pParams);
```

### <a name="parameters"></a>參數

*pParams*<br/>
在[CMFCToolTipInfo 類別](../../mfc/reference/cmfctooltipinfo-class.md)物件的指標, 其中包含顯示參數。

### <a name="remarks"></a>備註

每當顯示工具提示時, 就會使用*pParams*指定的色彩和視覺化樣式繪製。 *PParams*的值會儲存在 protected 成員`m_Params`中, 而衍生類別可加以存取, 覆寫[CMFCToolTipCtrl:: OnDrawBorder](#ondrawborder)、 [CMFCToolTipCtrl:: OnDrawIcon](#ondrawicon)、 [CMFCToolTipCtrl:: OnDrawLabel](#ondrawlabel)、 [CMFCToolTipCtrl:: OnDrawSeparator](#ondrawseparator)或[CMFCToolTipCtrl:: OnFillBackground](#onfillbackground) , 以維護指定的外觀。

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CToolTipCtrl 類別](../../mfc/reference/ctooltipctrl-class.md)<br/>
[CTooltipManager 類別](../../mfc/reference/ctooltipmanager-class.md)<br/>
[CMFCToolTipInfo 類別](../../mfc/reference/cmfctooltipinfo-class.md)<br/>
[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)
