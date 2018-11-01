---
title: CD2DGradientBrush 類別
ms.date: 11/04/2016
f1_keywords:
- CD2DGradientBrush
- AFXRENDERTARGET/CD2DGradientBrush
- AFXRENDERTARGET/CD2DGradientBrush::CD2DGradientBrush
- AFXRENDERTARGET/CD2DGradientBrush::Destroy
- AFXRENDERTARGET/CD2DGradientBrush::m_arGradientStops
- AFXRENDERTARGET/CD2DGradientBrush::m_colorInterpolationGamma
- AFXRENDERTARGET/CD2DGradientBrush::m_extendMode
- AFXRENDERTARGET/CD2DGradientBrush::m_pGradientStops
helpviewer_keywords:
- CD2DGradientBrush [MFC], CD2DGradientBrush
- CD2DGradientBrush [MFC], Destroy
- CD2DGradientBrush [MFC], m_arGradientStops
- CD2DGradientBrush [MFC], m_colorInterpolationGamma
- CD2DGradientBrush [MFC], m_extendMode
- CD2DGradientBrush [MFC], m_pGradientStops
ms.assetid: 5bf133e6-16b7-4e3a-845d-0ce63fafe5ec
ms.openlocfilehash: bc26dd495fb9bd91aaf5eac192011faad80bc668
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506050"
---
# <a name="cd2dgradientbrush-class"></a>CD2DGradientBrush 類別

CD2DLinearGradientBrush 和 CD2DRadialGradientBrush 類別的基底類別。

## <a name="syntax"></a>語法

```
class CD2DGradientBrush : public CD2DBrush;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2DGradientBrush::CD2DGradientBrush](#cd2dgradientbrush)|建構 CD2DGradientBrush 物件。|
|[CD2DGradientBrush:: ~ CD2DGradientBrush](#cd2dgradientbrush__~cd2dgradientbrush)|解構函式。 D2D 漸層筆刷物件正在被終結時呼叫。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CD2DGradientBrush::Destroy](#destroy)|終結 CD2DGradientBrush 物件。 (覆寫[CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy)。)|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CD2DGradientBrush::m_arGradientStops](#m_argradientstops)|D2D1_GRADIENT_STOP 結構的陣列。|
|[CD2DGradientBrush::m_colorInterpolationGamma](#m_colorinterpolationgamma)|在色彩漸層停駐點之間的內插補點會執行空間。|
|[CD2DGradientBrush::m_extendMode](#m_extendmode)|正規化 [0，1] 範圍之外的漸層的行為。|
|[CD2DGradientBrush::m_pGradientStops](#m_pgradientstops)|D2D1_GRADIENT_STOP 結構陣列的指標。|

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

`CD2DGradientBrush`

## <a name="requirements"></a>需求

**標頭：** afxrendertarget.h

##  <a name="_dtorcd2dgradientbrush"></a>  CD2DGradientBrush:: ~ CD2DGradientBrush

解構函式。 D2D 漸層筆刷物件正在被終結時呼叫。

```
virtual ~CD2DGradientBrush();
```

##  <a name="cd2dgradientbrush"></a>  CD2DGradientBrush::CD2DGradientBrush

建構 CD2DGradientBrush 物件。

```
CD2DGradientBrush(
    CRenderTarget* pParentTarget,
    const D2D1_GRADIENT_STOP* gradientStops,
    UINT gradientStopsCount,
    D2D1_GAMMA colorInterpolationGamma = D2D1_GAMMA_2_2,
    D2D1_EXTEND_MODE extendMode = D2D1_EXTEND_MODE_CLAMP,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>參數

*pParentTarget*<br/>
到轉譯目標的指標。

*gradientStops*<br/>
D2D1_GRADIENT_STOP 結構陣列的指標。

*gradientStopsCount*<br/>
值大於或等於 1，gradientStops 陣列中指定的漸層停駐點數目。

*colorInterpolationGamma*<br/>
在色彩漸層停駐點之間的內插補點會執行空間。

*extendMode*<br/>
正規化 [0，1] 範圍之外的漸層的行為。

*pBrushProperties*<br/>
不透明度和筆刷轉換指標。

*bAutoDestroy*<br/>
表示擁有者 (pParentTarget) 將會終結物件。

##  <a name="destroy"></a>  CD2DGradientBrush::Destroy

終結 CD2DGradientBrush 物件。

```
virtual void Destroy();
```

##  <a name="m_argradientstops"></a>  CD2DGradientBrush::m_arGradientStops

D2D1_GRADIENT_STOP 結構的陣列。

```
CArray<D2D1_GRADIENT_STOP, D2D1_GRADIENT_STOP> m_arGradientStops;
```

##  <a name="m_colorinterpolationgamma"></a>  CD2DGradientBrush::m_colorInterpolationGamma

在色彩漸層停駐點之間的內插補點會執行空間。

```
D2D1_GAMMA m_colorInterpolationGamma;
```

##  <a name="m_extendmode"></a>  CD2DGradientBrush::m_extendMode

正規化 [0，1] 範圍之外的漸層的行為。

```
D2D1_EXTEND_MODE m_extendMode;
```

##  <a name="m_pgradientstops"></a>  CD2DGradientBrush::m_pGradientStops

D2D1_GRADIENT_STOP 結構陣列的指標。

```
ID2D1GradientStopCollection* m_pGradientStops;
```

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
