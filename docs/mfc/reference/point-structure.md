---
title: POINT 結構 |Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- POINT
- LPPOINT
dev_langs:
- C++
helpviewer_keywords:
- LPPOINT structure [MFC]
- POINT structure [MFC]
ms.assetid: 965736d8-4e53-41b6-9b8b-6961992dd21f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1d2aaafe65b742ded6c0adf49fac430679e24380
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2018
ms.locfileid: "49334512"
---
# <a name="point-structure"></a>POINT 結構

`POINT`結構會定義 x*-* 和資料點的 y 座標。

## <a name="syntax"></a>語法

```
typedef struct tagPOINT {
    LONG x;
    LONG y;
} POINT;
```

#### <a name="parameters"></a>參數

*x*<br/>
指定點的 x 座標。

*y*<br/>
指定點的 y 座標。

## <a name="example"></a>範例

[!code-cpp[NVC_MFC_Utilities#37](../../mfc/codesnippet/cpp/point-structure1_1.cpp)]

## <a name="requirements"></a>需求

**標頭：** windef.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CPoint 類別](../../atl-mfc-shared/reference/cpoint-class.md)
