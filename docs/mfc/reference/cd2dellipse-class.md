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
ms.openlocfilehash: 21087682d40dac521cc949a39ef4b1aab23e7d71
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177220"
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
|[CD2DEllipse::CD2DEllipse](#cd2dellipse)|多載。 `CD2DEllipse` 從`D2D1_ELLIPSE`物件結構建立物件。|

## <a name="inheritance-hierarchy"></a>繼承階層

`D2D1_ELLIPSE`

`CD2DEllipse`

## <a name="requirements"></a>需求

**標頭:** afxrendertarget。h

##  <a name="cd2dellipse"></a>CD2DEllipse:: CD2DEllipse

從 CD2DRectF 物件中, 建立 CD2DEllipse 物件。

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

*ellipse*<br/>
來源橢圓形

*ptCenter*<br/>
橢圓形的中心點。

*sizeRadius*<br/>
橢圓形的 X 半徑和 Y 半徑。

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
