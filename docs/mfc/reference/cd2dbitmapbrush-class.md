---
title: CD2DBitmapBrush 類別
ms.date: 11/04/2016
f1_keywords:
- CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::CD2DBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::Attach
- AFXRENDERTARGET/CD2DBitmapBrush::Create
- AFXRENDERTARGET/CD2DBitmapBrush::Destroy
- AFXRENDERTARGET/CD2DBitmapBrush::Detach
- AFXRENDERTARGET/CD2DBitmapBrush::Get
- AFXRENDERTARGET/CD2DBitmapBrush::GetBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::GetExtendModeX
- AFXRENDERTARGET/CD2DBitmapBrush::GetExtendModeY
- AFXRENDERTARGET/CD2DBitmapBrush::GetInterpolationMode
- AFXRENDERTARGET/CD2DBitmapBrush::SetBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::SetExtendModeX
- AFXRENDERTARGET/CD2DBitmapBrush::SetExtendModeY
- AFXRENDERTARGET/CD2DBitmapBrush::SetInterpolationMode
- AFXRENDERTARGET/CD2DBitmapBrush::CommonInit
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmap
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmapBrush
- AFXRENDERTARGET/CD2DBitmapBrush::m_pBitmapBrushProperties
helpviewer_keywords:
- CD2DBitmapBrush [MFC], CD2DBitmapBrush
- CD2DBitmapBrush [MFC], Attach
- CD2DBitmapBrush [MFC], Create
- CD2DBitmapBrush [MFC], Destroy
- CD2DBitmapBrush [MFC], Detach
- CD2DBitmapBrush [MFC], Get
- CD2DBitmapBrush [MFC], GetBitmap
- CD2DBitmapBrush [MFC], GetExtendModeX
- CD2DBitmapBrush [MFC], GetExtendModeY
- CD2DBitmapBrush [MFC], GetInterpolationMode
- CD2DBitmapBrush [MFC], SetBitmap
- CD2DBitmapBrush [MFC], SetExtendModeX
- CD2DBitmapBrush [MFC], SetExtendModeY
- CD2DBitmapBrush [MFC], SetInterpolationMode
- CD2DBitmapBrush [MFC], CommonInit
- CD2DBitmapBrush [MFC], m_pBitmap
- CD2DBitmapBrush [MFC], m_pBitmapBrush
- CD2DBitmapBrush [MFC], m_pBitmapBrushProperties
ms.assetid: 46ebbe34-66e0-44c8-af1d-d129e851de5e
ms.openlocfilehash: e26202392bf4783598aec0dddfea514fce806a8c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369304"
---
# <a name="cd2dbitmapbrush-class"></a>CD2DBitmapBrush 類別

ID2D1 位地圖畫筆的包裝器。

## <a name="syntax"></a>語法

