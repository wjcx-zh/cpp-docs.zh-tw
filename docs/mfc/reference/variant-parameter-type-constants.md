---
title: 變異參數類型常數
ms.date: 11/04/2016
f1_keywords:
- VTS_YPOS_HIMETRIC
- VTS_PICTURE
- VTS_FONT
- VTS_XPOS_HIMETRIC
- VTS_XPOS_PIXELS
- VTS_XSIZE_HIMETRIC
- VTS_YPOS_PIXELS
- VTS_TRISTATE
- VTS_HANDLE
- VTS_YSIZE_HIMETRIC
- VTS_COLOR
- VTS_OPTEXCLUSIVE
- VTS_YSIZE_PIXELS
- VTS_XSIZE_PIXELS
helpviewer_keywords:
- VTS_XPOS_HIMETRIC constant [MFC]
- VTS_FONT constant [MFC]
- VTS_XPOS_PIXELS constant [MFC]
- VTS_COLOR constant [MFC]
- Variants [MFC]
- VTS_YPOS_PIXELS constant [MFC]
- VTS_YSIZE_HIMETRIC constant [MFC]
- VTS_YPOS_HIMETRIC constant [MFC]
- Variants, parameter type constants
- Variant data constants [MFC]
- VTS_PICTURE constant [MFC]
- VTS_TRISTATE constant [MFC]
- VTS_XSIZE_HIMETRIC constant [MFC]
- VTS_HANDLE constant [MFC]
- VTS_XSIZE_PIXELS constant [MFC]
- VTS_OPTEXCLUSIVE constant [MFC]
- VTS_YSIZE_PIXELS constant [MFC]
ms.assetid: de99c7a9-7aae-4dc4-b723-40c6380543ab
ms.openlocfilehash: b15a303f69ce13cf3ba3b6c1c0739acdb8a33c7c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62309471"
---
# <a name="variant-parameter-type-constants"></a>變異參數類型常數

本主題會列出新的常數，表示設計為搭配 Microsoft Foundation 類別庫的 OLE 控制項類別的 variant 參數類型。

以下是類別的常數清單：

##  <a name="_mfc_variant_data_constants"></a> 變異資料常數

- VTS_COLOR 的 32 位元整數，用來表示的 RGB 色彩值。

- VTS_FONT A 指標`IFontDisp`OLE 字型物件介面。

- VTS_HANDLE Windows 控制代碼值。

- VTS_PICTURE A 指標`IPictureDisp`OLE 圖片物件的介面。

- VTS_OPTEXCLUSIVE 的 16 位元值用於要使用的控制項，例如選項按鈕群組中的控制項。 此類型會告訴容器，是否群組中的一個控制項，則為 TRUE 的值，所有其他項目必須是 FALSE。

- VTS_TRISTATE 的 16 位元帶正負號可以是下列三個可能的值 （選取、 清除、 無法使用），例如，核取方塊的內容所使用的整數。

- VTS_XPOS_HIMETRIC 的 32 位元不帶正負號的整數來代表沿著 x 軸的位置以 himetric 為單位。

- VTS_YPOS_HIMETRIC 的 32 位元不帶正負號的整數來代表沿著 y 軸的位置以 himetric 為單位。

- VTS_XPOS_PIXELS 的 32 位元不帶正負號的整數來代表沿著 x 軸單位為像素的位置。

- VTS_YPOS_PIXELS 的 32 位元不帶正負號的整數來表示像素為單位沿著 y 軸位置。

- VTS_XSIZE_PIXELS 的 32 位元不帶正負號的整數來表示像素為單位的畫面物件的寬度。

- VTS_YSIZE_PIXELS 的 32 位元不帶正負號的整數來代表像素為單位的畫面物件的高度。

- VTS_XSIZE_HIMETRIC 的 32 位元不帶正負號的整數來代表以 himetric 為單位的畫面物件的寬度。

- VTS_YSIZE_HIMETRIC 的 32 位元不帶正負號的整數來代表以 himetric 為單位的畫面物件的高度。

    > [!NOTE]
    >  對於所有 variant 類型，除了 VTS_FONT 和 VTS_PICTURE，提供變異資料常數的指標，定義其他變數的常數。 這些常數會命名為使用 VTS_P`constantname`慣例。 比方說，VTS_PCOLOR 是 VTS_COLOR 常數的指標。

## <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
