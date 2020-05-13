---
title: CMFCTabToolTipInfo 結構
ms.date: 11/04/2016
f1_keywords:
- CMFCTabToolTipInfo
helpviewer_keywords:
- CMFCTabToolTipInfo struct
ms.assetid: 9c3b3fb9-1497-4d59-932b-0da9348dd5e2
ms.openlocfilehash: a507d1e69b3524074e50fde0e87fc5ebb6e5ca03
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367333"
---
# <a name="cmfctabtooltipinfo-structure"></a>CMFCTabToolTipInfo 結構

此結構提供有關使用者懸停的 MDI 選項卡的資訊。

## <a name="syntax"></a>語法

```
struct CMFCTabToolTipInfo
```

## <a name="members"></a>成員

### <a name="data-members"></a>資料成員

|名稱|描述|
|----------|-----------------|
|[CMFCTabTool提示資訊::m_nTabIndex](#m_ntabindex)|指定選項卡控制項的索引。|
|[CMFCTabTool提示資訊::m_pTabWnd](#m_ptabwnd)|指向選項卡控件的指標。|
|[CMFCTabTool提示資訊::m_strText](#m_strtext)|工具提示文字。|

## <a name="remarks"></a>備註

指向結構的`CMFCTabToolTipInfo`指標作為AFX_WM_ON_GET_TAB_TOOLTIP消息的參數傳遞。 啟用 MDI 選項卡且使用者懸停在選項卡控制項上時,將生成此消息。

## <a name="example"></a>範例

下面的範例顯示如何在`CMFCTabToolTipInfo` [MDITabsDemo 範例中使用:MFC 選項卡式 MDI 應用程式](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CMFCTabToolTipInfo](../../mfc/reference/cmfctabtooltipinfo-structure.md)

## <a name="requirements"></a>需求

**標頭：** afxbasetabctrl.h

## <a name="cmfctabtooltipinfom_ntabindex"></a><a name="m_ntabindex"></a>CMFCTabTool提示資訊::m_nTabIndex

指定選項卡控制項的索引。

```
int m_nTabIndex;
```

### <a name="remarks"></a>備註

用戶懸停在其中的選項卡的索引。

### <a name="example"></a>範例

下面的範例顯示如何在`m_nTabIndex` [MDITabsDemo 範例中使用:MFC 選項卡式 MDI 應用程式](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="cmfctabtooltipinfom_ptabwnd"></a><a name="m_ptabwnd"></a>CMFCTabTool提示資訊::m_pTabWnd

指向選項卡控件的指標。

```
CMFCBaseTabCtrl* m_pTabWnd;
```

### <a name="example"></a>範例

下面的範例顯示如何在`m_pTabWnd` [MDITabsDemo 範例中使用:MFC 選項卡式 MDI 應用程式](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="cmfctabtooltipinfom_strtext"></a><a name="m_strtext"></a>CMFCTabTool提示資訊::m_strText

工具提示文字。

```
CString m_strText;
```

### <a name="remarks"></a>備註

如果字串為空,則不顯示工具提示。

### <a name="example"></a>範例

下面的範例顯示如何在`m_strText` [MDITabsDemo 範例中使用:MFC 選項卡式 MDI 應用程式](../../overview/visual-cpp-samples.md)。

[!code-cpp[NVC_MFC_MDITabsDemo#2](../../mfc/reference/codesnippet/cpp/cmfctabtooltipinfo-structure_1.cpp)]

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)
