---
title: ABCFLOAT 結構
ms.date: 11/04/2016
f1_keywords:
- ABCFLOAT
helpviewer_keywords:
- ABCFLOAT structure [MFC]
ms.assetid: 338e7e15-9d2c-42d0-aa80-273acfde5cc5
ms.openlocfilehash: b9e3923e8c70e38fe5efe959db8da43118cc6445
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50443652"
---
# <a name="abcfloat-structure"></a>ABCFLOAT 結構

`ABCFLOAT`結構包含 A、 B 和 C 字型字元的寬度。

## <a name="syntax"></a>語法

```
typedef struct _ABCFLOAT { /* abcf */
    FLOAT abcfA;
    FLOAT abcfB;
    FLOAT abcfC;
} ABCFLOAT;
```

#### <a name="parameters"></a>參數

*abcfA*<br/>
指定字元的 A 間距。 A 間距是在繪製字元圖像之前要加入至目前位置的距離。

*abcfB*<br/>
指定字元的 B 間距。 B 間距是繪製字元圖像部分的寬度。

*abcfC*<br/>
指定字元的 C 間距。 C 間距是要加入至目前位置，以便在字元圖像右邊加上空白字元的距離。

## <a name="remarks"></a>備註

A、 B 和 C 的寬度會沿著字型的基準線測量。 字元遞增 （總寬度） 的字元是 A、 B 和 C 空間的總和。 A 或 C 間距可以是負數值，用於標示留白部分或突出部分。

## <a name="requirements"></a>需求

**標頭：** wingdi.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)

