---
title: CMFCToolTipInfo 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCToolTipInfo
- AFXTOOLTIPCTRL/CMFCToolTipInfo
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bBalloonTooltip
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bBoldLabel
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawDescription
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawIcon
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bDrawSeparator
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bRoundedCorners
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_bVislManagerTheme
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrBorder
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrFill
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrFillGradient
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_clrText
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_nGradientAngle
- AFXTOOLTIPCTRL/CMFCToolTipInfo::m_nMaxDescrWidth
helpviewer_keywords:
- CMFCToolTipInfo [MFC], m_bBalloonTooltip
- CMFCToolTipInfo [MFC], m_bBoldLabel
- CMFCToolTipInfo [MFC], m_bDrawDescription
- CMFCToolTipInfo [MFC], m_bDrawIcon
- CMFCToolTipInfo [MFC], m_bDrawSeparator
- CMFCToolTipInfo [MFC], m_bRoundedCorners
- CMFCToolTipInfo [MFC], m_bVislManagerTheme
- CMFCToolTipInfo [MFC], m_clrBorder
- CMFCToolTipInfo [MFC], m_clrFill
- CMFCToolTipInfo [MFC], m_clrFillGradient
- CMFCToolTipInfo [MFC], m_clrText
- CMFCToolTipInfo [MFC], m_nGradientAngle
- CMFCToolTipInfo [MFC], m_nMaxDescrWidth
ms.assetid: f9d3d7f8-1f08-4342-a7b2-683860e5d2a5
ms.openlocfilehash: 000a2fd33928e59685efa6f145406542a4935819
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377341"
---
# <a name="cmfctooltipinfo-class"></a>CMFCToolTipInfo 類別

儲存工具提示視覺外觀的相關資訊。

## <a name="syntax"></a>語法

