---
title: CD2DLayer 類別
ms.date: 11/04/2016
f1_keywords:
- CD2DLayer
- AFXRENDERTARGET/CD2DLayer
- AFXRENDERTARGET/CD2DLayer::CD2DLayer
- AFXRENDERTARGET/CD2DLayer::Attach
- AFXRENDERTARGET/CD2DLayer::Create
- AFXRENDERTARGET/CD2DLayer::Destroy
- AFXRENDERTARGET/CD2DLayer::Detach
- AFXRENDERTARGET/CD2DLayer::Get
- AFXRENDERTARGET/CD2DLayer::GetSize
- AFXRENDERTARGET/CD2DLayer::IsValid
- AFXRENDERTARGET/CD2DLayer::m_pLayer
helpviewer_keywords:
- CD2DLayer [MFC], CD2DLayer
- CD2DLayer [MFC], Attach
- CD2DLayer [MFC], Create
- CD2DLayer [MFC], Destroy
- CD2DLayer [MFC], Detach
- CD2DLayer [MFC], Get
- CD2DLayer [MFC], GetSize
- CD2DLayer [MFC], IsValid
- CD2DLayer [MFC], m_pLayer
ms.assetid: 2f96378e-66bb-40d1-9661-6afe324de3c1
ms.openlocfilehash: 30025d6097e439c07202d144a6e549845b78ffa6
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754754"
---
# <a name="cd2dlayer-class"></a>CD2DLayer 類別

ID2D1Layer 的包裝器。

## <a name="syntax"></a>語法

```
class CD2DLayer : public CD2DResource;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2DLayer:CD2DLayer](#cd2dlayer)|構造 CD2DLayer 物件。|
|[CD2DLayer:*CD2DLayer](#_dtorcd2dlayer)|解構函式。 銷毀 D2D 圖層物件時調用。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CD2DLayer:附加](#attach)|將現有資源介面附加到物件|
|[CD2DLayer:建立](#create)|創建 CD2DLayer。 (覆寫[CD2D 資源:建立](../../mfc/reference/cd2dresource-class.md#create).)|
|[CD2DLayer::D](#destroy)|銷毀 CD2DLayer 物件。 (覆蓋[CD2D 資源::D)](../../mfc/reference/cd2dresource-class.md#destroy)|
|[CD2DLayer::D](#detach)|從物件分離資源介面|
|[CD2DLayer:取得](#get)|傳回 ID2D1Layer 介面|
|[CD2DLayer:取得 Size](#getsize)|傳回與裝置的像素的成成目標的大小|
|[CD2DLayer:有效](#isvalid)|檢查資源有效性(覆寫[CD2D 資源::有效](../../mfc/reference/cd2dresource-class.md#isvalid)。)|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CD2DLayer::操作員 ID2D1Layer*](#operator_id2d1layer_star)|傳回 ID2D1Layer 介面|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CD2DLayer:m_pLayer](#m_player)|存儲指向 ID2D1Layer 物件的指標。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CD2D 資源](../../mfc/reference/cd2dresource-class.md)

`CD2DLayer`

## <a name="requirements"></a>需求

**標題:** afxrendertarget.h

## <a name="cd2dlayercd2dlayer"></a><a name="_dtorcd2dlayer"></a>CD2DLayer:*CD2DLayer

解構函式。 銷毀 D2D 圖層物件時調用。

```
virtual ~CD2DLayer();
```

## <a name="cd2dlayerattach"></a><a name="attach"></a>CD2DLayer:附加

將現有資源介面附加到物件

```cpp
void Attach(ID2D1Layer* pResource);
```

### <a name="parameters"></a>參數

*p資源*<br/>
現有資源介面。 無法為 NULL

## <a name="cd2dlayercd2dlayer"></a><a name="cd2dlayer"></a>CD2DLayer:CD2DLayer

構造 CD2DLayer 物件。

```
CD2DLayer(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>參數

*p 父目標*<br/>
指向渲染目標的指標。

*bAuto銷毀*<br/>
指示物件將被擁有者(pParentTarget)銷毀。

## <a name="cd2dlayercreate"></a><a name="create"></a>CD2DLayer:建立

創建 CD2DLayer。

```
virtual HRESULT Create(CRenderTarget* pRenderTarget);
```

### <a name="parameters"></a>參數

*pRender 目標*<br/>
指向渲染目標的指標。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 S_OK。 否則,它將返回一個HRESULT錯誤代碼。

## <a name="cd2dlayerdestroy"></a><a name="destroy"></a>CD2DLayer::D

銷毀 CD2DLayer 物件。

```
virtual void Destroy();
```

## <a name="cd2dlayerdetach"></a><a name="detach"></a>CD2DLayer::D

從物件分離資源介面

```
ID2D1Layer* Detach();
```

### <a name="return-value"></a>傳回值

指向分離的資源介面的指標。

## <a name="cd2dlayerget"></a><a name="get"></a>CD2DLayer:取得

傳回 ID2D1Layer 介面

```
ID2D1Layer* Get();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化,則指向 ID2D1Layer 介面或 NULL 的指標。

## <a name="cd2dlayergetsize"></a><a name="getsize"></a>CD2DLayer:取得 Size

傳回與裝置的像素的成成目標的大小

```
CD2DSizeF GetSize() const;
```

### <a name="return-value"></a>傳回值

以與裝置的像素表示成成目標的目前大小

## <a name="cd2dlayerisvalid"></a><a name="isvalid"></a>CD2DLayer:有效

檢查資源有效性

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>傳回值

如果資源有效,則為 TRUE;否則 FALSE。

## <a name="cd2dlayerm_player"></a><a name="m_player"></a>CD2DLayer:m_pLayer

存儲指向 ID2D1Layer 物件的指標。

```
ID2D1Layer* m_pLayer;
```

## <a name="cd2dlayeroperator-id2d1layer"></a><a name="operator_id2d1layer_star"></a>CD2DLayer::操作員 ID2D1Layer*

傳回 ID2D1Layer 介面

```
operator ID2D1Layer* ();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化,則指向 ID2D1Layer 介面或 NULL 的指標。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
