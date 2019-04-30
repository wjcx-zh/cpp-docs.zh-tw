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
ms.openlocfilehash: b8fe808c3147fa52c5041e2988822ace0ba60896
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396336"
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
|[CD2DPointF::CD2DPointF](#cd2dpointf)|多載。 建構`CD2DPointF`物件從`D2D1_POINT_2F`物件。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CD2DPointF::operator CPoint](#operator_cpoint)|將轉換`CD2DPointF`至`CPoint`物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`D2D1_POINT_2F`

`CD2DPointF`

## <a name="requirements"></a>需求

**標頭：** afxrendertarget.h

##  <a name="cd2dpointf"></a>  CD2DPointF::CD2DPointF

建構 CD2DPointF 物件從 CPoint 物件。

```
CD2DPointF(const CPoint& pt);
CD2DPointF(const D2D1_POINT_2F& pt);
CD2DPointF(const D2D1_POINT_2F* pt);
CD2DPointF(FLOAT fX = 0., FLOAT fY = 0.);
```

### <a name="parameters"></a>參數

*pt*<br/>
來源點

*fX*<br/>
來源 X

*fY*<br/>
source Y

##  <a name="operator_cpoint"></a>  CD2DPointF::operator CPoint

將 CD2DPointF 轉換 CPoint 物件。

```
operator CPoint();
```

### <a name="return-value"></a>傳回值

目前的 D2D 點值。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
