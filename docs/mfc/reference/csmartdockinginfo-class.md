---
title: CSmartDockingInfo 類別
ms.date: 11/19/2018
f1_keywords:
- CSmartDockingInfo
- AFXDOCKINGMANAGER/CSmartDockingInfo
- AFXDOCKINGMANAGER/CSmartDockingInfo::CopyTo
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_bUseThemeColorInShading
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrBaseBackground
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrToneDest
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrToneSrc
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_clrTransparent
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_nCentralGroupOffset
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_sizeTotal
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_uiMarkerBmpResID
- AFXDOCKINGMANAGER/CSmartDockingInfo::m_uiMarkerLightBmpResID
helpviewer_keywords:
- CSmartDockingInfo [MFC], CopyTo
- CSmartDockingInfo [MFC], m_bUseThemeColorInShading
- CSmartDockingInfo [MFC], m_clrBaseBackground
- CSmartDockingInfo [MFC], m_clrToneDest
- CSmartDockingInfo [MFC], m_clrToneSrc
- CSmartDockingInfo [MFC], m_clrTransparent
- CSmartDockingInfo [MFC], m_nCentralGroupOffset
- CSmartDockingInfo [MFC], m_sizeTotal
- CSmartDockingInfo [MFC], m_uiMarkerBmpResID
- CSmartDockingInfo [MFC], m_uiMarkerLightBmpResID
ms.assetid: cab04f38-4bc1-4378-9337-c56fc87fbd68
ms.openlocfilehash: c0ccb9f728add37230cbfd88cc8f6c9b1696fa2e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318232"
---
# <a name="csmartdockinginfo-class"></a>CSmartDockingInfo 類別

定義智慧停駐標記的外觀。

## <a name="syntax"></a>語法

