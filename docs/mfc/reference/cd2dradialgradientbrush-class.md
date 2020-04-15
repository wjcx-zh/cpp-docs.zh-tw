---
title: CD2DRadialGradientBrush 類別
ms.date: 11/04/2016
f1_keywords:
- CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::CD2DRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::Attach
- AFXRENDERTARGET/CD2DRadialGradientBrush::Create
- AFXRENDERTARGET/CD2DRadialGradientBrush::Destroy
- AFXRENDERTARGET/CD2DRadialGradientBrush::Detach
- AFXRENDERTARGET/CD2DRadialGradientBrush::Get
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetCenter
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetGradientOriginOffset
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetRadiusX
- AFXRENDERTARGET/CD2DRadialGradientBrush::GetRadiusY
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetCenter
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetGradientOriginOffset
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetRadiusX
- AFXRENDERTARGET/CD2DRadialGradientBrush::SetRadiusY
- AFXRENDERTARGET/CD2DRadialGradientBrush::m_pRadialGradientBrush
- AFXRENDERTARGET/CD2DRadialGradientBrush::m_RadialGradientBrushProperties
helpviewer_keywords:
- CD2DRadialGradientBrush [MFC], CD2DRadialGradientBrush
- CD2DRadialGradientBrush [MFC], Attach
- CD2DRadialGradientBrush [MFC], Create
- CD2DRadialGradientBrush [MFC], Destroy
- CD2DRadialGradientBrush [MFC], Detach
- CD2DRadialGradientBrush [MFC], Get
- CD2DRadialGradientBrush [MFC], GetCenter
- CD2DRadialGradientBrush [MFC], GetGradientOriginOffset
- CD2DRadialGradientBrush [MFC], GetRadiusX
- CD2DRadialGradientBrush [MFC], GetRadiusY
- CD2DRadialGradientBrush [MFC], SetCenter
- CD2DRadialGradientBrush [MFC], SetGradientOriginOffset
- CD2DRadialGradientBrush [MFC], SetRadiusX
- CD2DRadialGradientBrush [MFC], SetRadiusY
- CD2DRadialGradientBrush [MFC], m_pRadialGradientBrush
- CD2DRadialGradientBrush [MFC], m_RadialGradientBrushProperties
ms.assetid: 6c76d84a-d831-4ee2-96f1-82c1f5b0d6a9
ms.openlocfilehash: aca9606271040e5c5c9aee81be0a08b64cf2bab7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369136"
---
# <a name="cd2dradialgradientbrush-class"></a>CD2DRadialGradientBrush 類別

用於 ID2D1 Radial 梯度畫筆的包裝器。

## <a name="syntax"></a>語法

