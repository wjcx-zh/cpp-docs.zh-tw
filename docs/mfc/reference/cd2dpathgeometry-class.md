---
title: CD2DPathGeometry 類別
ms.date: 11/04/2016
f1_keywords:
- CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry::CD2DPathGeometry
- AFXRENDERTARGET/CD2DPathGeometry::Attach
- AFXRENDERTARGET/CD2DPathGeometry::Create
- AFXRENDERTARGET/CD2DPathGeometry::Destroy
- AFXRENDERTARGET/CD2DPathGeometry::Detach
- AFXRENDERTARGET/CD2DPathGeometry::GetFigureCount
- AFXRENDERTARGET/CD2DPathGeometry::GetSegmentCount
- AFXRENDERTARGET/CD2DPathGeometry::Open
- AFXRENDERTARGET/CD2DPathGeometry::Stream
- AFXRENDERTARGET/CD2DPathGeometry::m_pPathGeometry
helpviewer_keywords:
- CD2DPathGeometry [MFC], CD2DPathGeometry
- CD2DPathGeometry [MFC], Attach
- CD2DPathGeometry [MFC], Create
- CD2DPathGeometry [MFC], Destroy
- CD2DPathGeometry [MFC], Detach
- CD2DPathGeometry [MFC], GetFigureCount
- CD2DPathGeometry [MFC], GetSegmentCount
- CD2DPathGeometry [MFC], Open
- CD2DPathGeometry [MFC], Stream
- CD2DPathGeometry [MFC], m_pPathGeometry
ms.assetid: 686216eb-5080-4242-ace5-8fa1ce96307c
ms.openlocfilehash: 59ef82151983720b654502ccf3ca647e55366268
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369174"
---
# <a name="cd2dpathgeometry-class"></a>CD2DPathGeometry 類別

ID2D1Path幾何的包裝。

## <a name="syntax"></a>語法

```
class CD2DPathGeometry : public CD2DGeometry;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2D 路徑幾何:CD2D路徑幾何](#cd2dpathgeometry)|構造 CD2DPath 幾何物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CD2DPath幾何:附加](#attach)|將現有資源介面附加到物件|
|[CD2DPath幾何:建立](#create)|創建 CD2DPath 幾何體。 (覆寫[CD2D 資源:建立](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DPath幾何::D](#destroy)|銷毀 CD2DPath 幾何物件。 (覆蓋[CD2D 幾何::Destroy](../../mfc/reference/cd2dgeometry-class.md#destroy).)|
|[CD2DPath幾何::Detach](#detach)|從物件分離資源介面|
|[CD2DPath幾何:取得圖計數](#getfigurecount)|檢索路徑幾何體中的圖形數。|
|[CD2D路徑幾何:取得細分計數](#getsegmentcount)|檢索路徑幾何體中的線段數。|
|[CD2DPath幾何:開啟](#open)|檢索用於用圖形和線段填充路徑幾何體的幾何接收器。|
|[CD2DPath幾何:流](#stream)|將路徑幾何體的內容複製到指定的 ID2D1 幾何基克。|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CD2DPath幾何::m_pPathGeometry](#m_ppathgeometry)|指向 ID2D1 路徑幾何的指標。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CD2D 資源](../../mfc/reference/cd2dresource-class.md)

[CD2D 幾何](../../mfc/reference/cd2dgeometry-class.md)

`CD2DPathGeometry`

## <a name="requirements"></a>需求

**標題:** afxrendertarget.h

## <a name="cd2dpathgeometryattach"></a><a name="attach"></a>CD2DPath幾何:附加

將現有資源介面附加到物件

```
void Attach(ID2D1PathGeometry* pResource);
```

### <a name="parameters"></a>參數

*p資源*<br/>
現有資源介面。 無法為 NULL

## <a name="cd2dpathgeometrycd2dpathgeometry"></a><a name="cd2dpathgeometry"></a>CD2D 路徑幾何:CD2D路徑幾何

構造 CD2DPath 幾何物件。

```
CD2DPathGeometry(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>參數

*p 父目標*<br/>
指向渲染目標的指標。

*bAuto銷毀*<br/>
指示物件將被擁有者(pParentTarget)銷毀。

## <a name="cd2dpathgeometrycreate"></a><a name="create"></a>CD2DPath幾何:建立

創建 CD2DPath 幾何體。

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>參數

*pRender 目標*<br/>
指向渲染目標的指標。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則,它將返回一個HRESULT錯誤代碼。

## <a name="cd2dpathgeometrydestroy"></a><a name="destroy"></a>CD2DPath幾何::D

銷毀 CD2DPath 幾何物件。

```
virtual void Destroy();
```

## <a name="cd2dpathgeometrydetach"></a><a name="detach"></a>CD2DPath幾何::Detach

從物件分離資源介面

```
ID2D1PathGeometry* Detach();
```

### <a name="return-value"></a>傳回值

指向分離的資源介面的指標。

## <a name="cd2dpathgeometrygetfigurecount"></a><a name="getfigurecount"></a>CD2DPath幾何:取得圖計數

檢索路徑幾何體中的圖形數。

```
int GetFigureCount() const;
```

### <a name="return-value"></a>傳回值

返回路徑幾何體中的圖形數。

## <a name="cd2dpathgeometrygetsegmentcount"></a><a name="getsegmentcount"></a>CD2D路徑幾何:取得細分計數

檢索路徑幾何體中的線段數。

```
int GetSegmentCount() const;
```

### <a name="return-value"></a>傳回值

返回路徑幾何體中的線段數。

## <a name="cd2dpathgeometrym_ppathgeometry"></a><a name="m_ppathgeometry"></a>CD2DPath幾何::m_pPathGeometry

指向 ID2D1 路徑幾何的指標。

```
ID2D1PathGeometry* m_pPathGeometry;
```

## <a name="cd2dpathgeometryopen"></a><a name="open"></a>CD2DPath幾何:開啟

檢索用於用圖形和線段填充路徑幾何體的幾何接收器。

```
ID2D1GeometrySink* Open();
```

### <a name="return-value"></a>傳回值

指向 ID2D1 Geometry Sink 的指標,用於用圖形和線段填充路徑幾何體。

## <a name="cd2dpathgeometrystream"></a><a name="stream"></a>CD2DPath幾何:流

將路徑幾何體的內容複製到指定的 ID2D1 幾何基克。

```
BOOL Stream(ID2D1GeometrySink* geometrySink);
```

### <a name="parameters"></a>參數

*幾何結構*<br/>
將路徑幾何體的內容複製到的接收器。 修改此接收器不會更改此路徑幾何體的內容。

### <a name="return-value"></a>傳回值

如果該方法成功,它將返回 TRUE。 否則,它將返回 FALSE。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
