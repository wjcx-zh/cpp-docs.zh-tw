---
title: CD2DBrush 類別
ms.date: 11/04/2016
f1_keywords:
- CD2DBrush
- AFXRENDERTARGET/CD2DBrush
- AFXRENDERTARGET/CD2DBrush::CD2DBrush
- AFXRENDERTARGET/CD2DBrush::Attach
- AFXRENDERTARGET/CD2DBrush::Destroy
- AFXRENDERTARGET/CD2DBrush::Detach
- AFXRENDERTARGET/CD2DBrush::Get
- AFXRENDERTARGET/CD2DBrush::GetOpacity
- AFXRENDERTARGET/CD2DBrush::GetTransform
- AFXRENDERTARGET/CD2DBrush::IsValid
- AFXRENDERTARGET/CD2DBrush::SetOpacity
- AFXRENDERTARGET/CD2DBrush::SetTransform
- AFXRENDERTARGET/CD2DBrush::m_pBrush
- AFXRENDERTARGET/CD2DBrush::m_pBrushProperties
helpviewer_keywords:
- CD2DBrush [MFC], CD2DBrush
- CD2DBrush [MFC], Attach
- CD2DBrush [MFC], Destroy
- CD2DBrush [MFC], Detach
- CD2DBrush [MFC], Get
- CD2DBrush [MFC], GetOpacity
- CD2DBrush [MFC], GetTransform
- CD2DBrush [MFC], IsValid
- CD2DBrush [MFC], SetOpacity
- CD2DBrush [MFC], SetTransform
- CD2DBrush [MFC], m_pBrush
- CD2DBrush [MFC], m_pBrushProperties
ms.assetid: 0d2c0857-2261-48a8-8ee0-a88cbf08499a
ms.openlocfilehash: d03fb6f398e18957f68fc18c78d8a397efc67506
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369272"
---
# <a name="cd2dbrush-class"></a>CD2DBrush 類別

ID2D1Brush 的包裝器。

## <a name="syntax"></a>語法

```
class CD2DBrush : public CD2DResource;
```

## <a name="members"></a>成員

### <a name="protected-constructors"></a>受保護的建構函式

