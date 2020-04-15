---
title: CBitmapRenderTarget 類別
ms.date: 11/04/2016
f1_keywords:
- CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::CBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::Attach
- AFXRENDERTARGET/CBitmapRenderTarget::Detach
- AFXRENDERTARGET/CBitmapRenderTarget::GetBitmap
- AFXRENDERTARGET/CBitmapRenderTarget::GetBitmapRenderTarget
- AFXRENDERTARGET/CBitmapRenderTarget::m_pBitmapRenderTarget
helpviewer_keywords:
- CBitmapRenderTarget [MFC], CBitmapRenderTarget
- CBitmapRenderTarget [MFC], Attach
- CBitmapRenderTarget [MFC], Detach
- CBitmapRenderTarget [MFC], GetBitmap
- CBitmapRenderTarget [MFC], GetBitmapRenderTarget
- CBitmapRenderTarget [MFC], m_pBitmapRenderTarget
ms.assetid: c89a4437-812e-4943-acb2-b429a04cc4d2
ms.openlocfilehash: 6249c121f7bcca0675a8138baef0e2cdc9e632d8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352594"
---
# <a name="cbitmaprendertarget-class"></a>CBitmapRenderTarget 類別

ID2D1BitmapRenderTarget 的包裝。

## <a name="syntax"></a>語法

```
class CBitmapRenderTarget : public CRenderTarget;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[C 位映射渲染目標::C 位貼圖成成目標](#cbitmaprendertarget)|構造 CBitmapRenderTarget 物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CBitmap渲染目標::附加](#attach)|將現有渲染目標介面附加到物件|
|[CBitmapRender目標::D](#detach)|從物件分離成成目標介面|
|[C 位映射渲染目標::取得點陣圖](#getbitmap)|檢索此渲染目標的位圖。 返回的點陣圖可用於繪圖操作。|
|[C 位貼圖渲染目標::取得位貼圖渲染目標](#getbitmaprendertarget)|傳回代碼2D1 位映射渲染目標介面|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CBitmap渲染目標::運算符 ID2D1 位貼圖渲染目標*](#operator_id2d1bitmaprendertarget_star)|傳回代碼2D1 位映射渲染目標介面|

### <a name="protected-data-members"></a>受保護的資料成員

|名稱|描述|
|----------|-----------------|
|[CBitmap渲染目標::m_pBitmapRenderTarget](#m_pbitmaprendertarget)|指向 ID2D1BitmapRenderTarget 物件的指標。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

[CObject](../../mfc/reference/cobject-class.md)

[CRender 目標](../../mfc/reference/crendertarget-class.md)

`CBitmapRenderTarget`

## <a name="requirements"></a>需求

**標題:** afxrendertarget.h

## <a name="cbitmaprendertargetattach"></a><a name="attach"></a>CBitmap渲染目標::附加

將現有渲染目標介面附加到物件

```
void Attach(ID2D1BitmapRenderTarget* pTarget);
```

### <a name="parameters"></a>參數

*p 目標*<br/>
現有渲染目標介面。 無法為 NULL

## <a name="cbitmaprendertargetcbitmaprendertarget"></a><a name="cbitmaprendertarget"></a>C 位映射渲染目標::C 位貼圖成成目標

構造 CBitmapRenderTarget 物件。

```
CBitmapRenderTarget();
```

## <a name="cbitmaprendertargetdetach"></a><a name="detach"></a>CBitmapRender目標::D

從物件分離成成目標介面

```
ID2D1BitmapRenderTarget* Detach();
```

### <a name="return-value"></a>傳回值

指向分離的渲染目標介面的指標。

## <a name="cbitmaprendertargetgetbitmap"></a><a name="getbitmap"></a>C 位映射渲染目標::取得點陣圖

檢索此渲染目標的位圖。 返回的點陣圖可用於繪圖操作。

```
BOOL GetBitmap(CD2DBitmap& bitmap);
```

### <a name="parameters"></a>參數

*點陣圖*<br/>
當此方法返回時,包含此渲染目標的有效位圖。 此點陣圖可用於繪圖操作。

### <a name="return-value"></a>傳回值

如果該方法成功,它將返回 TRUE。 否則,它將返回 FALSE。

## <a name="cbitmaprendertargetgetbitmaprendertarget"></a><a name="getbitmaprendertarget"></a>C 位貼圖渲染目標::取得位貼圖渲染目標

傳回代碼2D1 位映射渲染目標介面

```
ID2D1BitmapRenderTarget* GetBitmapRenderTarget();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化,則指向 ID2D1BitmapRenderTarget 介面或 NULL 的指標。

## <a name="cbitmaprendertargetm_pbitmaprendertarget"></a><a name="m_pbitmaprendertarget"></a>CBitmap渲染目標::m_pBitmapRenderTarget

指向 ID2D1BitmapRenderTarget 物件的指標。

```
ID2D1BitmapRenderTarget* m_pBitmapRenderTarget;
```

## <a name="cbitmaprendertargetoperator-id2d1bitmaprendertarget"></a><a name="operator_id2d1bitmaprendertarget_star"></a>CBitmap渲染目標::運算符 ID2D1 位貼圖渲染目標*

傳回代碼2D1 位映射渲染目標介面

```
operator ID2D1BitmapRenderTarget*();
```

### <a name="return-value"></a>傳回值

如果物件尚未初始化,則指向 ID2D1BitmapRenderTarget 介面或 NULL 的指標。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
