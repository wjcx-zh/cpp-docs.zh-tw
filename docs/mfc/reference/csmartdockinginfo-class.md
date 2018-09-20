---
title: CSmartDockingInfo 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 691ca4cd03865b348a17e56787c419cbd222fb4f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407731"
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
|[CSmartDockingInfo::CopyTo](#copyto)|將目前的智慧停駐資訊參數複製到所提供[CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md)物件。|

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CSmartDockingInfo::m_bUseThemeColorInShading](#m_busethemecolorinshading)|指定是否要使用目前的佈景主題色彩時，架構會顯示智慧停駐標記。|
|[CSmartDockingInfo::m_clrBaseBackground](#m_clrbasebackground)|指定智慧停駐標記的基底的背景色彩。|
|[CSmartDockingInfo::m_clrToneDest](#m_clrtonedest)|指定取代的色彩`m_clrToneSrc`智慧停駐標記點陣圖中。|
|[CSmartDockingInfo::m_clrToneSrc](#m_clrtonesrc)|指定的智慧停駐標記點陣圖的色彩。|
|[CSmartDockingInfo::m_clrTransparent](#m_clrtransparent)|透明時，請指定智慧停駐標記點陣圖的色彩。|
|[CSmartDockingInfo::m_nCentralGroupOffset](#m_ncentralgroupoffset)|指定從中央群組矩形界限的智慧停駐標記的中央群組的位移。|
|[CSmartDockingInfo::m_sizeTotal](#m_sizetotal)|指定群組中的所有智慧停駐標記的大小總計。|
|[CSmartDockingInfo::m_uiMarkerBmpResID](#m_uimarkerbmpresid)|定義的資源識別碼的架構會使用針對智慧停駐標記不反白顯示的點陣圖。|
|[CSmartDockingInfo::m_uiMarkerLightBmpResID](#m_uimarkerlightbmpresid)|定義的資源識別碼的架構會使用針對智慧停駐標記反白顯示的點陣圖。|

## <a name="remarks"></a>備註

Framework 控點內部智慧停駐標記。 下圖顯示標準的智慧停駐標記：

![智慧停駐的標準標記](../../mfc/reference/media/nextsdmarkers.png "nextsdmarkers")

在此圖中，在左側的映像會顯示沒有啟用索引標籤停駐集中的群組智慧停駐標記。 中間影像顯示右邊緣智慧停駐標記。 右側影像顯示停駐索引標籤啟用有中央群組智慧停駐標記。 中央群組智慧停駐標記有一個主要的點陣圖和五個智慧停駐標記的點陣圖。

您可以自訂智慧停駐標記的下列參數：

- 色彩。 例如，您可以將標記在圖中的藍色色彩取代任何使用者定義的色彩。

- 透明色彩。

- 週框矩形框線從中央群組中的智慧停駐標記的位移。

- 主要點陣圖表示中央的群組。

- 代表規則和反白顯示的點陣圖智慧停駐標記。

下圖顯示已自訂的智慧停駐標記的範例：

![智慧停駐的自訂標記](../../mfc/reference/media/nextsdmarkerscustom.png "nextsdmarkerscustom")

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md)

## <a name="requirements"></a>需求

**標頭：** afxDockingManager.h

##  <a name="copyto"></a>  CSmartDockingInfo::CopyTo

將目前的智慧停駐參數複製到所提供[CSmartDockingInfo](../../mfc/reference/csmartdockinginfo-class.md)物件。

```
void CopyTo(CSmartDockingInfo& params);
```

### <a name="parameters"></a>參數

*params*<br/>
[out]型別的物件`CSmartDockingInfo`，並填入目前的智慧停駐參數。

##  <a name="m_busethemecolorinshading"></a>  CSmartDockingInfo::m_bUseThemeColorInShading

指定是否要使用目前的佈景主題色彩時，架構會顯示智慧停駐標記。

```
BOOL m_bUseThemeColorInShading;
```

### <a name="remarks"></a>備註

如果為 TRUE，會使用目前的佈景主題色彩; 繪製標記否則這些標記會繪製以淺藍色顯示。

預設值為 FALSE。

##  <a name="m_clrbasebackground"></a>  CSmartDockingInfo::m_clrBaseBackground

指定智慧停駐標記的基底的背景色彩。

```
COLORREF m_clrBaseBackground;
```

##  <a name="m_clrtonedest"></a>  CSmartDockingInfo::m_clrToneDest

指定將會取代的色彩`m_clrToneSrc`智慧停駐標記點陣圖中。

```
COLORREF m_clrToneDest;
```

### <a name="remarks"></a>備註

設定此值，以程式設計方式變更標記點陣圖的色彩。 比方說，如果您想要變更架構所隨附的標準標記的色彩，此值設所需的色彩。 根據預設， [CSmartDockingInfo::m_clrToneSrc](#m_clrtonesrc)設為 61，123 (241） 的 RGB （藍色彩）。

若要變更自訂標記的色彩，您必須同時指定`m_clrToneDest`和`m_clrToneSrc`。

##  <a name="m_clrtonesrc"></a>  CSmartDockingInfo::m_clrToneSrc

指定的智慧停駐標記點陣圖的色彩。

```
COLORREF m_clrToneSrc;
```

### <a name="remarks"></a>備註

只有在您想要自訂點陣圖的色彩取代另一種色彩時，請設定此值。 您沒有設定此值，如果您要變更的色彩 （提供的架構） 的標準標記。

使用`(COLORREF)-1`保留空白智慧停駐群組的成員。

##  <a name="m_clrtransparent"></a>  CSmartDockingInfo::m_clrTransparent

透明時，請指定智慧停駐標記點陣圖的色彩。

```
COLORREF m_clrTransparent;
```

### <a name="remarks"></a>備註

當您在停駐的群組中顯示自訂標記和自訂點陣圖時，您必須設定此值。

##  <a name="m_ncentralgroupoffset"></a>  CSmartDockingInfo::m_nCentralGroupOffset

指定智慧停駐標記的中央的群組和中央群組矩形界限之間的位移。

```
int m_nCentralGroupOffset;
```

### <a name="remarks"></a>備註

指定此值，如果您想要變更自訂標記與智慧停駐標記的中央群組的界限之間的預設位移。 預設位移為 5 像素。

##  <a name="m_sizetotal"></a>  CSmartDockingInfo::m_sizeTotal

指定封入中央的群組中的所有智慧停駐標記的周框的大小總計。

```
CSize m_sizeTotal;
```

### <a name="remarks"></a>備註

設定`m_sizeTotal`中央群組標記的週框矩形的大小。 您必須指定這個值，如果您使用自訂點陣圖的標記。

##  <a name="m_uimarkerbmpresid"></a>  CSmartDockingInfo::m_uiMarkerBmpResID

定義的資源識別碼用於非反白顯示自訂智慧停駐標記的點陣圖。

```
UINT m_uiMarkerBmpResID[AFX_SD_MARKERS_NUM];
```

### <a name="remarks"></a>備註

這個陣列中填入的資源識別碼代表智慧停駐標記的點陣圖。 AFX_SD_MARKERS_NUM 目前定義為 5。 您填滿陣列，如下所示：

```cpp
params.m_uiMarkerBmpResID[0] = IDB_MARKER_LEFT;
params.m_uiMarkerBmpResID[1] = IDB_MARKER_RIGHT;
params.m_uiMarkerBmpResID[2] = IDB_MARKER_TOP;
params.m_uiMarkerBmpResID[3] = IDB_MARKER_BOTTOM;
params.m_uiMarkerBmpResID[4] = IDB_MARKER_CENTER;
```

##  <a name="m_uimarkerlightbmpresid"></a>  CSmartDockingInfo::m_uiMarkerLightBmpResID

定義的資源識別碼用於反白顯示自訂的智慧停駐標記的點陣圖。

```
UINT m_uiMarkerLightBmpResID[AFX_SD_MARKERS_NUM];
```

### <a name="remarks"></a>備註

這個陣列中填入的資源識別碼代表反白顯示的智慧停駐標記的點陣圖。 AFX_SD_MARKERS_NUM 目前定義為 5。 您填滿陣列，如下所示：

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
