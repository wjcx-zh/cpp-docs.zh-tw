---
title: ABC 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- ABC
dev_langs:
- C++
helpviewer_keywords:
- ABC structure [MFC]
ms.assetid: 32663839-c3b7-4f47-896c-b15329c96bc8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6a977e3f0efd763ee416348f11e3c6b016c0d42e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373708"
---
# <a name="abc-structure"></a>ABC 結構

`ABC`結構包含 TrueType 字型字元的寬度。

## <a name="syntax"></a>語法

```
typedef struct _ABC { /* abc */
    int abcA;
    UINT abcB;
    int abcC;
} ABC;
```

#### <a name="parameters"></a>參數

*abcA*<br/>
指定字元的 A 間距。 A 間距是在繪製字元圖像之前要加入至目前位置的距離。

*abcB*<br/>
指定字元的 B 間距。 B 間距是繪製字元圖像部分的寬度。

*abcC*<br/>
指定字元的 C 間距。 C 間距是要加入至目前位置，以便在字元圖像右邊加上空白字元的距離。

## <a name="remarks"></a>備註

字元的總寬度為 A、B 和 C 間距的總和。 A 或 C 間距可以是負數值，用於標示留白部分或突出部分。

## <a name="requirements"></a>需求

**標頭：** wingdi.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDC::GetCharABCWidths](../../mfc/reference/cdc-class.md#getcharabcwidths)


