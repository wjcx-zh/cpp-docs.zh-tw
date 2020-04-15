---
title: CD2DSolidColorBrush 類別
ms.date: 03/27/2019
f1_keywords:
- CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush::CD2DSolidColorBrush
- AFXRENDERTARGET/CD2DSolidColorBrush::Attach
- AFXRENDERTARGET/CD2DSolidColorBrush::Create
- AFXRENDERTARGET/CD2DSolidColorBrush::Destroy
- AFXRENDERTARGET/CD2DSolidColorBrush::Detach
- AFXRENDERTARGET/CD2DSolidColorBrush::Get
- AFXRENDERTARGET/CD2DSolidColorBrush::GetColor
- AFXRENDERTARGET/CD2DSolidColorBrush::SetColor
- AFXRENDERTARGET/CD2DSolidColorBrush::m_colorSolid
- AFXRENDERTARGET/CD2DSolidColorBrush::m_pSolidColorBrush
helpviewer_keywords:
- CD2DSolidColorBrush [MFC], CD2DSolidColorBrush
- CD2DSolidColorBrush [MFC], Attach
- CD2DSolidColorBrush [MFC], Create
- CD2DSolidColorBrush [MFC], Destroy
- CD2DSolidColorBrush [MFC], Detach
- CD2DSolidColorBrush [MFC], Get
- CD2DSolidColorBrush [MFC], GetColor
- CD2DSolidColorBrush [MFC], SetColor
- CD2DSolidColorBrush [MFC], m_colorSolid
- CD2DSolidColorBrush [MFC], m_pSolidColorBrush
ms.assetid: d4506637-acce-4f74-8a9b-f0a45571a735
ms.openlocfilehash: 5aa3d7688046b0c1b04983f2d27fe5579dd7c680
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369050"
---
# <a name="cd2dsolidcolorbrush-class"></a>CD2DSolidColorBrush 類別

ID2D1SolidColorBrush 的包裝器。

## <a name="syntax"></a>語法

```
class CD2DSolidColorBrush : public CD2DBrush;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2D純色筆::CD2D純色筆](#cd2dsolidcolorbrush)|已多載。 建構 CD2DSolidColorBrush 物件。|
|[CD2D純色筆::*CD2D純色刷](#_dtorcd2dsolidcolorbrush)|解構函式。 銷毀 D2D 實體畫筆物件時調用。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CD2D 純色筆::附加](#attach)|將現有資源介面附加到物件|
|[CD2D純色筆::建立](#create)|創建 CD2D 純色畫筆。 (覆寫[CD2D 資源:建立](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2D純色筆::D](#destroy)|銷毀 CD2DSolidColorBrush 物件。 (覆蓋[CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|
|[CD2D純色筆::D](#detach)|從物件分離資源介面|
|[CD2D純色筆:取得](#get)|傳回 ID2D1 純色筆介面|
|[CD2D純色筆::取得顏色](#getcolor)|檢索純色筆的顏色|
|[CD2D純色筆::設定顏色](#setcolor)|指定此純色筆刷的顏色|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CD2D純色筆::操作員 ID2D1 純色筆*](#operator_id2d1solidcolorbrush_star)|傳回 ID2D1 純色筆介面|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CD2D純色筆::m_colorSolid](#m_colorsolid)|刷純色。|
|[CD2D純色筆::m_pSolidColorBrush](#m_psolidcolorbrush)|儲存指向 ID2D1SolidColorBrush 物件的指標。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CD2D 資源](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

[CD2D純色筆刷](../../mfc/reference/cd2dsolidcolorbrush-class.md)

## <a name="requirements"></a>需求

**標題:** afxrendertarget.h

## <a name="cd2dsolidcolorbrushcd2dsolidcolorbrush"></a><a name="_dtorcd2dsolidcolorbrush"></a>CD2D純色筆::*CD2D純色刷

解構函式。 銷毀 D2D 實體畫筆物件時調用。

```
virtual ~CD2DSolidColorBrush();
```

## <a name="cd2dsolidcolorbrushattach"></a><a name="attach"></a>CD2D 純色筆::附加

將現有資源介面附加到物件

```
void Attach(ID2D1SolidColorBrush* pResource);
```

### <a name="parameters"></a>參數

*p資源*<br/>
現有資源介面。 無法為 NULL

## <a name="cd2dsolidcolorbrushcd2dsolidcolorbrush"></a><a name="cd2dsolidcolorbrush"></a>CD2D純色筆::CD2D純色筆

建構 CD2DSolidColorBrush 物件。

```
CD2DSolidColorBrush(
    CRenderTarget* pParentTarget,
    D2D1_COLOR_F color,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);

