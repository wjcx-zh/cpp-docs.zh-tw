---
title: CMFCDragFrameImpl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMFCDragFrameImpl
dev_langs:
- C++
helpviewer_keywords:
- CMFCDragFrameImpl class [MFC]
ms.assetid: 500cd824-8188-43c2-8754-b7bb46b5648a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fa4846ec2d6263e353dec05d145f6e2e33a59eb4
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50062375"
---
# <a name="cmfcdragframeimpl-class"></a>CMFCDragFrameImpl 類別

`CMFCDragFrameImpl`類別繪製使用者以標準停駐模式拖曳窗格時，會出現的拖曳矩形。
如需詳細資訊，請參閱中的原始程式碼**VC\\atlmfc\\src\\mfc** Visual Studio 安裝資料夾。

## <a name="syntax"></a>語法

```
class CMFCDragFrameImpl
```

## <a name="remarks"></a>備註

這個類別的物件在每個內嵌[CPane 類別](../../mfc/reference/cpane-class.md)物件。 因此，會使用每個窗格`CanFloat`方法會在使用者拖曳時，會顯示拖曳矩形。

您可以使用來控制拖放矩形的粗細[AFX_GLOBAL_DATA::m_nDragFrameThicknessFloat](afx-global-data-structure.md#m_ndragframethicknessfloat)並[AFX_GLOBAL_DATA::m_nDragFrameThicknessDock](afx-global-data-structure.md#m_ndragframethicknessdock)。

## <a name="inheritance-hierarchy"></a>繼承階層

[CMFCDragFrameImpl](../../mfc/reference/cmfcdragframeimpl-class.md)

## <a name="requirements"></a>需求

**標頭：** afxdragframeimpl.h

##  <a name="enddrawdragframe"></a>  CMFCDragFrameImpl::EndDrawDragFrame

```
void EndDrawDragFrame(BOOL bClearInternalRects = TRUE);
```

### <a name="parameters"></a>參數

[in]*bClearInternalRects*<br/>

### <a name="remarks"></a>備註

##  <a name="init"></a>  CMFCDragFrameImpl::Init

```
void Init(CWnd* pDraggedWnd);
```

### <a name="parameters"></a>參數

[in]*pDraggedWnd*<br/>

### <a name="remarks"></a>備註

##  <a name="movedragframe"></a>  CMFCDragFrameImpl::MoveDragFrame

```
void MoveDragFrame(BOOL bForceMove = FALSE);
```

### <a name="parameters"></a>參數

[in]*bForceMove*<br/>

### <a name="remarks"></a>備註

##  <a name="placetabpredocking"></a>  CMFCDragFrameImpl::PlaceTabPreDocking

```
void PlaceTabPreDocking(
    CBaseTabbedPane* pTabbedBar,
    BOOL bFirstTime);

void PlaceTabPreDocking(CWnd* pCBarToPlaceOn);
```

### <a name="parameters"></a>參數

[in]*pTabbedBar*<br/>

[in]*bFirstTime*<br/>

[in]*pCBarToPlaceOn*<br/>

### <a name="remarks"></a>備註

##  <a name="removetabpredocking"></a>  CMFCDragFrameImpl::RemoveTabPreDocking

```
void RemoveTabPreDocking(CDockablePane* pOldTargetBar = NULL);
```

### <a name="parameters"></a>參數

[in]*pOldTargetBar*<br/>

### <a name="remarks"></a>備註

##  <a name="resetstate"></a>  CMFCDragFrameImpl::ResetState

```
void ResetState();
```

### <a name="remarks"></a>備註

## <a name="see-also"></a>另請參閱

[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CPane 類別](../../mfc/reference/cpane-class.md)