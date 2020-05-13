---
title: CD2DPointF 類別
ms.date: 11/04/2016
f1_keywords:
- CD2DPointF
- AFXRENDERTARGET/CD2DPointF
- AFXRENDERTARGET/CD2DPointF::CD2DPointF
helpviewer_keywords:
- CD2DPointF [MFC], CD2DPointF
ms.assetid: 30f72083-1c8a-4f50-adb2-72dbbe3522d4
ms.openlocfilehash: 5d66c31289f9e17df99df4681cff1d5cf6a0ec86
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369164"
---
# <a name="cd2dpointf-class"></a>CD2DPointF 類別

`D2D1_POINT_2F`的包裝函式。

## <a name="syntax"></a>語法

```
class CD2DPointF : public D2D1_POINT_2F;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2DPointF:CD2DPointF](#cd2dpointf)|已多載。 從`CD2DPointF``D2D1_POINT_2F`物件構造物件。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CD2DPointF::運算符 CPoint](#operator_cpoint)|轉換為`CD2DPointF``CPoint`物件。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`D2D1_POINT_2F`

`CD2DPointF`

## <a name="requirements"></a>需求

**標題:** afxrendertarget.h

## <a name="cd2dpointfcd2dpointf"></a><a name="cd2dpointf"></a>CD2DPointF:CD2DPointF

從 CPoint 物件構造 CD2DPointF 物件。

```
CD2DPointF(const CPoint& pt);
CD2DPointF(const D2D1_POINT_2F& pt);
CD2DPointF(const D2D1_POINT_2F* pt);
CD2DPointF(FLOAT fX = 0., FLOAT fY = 0.);
```

### <a name="parameters"></a>參數

*pt*<br/>
源點

*外匯*<br/>
來源 X

*fY*<br/>
源 Y

## <a name="cd2dpointfoperator-cpoint"></a><a name="operator_cpoint"></a>CD2DPointF::運算符 CPoint

將 CD2DPointF 轉換為 CPoint 物件。

```
operator CPoint();
```

### <a name="return-value"></a>傳回值

D2D 點的當前值。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
