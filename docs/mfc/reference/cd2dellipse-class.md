---
title: CD2DEllipse 類別
ms.date: 08/29/2019
f1_keywords:
- CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse
- AFXRENDERTARGET/CD2DEllipse::CD2DEllipse
helpviewer_keywords:
- CD2DEllipse [MFC], CD2DEllipse
ms.assetid: e9f02f54-acf2-427e-b349-db50cd9a77df
ms.openlocfilehash: 82ad2fbfb8558486134f85d7ec9bcaa6eb4e7507
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369264"
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
|[CD2DEllipse:CD2DEllipse](#cd2dellipse)|已多載。 從`CD2DEllipse``D2D1_ELLIPSE`物件構造物件。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`D2D1_ELLIPSE`

`CD2DEllipse`

## <a name="requirements"></a>需求

**標題:** afxrendertarget.h

## <a name="cd2dellipsecd2dellipse"></a><a name="cd2dellipse"></a>CD2DEllipse:CD2DEllipse

從 CD2DRectF 物件建構 CD2DEllipse 物件。

```
CD2DEllipse(const CD2DRectF& rect);
CD2DEllipse(const D2D1_ELLIPSE& ellipse);
CD2DEllipse(const D2D1_ELLIPSE* ellipse);

CD2DEllipse(
    const CD2DPointF& ptCenter,
    const CD2DSizeF& sizeRadius);
```

### <a name="parameters"></a>參數

*矩形*<br/>
來源矩形

*ellipse*<br/>
源橢圓

*ptCenter*<br/>
橢圓的中心點。

*大小半徑*<br/>
橢圓的 X 半徑和 Y 半徑。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
