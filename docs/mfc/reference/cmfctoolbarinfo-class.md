---
title: CMFCToolBarInfo 類別
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarInfo
- AFXTOOLBAR/CMFCToolBarInfo
- AFXTOOLBAR/CMFCToolBarInfo::m_uiColdResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiHotResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeColdResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiLargeHotResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiMenuDisabledResID
- AFXTOOLBAR/CMFCToolBarInfo::m_uiMenuResID
helpviewer_keywords:
- CMFCToolBarInfo [MFC], m_uiColdResID
- CMFCToolBarInfo [MFC], m_uiDisabledResID
- CMFCToolBarInfo [MFC], m_uiHotResID
- CMFCToolBarInfo [MFC], m_uiLargeColdResID
- CMFCToolBarInfo [MFC], m_uiLargeDisabledResID
- CMFCToolBarInfo [MFC], m_uiLargeHotResID
- CMFCToolBarInfo [MFC], m_uiMenuDisabledResID
- CMFCToolBarInfo [MFC], m_uiMenuResID
ms.assetid: 6dc84482-eaaa-491f-aa5d-dd7a57886b46
ms.openlocfilehash: 593d1665751f7322fc2a9cee307620df88d46876
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376198"
---
# <a name="cmfctoolbarinfo-class"></a>CMFCToolBarInfo 類別

包含在各種狀態下工具列影像的資源 ID。 `CMFCToolBarInfo`是用作[CMFCToolBar::LoadToolBarEx](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex)方法參數的幫助器類。

## <a name="syntax"></a>語法

```
class CMFCToolBarInfo
```

## <a name="members"></a>成員

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMFCToolBarinfo:m_uiColdResID](#m_uicoldresid)|包含常規(冷)工具列圖像的工具列位圖的資源 ID。|
|[CMFCToolBarinfo:m_uiDisabledResID](#m_uidisabledresid)|包含停用工具列影像的工具列位圖的資源 ID。|
|[CMFCToolBarinfo:m_uiHotResID](#m_uihotresid)|包含選取(熱)工具列影像的工具列位圖的資源 ID。|
|[CMFCToolBarInfo:m_uiLargeColdResID](#m_uilargecoldresid)|包含大型常規工具列圖像的工具列位圖的資源 ID。|
|[CMFCToolBarInfo:m_uiLargeDisabledResID](#m_uilargedisabledresid)|包含大型禁用工具列圖像的工具列位圖的資源 ID。|
|[CMFCToolBarInfo:m_uiLargeHotResID](#m_uilargehotresid)|包含大型選定工具列圖像的工具列位圖的資源 ID。|
|[CMFCToolBarinfo:m_uiMenuDisabledResID](#m_uimenudisabledresid)|包含關閉選單影像的工具列位圖的資源 ID。|
|[CMFCToolBarinfo:m_uiMenuResID](#m_uimenuresid)|包含功能表影像的工具列點圖的資源 ID。|

## <a name="remarks"></a>備註

完整的工具列點圖由固定大小的小工具列圖像(按鈕)組成。 存儲在`CMFCToolBarInfo`物件中的每個資源 ID 都是一個位圖,其中包含一組處於單一狀態的工具列圖像(例如,選定、禁用、大型或功能表圖像)。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CMFCToolBarInfo](../../mfc/reference/cmfctoolbarinfo-class.md)

## <a name="requirements"></a>需求

**標題:** afxtoolbar.h

## <a name="cmfctoolbarinfom_uicoldresid"></a><a name="m_uicoldresid"></a>CMFCToolBarinfo:m_uiColdResID

為工具列的所有常規按鈕圖像指定資源 ID。

```
UINT m_uiColdResID;
```

## <a name="cmfctoolbarinfom_uidisabledresid"></a><a name="m_uidisabledresid"></a>CMFCToolBarinfo:m_uiDisabledResID

為工具列的按鈕不可用圖像指定資源 ID。

```
UINT m_uiDisabledResID;
```

## <a name="cmfctoolbarinfom_uihotresid"></a><a name="m_uihotresid"></a>CMFCToolBarinfo:m_uiHotResID

為工具列的所有突出顯示的按鈕圖像指定資源 ID。

```
UINT m_uiHotResID
```

## <a name="cmfctoolbarinfom_uilargecoldresid"></a><a name="m_uilargecoldresid"></a>CMFCToolBarInfo:m_uiLargeColdResID

為工具列的所有大型常規按鈕圖像指定資源 ID。

```
UINT m_uiLargeColdResID
```

## <a name="cmfctoolbarinfom_uilargedisabledresid"></a><a name="m_uilargedisabledresid"></a>CMFCToolBarInfo:m_uiLargeDisabledResID

為工具列的所有大型禁用按鈕圖像指定資源 ID。

```
UINT m_uiLargeDisabledResID;
```

## <a name="cmfctoolbarinfom_uilargehotresid"></a><a name="m_uilargehotresid"></a>CMFCToolBarInfo:m_uiLargeHotResID

為工具列的所有大型突出顯示圖像指定資源 ID。

```
UINT m_uiLargeHotResID;
```

## <a name="cmfctoolbarinfom_uimenudisabledresid"></a><a name="m_uimenudisabledresid"></a>CMFCToolBarinfo:m_uiMenuDisabledResID

為工具列的命令不可用圖像指定資源 ID。

```
UINT m_uiMenuDisabledResID;
```

## <a name="cmfctoolbarinfom_uimenuresid"></a><a name="m_uimenuresid"></a>CMFCToolBarinfo:m_uiMenuResID

為工具列的所有常規功能表項圖像指定資源 ID。

```
UINT m_uiMenuResID;
```

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)
