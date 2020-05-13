---
title: CD2DRoundedRect 類別
ms.date: 11/04/2016
f1_keywords:
- CD2DRoundedRect
- AFXRENDERTARGET/CD2DRoundedRect
- AFXRENDERTARGET/CD2DRoundedRect::CD2DRoundedRect
helpviewer_keywords:
- CD2DRoundedRect [MFC], CD2DRoundedRect
ms.assetid: 06207fb5-e92b-41c0-bceb-b45d8f466531
ms.openlocfilehash: 5189f3d824c008845570eac6eead4a35be1e483d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369079"
---
# <a name="cd2droundedrect-class"></a>CD2DRoundedRect 類別

`D2D1_ROUNDED_RECT`的包裝函式。

## <a name="syntax"></a>語法

```
class CD2DRoundedRect : public D2D1_ROUNDED_RECT;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2D 四捨五入:CD2D 四捨五入](#cd2droundedrect)|已多載。 從`CD2DRoundedRect``D2D1_ROUNDED_RECT`物件構造物件。|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`D2D1_ROUNDED_RECT`

[CD2D 四捨五入](../../mfc/reference/cd2droundedrect-class.md)

## <a name="requirements"></a>需求

**標題:** afxrendertarget.h

## <a name="cd2droundedrectcd2droundedrect"></a><a name="cd2droundedrect"></a>CD2D 四捨五入:CD2D 四捨五入

從 CD2DRectF 物件建構 CD2D 四捨五入重新物件。

```
CD2DRoundedRect(
    const CD2DRectF& rectIn,
    const CD2DSizeF& sizeRadius);

CD2DRoundedRect(const D2D1_ROUNDED_RECT& rectIn);
CD2DRoundedRect(const D2D1_ROUNDED_RECT* rectIn);
```

### <a name="parameters"></a>參數

*雷金*<br/>
來源矩形

*大小半徑*<br/>
半徑大小

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
