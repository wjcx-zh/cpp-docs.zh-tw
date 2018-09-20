---
title: 點陣圖結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- BITMAP
dev_langs:
- C++
helpviewer_keywords:
- BITMAP structure [MFC]
ms.assetid: 05d33b4d-7232-4643-a108-87dda8ff5f22
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3169d3b8baad29cb79ee1ff8a25685c06414ac98
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46427715"
---
# <a name="bitmap-structure"></a>BITMAP 結構

**點陣圖**結構會定義高度、 寬度、 色彩格式和位元邏輯點陣圖值 **。**

## <a name="syntax"></a>語法

```
typedef struct tagBITMAP {  /* bm */
    int bmType;
    int bmWidth;
    int bmHeight;
    int bmWidthBytes;
    BYTE bmPlanes;
    BYTE bmBitsPixel;
    LPVOID bmBits;
} BITMAP;
```

#### <a name="parameters"></a>參數

*bmType*<br/>
指定點陣圖類型。 在邏輯點陣圖中，此成員必須是 0。

*bmWidth*<br/>
以像素為單位指定點陣圖的寬度。 寬度必須大於 0。

*bmHeight*<br/>
以光柵行為單位指定點陣圖的高度。 高度必須大於 0。

*bmWidthBytes*<br/>
指定每個光柵行的位元組數。 這個值必須是偶數，因為繪圖裝置介面 (GDI) 會假設點陣圖格式的位元值為整數 (2 位元組) 值陣列。 亦即*bmWidthBytes* \* 8 必須是大於或等於時所取得的值 16 的下一個倍數*bmWidth*成員乘以*bmBitsPixel*成員。

*bmPlanes*<br/>
指定點陣圖中色彩平面的數目。

*bmBitsPixel*<br/>
在定義像素所需的每個平面上指定相鄰色彩位元數量。

*Bitmap*<br/>
指向點陣圖中位元值的位置。 *Bitmap*成員必須是 1 個位元組值陣列的長指標。

## <a name="remarks"></a>備註

目前所使用的點陣圖格式為單色和彩色。 單色點陣圖使用 1 位元 1 平面格式。 每個掃描的位元組皆為 16 的倍數。

掃描組織，如下所示的單色點陣圖的高度*n*:

```
Scan 0
Scan 1
.
.
.
Scan n-2
Scan n-1
```

在單色裝置上的像素不是黑色就是白色。 如果在點陣圖中對應的位元為 1，則像素已開啟 (白色)。 如果在點陣圖中對應的位元為 0，則像素會關閉 (黑色)。

所有裝置都支援具有 RC_BITBLT 位元組中 GETDEVICECAPS 索引的點陣圖[rastercaps](../../mfc/reference/cdc-class.md#getdevicecaps)成員函式。

每個裝置有其獨特的色彩格式。 若要從一部裝置的點陣圖傳輸到另一個中，使用[GetDIBits](/windows/desktop/api/wingdi/nf-wingdi-getdibits)並[SetDIBits](/windows/desktop/api/wingdi/nf-wingdi-setdibits) Windows 函式。

## <a name="requirements"></a>需求

**標頭：** wingdi.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[Createbitmapindirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect)
