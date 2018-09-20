---
title: CBitmapRenderTarget 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::Attach
- AFXRENDERTARGET/CBitmapRenderTarget::Detach
- AFXRENDERTARGET/CBitmapRenderTarget::GetBitmap
- AFXRENDERTARGET/CBitmapRenderTarget::GetBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::m_pBitmapRenderTarget
dev_langs:
- C++
helpviewer_keywords:
- CBitmapRenderTarget [MFC], CBitmapRenderTarget
- CBitmapRenderTarget [MFC], Attach
- CBitmapRenderTarget [MFC], Detach
- CBitmapRenderTarget [MFC], GetBitmap
- CBitmapRenderTarget [MFC], GetBitmapRenderTarget
- CBitmapRenderTarget [MFC], m_pBitmapRenderTarget
ms.assetid: c89a4437-812e-4943-acb2-b429a04cc4d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ee70825711efd82ce451a0433a63d98d93850552
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417055"
---
# <a name="cbitmaprendertarget-class"></a>CBitmapRenderTarget 類別

ID2D1BitmapRenderTarget 包裝函式。

## <a name="syntax"></a>語法

```
class CBitmapRenderTarget : public CRenderTarget;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CBitmapRenderTarget::CBitmapRenderTarget](#cbitmaprendertarget)|建構 CBitmapRenderTarget 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CBitmapRenderTarget::Attach](#attach)|將現有的轉譯目標物件的介面|
|[CBitmapRenderTarget::Detach](#detach)|中斷連結物件的轉譯目標介面|
|[CBitmapRenderTarget::GetBitmap](#getbitmap)|擷取此呈現目標的點陣圖。 傳回的點陣圖可以用於繪製作業。|
|[CBitmapRenderTarget::GetBitmapRenderTarget](#getbitmaprendertarget)|傳回 ID2D1BitmapRenderTarget 介面|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CBitmapRenderTarget::operator ID2D1BitmapRenderTarget *](#operator_id2d1bitmaprendertarget_star)|傳回 ID2D1BitmapRenderTarget 介面|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CBitmapRenderTarget::m_pBitmapRenderTarget](#m_pbitmaprendertarget)|ID2D1BitmapRenderTarget 物件的指標。|

## <a name="inheritance-hierarchy"></a>繼承階層

[CObject](../../mfc/reference/cobject-class.md)

[CRenderTarget](../../mfc/reference/crendertarget-class.md)

`CBitmapRenderTarget`

## <a name="requirements"></a>需求

**標頭：** afxrendertarget.h

##  <a name="attach"></a>  CBitmapRenderTarget::Attach

將現有的轉譯目標物件的介面

```
void Attach(ID2D1BitmapRenderTarget* pTarget);
```

### <a name="parameters"></a>參數

*pTarget*<br/>
現有的轉譯目標介面。 不能是 NULL

##  <a name="cbitmaprendertarget"></a>  CBitmapRenderTarget::CBitmapRenderTarget

建構 CBitmapRenderTarget 物件。

```
CBitmapRenderTarget();
```

##  <a name="detach"></a>  CBitmapRenderTarget::Detach

中斷連結物件的轉譯目標介面

```
ID2D1BitmapRenderTarget* Detach();
```

### <a name="return-value"></a>傳回值

卸離的指標轉譯目標的介面。

##  <a name="getbitmap"></a>  CBitmapRenderTarget::GetBitmap

擷取此呈現目標的點陣圖。 傳回的點陣圖可以用於繪製作業。

```
BOOL GetBitmap(CD2DBitmap& bitmap);
```

### <a name="parameters"></a>參數

*點陣圖*<br/>
當這個方法傳回時，包含此轉譯目標的有效點陣圖。 此點陣圖可以用於繪製作業。

### <a name="return-value"></a>傳回值

如果方法成功，它會傳回 TRUE。 否則，它會傳回 FALSE。

##  <a name="getbitmaprendertarget"></a>  CBitmapRenderTarget::GetBitmapRenderTarget

傳回 ID2D1BitmapRenderTarget 介面

```
ID2D1BitmapRenderTarget* GetBitmapRenderTarget();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化為 NULL 的 ID2D1BitmapRenderTarget 介面的指標。

##  <a name="m_pbitmaprendertarget"></a>  CBitmapRenderTarget::m_pBitmapRenderTarget

ID2D1BitmapRenderTarget 物件的指標。

```
ID2D1BitmapRenderTarget* m_pBitmapRenderTarget;
```

##  <a name="operator_id2d1bitmaprendertarget_star"></a>  CBitmapRenderTarget::operator ID2D1BitmapRenderTarget *

傳回 ID2D1BitmapRenderTarget 介面

```
operator ID2D1BitmapRenderTarget*();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化為 NULL 的 ID2D1BitmapRenderTarget 介面的指標。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
