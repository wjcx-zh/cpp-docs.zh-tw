---
title: ABCFLOAT 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- ABCFLOAT
dev_langs:
- C++
helpviewer_keywords:
- ABCFLOAT structure [MFC]
ms.assetid: 338e7e15-9d2c-42d0-aa80-273acfde5cc5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a9bbece0773c14a4a8b545bc56209bf682e22c0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375407"
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

