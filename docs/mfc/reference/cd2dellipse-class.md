---
title: CD2DEllipse 類別
ms.date: 11/04/2016
f1_keywords:
- CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse::CD2DEllipse
helpviewer_keywords:
- CD2DEllipse [MFC], CD2DEllipse
ms.assetid: e9f02f54-acf2-427e-b349-db50cd9a77df
ms.openlocfilehash: aa280215aaac55e3aaa9542ca1ab2bd9d21655e8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50642033"
---
# <a name="cd2dellipse-class"></a>CD2DEllipse 類別

`D2D1_ELLIPSE`的包裝函式。

## <a name="syntax"></a>語法

```
class CD2DEllipse : public D2D1_ELLIPSE;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2DEllipse::CD2DEllipse](#cd2dellipse)|多載。 建構`CD2DEllipse`物件從`D2D1_ELLIPSE`物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`D2D1_ELLIPSE`

`CD2DEllipse`

## <a name="requirements"></a>需求

**標頭：** afxrendertarget.h

##  <a name="cd2dellipse"></a>  CD2DEllipse::CD2DEllipse

建構 CD2DEllipse 物件從 CD2DRectF 物件。

```
CD2DEllipse(const CD2DRectF& rect);
CD2DEllipse(const D2D1_ELLIPSE& ellipse);
  CD2DEllipse(const D2D1_ELLIPSE* ellipse);

CD2DEllipse(
    const CD2DPointF& ptCenter,
    const CD2DSizeF& sizeRadius);
```

### <a name="parameters"></a>參數

*rect*<br/>
來源矩形

*橢圓形*<br/>
來源橢圓形

*ptCenter*<br/>
橢圓形的中心點。

*sizeRadius*<br/>
X 半徑和橢圓形 Y 半徑。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
