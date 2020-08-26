---
title: 圖元 HIMETRIC 轉換全域函式
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlHiMetricToPixel
- atlwin/ATL::AtlPixelToHiMetric
ms.assetid: ecb1b1b2-7e9d-4fbc-a855-16252d2d794c
ms.openlocfilehash: e71dccbccbe43ea7df3b6a7005da138a8e31aeb3
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88834683"
---
# <a name="pixelhimetric-conversion-global-functions"></a>圖元/HIMETRIC 轉換全域函式

這些函式支援對圖元和 HIMETRIC 單位進行轉換。

> [!IMPORTANT]
> 下表所列的函數不能用於在 Windows 執行階段中執行的應用程式。

|名稱|描述|
|-|-|
|[AtlHiMetricToPixel](#atlhimetrictopixel)|將 HIMETRIC 單位 (每個單位為0.01 毫米) 轉換為圖元。|
|[AtlPixelToHiMetric](#atlpixeltohimetric)|將圖元轉換成 HIMETRIC 單位 (每個單位為0.01 毫米) 。|

## <a name="atlhimetrictopixel"></a><a name="atlhimetrictopixel"></a> AtlHiMetricToPixel

將以 HIMETRIC 為單位 (每一單位為 0.01 公釐) 的物件大小轉換成以像素為單位的螢幕裝置大小。

```
extern void AtlHiMetricToPixel(
    const SIZEL* lpSizeInHiMetric,
    LPSIZEL lpSizeInPix);
```

### <a name="parameters"></a>參數

*lpSizeInHiMetric*<br/>
在HIMETRIC 單位中物件大小的指標。

*lpSizeInPix*<br/>
擴展要傳回物件大小（以圖元為單位）的指標。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#49](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_1.cpp)]

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="atlpixeltohimetric"></a><a name="atlpixeltohimetric"></a> AtlPixelToHiMetric

將物件在螢幕裝置上以像素為單位的大小，轉換成以 HIMETRIC 為單位 (每一單位為 0.01 公釐) 的大小。

```
extern void AtlPixelToHiMetric(
    const SIZEL* lpSizeInPix,
    LPSIZEL lpSizeInHiMetric);
```

### <a name="parameters"></a>參數

*lpSizeInPix*<br/>
在物件大小的指標（以圖元為單位）。

*lpSizeInHiMetric*<br/>
擴展要傳回 HIMETRIC 單位中物件大小的位置指標。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#51](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_2.cpp)]

### <a name="requirements"></a>規格需求

**標頭：** atlwin。h

## <a name="see-also"></a>請參閱

[函式](../../atl/reference/atl-functions.md)