```
class CD2DRadialGradientBrush : public CD2DGradientBrush;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2D 徑梯度刷::CD2D 半徑梯度刷](#cd2dradialgradientbrush)|建構 CD2D 線性漸變畫筆物件。|
|[CD2D 徑梯度刷:*CD2D半徑梯度刷](#_dtorcd2dradialgradientbrush)|解構函式。 銷毀 D2D 徑向漸變畫筆物件時調用。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CD2D 輻射梯度畫筆::附加](#attach)|將現有資源介面附加到物件|
|[CD2D 半徑漸層筆:建立](#create)|創建 CD2DRadial 漸變畫筆。 (覆寫[CD2D 資源:建立](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DRadial梯度刷::D](#destroy)|銷毀 CD2DRadial 梯度畫筆物件。 (覆蓋[CD2D 梯度畫筆::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy).)|
|[CD2DRadial 梯度畫筆::D](#detach)|從物件分離資源介面|
|[CD2D 半徑梯度畫筆:取得](#get)|傳回 ID2D1 徑向漸層線|
|[CD2D 半徑梯度畫筆::獲取中心](#getcenter)|檢索漸變橢圓的中心|
|[CD2D 半徑梯度畫筆::獲取梯度原點偏移](#getgradientoriginoffset)|檢索漸變原點的偏移量相對於漸變橢圓的中心|
|[CD2D 半徑梯度畫筆::取得 RadiusX](#getradiusx)|檢索漸變橢圓的 x 半徑|
|[CD2D 半徑梯度畫筆::獲取半徑](#getradiusy)|檢索漸變橢圓的 y 半徑|
|[CD2D 半徑梯度畫筆::設置中心](#setcenter)|指定筆標空間中漸變橢圓的中心|
|[CD2D 半徑梯度畫筆::設定漸變原點偏移](#setgradientoriginoffset)|指定漸變原點的偏移量相對於漸變橢圓的中心|
|[CD2D 半徑梯度畫筆::SetRadiusX](#setradiusx)|在筆刷橢圓的 x 半徑|
|[CD2D 半徑梯度畫筆::SetRadiusY](#setradiusy)|在筆刷橢圓的 y 半徑|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CD2D 輻射梯度畫筆::操作員 ID2D1 輻射梯度畫筆*](#operator_id2d1radialgradientbrush_star)|傳回 ID2D1 徑向漸層線|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CD2D 輻射梯度畫筆::m_pRadialGradientBrush](#m_pradialgradientbrush)|指向 ID2D1 Radial 梯度畫筆的指標。|
|[CD2D半徑梯度畫筆::m_RadialGradientBrushProperties](#m_radialgradientbrushproperties)|畫筆漸變的中心、漸變原點偏移以及 x 半徑和 y 半徑。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CD2D 資源](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2D 梯度畫筆](../../mfc/reference/cd2dgradientbrush-class.md)

`CD2DRadialGradientBrush`

## <a name="requirements"></a>需求

**標題:** afxrendertarget.h

## <a name="cd2dradialgradientbrushcd2dradialgradientbrush"></a><a name="_dtorcd2dradialgradientbrush"></a>CD2D 徑梯度刷:*CD2D半徑梯度刷

解構函式。 銷毀 D2D 徑向漸變畫筆物件時調用。

```
virtual ~CD2DRadialGradientBrush();
```

## <a name="cd2dradialgradientbrushattach"></a><a name="attach"></a>CD2D 輻射梯度畫筆::附加

將現有資源介面附加到物件

```
void Attach(ID2D1RadialGradientBrush* pResource);
```

### <a name="parameters"></a>參數

*p資源*<br/>
現有資源介面。 無法為 NULL

## <a name="cd2dradialgradientbrushcd2dradialgradientbrush"></a><a name="cd2dradialgradientbrush"></a>CD2D 徑梯度刷::CD2D 半徑梯度刷

建構 CD2D 線性漸變畫筆物件。

```
CD2DRadialGradientBrush(
    CRenderTarget* pParentTarget,
    const D2D1_GRADIENT_STOP* gradientStops,
    UINT gradientStopsCount,
    D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES RadialGradientBrushProperties,
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

*把漸層筆屬性*<br/>
畫筆漸變的中心、漸變原點偏移以及 x 半徑和 y 半徑。

*顏色插值伽馬*<br/>
在漸變停止之間執行顏色插值的空間。

*擴充模式*<br/>
漸變在 [0,1] 規範化範圍之外的行為。

*pBrush 屬性*<br/>
指向畫筆的不一用性和變換的指標。

*bAuto銷毀*<br/>
指示物件將被擁有者(pParentTarget)銷毀。

## <a name="cd2dradialgradientbrushcreate"></a><a name="create"></a>CD2D 半徑漸層筆:建立

創建 CD2DRadial 漸變畫筆。

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>參數

*pRender 目標*<br/>
指向渲染目標的指標。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則,它將返回一個HRESULT錯誤代碼。

## <a name="cd2dradialgradientbrushdestroy"></a><a name="destroy"></a>CD2DRadial梯度刷::D

銷毀 CD2DRadial 梯度畫筆物件。

```
virtual void Destroy();
```

## <a name="cd2dradialgradientbrushdetach"></a><a name="detach"></a>CD2DRadial 梯度畫筆::D

從物件分離資源介面

```
ID2D1RadialGradientBrush* Detach();
```

### <a name="return-value"></a>傳回值

指向分離的資源介面的指標。

## <a name="cd2dradialgradientbrushget"></a><a name="get"></a>CD2D 半徑梯度畫筆:取得

傳回 ID2D1 徑向漸層線

```
ID2D1RadialGradientBrush* Get();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化,則指向 ID2D1Radial 梯度畫筆介面或 NULL 的指標。

## <a name="cd2dradialgradientbrushgetcenter"></a><a name="getcenter"></a>CD2D 半徑梯度畫筆::獲取中心

檢索漸變橢圓的中心

```
CD2DPointF GetCenter() const;
```

### <a name="return-value"></a>傳回值

漸變橢圓的中心。 此值在畫筆的座標空間中表示

## <a name="cd2dradialgradientbrushgetgradientoriginoffset"></a><a name="getgradientoriginoffset"></a>CD2D 半徑梯度畫筆::獲取梯度原點偏移

檢索漸變原點的偏移量相對於漸變橢圓的中心

```
CD2DPointF GetGradientOriginOffset() const;
```

### <a name="return-value"></a>傳回值

漸變原點的偏移量來自漸變橢圓的中心。 此值在畫筆的座標空間中表示

## <a name="cd2dradialgradientbrushgetradiusx"></a><a name="getradiusx"></a>CD2D 半徑梯度畫筆::取得 RadiusX

檢索漸變橢圓的 x 半徑

```
FLOAT GetRadiusX() const;
```

### <a name="return-value"></a>傳回值

漸變橢圓的 x 半徑。 此值在畫筆的座標空間中表示

## <a name="cd2dradialgradientbrushgetradiusy"></a><a name="getradiusy"></a>CD2D 半徑梯度畫筆::獲取半徑

檢索漸變橢圓的 y 半徑

```
FLOAT GetRadiusY() const;
```

### <a name="return-value"></a>傳回值

漸變橢圓的 y 半徑。 此值在畫筆的座標空間中表示

## <a name="cd2dradialgradientbrushm_pradialgradientbrush"></a><a name="m_pradialgradientbrush"></a>CD2D 輻射梯度畫筆::m_pRadialGradientBrush

指向 ID2D1 Radial 梯度畫筆的指標。

```
ID2D1RadialGradientBrush* m_pRadialGradientBrush;
```

## <a name="cd2dradialgradientbrushm_radialgradientbrushproperties"></a><a name="m_radialgradientbrushproperties"></a>CD2D半徑梯度畫筆::m_RadialGradientBrushProperties

畫筆漸變的中心、漸變原點偏移以及 x 半徑和 y 半徑。

```
D2D1_RADIAL_GRADIENT_BRUSH_PROPERTIES m_RadialGradientBrushProperties;
```

## <a name="cd2dradialgradientbrushoperator-id2d1radialgradientbrush"></a><a name="operator_id2d1radialgradientbrush_star"></a>CD2D 輻射梯度畫筆::操作員 ID2D1 輻射梯度畫筆*

傳回 ID2D1 徑向漸層線

```
operator ID2D1RadialGradientBrush*();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化,則指向 ID2D1Radial 梯度畫筆介面或 NULL 的指標。

## <a name="cd2dradialgradientbrushsetcenter"></a><a name="setcenter"></a>CD2D 半徑梯度畫筆::設置中心

指定筆標空間中漸變橢圓的中心

```
void SetCenter(CD2DPointF point);
```

### <a name="parameters"></a>參數

*點*<br/>
漸變橢圓的中心,位於畫筆的座標空間中

## <a name="cd2dradialgradientbrushsetgradientoriginoffset"></a><a name="setgradientoriginoffset"></a>CD2D 半徑梯度畫筆::設定漸變原點偏移

指定漸變原點的偏移量相對於漸變橢圓的中心

```
void SetGradientOriginOffset(CD2DPointF gradientOriginOffset);
```

### <a name="parameters"></a>參數

*梯度原點偏移*<br/>
漸變原點的偏移量來自漸變橢圓的中心

## <a name="cd2dradialgradientbrushsetradiusx"></a><a name="setradiusx"></a>CD2D 半徑梯度畫筆::SetRadiusX

在筆刷橢圓的 x 半徑

```
void SetRadiusX(FLOAT radiusX);
```

### <a name="parameters"></a>參數

*半徑X*<br/>
漸變橢圓的 x 半徑。 這個值位於畫筆的座標空間中

## <a name="cd2dradialgradientbrushsetradiusy"></a><a name="setradiusy"></a>CD2D 半徑梯度畫筆::SetRadiusY

在筆刷橢圓的 y 半徑

```
void SetRadiusY(FLOAT radiusY);
```

### <a name="parameters"></a>參數

*半徑Y*<br/>
漸變橢圓的 y 半徑。 這個值位於畫筆的座標空間中

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