```
class CMFCToolTipInfo
```

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CMFCToolTipInfo::operator=](#operator_eq)||

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMFCTool提示資訊::m_bBalloonTooltip](#m_bballoontooltip)|一個布林值變數，指出工具提示是否有氣球外觀。|
|[CMFCToolTipInfo::m_bBoldLabel](#m_bboldlabel)|一個布林值變數，指出工具提示標籤是否以粗體字顯示。|
|[CMFCToolTipInfo::m_bDrawDescription](#m_bdrawdescription)|一個布林值變數，指出工具提示是否包含描述。|
|[CMFCToolTipInfo::m_bDrawIcon](#m_bdrawicon)|一個布林值變數，指出工具提示是否包含圖示。|
|[CMFCToolTipInfo::m_bDrawSeparator](#m_bdrawseparator)|一個布林值變數，指出是否要在工具提示標籤與工具提示描述之間顯示分隔符號。|
|[CMFCToolTipInfo::m_bRoundedCorners](#m_broundedcorners)|一個布林值變數，指出工具提示是否有圓角。|
|[CMFCToolTipInfo::m_bVislManagerTheme](#m_bvislmanagertheme)|一個布爾變數,指示工具提示的外觀是否應由可視化管理器控制(請參閱[CMFCVisual Manager 類](../../mfc/reference/cmfcvisualmanager-class.md))。|
|[CMFCToolTipInfo::m_clrBorder](#m_clrborder)|工具提示框線的色彩。|
|[CMFCToolTipInfo::m_clrFill](#m_clrfill)|工具提示背景的色彩。|
|[CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient)|工具提示中填入的漸層色彩。|
|[CMFCToolTipInfo::m_clrText](#m_clrtext)|工具提示的文字色彩。|
|[CMFCToolTipInfo::m_nGradientAngle](#m_ngradientangle)|工具提示中填入的漸層角度。|
|[CMFCToolTipInfo::m_nMaxDescrWidth](#m_nmaxdescrwidth)|工具提示描述的最大可能寬度，以像素為單位。|

## <a name="remarks"></a>備註

將[CMFCToolTipCtrl](../../mfc/reference/cmfctooltipctrl-class.md)`CMFCToolTipInfo`類和[CTooltipManager 類](../../mfc/reference/ctooltipmanager-class.md)一起使用,在應用程式中實現自訂的工具提示。 有關如何使用這些工具提示類別的範例,請參閱[CMFCToolTipCtrl 類別主題](../../mfc/reference/cmfctooltipctrl-class.md)。

## <a name="example"></a>範例

下列範例示範如何設定 `CMFCToolTipInfo` 類別中各種成員變數的值。

[!code-cpp[NVC_MFC_RibbonApp#42](../../mfc/reference/codesnippet/cpp/cmfctooltipinfo-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)

## <a name="requirements"></a>需求

**標題:** afxtooltipctrl.h

## <a name="cmfctooltipinfom_bballoontooltip"></a><a name="m_bballoontooltip"></a>CMFCTool提示資訊::m_bBalloonTooltip

指定所有工具提示的顯示樣式。

```
BOOL m_bBalloonTooltip;
```

### <a name="remarks"></a>備註

TRUE 表示工具提示使用氣球樣式,FALSE 表示工具提示使用矩形樣式。

## <a name="cmfctooltipinfom_bboldlabel"></a><a name="m_bboldlabel"></a>CMFCTool提示資訊::m_bBoldLabel

指定工具提示文字的字型是否為粗體。

```
BOOL m_bBoldLabel;
```

### <a name="remarks"></a>備註

將此成員設置為 TRUE 以顯示帶有粗體字型的工具提示文本,或將 FALSE 設定為顯示非粗體字型的工具提示標籤。

## <a name="cmfctooltipinfom_bdrawdescription"></a><a name="m_bdrawdescription"></a>CMFCTool提示資訊::m_bDrawDescription

指定每個工具提示是否顯示描述文本。

```
BOOL m_bDrawDescription;
```

### <a name="remarks"></a>備註

將此成員設定為 TRUE 以顯示說明,或 FALSE 以隱藏說明。 您可以通過呼叫[CMFCToolTipCtrl:::設定描述](../../mfc/reference/cmfctooltipctrl-class.md#setdescription)來指定工具提示上的說明

## <a name="cmfctooltipinfom_bdrawicon"></a><a name="m_bdrawicon"></a>CMFCTool提示資訊::m_bDrawIcon

指定是否顯示所有工具提示顯示圖示。

```
BOOL m_bDrawIcon;
```

### <a name="remarks"></a>備註

將此成員設置為 TRUE 以在每個工具提示上顯示圖示,或「FALSE」顯示沒有圖示的工具提示。

## <a name="cmfctooltipinfom_bdrawseparator"></a><a name="m_bdrawseparator"></a>CMFCTool提示資訊::m_bDrawSeparator

指定每個工具提示的標籤和說明之間是否有分隔符。

```
BOOL m_bDrawSeparator;
```

### <a name="remarks"></a>備註

將此成員設定為 TRUE 以在工具提示標籤和說明之間顯示分隔符,或將 FALSE 設定為顯示沒有分隔符的工具提示。

## <a name="cmfctooltipinfom_broundedcorners"></a><a name="m_broundedcorners"></a>CMFCTool提示資訊::m_bRoundedCorners

指定所有工具提示是否具有圓角。

```
BOOL m_bRoundedCorners;
```

### <a name="remarks"></a>備註

將此成員設置為 TRUE 以在工具提示上顯示圓角,或「FALSE」以在工具提示上顯示矩形角。

## <a name="cmfctooltipinfom_clrborder"></a><a name="m_clrborder"></a>CMFCTool提示資訊:m_clrBorder

指定所有工具提示上的邊框顏色。

```
COLORREF m_clrBorder;
```

## <a name="cmfctooltipinfom_clrfill"></a><a name="m_clrfill"></a>CMFCTool提示資訊::m_clrFill

指定工具提示背景的顏色。

```
COLORREF m_clrFill;
```

### <a name="remarks"></a>備註

如果[CMFCToolTipInfo:m_clrFillGradient](#m_clrfillgradient)為 -1,則工具`m_clrFill`提示背景顏色為 。 否則,`m_clrFill`指定漸變開頭的顏色,`m_clrFillGradient`並指定漸變末尾的顏色。 [CMFCToolTipInfo:m_nGradientAngle](#m_ngradientangle)確定漸變的方向。

## <a name="cmfctooltipinfom_clrfillgradient"></a><a name="m_clrfillgradient"></a>CMFCTool提示資訊:m_clrFillGradient

指定工具提示漸變背景的結束顏色。

```
COLORREF m_clrFillGradient;
```

### <a name="remarks"></a>備註

如果`m_clrFillGradient`為 -1,則沒有漸變。 否則,漸變初始顏色由[CMFCToolTipInfo::m_clrFill](#m_clrfill)指定,漸變完成顏色`m_clrFillGradient`由 指定 。 [CMFCToolTipInfo:m_nGradientAngle](#m_ngradientangle)確定漸變的方向。

## <a name="cmfctooltipinfom_clrtext"></a><a name="m_clrtext"></a>CMFCTool提示資訊::m_clrText

指定所有工具提示的文字顏色。

```
COLORREF m_clrText;
```

## <a name="cmfctooltipinfom_ngradientangle"></a><a name="m_ngradientangle"></a>CMFCTool提示資訊::m_nGradientAngle

指定在工具提示的背景上繪製漸變的角度。

```
int m_nGradientAngle;
```

### <a name="remarks"></a>備註

`m_nGradientAngle`指定工具尖背景上的漸變與水準偏移的角度(以度表示)。 如果`m_nGradientAngle`為 0,則從左向右繪製漸變。 如果`m_nGradientAngle`介於 1 和 360 之間,則漸變按該度數順時針旋轉。 如果`m_nGradientAngle`為 -1(預設值),則漸變從上到下繪製。 這與設置為`m_nGradientAngle`90 相同。

[CMFCToolTipInfo::m_clrFill](#m_clrfill)`clrFill`指定漸變開頭的顏色[,CMFCToolTipInfo::m_clrFillGradient](#m_clrfillgradient)`clrFillGradient`指定漸變末端的顏色。 如果`m_clrFillGradient`為 -1,則沒有漸變。

## <a name="cmfctooltipinfom_nmaxdescrwidth"></a><a name="m_nmaxdescrwidth"></a>CMFCTool提示資訊::m_nMaxDescrWidth

指定它在每個工具提示中顯示的描述的最大寬度。 如果描述寬度超過指定值,則換行文本。

```
int m_nMaxDescrWidth;
```

## <a name="cmfctooltipinfom_bvislmanagertheme"></a><a name="m_bvislmanagertheme"></a>CMFCTool提示資訊::m_bVislManagerTheme

指定應用程式的視覺化管理員是否控制所有工具提示的外觀。

```
BOOL m_bVislManagerTheme;
```

### <a name="remarks"></a>備註

如果`m_bVislManagerTheme`為 TRUE,則每個工具提示都會在應用程式的視覺管理器出現在螢幕上之前向應用程式的視覺管理員請求新的[CMFCToolTipInfo,](../../mfc/reference/cmfctooltipinfo-class.md)並使用該物件中的值來確定它們的外觀。 [您的 CMFCToolTipInfo](../../mfc/reference/cmfctooltipinfo-class.md)的其他成員將被忽略。

## <a name="cmfctooltipinfooperator"></a><a name="operator_eq"></a>CMFCTool提示資訊::操作員*

有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

```
CMFCToolTipInfo& operator=(CMFCToolTipInfo& src);
```

### <a name="parameters"></a>參數

[在]*斯爾克*<br/>

### <a name="return-value"></a>傳回值

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CTooltip管理員類別](../../mfc/reference/ctooltipmanager-class.md)<br/>
[CMFCToolTipCtrl 類別](../../mfc/reference/cmfctooltipctrl-class.md)
