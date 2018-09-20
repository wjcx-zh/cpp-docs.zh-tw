---
title: CMFCToolBarInfo 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7825983fbc70dafbbcc96221b8a38c3ae4e939c5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435437"
---
# <a name="cmfctoolbarinfo-class"></a>CMFCToolBarInfo 類別

包含在各種狀態下工具列影像的資源 ID。 `CMFCToolBarInfo` 是一個 helper 類別，可做為參數的[cmfctoolbar:: Loadtoolbarex](../../mfc/reference/cmfctoolbar-class.md#loadtoolbarex)方法。

## <a name="syntax"></a>語法

```
class CMFCToolBarInfo
```

## <a name="members"></a>成員

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMFCToolBarInfo::m_uiColdResID](#m_uicoldresid)|包含規則 （冷） 的工具列影像的工具列點陣圖的資源識別碼。|
|[CMFCToolBarInfo::m_uiDisabledResID](#m_uidisabledresid)|包含已停用的工具列影像的工具列點陣圖的資源識別碼。|
|[CMFCToolBarInfo::m_uiHotResID](#m_uihotresid)|包含所選的 （熱） 工具列影像的工具列點陣圖的資源識別碼。|
|[CMFCToolBarInfo::m_uiLargeColdResID](#m_uilargecoldresid)|包含大型的一般工具列影像的工具列點陣圖的資源識別碼。|
|[CMFCToolBarInfo::m_uiLargeDisabledResID](#m_uilargedisabledresid)|包含大型的工具列點陣圖的資源識別碼已停用工具列影像。|
|[CMFCToolBarInfo::m_uiLargeHotResID](#m_uilargehotresid)|包含大型的所選的工具列影像的工具列點陣圖的資源識別碼。|
|[CMFCToolBarInfo::m_uiMenuDisabledResID](#m_uimenudisabledresid)|包含已停用的功能表影像的工具列點陣圖的資源識別碼。|
|[CMFCToolBarInfo::m_uiMenuResID](#m_uimenuresid)|包含功能表影像的工具列點陣圖的資源識別碼。|

## <a name="remarks"></a>備註

完整的工具列點陣圖所組成的固定大小的小型工具列影像 （按鈕）。 儲存在每個資源識別碼`CMFCToolBarInfo`物件是包含一組完整工具列中的映像 （適用於範例中，選取、 已停用、 大型或功能表影像） 的單一狀態的點陣圖。

## <a name="inheritance-hierarchy"></a>繼承階層

[CMFCToolBarInfo](../../mfc/reference/cmfctoolbarinfo-class.md)

## <a name="requirements"></a>需求

**標頭：** afxtoolbar.h

##  <a name="m_uicoldresid"></a>  CMFCToolBarInfo::m_uiColdResID

指定工具列的所有標準按鈕影像的資源識別碼。

```
UINT m_uiColdResID;
```

##  <a name="m_uidisabledresid"></a>  CMFCToolBarInfo::m_uiDisabledResID

指定工具列的按鈕無法使用的映像的資源識別碼。

```
UINT m_uiDisabledResID;
```

##  <a name="m_uihotresid"></a>  CMFCToolBarInfo::m_uiHotResID

指定工具列的所有反白顯示的按鈕影像的資源識別碼。

```
UINT m_uiHotResID
```

##  <a name="m_uilargecoldresid"></a>  CMFCToolBarInfo::m_uiLargeColdResID

指定工具列的所有規則的大型按鈕影像的資源識別碼。

```
UINT m_uiLargeColdResID
```

##  <a name="m_uilargedisabledresid"></a>  CMFCToolBarInfo::m_uiLargeDisabledResID

指定工具列的所有已停用的大型按鈕影像的資源識別碼。

```
UINT m_uiLargeDisabledResID;
```

##  <a name="m_uilargehotresid"></a>  CMFCToolBarInfo::m_uiLargeHotResID

指定的工具列的所有大型反白顯示映像的資源識別碼。

```
UINT m_uiLargeHotResID;
```

##  <a name="m_uimenudisabledresid"></a>  CMFCToolBarInfo::m_uiMenuDisabledResID

指定工具列的命令無法使用的映像的資源識別碼。

```
UINT m_uiMenuDisabledResID;
```

##  <a name="m_uimenuresid"></a>  CMFCToolBarInfo::m_uiMenuResID

指定工具列的所有標準功能表項目影像的資源識別碼。

```
UINT m_uiMenuResID;
```

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar 類別](../../mfc/reference/cmfctoolbar-class.md)
