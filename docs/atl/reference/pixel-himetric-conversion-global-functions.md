---
title: 像素-HIMETRIC 轉換全域函式
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlHiMetricToPixel
- atlwin/ATL::AtlPixelToHiMetric
ms.assetid: ecb1b1b2-7e9d-4fbc-a855-16252d2d794c
ms.openlocfilehash: 43a12985f259603a9b67f22f7a7891bf847c0b0f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272330"
---
# <a name="pixelhimetric-conversion-global-functions"></a>像素/HIMETRIC 轉換全域函式

這些函式提供支援像素和 HIMETRIC 單位來回轉換。

> [!IMPORTANT]
>  下表所列出的函數不能在 Windows 執行階段中執行的應用程式。

|||
|-|-|
|[AtlHiMetricToPixel](#atlhimetrictopixel)|將像素 himetric 為單位 （每個單位為 0.01 公釐）。|
|[AtlPixelToHiMetric](#atlpixeltohimetric)|將像素轉換成 himetric 為單位 （每個單位為 0.01 公釐）。|

##  <a name="atlhimetrictopixel"></a>  AtlHiMetricToPixel

將以 HIMETRIC 為單位 (每一單位為 0.01 公釐) 的物件大小轉換成以像素為單位的螢幕裝置大小。

```
extern void AtlHiMetricToPixel(
    const SIZEL* lpSizeInHiMetric,
    LPSIZEL lpSizeInPix);
```

### <a name="parameters"></a>參數

*lpSizeInHiMetric*<br/>
[in]物件，以 himetric 為單位的大小指標。

*lpSizeInPix*<br/>
[out]物件的大小，單位為像素所要傳回的指標。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#49](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_1.cpp)]

### <a name="requirements"></a>需求

**標頭：** atlwin.h

##  <a name="atlpixeltohimetric"></a>  AtlPixelToHiMetric

將物件在螢幕裝置上以像素為單位的大小，轉換成以 HIMETRIC 為單位 (每一單位為 0.01 公釐) 的大小。

```
extern void AtlPixelToHiMetric(
    const SIZEL* lpSizeInPix,
    LPSIZEL lpSizeInHiMetric);
```

### <a name="parameters"></a>參數

*lpSizeInPix*<br/>
[in]物件的像素為單位的大小指標。

*lpSizeInHiMetric*<br/>
[out]物件的大小，以 himetric 為單位所要傳回的指標。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#51](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_2.cpp)]

### <a name="requirements"></a>需求

**標頭：** atlwin.h

## <a name="see-also"></a>另請參閱

[函式](../../atl/reference/atl-functions.md)
