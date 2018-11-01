---
title: XFORM 結構
ms.date: 11/04/2016
f1_keywords:
- XFORM
helpviewer_keywords:
- XFORM structure [MFC]
ms.assetid: 4fb4ef5b-05d2-4884-82d1-1cb8f7be6302
ms.openlocfilehash: 621a01accf3c323f8098da68667f06f48b9d169b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50457248"
---
# <a name="xform-structure"></a>XFORM 結構

`XFORM`結構具有下列格式：

## <a name="syntax"></a>語法

```
typedef struct  tagXFORM {  /* xfrm */
    FLOAT eM11;
    FLOAT eM12;
    FLOAT eM21;
    FLOAT eM22;
    FLOAT eDx;
    FLOAT eDy;
} XFORM;
```

## <a name="remarks"></a>備註

`XFORM`結構指定的分頁空間轉換至世界空間。 `eDx`和`eDy`成員分別指定水平及垂直轉譯元件。 下表顯示其他成員使用方式，視作業而定：

|運算|eM11|eM12|eM21|eM22|
|---------------|----------|----------|----------|----------|
|`Rotation`|旋轉角度的餘弦值|旋轉角度的正弦值|負數的旋轉角度的正弦值|旋轉角度的餘弦值|
|`Scaling`|水平縮放的元件|Nothing|Nothing|垂直縮放的元件|
|`Shear`|Nothing|水平的比例常數|垂直的比例常數|Nothing|
|`Reflection`|水平的反映元件|Nothing|Nothing|垂直反映元件|

## <a name="requirements"></a>需求

**標頭：** wingdi.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CRgn::CreateFromData](../../mfc/reference/crgn-class.md#createfromdata)

