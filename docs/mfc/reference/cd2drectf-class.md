---
title: CD2DRectF 類別
ms.date: 11/04/2016
f1_keywords:
- CD2DRectF
- AFXRENDERTARGET/CD2DRectF
- AFXRENDERTARGET/CD2DRectF::CD2DRectF
- AFXRENDERTARGET/CD2DRectF::IsNull
helpviewer_keywords:
- CD2DRectF [MFC], CD2DRectF
- CD2DRectF [MFC], IsNull
ms.assetid: 87c12d87-9d18-4a19-ba14-0f51d6b6835a
ms.openlocfilehash: 9b91cfaec3827a61152c4116b56e817a436606be
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/31/2019
ms.locfileid: "68682394"
---
# <a name="cd2drectf-class"></a>CD2DRectF 類別

`D2D1_RECT_F`的包裝函式。

## <a name="syntax"></a>語法

```
class CD2DRectF : public D2D1_RECT_F;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2DRectF::CD2DRectF](#cd2drectf)|多載。 `CD2DRectF` 從`D2D1_RECT_F`物件結構建立物件。|

### <a name="public-methods"></a>公用方法

|名稱|說明|
|----------|-----------------|
|[CD2DRectF::IsNull](#isnull)|傳回**布林**值, 指出運算式是否不包含有效的資料 (Null)。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CD2DRectF:: operator CRect](#operator_crect)|轉換`CD2DRectF` 成`CRect`物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`D2D1_RECT_F`

`CD2DRectF`

## <a name="requirements"></a>需求

**標頭:** afxrendertarget。h

##  <a name="cd2drectf"></a>  CD2DRectF::CD2DRectF

從 CRect 物件中, 建立 CD2DRectF 物件。

```
CD2DRectF(const CRect& rect);
CD2DRectF(const D2D1_RECT_F& rect);
CD2DRectF(const D2D1_RECT_F* rect);

CD2DRectF(
    FLOAT fLeft = 0.,
    FLOAT fTop = 0.,
    FLOAT fRight = 0.,
    FLOAT fBottom = 0.);
```

### <a name="parameters"></a>參數

*rect*<br/>
來源矩形

*fLeft*<br/>
來源左邊座標

*fTop*<br/>
來源最上層座標

*fRight*<br/>
來源右座標

*fBottom*<br/>
來源底部座標

##  <a name="isnull"></a>  CD2DRectF::IsNull

傳回布林值, 指出運算式是否不包含有效的資料 (Null)。

```
BOOL IsNull() const;
```

### <a name="return-value"></a>傳回值

如果矩形的上、左、下和右值全都等於 0, 則為 TRUE;否則為 FALSE。

##  <a name="operator_crect"></a>  CD2DRectF::operator CRect

將 CD2DRectF 轉換為 CRect 物件。

```
operator CRect();
```

### <a name="return-value"></a>傳回值

D2D 矩形的目前值。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
