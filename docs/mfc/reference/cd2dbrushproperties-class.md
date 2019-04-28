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
ms.openlocfilehash: 5ca791af658ee719b2e6d6ea78f82e23a66edc98
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62253721"
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
|[CD2DBrushProperties::CD2DBrushProperties](#cd2dbrushproperties)|多載。 建立`CD2D_BRUSH_PROPERTIES`結構|

### <a name="protected-methods"></a>保護方法

|名稱|描述|
|----------|-----------------|
|[CD2DBrushProperties::CommonInit](#commoninit)|初始化物件|

## <a name="inheritance-hierarchy"></a>繼承階層

`D2D1_BRUSH_PROPERTIES`

`CD2DBrushProperties`

## <a name="requirements"></a>需求

**標頭：** afxrendertarget.h

##  <a name="cd2dbrushproperties"></a>  CD2DBrushProperties::CD2DBrushProperties

建立 CD2D_BRUSH_PROPERTIES 結構

```
CD2DBrushProperties();
CD2DBrushProperties(FLOAT _opacity);

CD2DBrushProperties(
    D2D1_MATRIX_3X2_F _transform,
    FLOAT _opacity = 1.);
```

### <a name="parameters"></a>參數

*_opacity*<br/>
筆刷的基底的不透明度。 預設值為 1.0。

*_transform*<br/>
要套用到筆刷的轉換

##  <a name="commoninit"></a>  CD2DBrushProperties::CommonInit

初始化物件

```
void CommonInit();
```

## <a name="see-also"></a>另請參閱

[類別](../../mfc/reference/mfc-classes.md)