|名稱|描述|
|----------|-----------------|
|[CD2DBrush:CD2DBrush](#cd2dbrush)|構造 CD2DBrush 物件。|
|[CD2DBrush:*CD2DBrush](#_dtorcd2dbrush)|解構函式。 銷毀 D2D 畫筆物件時調用。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CD2DBrush:附加](#attach)|將現有資源介面附加到物件|
|[CD2DBrush::D](#destroy)|銷毀 CD2DBrush 物件。 (覆蓋[CD2D 資源::D)](../../mfc/reference/cd2dresource-class.md#destroy)|
|[CD2DBrush::D](#detach)|從物件分離資源介面|
|[CD2DBrush:取得](#get)|傳回 ID2D1Brush 介面|
|[CD2DBrush:取得機會](#getopacity)|取得此筆刷的不恰當程度|
|[CD2DBrush:取得轉換](#gettransform)|取得成成一個目標的現層|
|[CD2DBrush:有效](#isvalid)|檢查資源有效性(覆寫[CD2D 資源::有效](../../mfc/reference/cd2dresource-class.md#isvalid)。)|
|[CD2DBrush:SetOpaa](#setopacity)|設定此筆刷的不恰當程度|
|[CD2DBrush::設定轉換](#settransform)|將指定的轉換應用於渲染目標,替換現有變換。 所有後續繪圖操作都發生在轉換的空間中|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CD2DBrush::操作員 ID2D1Brush*](#operator_id2d1brush_star)|傳回 ID2D1Brush 介面|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CD2DBrush:m_pBrush](#m_pbrush)|存儲指向 ID2D1Brush 物件的指標。|
|[CD2DBrush:m_pBrushProperties](#m_pbrushproperties)|畫筆屬性。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CD2D 資源](../../mfc/reference/cd2dresource-class.md)

`CD2DBrush`

## <a name="requirements"></a>需求

**標題:** afxrendertarget.h

## <a name="cd2dbrushcd2dbrush"></a><a name="_dtorcd2dbrush"></a>CD2DBrush:*CD2DBrush

解構函式。 銷毀 D2D 畫筆物件時調用。

```
virtual ~CD2DBrush();
```

## <a name="cd2dbrushattach"></a><a name="attach"></a>CD2DBrush:附加

將現有資源介面附加到物件。

```
void Attach(ID2D1Brush* pResource);
```

### <a name="parameters"></a>參數

*p資源*<br/>
現有資源介面。 不能是 NULL。

## <a name="cd2dbrushcd2dbrush"></a><a name="cd2dbrush"></a>CD2DBrush:CD2DBrush

構造 CD2DBrush 物件。

```
CD2DBrush(
    CRenderTarget* pParentTarget,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>參數

*p 父目標*<br/>
指向渲染目標的指標。

*pBrush 屬性*<br/>
指向畫筆的不一用性和變換的指標。

*bAuto銷毀*<br/>
指示物件將被擁有者(pParentTarget)銷毀。

## <a name="cd2dbrushdestroy"></a><a name="destroy"></a>CD2DBrush::D

銷毀 CD2DBrush 物件。

```
virtual void Destroy();
```

## <a name="cd2dbrushdetach"></a><a name="detach"></a>CD2DBrush::D

從物件分離資源介面。

```
ID2D1Brush* Detach();
```

### <a name="return-value"></a>傳回值

指向分離的資源介面的指標。

## <a name="cd2dbrushget"></a><a name="get"></a>CD2DBrush:取得

傳回 ID2D1Brush 介面

```
ID2D1Brush* Get();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化,則指向 ID2D1Brush 介面或 NULL 的指標。

## <a name="cd2dbrushgetopacity"></a><a name="getopacity"></a>CD2DBrush:取得機會

取得此筆刷的不恰當程度

```
FLOAT GetOpacity() const;
```

### <a name="return-value"></a>傳回值

零和 1 之間的值,指示畫筆的不恰當性。 此值是一個常量乘數,它線性縮放畫筆填充的所有圖元的 alpha 值。 不一元值在乘以 0 到 1 的範圍內夾緊, 然後再相乘。

## <a name="cd2dbrushgettransform"></a><a name="gettransform"></a>CD2DBrush:取得轉換

取得成成一個目標的現層

```
void GetTransform(D2D1_MATRIX_3X2_F* transform) const;
```

### <a name="parameters"></a>參數

*變換*<br/>
當返回時,包含渲染目標的當前變換。 此參數傳遞時未經初始化。

## <a name="cd2dbrushisvalid"></a><a name="isvalid"></a>CD2DBrush:有效

檢查資源有效性

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>傳回值

如果資源有效,則為 TRUE;否則 FALSE。

## <a name="cd2dbrushm_pbrush"></a><a name="m_pbrush"></a>CD2DBrush:m_pBrush

存儲指向 ID2D1Brush 物件的指標。

```
ID2D1Brush* m_pBrush;
```

## <a name="cd2dbrushm_pbrushproperties"></a><a name="m_pbrushproperties"></a>CD2DBrush:m_pBrushProperties

畫筆屬性。

```
CD2DBrushProperties* m_pBrushProperties;
```

## <a name="cd2dbrushoperator-id2d1brush"></a><a name="operator_id2d1brush_star"></a>CD2DBrush::操作員 ID2D1Brush*

傳回 ID2D1Brush 介面

```
operator ID2D1Brush*();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化,則指向 ID2D1Brush 介面或 NULL 的指標。

## <a name="cd2dbrushsetopacity"></a><a name="setopacity"></a>CD2DBrush:SetOpaa

設定此筆刷的不恰當程度

```
void SetOpacity(FLOAT opacity);
```

### <a name="parameters"></a>參數

*透明度*<br/>
零和 1 之間的值,指示畫筆的不恰當性。 此值是一個常量乘數,它線性縮放畫筆填充的所有圖元的 alpha 值。 不一元值在乘以 0 到 1 的範圍內夾緊, 然後再相乘。

## <a name="cd2dbrushsettransform"></a><a name="settransform"></a>CD2DBrush::設定轉換

將指定的轉換應用於渲染目標,替換現有變換。 所有後續繪圖操作都發生在轉換的空間中。

```
void SetTransform(const D2D1_MATRIX_3X2_F* transform);
```

### <a name="parameters"></a>參數

*變換*<br/>
套用成成成成成目標轉換

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
