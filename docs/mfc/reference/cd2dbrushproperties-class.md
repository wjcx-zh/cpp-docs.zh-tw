---
title: CD2DBrushProperties 類別
ms.date: 11/04/2016
f1_keywords:
- CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties::CD2DBrushProperties
- AFXRENDERTARGET/CD2DBrushProperties::CommonInit
helpviewer_keywords:
- CD2DBrushProperties [MFC], CD2DBrushProperties
- CD2DBrushProperties [MFC], CommonInit
ms.assetid: c77d717f-0a16-4d74-b2ce-0ae1766ed6f9
ms.openlocfilehash: bf6399d2a245addb7e2e65100d33643fcd54e893
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369294"
---
# <a name="cd2dbrushproperties-class"></a>CD2DBrushProperties 類別

`D2D1_BRUSH_PROPERTIES`的包裝函式。

## <a name="syntax"></a>語法

```
class CD2DBrushProperties : public D2D1_BRUSH_PROPERTIES;
```

## <a name="members"></a>成員

### <a name="public-constructors"></a>公用建構函式

|名稱|描述|
|----------|-----------------|
|[CD2DBrush 屬性:CD2DBrush 屬性](#cd2dbrushproperties)|已多載。 建立`CD2D_BRUSH_PROPERTIES`結構|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CD2DBrush 屬性::通用](#commoninit)|初始化物件|

## <a name="inheritance-hierarchy"></a>繼承階層架構

`D2D1_BRUSH_PROPERTIES`

`CD2DBrushProperties`

## <a name="requirements"></a>需求

**標題:** afxrendertarget.h

## <a name="cd2dbrushpropertiescd2dbrushproperties"></a><a name="cd2dbrushproperties"></a>CD2DBrush 屬性:CD2DBrush 屬性

建立CD2D_BRUSH_PROPERTIES結構

```
CD2DBrushProperties();
CD2DBrushProperties(FLOAT _opacity);

CD2DBrushProperties(
    D2D1_MATRIX_3X2_F _transform,
    FLOAT _opacity = 1.);
```

### <a name="parameters"></a>參數

*_opacity*<br/>
畫筆的基本不一性。 預設值為 1.0。

*_transform*<br/>
套用成筆刷的轉換

## <a name="cd2dbrushpropertiescommoninit"></a><a name="commoninit"></a>CD2DBrush 屬性::通用

初始化物件

```
void CommonInit();
```

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
