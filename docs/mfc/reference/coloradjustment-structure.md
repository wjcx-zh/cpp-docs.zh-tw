---
title: COLORADJUSTMENT 結構 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- COLORADJUSTMENT
dev_langs:
- C++
helpviewer_keywords:
- COLORADJUSTMENT structure [MFC]
ms.assetid: 67fc4e63-0e0e-4fcb-8c45-aa5ebfefa013
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 682bbe2e9a4987ca30614e9210198193de977e3e
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066288"
---
# <a name="coloradjustment-structure"></a>COLORADJUSTMENT 結構

`COLORADJUSTMENT`結構會定義 Windows 所使用的色彩調整值`StretchBlt`並`StretchDIBits`函式時`StretchBlt`模式是半色調。

## <a name="syntax"></a>語法

```
typedef struct  tagCOLORADJUSTMENT {    /* ca */
    WORD caSize;
    WORD caFlags;
    WORD caIlluminantIndex;
    WORD caRedGamma;
    WORD caGreenGamma;
    WORD caBlueGamma;
    WORD caReferenceBlack;
    WORD caReferenceWhite;
    SHORT caContrast;
    SHORT caBrightness;
    SHORT caColorfulness;
    SHORT caRedGreenTint;
} COLORADJUSTMENT;
```

#### <a name="parameters"></a>參數

*caSize*<br/>
指定結構的大小，以位元組為單位。

*caFlags*<br/>
指定應如何準備輸出映像。 這個成員可以設定為 NULL 或下列值的任何組合：

- CA_NEGATIVE 指定，會顯示原始的映像的負值。

- CA_LOG_FILTER 指定一個對數函式，應該套用至最終輸出色彩的密度。 明亮度較低時，這會增加的色彩對比。

*caIlluminantIndex*<br/>
指定用以檢視映像物件的光源的亮度。 這個成員可以設定為下列值之一：

- ILLUMINANT_EQUAL_ENERGY

- ILLUMINANT_A

- ILLUMINANT_B

- ILLUMINANT_C

- ILLUMINANT_D50

- ILLUMINANT_D55

- ILLUMINANT_D65

- ILLUMINANT_D75

- ILLUMINANT_F2

- ILLUMINANT_TURNGSTEN

- ILLUMINANT_DAYLIGHT

- ILLUMINANT_FLUORESCENT

- ILLUMINANT_NTSC

*caRedGamma*<br/>
指定來源色彩的紅色主要的第 n 個電源 gamma 修正值。 值必須是介於 2,500 65000 之間。 值為 10,000 表示 gamma 修正。

*caGreenGamma*<br/>
指定來源色彩的綠色主要的第 n 個電源 gamma 修正值。 值必須是介於 2,500 65000 之間。 值為 10,000 表示 gamma 修正。

*caBlueGamma*<br/>
指定來源色彩藍色原色的第 n 個電源 gamma 修正值。 值必須是介於 2,500 65000 之間。 值為 10,000 表示 gamma 修正。

*caReferenceBlack*<br/>
指定來源色彩為黑色的參考。 任何節點要深一點的色彩會被視為黑色。 值必須是介於 0 到 4000。

*caReferenceWhite*<br/>
指定來源色彩為白色的參考。 任何會比這更亮的色彩會被視為空白。 值必須是介於 6,000 為 10,000。

*caContrast*<br/>
指定要套用至來源物件的對比數量。 值必須介於-100 到 100 之間。 值為 0 表示無對比調整。

*caBrightness*<br/>
指定要套用至來源物件的亮度。 值必須介於-100 到 100 之間。 值為 0 表示無亮度調整。

*caColorfulness*<br/>
指定要套用至來源物件的 colorfulness 數量。 值必須介於-100 到 100 之間。 值為 0 表示無 colorfulness 調整。

*caRedGreenTint*<br/>
指定要套用至來源物件的紅色或綠色濃淡調整數量。 值必須介於-100 到 100 之間。 正數會調整針對 red 和負數的數字調整朝向綠色。 0 表示無濃淡調整。

## <a name="requirements"></a>需求

**標頭：** wingdi.h

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CDC::GetColorAdjustment](../../mfc/reference/cdc-class.md#getcoloradjustment)

