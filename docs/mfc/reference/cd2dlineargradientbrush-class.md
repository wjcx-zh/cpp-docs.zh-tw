---
title: CD2DLinearGradientBrush 類別
ms.date: 11/04/2016
f1_keywords:
- CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush::CD2DLinearGradientBrush
- AFXRENDERTARGET/CD2DLinearGradientBrush::Attach
- AFXRENDERTARGET/CD2DLinearGradientBrush::Create
- AFXRENDERTARGET/CD2DLinearGradientBrush::Destroy
- AFXRENDERTARGET/CD2DLinearGradientBrush::Detach
- AFXRENDERTARGET/CD2DLinearGradientBrush::Get
- AFXRENDERTARGET/CD2DLinearGradientBrush::GetEndPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::GetStartPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::SetEndPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::SetStartPoint
- AFXRENDERTARGET/CD2DLinearGradientBrush::m_LinearGradientBrushProperties
- AFXRENDERTARGET/CD2DLinearGradientBrush::m_pLinearGradientBrush
helpviewer_keywords:
- CD2DLinearGradientBrush [MFC], CD2DLinearGradientBrush
- CD2DLinearGradientBrush [MFC], Attach
- CD2DLinearGradientBrush [MFC], Create
- CD2DLinearGradientBrush [MFC], Destroy
- CD2DLinearGradientBrush [MFC], Detach
- CD2DLinearGradientBrush [MFC], Get
- CD2DLinearGradientBrush [MFC], GetEndPoint
- CD2DLinearGradientBrush [MFC], GetStartPoint
- CD2DLinearGradientBrush [MFC], SetEndPoint
- CD2DLinearGradientBrush [MFC], SetStartPoint
- CD2DLinearGradientBrush [MFC], m_LinearGradientBrushProperties
- CD2DLinearGradientBrush [MFC], m_pLinearGradientBrush
ms.assetid: d4be9ff9-0ea8-45e6-9b8d-f3bc5673cbac
ms.openlocfilehash: d87cdae5c24eae391be8db2fcdd04f91d592e427
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81753152"
---
# <a name="cd2dlineargradientbrush-class"></a>CD2DLinearGradientBrush 類別

ID2D1線性漸變筆的包裝器。

## <a name="syntax"></a>語法

