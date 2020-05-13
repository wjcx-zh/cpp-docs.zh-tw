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
ms.openlocfilehash: f73c72830216679f8a91d0037d48c1e1b8e400c3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372858"
---
# <a name="variant-parameter-type-constants"></a>變異參數類型常數

本主題列出了新的常量,指示設計用於 Microsoft 基礎類庫的 OLE 控件類的變體參數類型。

以下是類別的清單:

## <a name="variant-data-constants"></a><a name="_mfc_variant_data_constants"></a>變體資料常量

- VTS_COLOR 用於表示 RGB 顏色值的 32 位整數。

- VTS_FONT指向 OLE`IFontDisp`字體物件介面的指標。

- VTS_HANDLE Windows 句柄值。

- VTS_PICTURE指向 OLE`IPictureDisp`圖片物件的介面的指標。

- VTS_OPTEXCLUSIVE 用於用於一組控制件(如單選按鈕)中的控制項的 16 位元值。 此類型告訴容器,如果組中的一個控件具有 TRUE 值,則所有其他控制項都必須為 FALSE。

- VTS_TRISTATE 16 位元簽名整數,用於具有三種可能值之一的屬性(選中、清除、不可用),例如複選框。

- VTS_XPOS_HIMETRIC 32 位元無符號整數,用於表示在 HIMETRIC 單位中沿 x 軸的位置。

- VTS_YPOS_HIMETRIC 32 位元無符號整數,用於表示沿 y 軸的位置(以 HIMETRIC 為單位)。

- VTS_XPOS_PIXELS 32 位元無符號整數,用於表示 x 軸沿線的位置(以圖元為單位)。

- VTS_YPOS_PIXELS 32 位元無符號整數,用於以圖元表示沿 y 軸的位置。

- VTS_XSIZE_PIXELS 32 位元無符號整數,用於以圖元表示螢幕物件的寬度。

- VTS_YSIZE_PIXELS 32 位元無符號整數,用於以圖元表示螢幕物件的高度。

- VTS_XSIZE_HIMETRIC 用於表示 HIMETRIC 單位螢幕物件的寬度的 32 位無符號整數。

- VTS_YSIZE_HIMETRIC 32 位元無符號整數,用於表示 HIMETRIC 單位中的螢幕物件的高度。

    > [!NOTE]
    >  已為所有變數類型定義了其他變體常量,但提供指向變體數據常量的VTS_FONT和VTS_PICTURE除外。 這些常量使用VTS_P`constantname`約定命名。 例如,VTS_PCOLOR是指向VTS_COLOR常量的指標。

## <a name="requirements"></a>需求

**標頭：** afxdisp.h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)
