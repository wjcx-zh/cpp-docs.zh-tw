---
title: CMFCDragFrameImpl 類別
ms.date: 10/18/2018
f1_keywords:
- CMFCDragFrameImpl
helpviewer_keywords:
- CMFCDragFrameImpl class [MFC]
ms.assetid: 500cd824-8188-43c2-8754-b7bb46b5648a
ms.openlocfilehash: 527fd089962e05c44a7e47b1ae52345116da4470
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752436"
---
# <a name="cmfcdragframeimpl-class"></a>CMFCDragFrameImpl 類別

類`CMFCDragFrameImpl`繪製在標準停靠模式下拖動窗格時出現的拖動矩形。
有關詳細資訊,請參閱位於 Visual Studio 安裝的**VC\\\\\\atlmfc src mfc**資料夾中的原始程式碼。

## <a name="syntax"></a>語法

```
class CMFCDragFrameImpl
```

## <a name="remarks"></a>備註

此類的物件嵌入在每個[CPane 類](../../mfc/reference/cpane-class.md)物件中。 因此,當使用者拖動該方法時,`CanFloat`使用 方法的每個窗格都會顯示拖動矩形。

您可以使用[AFX_GLOBAL_DATA:m_nDragFrameThicknessFloat](afx-global-data-structure.md#m_ndragframethicknessfloat)和[AFX_GLOBAL_DATA:m_nDragFrameThicknessDock](afx-global-data-structure.md#m_ndragframethicknessdock)來控制拖動矩形的厚度。

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CMFCDragFrameImpl](../../mfc/reference/cmfcdragframeimpl-class.md)

## <a name="requirements"></a>需求

**標題:** afxdragframeimpl.h

## <a name="cmfcdragframeimplenddrawdragframe"></a><a name="enddrawdragframe"></a>CMFCDragFrameimpl::結束繪製拖動框架

```cpp
void EndDrawDragFrame(BOOL bClearInternalRects = TRUE);
```

### <a name="parameters"></a>參數

[在]*b清除內部重新*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcdragframeimplinit"></a><a name="init"></a>CMFCDragframeimpl::Init

```cpp
void Init(CWnd* pDraggedWnd);
```

### <a name="parameters"></a>參數

[在]*普拉普恩德*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcdragframeimplmovedragframe"></a><a name="movedragframe"></a>CMFCDragFrameimpl::移動拖動框架

```cpp
void MoveDragFrame(BOOL bForceMove = FALSE);
```

### <a name="parameters"></a>參數

[在]*bForceMove*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcdragframeimplplacetabpredocking"></a><a name="placetabpredocking"></a>CMFCDragFrameimpl::PlaceTab預對接

```cpp
void PlaceTabPreDocking(
    CBaseTabbedPane* pTabbedBar,
    BOOL bFirstTime);

void PlaceTabPreDocking(CWnd* pCBarToPlaceOn);
```

### <a name="parameters"></a>參數

[在]*pTabbedBar*<br/>

[在]*b 第一次*<br/>

[在]*pCBARtoPlaceon*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcdragframeimplremovetabpredocking"></a><a name="removetabpredocking"></a>CMFCDragFrameimpl::刪除TabpreDocking

```cpp
void RemoveTabPreDocking(CDockablePane* pOldTargetBar = NULL);
```

### <a name="parameters"></a>參數

[在]*pOldTargetBar*<br/>

### <a name="remarks"></a>備註

## <a name="cmfcdragframeimplresetstate"></a><a name="resetstate"></a>CMFCDragFrameimpl::重置狀態

```cpp
void ResetState();
```

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CPane Class](../../mfc/reference/cpane-class.md)
