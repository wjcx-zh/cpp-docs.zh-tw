---
title: CMFCTabToolTipInfo 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCTabToolTipInfo
dev_langs:
- C++
helpviewer_keywords:
- CMFCTabToolTipInfo struct
ms.assetid: 9c3b3fb9-1497-4d59-932b-0da9348dd5e2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 21e612615110370922d71e1acaebcda56b2e692e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46435450"
---
# <a name="cmfctabtooltipinfo-structure"></a>CMFCTabToolTipInfo 結構

此結構會提供使用者停留的 MDI 索引標籤的相關資訊。

## <a name="syntax"></a>語法

```
struct CMFCTabToolTipInfo
```

## <a name="members"></a>成員

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMFCTabToolTipInfo::m_nTabIndex](#m_ntabindex)|指定的索引標籤控制項的索引。|
|[CMFCTabToolTipInfo::m_pTabWnd](#m_ptabwnd)|指標，此索引標籤控制項。|
|[CMFCTabToolTipInfo::m_strText](#m_strtext)|工具提示文字。|

## <a name="remarks"></a>備註

指標`CMFCTabToolTipInfo`AFX_WM_ON_GET_TAB_TOOLTIP 訊息的參數形式傳遞結構。 已啟用 MDI 索引標籤，而且使用者將滑鼠指標停留在索引標籤控制項上時，會產生此訊息。

## <a name="example"></a>範例

下列範例示範如何`CMFCTabToolTipInfo`用於[MDITabsDemo 範例： MFC 索引標籤式 MDI 應用程式](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層

[CMFCTabToolTipInfo](../../mfc/reference/cmfctabtooltipinfo-structure.md)

## <a name="requirements"></a>需求

**標頭：** afxbasetabctrl.h

##  <a name="m_ntabindex"></a>  CMFCTabToolTipInfo::m_nTabIndex

指定的索引標籤控制項的索引。

```
int m_nTabIndex;
```

### <a name="remarks"></a>備註

暫留的使用者 索引標籤的索引。

### <a name="example"></a>範例

下列範例示範如何`m_nTabIndex`用於[MDITabsDemo 範例： MFC 索引標籤式 MDI 應用程式](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

##  <a name="m_ptabwnd"></a>  CMFCTabToolTipInfo::m_pTabWnd

指標，此索引標籤控制項。

```
CMFCBaseTabCtrl* m_pTabWnd;
```

### <a name="example"></a>範例

下列範例示範如何`m_pTabWnd`用於[MDITabsDemo 範例： MFC 索引標籤式 MDI 應用程式](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

##  <a name="m_strtext"></a>  CMFCTabToolTipInfo::m_strText

工具提示文字。

```
CString m_strText;
```

### <a name="remarks"></a>備註

如果字串是空的不會顯示工具提示。

### <a name="example"></a>範例

下列範例示範如何`m_strText`用於[MDITabsDemo 範例： MFC 索引標籤式 MDI 應用程式](../../visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