```
class CD2DBitmapBrush : public CD2DBrush;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2DBitmapBrush::CD2DBitmapBrush](#cd2dbitmapbrush)|已多載。 從文件構造 CD2DBitmapBrush 物件。|
|[CD2DBitmapBrush:*CD2DBitmapBrush](#dtor)|解構函式。 銷毀 D2D 位圖畫筆物件時調用。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CD2DBitmapBrush::附加](#attach)|將現有資源介面附加到物件|
|[CD2DBitmapBrush:建立](#create)|創建 CD2DBitmapBrush。 (覆寫[CD2D 資源:建立](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DBitmapBrush::D](#destroy)|銷毀 CD2DBitmapBrush 物件。 (覆蓋[CD2DBrush::Destroy](../../mfc/reference/cd2dbrush-class.md#destroy).)|
|[CD2DBitmapBrush::Detach](#detach)|從物件分離資源介面|
|[CD2DBitmapBrush:取得](#get)|傳回 ID2D1 位地圖筆刷介面|
|[CD2DBitmapBrush::取得點陣圖](#getbitmap)|取得此筆刷筆繪製的點陣圖|
|[CD2DBitmapBrush::取得擴展模式X](#getextendmodex)|取得筆刷水平擺回超出其位圖的區域的方法|
|[CD2DBitmapBrush:取得擴充模式](#getextendmodey)|取得畫筆垂直繪製超出其位圖的區域切片的方法|
|[CD2DBitmapBrush:取得插值模式](#getinterpolationmode)|取得縮放或旋轉筆畫筆點的插數方法|
|[CD2DBitmapBrush::設定點陣圖](#setbitmap)|指定此筆刷的畫筆|
|[CD2DBitmapBrush::設定延伸模式X](#setextendmodex)|指定筆刷如何水平放置那些延伸到其位圖的區域|
|[CD2DBitmapBrush::設定延伸模式](#setextendmodey)|指定筆畫筆如何垂直繪製超出其位圖的區域的切片|
|[CD2DBitmapBrush:設定插值模式](#setinterpolationmode)|指定縮放或旋轉筆點貼圖時使用的插值模式|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CD2DBitmapBrush::通用](#commoninit)|初始化物件|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CD2DBitmapBrush::操作員 ID2D1 位地圖畫筆*](#operator_id2d1bitmapbrush_star)|傳回 ID2D1 位地圖筆刷介面|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CD2DBitmapBrush:m_pBitmap](#m_pbitmap)|存儲指向 CD2DBitmap 物件的指標。|
|[CD2DBitmapBrush::m_pBitmapBrush](#m_pbitmapbrush)|存儲指向 ID2D1BitmapBrush 物件的指標。|
|[CD2DBitmapBrush::m_pBitmapBrushProperties](#m_pbitmapbrushproperties)|位圖畫筆屬性。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CD2D 資源](../../mfc/reference/cd2dresource-class.md)

[CD2DBrush](../../mfc/reference/cd2dbrush-class.md)

`CD2DBitmapBrush`

## <a name="requirements"></a>需求

**標題:** afxrendertarget.h

## <a name="cd2dbitmapbrushcd2dbitmapbrush"></a><a name="dtor"></a>CD2DBitmapBrush:*CD2DBitmapBrush

解構函式。 銷毀 D2D 位圖畫筆物件時調用。

```
virtual ~CD2DBitmapBrush();
```

## <a name="cd2dbitmapbrushattach"></a><a name="attach"></a>CD2DBitmapBrush::附加

將現有資源介面附加到物件

```
void Attach(ID2D1BitmapBrush* pResource);
```

### <a name="parameters"></a>參數

*p資源*<br/>
現有資源介面。 無法為 NULL

## <a name="cd2dbitmapbrushcd2dbitmapbrush"></a><a name="cd2dbitmapbrush"></a>CD2DBitmapBrush::CD2DBitmapBrush

構造 CD2DBitmapBrush 物件。

```
CD2DBitmapBrush(
    CRenderTarget* pParentTarget,
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);

CD2DBitmapBrush(
    CRenderTarget* pParentTarget,
    UINT uiResID,
    LPCTSTR lpszType = NULL,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);

