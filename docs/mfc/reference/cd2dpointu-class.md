---
title: CD2DPointU 類別
ms.date: 11/04/2016
f1_keywords:
- CD2DPointU
- AFXRENDERTARGET/CD2DPointU
- AFXRENDERTARGET/CD2DPointU::CD2DPointU
helpviewer_keywords:
- CD2DPointU [MFC], CD2DPointU
ms.assetid: 04733f96-b6de-4a89-82e3-caad1e8087a9
ms.openlocfilehash: 138916efe781d8bef69a1c4eb61a73c5a405be67
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50551849"
---
# <a name="cd2dpointu-class"></a>CD2DPointU 類別

`D2D1_POINT_2U`的包裝函式。

## <a name="syntax"></a>語法

```
class CD2DPointU : public D2D1_POINT_2U;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2DPointU::CD2DPointU](#cd2dpointu)|多載。 建構`CD2DPointU`從物件`D2D1_POINT_2U`物件。|

### <a name="public-operators"></a>公用運算子

|名稱|描述|
|----------|-----------------|
|[CD2DPointU::operator CPoint](#operator_cpoint)|將轉換`CD2DPointU`至`CPoint`物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`D2D1_POINT_2U`

`CD2DPointU`

## <a name="requirements"></a>需求

**標頭：** afxrendertarget.h

##  <a name="cd2dpointu"></a>  CD2DPointU::CD2DPointU

建構 CD2DPointU 物件從 CPoint 物件。

```
CD2DPointU(const CPoint& pt);
CD2DPointU(const D2D1_POINT_2U& pt);
  CD2DPointU(const D2D1_POINT_2U* pt);
CD2DPointU(UINT32 uX = 0, UINT32 uY = 0);
```

### <a name="parameters"></a>參數

*太平洋時間*<br/>
來源點

*uX*<br/>
來源 X

*uY*<br/>
來源 Y

##  <a name="operator_cpoint"></a>  CD2DPointU::operator CPoint

將 CD2DPointU 轉換 CPoint 物件。

```
operator CPoint();
```

### <a name="return-value"></a>傳回值

目前的 D2D 點值。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
