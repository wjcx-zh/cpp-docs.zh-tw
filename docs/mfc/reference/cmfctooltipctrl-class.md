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
ms.openlocfilehash: 6c8bb41b82d1dca9235e1184c2152a61c07c8071
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377347"
---
# <a name="cmfctooltipctrl-class"></a>CMFCToolTipCtrl 類別

根據 [CToolTipCtrl Class](../../mfc/reference/ctooltipctrl-class.md)的擴充工具提示實作。 根據 `CMFCToolTipCtrl` 類別的工具提示可以顯示圖示、標籤和描述。 您可以使用漸層填滿、自訂文字和框線色彩、粗體文字、圓角或氣球樣式，自訂其視覺外觀。

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

## <a name="syntax"></a>語法

```cpp
class CMFCToolTipCtrl : public CToolTipCtrl
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|`CMFCToolTipCtrl::CMFCToolTipCtrl`|預設建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
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

將`CMFCToolTipCtrl``CMFCToolTipInfo`和[CTooltipManager 類](../../mfc/reference/ctooltipmanager-class.md)物件一起使用,在應用程式中實現自訂的工具提示。

例如，若要使用氣球樣式工具提示，請依照下列步驟：

1. 使用[CWinAppEx 類](../../mfc/reference/cwinappex-class.md)方法在應用程式中初始化工具提示管理器。

2. 建立 `CMFCToolTipInfo` 結構來指定您想要的視覺樣式：

    ```cpp
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