CD2DBitmapBrush(
    CRenderTarget* pParentTarget,
    LPCTSTR lpszImagePath,
    CD2DSizeU sizeDest = CD2DSizeU(0, 0),
    D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties = NULL,
    CD2DBrushProperties* pBrushProperties = NULL,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>參數

*p 父目標*<br/>
指向渲染目標的指標。

*pBitmapBrush 屬性*<br/>
指向擴展模式的指標和位圖畫筆的插值模式。

*pBrush 屬性*<br/>
指向畫筆的不一用性和變換的指標。

*bAuto銷毀*<br/>
指示物件將被擁有者(pParentTarget)銷毀。

*uiResID*<br/>
資源的資源識別碼。

*lpszType*<br/>
指向包含資源類型的空端字串的指標。

*大小 D 最大*<br/>
位圖的目標大小。

*lpsz 影像路徑*<br/>
包含檔案名稱的 null 中斷字串的指標。

## <a name="cd2dbitmapbrushcommoninit"></a><a name="commoninit"></a>CD2DBitmapBrush::通用

初始化物件

```
void CommonInit(D2D1_BITMAP_BRUSH_PROPERTIES* pBitmapBrushProperties);
```

### <a name="parameters"></a>參數

*pBitmapBrush 屬性*<br/>
指向位圖畫筆屬性的指標。

## <a name="cd2dbitmapbrushcreate"></a><a name="create"></a>CD2DBitmapBrush:建立

創建 CD2DBitmapBrush。

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>參數

*pRender 目標*<br/>
指向渲染目標的指標。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則,它將返回一個HRESULT錯誤代碼。

## <a name="cd2dbitmapbrushdestroy"></a><a name="destroy"></a>CD2DBitmapBrush::D

銷毀 CD2DBitmapBrush 物件。

```
virtual void Destroy();
```

## <a name="cd2dbitmapbrushdetach"></a><a name="detach"></a>CD2DBitmapBrush::Detach

從物件分離資源介面

```
ID2D1BitmapBrush* Detach();
```

### <a name="return-value"></a>傳回值

指向分離的資源介面的指標。

## <a name="cd2dbitmapbrushget"></a><a name="get"></a>CD2DBitmapBrush:取得

傳回 ID2D1 位地圖筆刷介面

```
ID2D1BitmapBrush* Get();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化,則指向 ID2D1BitmapBrush 介面或 NULL 的指標。

## <a name="cd2dbitmapbrushgetbitmap"></a><a name="getbitmap"></a>CD2DBitmapBrush::取得點陣圖

取得此筆刷筆繪製的點陣圖

```
CD2DBitmap* GetBitmap();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化,則指向 CD2DBitmap 物件或 NULL 的指標。

## <a name="cd2dbitmapbrushgetextendmodex"></a><a name="getextendmodex"></a>CD2DBitmapBrush::取得擴展模式X

取得筆刷水平擺回超出其位圖的區域的方法

```
D2D1_EXTEND_MODE GetExtendModeX() const;
```

### <a name="return-value"></a>傳回值

指定筆刷如何水平放置那些延伸到其位圖的區域的值

## <a name="cd2dbitmapbrushgetextendmodey"></a><a name="getextendmodey"></a>CD2DBitmapBrush:取得擴充模式

取得畫筆垂直繪製超出其位圖的區域切片的方法

```
D2D1_EXTEND_MODE GetExtendModeY() const;
```

### <a name="return-value"></a>傳回值

指定筆刷如何垂直繪製超出其位圖的區域的切片的值

## <a name="cd2dbitmapbrushgetinterpolationmode"></a><a name="getinterpolationmode"></a>CD2DBitmapBrush:取得插值模式

取得縮放或旋轉筆畫筆點的插數方法

```
D2D1_BITMAP_INTERPOLATION_MODE GetInterpolationMode() const;
```

### <a name="return-value"></a>傳回值

縮放或旋轉筆點圖時使用的插值方法

## <a name="cd2dbitmapbrushm_pbitmap"></a><a name="m_pbitmap"></a>CD2DBitmapBrush:m_pBitmap

存儲指向 CD2DBitmap 物件的指標。

```
CD2DBitmap* m_pBitmap;
```

## <a name="cd2dbitmapbrushm_pbitmapbrush"></a><a name="m_pbitmapbrush"></a>CD2DBitmapBrush::m_pBitmapBrush

存儲指向 ID2D1BitmapBrush 物件的指標。

```
ID2D1BitmapBrush* m_pBitmapBrush;
```

## <a name="cd2dbitmapbrushm_pbitmapbrushproperties"></a><a name="m_pbitmapbrushproperties"></a>CD2DBitmapBrush::m_pBitmapBrushProperties

位圖畫筆屬性。

```
D2D1_BITMAP_BRUSH_PROPERTIES* m_pBitmapBrushProperties;
```

## <a name="cd2dbitmapbrushoperator-id2d1bitmapbrush"></a><a name="operator_id2d1bitmapbrush_star"></a>CD2DBitmapBrush::操作員 ID2D1 位地圖畫筆*

傳回 ID2D1 位地圖筆刷介面

```
operator ID2D1BitmapBrush*();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化,則指向 ID2D1BitmapBrush 介面或 NULL 的指標。

## <a name="cd2dbitmapbrushsetbitmap"></a><a name="setbitmap"></a>CD2DBitmapBrush::設定點陣圖

指定此筆刷的畫筆

```
void SetBitmap(CD2DBitmap* pBitmap);
```

### <a name="parameters"></a>參數

*pBitmap*<br/>
筆刷的點陣圖來源

## <a name="cd2dbitmapbrushsetextendmodex"></a><a name="setextendmodex"></a>CD2DBitmapBrush::設定延伸模式X

指定筆刷如何水平放置那些延伸到其位圖的區域

```
void SetExtendModeX(D2D1_EXTEND_MODE extendModeX);
```

### <a name="parameters"></a>參數

*擴充模式X*<br/>
指定筆刷如何水平放置那些延伸到其位圖的區域的值

## <a name="cd2dbitmapbrushsetextendmodey"></a><a name="setextendmodey"></a>CD2DBitmapBrush::設定延伸模式

指定筆畫筆如何垂直繪製超出其位圖的區域的切片

```
void SetExtendModeY(D2D1_EXTEND_MODE extendModeY);
```

### <a name="parameters"></a>參數

*擴充模式*<br/>
指定筆刷如何垂直繪製超出其位圖的區域的切片的值

## <a name="cd2dbitmapbrushsetinterpolationmode"></a><a name="setinterpolationmode"></a>CD2DBitmapBrush:設定插值模式

指定縮放或旋轉筆點貼圖時使用的插值模式

```
void SetInterpolationMode(D2D1_BITMAP_INTERPOLATION_MODE interpolationMode);
```

### <a name="parameters"></a>參數

*插值模式*<br/>
調整或旋轉筆點圖時使用的插值模式

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
