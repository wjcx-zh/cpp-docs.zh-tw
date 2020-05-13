---
title: 像素-HIMETRIC 轉換全域函數
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::AtlHiMetricToPixel
- atlwin/ATL::AtlPixelToHiMetric
ms.assetid: ecb1b1b2-7e9d-4fbc-a855-16252d2d794c
ms.openlocfilehash: 08c72c0d8f3d061950d6945d9fb412c0a16355da
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326149"
---
# <a name="pixelhimetric-conversion-global-functions"></a>像素/HIMETRIC 轉換全域函數

這些函數支援將圖元和 HIMETRIC 單位轉換為和轉換。

> [!IMPORTANT]
> 下表中列出的函數不能在 Windows 執行時中執行的應用程式中使用。

|||
|-|-|
|[AtlHiMetricToPixel](#atlhimetrictopixel)|將 HIMETRIC 單位(每個單位為 0.01 毫米)轉換為圖元。|
|[AtlPixelToHiMetric](#atlpixeltohimetric)|將像素轉換為 HIMETRIC 單位(每個單位為 0.01 毫米)。|

## <a name="atlhimetrictopixel"></a><a name="atlhimetrictopixel"></a>atlhimetricto圖元

將以 HIMETRIC 為單位 (每一單位為 0.01 公釐) 的物件大小轉換成以像素為單位的螢幕裝置大小。

```
extern void AtlHiMetricToPixel(
    const SIZEL* lpSizeInHiMetric,
    LPSIZEL lpSizeInPix);
```

### <a name="parameters"></a>參數

*lpsizeinhimetric*<br/>
[在]指標指向以 HIMETRIC 單位為單位的物件大小。

*lpsizeInPix*<br/>
[出]指向要返回物件大小(以像素為單位)的指標。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#49](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_1.cpp)]

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="atlpixeltohimetric"></a><a name="atlpixeltohimetric"></a>AtlPixeltohimetric

將物件在螢幕裝置上以像素為單位的大小，轉換成以 HIMETRIC 為單位 (每一單位為 0.01 公釐) 的大小。

```
extern void AtlPixelToHiMetric(
    const SIZEL* lpSizeInPix,
    LPSIZEL lpSizeInHiMetric);
```

### <a name="parameters"></a>參數

*lpsizeInPix*<br/>
[在]指向物件大小(以像素為單位)的指標。

*lpsizeinhimetric*<br/>
[出]指向要返回物件大小(以 HIMETRIC 單位為單位)的指標。

### <a name="example"></a>範例

[!code-cpp[NVC_ATL_COM#51](../../atl/codesnippet/cpp/pixel-himetric-conversion-global-functions_2.cpp)]

### <a name="requirements"></a>需求

**標題:** atlwin.h

## <a name="see-also"></a>另請參閱

[函式](../../atl/reference/atl-functions.md)
