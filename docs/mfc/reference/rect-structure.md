---
title: RECT 結構
ms.date: 11/04/2016
f1_keywords:
- LPRECT
- RECT
helpviewer_keywords:
- RECT structure [MFC]
- LPRECT structure [MFC]
ms.assetid: 1b3160de-64e9-40d1-89eb-af3e0fd6acf0
ms.openlocfilehash: 1cb997fc0f1ec89eabf5e4d2c2c5ccb15e3bafec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549004"
---
# <a name="rect-structure"></a>RECT 結構

`RECT` 結構定義矩形的左上角和右下角的座標。

## <a name="syntax"></a>語法

```
typedef struct tagRECT {
    LONG left;
    LONG top;
    LONG right;
    LONG bottom;
} RECT;
```

## <a name="members"></a>成員

`left`<br/>
指定矩形左上角的 x 座標。

`top`<br/>
指定矩形左上角的 y 座標。

`right`<br/>
指定矩形右下角的 x 座標。

`bottom`<br/>
指定矩形右下角的 y 座標。

## <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#38](../../mfc/codesnippet/cpp/rect-structure1_1.cpp)]

## <a name="requirements"></a>需求

**標頭：** windef.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CRect 類別](../../atl-mfc-shared/reference/crect-class.md)
