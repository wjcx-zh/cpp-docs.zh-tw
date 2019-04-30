---
title: CD2DRectU 類別
ms.date: 11/04/2016
f1_keywords:
- CD2DRectU
- AFXRENDERTARGET/CD2DRectU
- AFXRENDERTARGET/CD2DRectU::CD2DRectU
- AFXRENDERTARGET/CD2DRectU::IsNull
helpviewer_keywords:
- CD2DRectU [MFC], CD2DRectU
- CD2DRectU [MFC], IsNull
ms.assetid: a62f17d1-011d-4867-8f51-fd7e7c00561d
ms.openlocfilehash: feb8af3992b9f56164ded0e3b6a4529a46fe2a1d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396284"
---
# <a name="cd2drectu-class"></a>CD2DRectU 類別

`D2D1_RECT_U`的包裝函式。

## <a name="syntax"></a>語法

```
class CD2DRectU : public D2D1_RECT_U;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2DRectU::CD2DRectU](#cd2drectu)|多載。 建構`CD2DRectU`物件從`D2D1_RECT_U`物件。|

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[CD2DRectU::IsNull](#isnull)|傳回**布林**值，指出運算式是否包含任何有效的資料 (NULL)。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CD2DRectU::operator CRect](#operator_crect)|將轉換`CD2DRectU`至`CRect`物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`D2D1_RECT_U`

`CD2DRectU`

## <a name="requirements"></a>需求

**標頭：** afxrendertarget.h

##  <a name="cd2drectu"></a>  CD2DRectU::CD2DRectU

建構 CD2DRectU 物件從 CRect 物件。

```
CD2DRectU(const CRect& rect);
CD2DRectU(const D2D1_RECT_U& rect);
  CD2DRectU(const D2D1_RECT_U* rect);

CD2DRectU(
    UINT32 uLeft = 0,
    UINT32 uTop = 0,
    UINT32 uRight = 0,
    UINT32 uBottom = 0);
```

### <a name="parameters"></a>參數

*rect*<br/>
來源矩形

*uLeft*<br/>
來源左方的座標

*uTop*<br/>
來源上方座標

*uRight*<br/>
來源座標

*uBottom*<br/>
來源下方座標

##  <a name="isnull"></a>  CD2DRectU::IsNull

傳回布林值，指出運算式是否包含任何有效的資料 (Null)。

```
BOOL IsNull() const;
```

### <a name="return-value"></a>傳回值

如果矩形的頂端、 左邊、 底部、 與正確的值設為 0，所有相等，則為 TRUE。否則為 FALSE。

##  <a name="operator_crect"></a>  CD2DRectU::operator CRect

CD2DRectU 將 CRect 物件。

```
operator CRect();
```

### <a name="return-value"></a>傳回值

D2D 矩形的目前值。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