```
class CSmartDockingInfo : public CObject
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|`CSmartDockingInfo::CSmartDockingInfo`|預設建構函式。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CSmartDocking資訊::複製到](#copyto)|將當前智慧停靠資訊參數複製到提供的[CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md)物件中。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CSmartDocking資訊:m_bUseThemeColorInShading](#m_busethemecolorinshading)|指定在框架顯示智慧停靠標記時是否使用當前主題顏色。|
|[CSmartDocking資訊::m_clrBaseBackground](#m_clrbasebackground)|指定智慧停靠標記的基本背景顏色。|
|[CSmartDocking資訊:m_clrToneDest](#m_clrtonedest)|指定在智慧停靠標記點`m_clrToneSrc`圖中替換的顏色。|
|[CSmartDocking資訊:m_clrToneSrc](#m_clrtonesrc)|指定智慧停靠標記位圖的顏色。|
|[CSmartDocking資訊:m_clrTransparent](#m_clrtransparent)|指定智慧停靠標記點圖在透明時的顏色。|
|[CSmartDocking資訊:m_nCentralGroupOffset](#m_ncentralgroupoffset)|指定智慧停靠標記的中心組與中心組矩形邊界的偏移量。|
|[CSmartDocking資訊:m_sizeTotal](#m_sizetotal)|指定組中所有智慧停靠標記的總大小。|
|[CSmartDocking資訊:m_uiMarkerBmpResID](#m_uimarkerbmpresid)|定義框架用於未突出顯示的智慧停靠標記的點陣圖的資源標識。|
|[CSmartDocking資訊:m_uiMarkerLightBmpResID](#m_uimarkerlightbmpresid)|定義框架用於突出顯示的智慧停靠標記的位圖的資源標識。|

## <a name="remarks"></a>備註

框架在內部處理智慧停靠標記。 下圖顯示了標準智慧停靠標記:

![智慧停駐的標準標記](../../mfc/reference/media/nextsdmarkers.png "智慧停駐的標準標記")

在此圖中,左側的圖像顯示未啟用與選項卡停靠的中心組智慧停靠標記。 中間的圖像顯示右邊緣智慧停靠標記。 右側的圖像顯示一個中央組智慧停靠標記,該標記已啟用了停靠選項卡。 中央組智慧停靠標記具有主位圖和五個智慧停靠標記位圖。

您可以自訂智慧嵌入標記的以下參數:

- 色彩。 例如,您可以將圖形中標記的藍色替換為任何使用者定義的顏色。

- 透明顏色。

- 中心組中智慧停靠標記的偏移量與邊界矩形的邊框。

- 表示中心組的主位圖。

- 表示常規和突出顯示的智慧停靠標記的位圖。

下圖顯示了已自訂的智慧停靠標記的範例:

![智慧停駐的自訂標記](../../mfc/reference/media/nextsdmarkerscustom.png "智慧停駐的自訂標記")

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md)

## <a name="requirements"></a>需求

**標題:** afxDockingManager.h

## <a name="csmartdockinginfocopyto"></a><a name="copyto"></a>CSmartDocking資訊::複製到

將當前智慧停靠參數複製到提供的[CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md)物件中。

```
void CopyTo(CSmartDockingInfo& params);
```

### <a name="parameters"></a>參數

*params*<br/>
[出]使用當前智慧停靠`CSmartDockingInfo`參數填充的類型物件。

## <a name="csmartdockinginfom_busethemecolorinshading"></a><a name="m_busethemecolorinshading"></a>CSmartDocking資訊:m_bUseThemeColorInShading

指定在框架顯示智慧停靠標記時是否使用當前主題顏色。

```
BOOL m_bUseThemeColorInShading;
```

### <a name="remarks"></a>備註

如果為 TRUE,則使用當前主題顏色繪製標記;如果為 TRUE,則使用當前主題顏色繪製標記。否則標記用淺藍色繪製。

預設值為 FALSE。

## <a name="csmartdockinginfom_clrbasebackground"></a><a name="m_clrbasebackground"></a>CSmartDocking資訊::m_clrBaseBackground

指定智慧停靠標記的基本背景顏色。

```
COLORREF m_clrBaseBackground;
```

## <a name="csmartdockinginfom_clrtonedest"></a><a name="m_clrtonedest"></a>CSmartDocking資訊:m_clrToneDest

指定將在智慧停靠標記點`m_clrToneSrc`圖中替換的顏色。

```
COLORREF m_clrToneDest;
```

### <a name="remarks"></a>備註

設定此值以以程式設計方式更改標記點圖的顏色。 例如,如果要更改框架中提供的標準標記的顏色,則將此值設置為所需的顏色。 默認情況下[,CSmartDockingInfo::m_clrToneSrc](#m_clrtonesrc)設置為 RGB(61、123、241)(藍色)。

要改變自訂標記的顏色,必須選擇`m_clrToneDest`與`m_clrToneSrc`。

## <a name="csmartdockinginfom_clrtonesrc"></a><a name="m_clrtonesrc"></a>CSmartDocking資訊:m_clrToneSrc

指定智慧停靠標記位圖的顏色。

```
COLORREF m_clrToneSrc;
```

### <a name="remarks"></a>備註

僅當要將自定義位圖的顏色替換為其他顏色時,才設置此值。 如果要更改標準(提供的框架)標記的顏色,則不必設置此值。

用於`(COLORREF)-1`使智慧停靠組的成員為空。

## <a name="csmartdockinginfom_clrtransparent"></a><a name="m_clrtransparent"></a>CSmartDocking資訊:m_clrTransparent

指定智慧停靠標記點圖在透明時的顏色。

```
COLORREF m_clrTransparent;
```

### <a name="remarks"></a>備註

在停靠組中顯示自訂標記和自定義點陣圖時,必須設置此值。

## <a name="csmartdockinginfom_ncentralgroupoffset"></a><a name="m_ncentralgroupoffset"></a>CSmartDocking資訊:m_nCentralGroupOffset

指定智慧停靠標記的中心組和中心組矩形的邊界之間的偏移量。

```
int m_nCentralGroupOffset;
```

### <a name="remarks"></a>備註

如果要更改自定義標記和智慧停靠標記中央組的邊界之間的預設偏移量,請指定此值。 預設偏移量為 5 圖元。

## <a name="csmartdockinginfom_sizetotal"></a><a name="m_sizetotal"></a>CSmartDocking資訊:m_sizeTotal

指定包含中心組中所有智慧停靠標記的邊界矩形的總大小。

```
CSize m_sizeTotal;
```

### <a name="remarks"></a>備註

設置為`m_sizeTotal`中心組標記的邊界矩形的大小。 如果要對標記使用自定義點陣圖,則需要指定此值。

## <a name="csmartdockinginfom_uimarkerbmpresid"></a><a name="m_uimarkerbmpresid"></a>CSmartDocking資訊:m_uiMarkerBmpResID

定義用於非突出顯示自定義智慧停靠標記的點陣圖的資源標識。

```
UINT m_uiMarkerBmpResID[AFX_SD_MARKERS_NUM];
```

### <a name="remarks"></a>備註

用表示智慧停靠標記的位圖的資源標識填充此陣列。 AFX_SD_MARKERS_NUM當前定義為 5。 以如下方式填充陣列:

```cpp
params.m_uiMarkerBmpResID[0] = IDB_MARKER_LEFT;
params.m_uiMarkerBmpResID[1] = IDB_MARKER_RIGHT;
params.m_uiMarkerBmpResID[2] = IDB_MARKER_TOP;
params.m_uiMarkerBmpResID[3] = IDB_MARKER_BOTTOM;
params.m_uiMarkerBmpResID[4] = IDB_MARKER_CENTER;
```

## <a name="csmartdockinginfom_uimarkerlightbmpresid"></a><a name="m_uimarkerlightbmpresid"></a>CSmartDocking資訊:m_uiMarkerLightBmpResID

定義用於突出顯示的自定義智慧停靠標記的點陣圖的資源標識。

```
UINT m_uiMarkerLightBmpResID[AFX_SD_MARKERS_NUM];
```

### <a name="remarks"></a>備註

用表示突出顯示的智慧停靠標記的位圖的資源標識填充此陣列。 AFX_SD_MARKERS_NUM當前定義為 5。 以如下方式填充陣列:

```cpp
params.m_uiMarkerLightBmpResID[0] = IDB_MARKER_LEFT_LIGHT;
params.m_uiMarkerLightBmpResID[1] = IDB_MARKER_RIGHT_LIGHT;
params.m_uiMarkerLightBmpResID[2] = IDB_MARKER_TOP_LIGHT;
params.m_uiMarkerLightBmpResID[3] = IDB_MARKER_BOTTOM_LIGHT;
params.m_uiMarkerLightBmpResID[4] = IDB_MARKER_CENTER_LIGHT;
```

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CObject 類別](../../mfc/reference/cobject-class.md)
