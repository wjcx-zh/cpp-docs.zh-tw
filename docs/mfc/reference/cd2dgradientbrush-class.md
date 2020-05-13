---
title: CD2DGradientBrush 類別
ms.date: 03/27/2019
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
ms.openlocfilehash: 861bc32382737bd6482a3d51eb8470bf834e8508
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369222"
---
# <a name="cd2dgradientbrush-class"></a>CD2DGradientBrush 類別

CD2D線性漸變畫筆和CD2DRadial 梯度畫筆類的基類。

## <a name="syntax"></a>語法

```
class CD2DGradientBrush : public CD2DBrush;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2D 梯度畫筆::CD2D 梯度畫筆](#cd2dgradientbrush)|構造 CD2D 梯度畫筆物件。|
|[CD2D 梯度畫筆:*CD2D 梯度畫筆](#_dtorcd2dgradientbrush)|解構函式。 銷毀 D2D 漸變畫筆物件時調用。|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CD2D梯度畫筆::D](#destroy)|銷毀 CD2D 梯度畫筆物件。 (覆蓋[CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CD2D 梯度畫筆::m_arGradientStops](#m_argradientstops)|D2D1_GRADIENT_STOP結構的陣列。|
|[CD2D 梯度畫筆::m_colorInterpolationGamma](#m_colorinterpolationgamma)|在漸變停止之間執行顏色插值的空間。|
|[CD2D 梯度畫筆::m_extendMode](#m_extendmode)|漸變在 [0,1] 規範化範圍之外的行為。|
|[CD2D 梯度畫筆::m_pGradientStops](#m_pgradientstops)|指向D2D1_GRADIENT_STOP結構陣列的指標。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CD2D 資源](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

`CD2DGradientBrush`

## <a name="requirements"></a>需求

**標題:** afxrendertarget.h

## <a name="cd2dgradientbrushcd2dgradientbrush"></a><a name="_dtorcd2dgradientbrush"></a>CD2D 梯度畫筆:*CD2D 梯度畫筆

解構函式。 銷毀 D2D 漸變畫筆物件時調用。

```
virtual ~CD2DGradientBrush();
```

## <a name="cd2dgradientbrushcd2dgradientbrush"></a><a name="cd2dgradientbrush"></a>CD2D 梯度畫筆::CD2D 梯度畫筆

構造 CD2D 梯度畫筆物件。

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

*p 父目標*<br/>
指向渲染目標的指標。

*梯度停止*<br/>
指向D2D1_GRADIENT_STOP結構陣列的指標。

*梯度停止計數*<br/>
大於或等於 1 的值,用於指定漸變數組中的漸變停止數。

*顏色插值伽馬*<br/>
在漸變停止之間執行顏色插值的空間。

*擴充模式*<br/>
漸變在 [0,1] 規範化範圍之外的行為。

*pBrush 屬性*<br/>
指向畫筆的不一用性和變換的指標。

*bAuto銷毀*<br/>
指示物件將被擁有者(pParentTarget)銷毀。

## <a name="cd2dgradientbrushdestroy"></a><a name="destroy"></a>CD2D梯度畫筆::D

銷毀 CD2D 梯度畫筆物件。

```
virtual void Destroy();
```

## <a name="cd2dgradientbrushm_argradientstops"></a><a name="m_argradientstops"></a>CD2D 梯度畫筆::m_arGradientStops

D2D1_GRADIENT_STOP結構的陣列。

```
CArray<D2D1_GRADIENT_STOP, D2D1_GRADIENT_STOP> m_arGradientStops;
```

## <a name="cd2dgradientbrushm_colorinterpolationgamma"></a><a name="m_colorinterpolationgamma"></a>CD2D 梯度畫筆::m_colorInterpolationGamma

在漸變停止之間執行顏色插值的空間。

```
D2D1_GAMMA m_colorInterpolationGamma;
```

## <a name="cd2dgradientbrushm_extendmode"></a><a name="m_extendmode"></a>CD2D 梯度畫筆::m_extendMode

漸變在 [0,1] 規範化範圍之外的行為。

```
D2D1_EXTEND_MODE m_extendMode;
```

## <a name="cd2dgradientbrushm_pgradientstops"></a><a name="m_pgradientstops"></a>CD2D 梯度畫筆::m_pGradientStops

指向D2D1_GRADIENT_STOP結構陣列的指標。

```
ID2D1GradientStopCollection* m_pGradientStops;
```

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