CD2DSolidColorBrush(
    CRenderTarget* pParentTarget,
    COLORREF color,
    int nAlpha = 255,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>參數

*p 父目標*<br/>
指向渲染目標的指標。

*顏色*<br/>
畫筆顏色的紅色、綠色、藍色和 Alpha 值。

*pBrush 屬性*<br/>
指向畫筆的不一用性和變換的指標。

*bAuto銷毀*<br/>
指示物件將被擁有者(pParentTarget)銷毀。

*n阿爾法*<br/>
畫筆顏色的不恰當性。

## <a name="cd2dsolidcolorbrushcreate"></a><a name="create"></a>CD2D純色筆::建立

創建 CD2D 純色畫筆。

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>參數

*pRender 目標*<br/>
指向渲染目標的指標。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則,它將返回一個HRESULT錯誤代碼。

## <a name="cd2dsolidcolorbrushdestroy"></a><a name="destroy"></a>CD2D純色筆::D

銷毀 CD2DSolidColorBrush 物件。

```
virtual void Destroy();
```

## <a name="cd2dsolidcolorbrushdetach"></a><a name="detach"></a>CD2D純色筆::D

從物件分離資源介面

```
ID2D1SolidColorBrush* Detach();
```

### <a name="return-value"></a>傳回值

指向分離的資源介面的指標。

## <a name="cd2dsolidcolorbrushget"></a><a name="get"></a>CD2D純色筆:取得

傳回 ID2D1 純色筆介面

```
ID2D1SolidColorBrush* Get();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化,則指向 ID2D1SolidColorBrush 介面或 NULL 的指標。

## <a name="cd2dsolidcolorbrushgetcolor"></a><a name="getcolor"></a>CD2D純色筆::取得顏色

檢索純色筆的顏色

```
D2D1_COLOR_F GetColor() const;
```

### <a name="return-value"></a>傳回值

此純色筆刷顏色

## <a name="cd2dsolidcolorbrushm_colorsolid"></a><a name="m_colorsolid"></a>CD2D純色筆::m_colorSolid

刷純色。

```
D2D1_COLOR_F m_colorSolid;
```

## <a name="cd2dsolidcolorbrushm_psolidcolorbrush"></a><a name="m_psolidcolorbrush"></a>CD2D純色筆::m_pSolidColorBrush

儲存指向 ID2D1SolidColorBrush 物件的指標。

```
ID2D1SolidColorBrush* m_pSolidColorBrush;
```

## <a name="cd2dsolidcolorbrushoperator-id2d1solidcolorbrush"></a><a name="operator_id2d1solidcolorbrush_star"></a>CD2D純色筆::操作員 ID2D1 純色筆*

傳回 ID2D1 純色筆介面

```
operator ID2D1SolidColorBrush*();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化,則指向 ID2D1SolidColorBrush 介面或 NULL 的指標。

## <a name="cd2dsolidcolorbrushsetcolor"></a><a name="setcolor"></a>CD2D純色筆::設定顏色

指定此純色筆刷的顏色

```
void SetColor(D2D1_COLOR_F color);
```

### <a name="parameters"></a>參數

*顏色*<br/>
此純色筆刷顏色

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