3. 使用[CTooltipManager:setTooltipParams](../../mfc/reference/ctooltipmanager-class.md#settooltipparams)方法使用物件中定義的樣式設定應用程式中所有工具提示`CMFCToolTipInfo`的視覺 樣式:

    ```cpp
    theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
        RUNTIME_CLASS (CMFCToolTipCtrl), &params);
    ```

您也可以從 `CMFCToolTipCtrl` 衍生新的類別，以控制工具提示的行為和呈現。 若要指定新的工具提示控制項類別，請使用 `CTooltipManager::SetTooltipParams` 方法：

```cpp
myApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    RUNTIME_CLASS (CMyToolTipCtrl))
```

若要還原預設工具提示控制類別，並將工具提示外觀重設為預設狀態，請在 `SetTooltipParams` 的執行階段類別和工具提示資訊參數中指定 NULL：

```cpp
theApp.GetTooltipManager ()->SetTooltipParams (AFX_TOOLTIP_TYPE_ALL,
    NULL,
    NULL);
```

## <a name="example"></a>範例

下列範例示範如何建構 `CMFCToolTipCtrl` 物件、設定工具提示顯示的描述，以及設定工具提示控制項的寬度。

[!code-cpp[NVC_MFC_RibbonApp#41](../../mfc/reference/codesnippet/cpp/cmfctooltipctrl-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CToolTipCtrl](../../mfc/reference/ctooltipctrl-class.md)

[CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)

## <a name="requirements"></a>需求

**標題:** afxtooltipctrl.h

## <a name="cmfctooltipctrlcmfctooltipctrl"></a><a name="cmfctooltipctrl"></a>CMFCToolTipCtrl::CMFCToolTipCtrl

```cpp
CMFCToolTipCtrl(CMFCToolTipInfo* pParams = NULL);
```

### <a name="parameters"></a>參數

[在]*pParams*<br/>

### <a name="remarks"></a>備註

## <a name="cmfctooltipctrlgeticonsize"></a><a name="geticonsize"></a>CMFCToolTipCtrl::取得圖示大小

傳回工具提示中的圖示大小。

```cpp
virtual CSize GetIconSize();
```

### <a name="return-value"></a>傳回值

圖示的大小(以像素為單位)。

## <a name="cmfctooltipctrlgetparams"></a><a name="getparams"></a>CMFCToolTipCtrl::GetParams

傳回工具提示的顯示設定。

```cpp
const CMFCToolTipInfo& GetParams() const;
```

### <a name="return-value"></a>傳回值

當前工具提示顯示設置 ,這些設置存儲在[CMFCToolTipInfo 類](../../mfc/reference/cmfctooltipinfo-class.md)物件中。

## <a name="cmfctooltipctrlondrawborder"></a><a name="ondrawborder"></a>CMFCToolTipCtrl::在繪製邊框

繪製工具提示的框線。

```cpp
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rect,
    COLORREF clrLine);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向設備上下文的指標。

*矩形*<br/>
[在]工具提示的邊界矩形。

*clrLine*<br/>
[在]邊框顏色。

### <a name="remarks"></a>備註

在派生類中重寫此方法以自定義工具提示邊框的外觀。

## <a name="cmfctooltipctrlondrawdescription"></a><a name="ondrawdescription"></a>CMFCToolTipCtrl::在畫描述

```cpp
virtual CSize OnDrawDescription(
    CDC* pDC,
    CRect rect,
    BOOL bCalcOnly);
```

### <a name="parameters"></a>參數

[在]*pDC*<br/>
[在]*rect*<br/>
[在]*bCalcOnly*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="cmfctooltipctrlondrawicon"></a><a name="ondrawicon"></a>CMFCToolTipctrl::畫中

在工具提示中顯示圖示。

```cpp
virtual BOOL OnDrawIcon(
    CDC* pDC,
    CRect rectImage);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向設備上下文的指標。

*rectImage*<br/>
[在]圖示的座標。

### <a name="return-value"></a>傳回值

如果繪製了圖示,則為 TRUE。 否則,FALSE。

### <a name="remarks"></a>備註

重寫派生類中的此方法以顯示自定義圖示。 您還必須重寫[CMFCToolTipCtrl::GetIconSize](#geticonsize)使工具提示能夠正確計算文本和說明的佈局。

## <a name="cmfctooltipctrlondrawlabel"></a><a name="ondrawlabel"></a>CMFCToolTipCtrl::在DrawLabel

繪製工具提示的標籤，或計算標籤的大小。

```cpp
virtual CSize OnDrawLabel(
    CDC* pDC,
    CRect rect,
    BOOL bCalcOnly);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向設備上下文的指標。

*矩形*<br/>
[在]標籤區域的邊界矩形。

*bCalcOnly*<br/>
[在]如果為 TRUE,將不會繪製標籤。

### <a name="return-value"></a>傳回值

標籤的大小,以像素為單位。

### <a name="remarks"></a>備註

如果要自定義工具提示標籤的外觀,請在派生類中重寫此方法。

## <a name="cmfctooltipctrlondrawseparator"></a><a name="ondrawseparator"></a>CMFCToolTipctrl:OnDraw分離器

工具提示中的標籤和描述之間繪製分隔符號。

```cpp
virtual void OnDrawSeparator(
    CDC* pDC,
    int x1,
    int x2,
    int y);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向設備上下文的指標。

*x1*<br/>
[在]分隔符左端的水平座標。

*x2*<br/>
[在]分隔符右端的水平座標。

*Y*<br/>
[在]分隔符的垂直座標。

### <a name="remarks"></a>備註

預設實現從點 (x1, y) 繪製一條線到點 (x2, y)。

重寫派生類中的此方法以自定義分隔符的外觀。

## <a name="cmfctooltipctrlonfillbackground"></a><a name="onfillbackground"></a>CMFCToolTipctrl::在填充背景

填滿工具提示背景。

```cpp
virtual void OnFillBackground(
    CDC* pDC,
    CRect rect,
    COLORREF& clrText,
    COLORREF& clrLine);
```

### <a name="parameters"></a>參數

*pDC*<br/>
[在]指向設備上下文的指標。

*矩形*<br/>
[在]指定要填充的區域的邊界矩形。

*clrText*<br/>
[在]工具提示前景顏色。

*clrLine*<br/>
[在]邊框的顏色和標籤和描述之間的分隔線。

### <a name="remarks"></a>備註

預設實現填充由*rect*指定的矩形,該矩形的顏色或圖案由最近對[CMFCToolTipCtrl 的呼叫指定::SetParams](#setparams)。

如果要自定義工具提示的外觀,請在派生類中重寫此方法。

## <a name="cmfctooltipctrlsetdescription"></a><a name="setdescription"></a>CMFCToolTipCtrl::設定描述

設定要由工具提示顯示的描述。

```cpp
virtual void SetDescription(const CString strDesrciption);
```

### <a name="parameters"></a>參數

*分吸*<br/>
[在]描述文字。

### <a name="remarks"></a>備註

描述文本顯示在分隔符下的工具提示上。

## <a name="cmfctooltipctrlsetfixedwidth"></a><a name="setfixedwidth"></a>CMFCToolTipCtrl::設定固定寬度

```cpp
void SetFixedWidth(
    int nWidthRegular,
    int nWidthLargeImage);
```

### <a name="parameters"></a>參數

[在]*nWidth 一般*<br/>
[在]*nWidth 大型影像*<br/>

### <a name="remarks"></a>備註

## <a name="cmfctooltipctrlsethotribbonbutton"></a><a name="sethotribbonbutton"></a>CMFCToolTipCtrl::設置Hot功能框按鈕

```cpp
void SetHotRibbonButton(CMFCRibbonButton* pRibbonButton);
```

### <a name="parameters"></a>參數

[在]*p 鍵按鈕*<br/>

### <a name="remarks"></a>備註

## <a name="cmfctooltipctrlsetlocation"></a><a name="setlocation"></a>CMFCToolTipCtrl::設定位置

```cpp
void SetLocation(CPoint pt);
```

### <a name="parameters"></a>參數

[在]*pt*<br/>

### <a name="remarks"></a>備註

## <a name="cmfctooltipctrlsetparams"></a><a name="setparams"></a>CMFCToolTipCtrl::SetParams

使用[CMFCToolTipInfo 類](../../mfc/reference/cmfctooltipinfo-class.md)物件指定工具提示的視覺外觀。

```cpp
void SetParams(CMFCToolTipInfo* pParams);
```

### <a name="parameters"></a>參數

*pParams*<br/>
[在]指向包含顯示參數的[CMFCToolTipInfo 類](../../mfc/reference/cmfctooltipinfo-class.md)物件的指標。

### <a name="remarks"></a>備註

每當顯示工具提示時,都會使用*pParam*指定的顏色和視覺樣式繪製工具提示。 *pParams*的值儲存在受保護`m_Params`的 成員中,該類可以覆蓋具有以下位置的派生類,該類重寫[CMFCToolTipCtrl::OnDrawBorder、CMFCToolTipctr LL:OnDrawIcon、CMFCToolTipctrl:onDrawTtrl、CMFCToolTipctrl:onDrawSeor](#ondrawborder)或[CMFCToolTipctrl:onFillInon](#onfillbackground) [CMFCToolTipCtrl::OnDrawIcon](#ondrawicon) [CMFCToolTipCtrl::OnDrawLabel](#ondrawlabel) [CMFCToolTipCtrl::OnDrawSeparator](#ondrawseparator)

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CToolTipCtrl Class](../../mfc/reference/ctooltipctrl-class.md)<br/>
[CTooltip管理員類別](../../mfc/reference/ctooltipmanager-class.md)<br/>
[CMFCToolTipInfo 類別](../../mfc/reference/cmfctooltipinfo-class.md)<br/>
[CWinAppEx 類別](../../mfc/reference/cwinappex-class.md)
