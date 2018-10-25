---
title: LOGPEN 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- LOGPEN
dev_langs:
- C++
helpviewer_keywords:
- LOGPEN structure [MFC]
ms.assetid: a89e8690-6b61-4af5-990c-7c82da24f3b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e0fa2a4b422a7bd1f36fc46837adec4136b693fb
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50064950"
---
# <a name="logpen-structure"></a>LOGPEN 結構

`LOGPEN`結構會定義樣式、 寬度和色彩的畫筆、 繪製物件，用來繪製線條和框線。 [CPen::CreatePenIndirect](../../mfc/reference/cpen-class.md#createpenindirect)函式會使用`LOGPEN`結構。

## <a name="syntax"></a>語法

```
typedef struct tagLOGPEN {  /* lgpn */
    UINT lopnStyle;
    POINT lopnWidth;
    COLORREF lopnColor;
} LOGPEN;
```

#### <a name="parameters"></a>參數

*lopnStyle*<br/>
指定的畫筆型別。 這個成員可以是下列值之一：

- PS_SOLID 建立穩固的畫筆。

- PS_DASH 建立虛線的畫筆。 （時才有效畫筆寬度為 1。）

- PS_DOT 建立虛線的畫筆。 （時才有效畫筆寬度為 1。）

- PS_DASHDOT 建立畫筆交替的虛線和點。 （時才有效畫筆寬度為 1。）

- PS_DASHDOTDOT 建立的畫筆交替的虛線和 double 的點。 （時才有效畫筆寬度為 1。）

- PS_NULL 會建立為 null 的畫筆。

- PS_INSIDEFRAME 由 GDI 上會建立 繪製封閉形狀的框架內線條的畫筆產生輸出指定的週框的函式 (例如`Ellipse`， `Rectangle`， `RoundRect`， `Pie`，和`Chord`成員函式）。 使用 GDI 使用此樣式時輸出未指定的週框的函式 (例如`LineTo`成員函式)，畫筆的繪圖區域不受限於一個框架。

   如果畫筆 PS_INSIDEFRAME 樣式和色彩的不符合，邏輯的色彩表中的色彩，畫筆會繪製遞色色彩。 PS_SOLID 畫筆樣式無法用於建立以遞色色彩的畫筆。 畫筆寬度小於或等於 1 時，等於 PS_SOLID PS_INSIDEFRAME 樣式。

   當 PS_INSIDEFRAME 樣式會搭配 GDI 物件以外的其他函式所產生`Ellipse`， `Rectangle`，和`RoundRect`，線條可能不完全指定的範圍內。

*lopnWidth*<br/>
指定的畫筆寬度，以邏輯單位表示。 如果`lopnWidth`成員為 0，畫筆為 1 個像素寬點陣不論目前的對應模式的裝置上。

*lopnColor*<br/>
指定的畫筆色彩。

## <a name="remarks"></a>備註

`y`中的值[點](../../mfc/reference/point-structure1.md)結構`lopnWidth`成員不在使用中。

## <a name="requirements"></a>需求

**標頭：** wingdi.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CPen::CreatePenIndirect](../../mfc/reference/cpen-class.md#createpenindirect)