```
class CD2DLinearGradientBrush : public CD2DGradientBrush;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2D線性梯度畫筆:CD2D線性梯度畫筆](#cd2dlineargradientbrush)|建構 CD2D 線性漸變畫筆物件。|
|[CD2D線性梯度畫筆:*CD2D線性梯度畫筆](#_dtorcd2dlineargradientbrush)|解構函式。 銷毀 D2D 線性漸變畫筆物件時調用。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CD2D線性漸變筆刷:附加](#attach)|將現有資源介面附加到物件|
|[CD2D 線性漸層刷筆刷:建立](#create)|創建 CD2D 線性漸變畫筆。 (覆寫[CD2D 資源:建立](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2D線性梯度畫筆::D](#destroy)|銷毀 CD2D 線性漸變畫筆物件。 (覆蓋[CD2D 梯度畫筆::Destroy](../../mfc/reference/cd2dgradientbrush-class.md#destroy).)|
|[CD2D線性梯度畫筆::D](#detach)|從物件分離資源介面|
|[CD2D 線性漸層刷筆刷:取得](#get)|傳回 ID2D1 線性漸層|
|[CD2D線性梯度畫筆::取得端點](#getendpoint)|檢索線性漸變的結束座標|
|[CD2D線性梯度畫筆::獲取起始點](#getstartpoint)|檢索線性漸層的起始座標|
|[CD2D 線性漸變筆刷:設定結束點](#setendpoint)|設定筆標空間中線性漸變的結束座標|
|[CD2D 線性漸變筆刷:設定起始點](#setstartpoint)|設定筆標空間中線性漸變的起始座標|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CD2D線性漸變筆刷::操作員 ID2D1 線性漸變筆刷*](#operator_id2d1lineargradientbrush_star)|傳回 ID2D1 線性漸層|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CD2D線性漸變畫筆::m_LinearGradientBrushProperties](#m_lineargradientbrushproperties)|漸變的開始和結束點。|
|[CD2D線性漸變畫筆::m_pLinearGradientBrush](#m_plineargradientbrush)|指向 ID2D1 線性漸變畫筆的指標。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CD2D 資源](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2D 梯度畫筆](../../mfc/reference/cd2dgradientbrush-class.md)

`CD2DLinearGradientBrush`

## <a name="requirements"></a>需求

**標題:** afxrendertarget.h

## <a name="cd2dlineargradientbrushcd2dlineargradientbrush"></a><a name="_dtorcd2dlineargradientbrush"></a>CD2D線性梯度畫筆:*CD2D線性梯度畫筆

解構函式。 銷毀 D2D 線性漸變畫筆物件時調用。

```
virtual ~CD2DLinearGradientBrush();
```

## <a name="cd2dlineargradientbrushattach"></a><a name="attach"></a>CD2D線性漸變筆刷:附加

將現有資源介面附加到物件

```cpp
void Attach(ID2D1LinearGradientBrush* pResource);
```

### <a name="parameters"></a>參數

*p資源*<br/>
現有資源介面。 無法為 NULL

## <a name="cd2dlineargradientbrushcd2dlineargradientbrush"></a><a name="cd2dlineargradientbrush"></a>CD2D線性梯度畫筆:CD2D線性梯度畫筆

建構 CD2D 線性漸變畫筆物件。

```
CD2DLinearGradientBrush(
    CRenderTarget* pParentTarget,
    const D2D1_GRADIENT_STOP* gradientStops,
    UINT gradientStopsCount,
    D2D1_LINEAR_GRADIENT_BRUSH_PROPERTIES LinearGradientBrushProperties,
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

*線性漸層式屬性*<br/>
漸變的開始和結束點。

*顏色插值伽馬*<br/>
在漸變停止之間執行顏色插值的空間。

*擴充模式*<br/>
漸變在 [0,1] 規範化範圍之外的行為。

*pBrush 屬性*<br/>
指向畫筆的不一用性和變換的指標。

*bAuto銷毀*<br/>
指示物件將被擁有者(pParentTarget)銷毀。

## <a name="cd2dlineargradientbrushcreate"></a><a name="create"></a>CD2D 線性漸層刷筆刷:建立

創建 CD2D 線性漸變畫筆。

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>參數

*pRender 目標*<br/>
指向渲染目標的指標。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則,它將返回一個HRESULT錯誤代碼。

## <a name="cd2dlineargradientbrushdestroy"></a><a name="destroy"></a>CD2D線性梯度畫筆::D

銷毀 CD2D 線性漸變畫筆物件。

```
virtual void Destroy();
```

## <a name="cd2dlineargradientbrushdetach"></a><a name="detach"></a>CD2D線性梯度畫筆::D

從物件分離資源介面

```
ID2D1LinearGradientBrush* Detach();
```

### <a name="return-value"></a>傳回值

指向分離的資源介面的指標。

## <a name="cd2dlineargradientbrushget"></a><a name="get"></a>CD2D 線性漸層刷筆刷:取得

傳回 ID2D1 線性漸層

```
ID2D1LinearGradientBrush* Get();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化,則指向 ID2D1線性漸變筆刷介面或 NULL 的指標。

## <a name="cd2dlineargradientbrushgetendpoint"></a><a name="getendpoint"></a>CD2D線性梯度畫筆::取得端點

檢索線性漸變的結束座標

```
CD2DPointF GetEndPoint() const;
```

### <a name="return-value"></a>傳回值

畫筆座標空間中線性漸變的結束二維座標

## <a name="cd2dlineargradientbrushgetstartpoint"></a><a name="getstartpoint"></a>CD2D線性梯度畫筆::獲取起始點

檢索線性漸層的起始座標

```
CD2DPointF GetStartPoint() const;
```

### <a name="return-value"></a>傳回值

畫筆座標空間中線性漸變的起始二維座標

## <a name="cd2dlineargradientbrushm_lineargradientbrushproperties"></a><a name="m_lineargradientbrushproperties"></a>CD2D線性漸變畫筆::m_LinearGradientBrushProperties

漸變的開始和結束點。

```
D2D1_LINEAR_GRADIENT_BRUSH_PROPERTIES m_LinearGradientBrushProperties;
```

## <a name="cd2dlineargradientbrushm_plineargradientbrush"></a><a name="m_plineargradientbrush"></a>CD2D線性漸變畫筆::m_pLinearGradientBrush

指向 ID2D1 線性漸變畫筆的指標。

```
ID2D1LinearGradientBrush* m_pLinearGradientBrush;
```

## <a name="cd2dlineargradientbrushoperator-id2d1lineargradientbrush"></a><a name="operator_id2d1lineargradientbrush_star"></a>CD2D線性漸變筆刷::操作員 ID2D1 線性漸變筆刷*

傳回 ID2D1 線性漸層

```
operator ID2D1LinearGradientBrush*();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化,則指向 ID2D1線性漸變筆刷介面或 NULL 的指標。

## <a name="cd2dlineargradientbrushsetendpoint"></a><a name="setendpoint"></a>CD2D 線性漸變筆刷:設定結束點

設定筆標空間中線性漸變的結束座標

```cpp
void SetEndPoint(CD2DPointF point);
```

### <a name="parameters"></a>參數

*點*<br/>
畫筆座標空間中線性漸變的結束二維座標

## <a name="cd2dlineargradientbrushsetstartpoint"></a><a name="setstartpoint"></a>CD2D 線性漸變筆刷:設定起始點

設定筆標空間中線性漸變的起始座標

```cpp
void SetStartPoint(CD2DPointF point);
```

### <a name="parameters"></a>參數

*點*<br/>
畫筆座標空間中線性漸變的起始二維座標

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
