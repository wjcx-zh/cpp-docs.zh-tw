---
title: CMFCImagePaintArea::IMAGE_EDIT_MODE 列舉
ms.date: 11/04/2016
f1_keywords:
- IMAGE_EDIT_MODE Enumeration
helpviewer_keywords:
- IMAGE_EDIT_MODE Enumeration method [MFC]
ms.assetid: e51db66a-fa1c-4766-9dac-a25b595f871a
ms.openlocfilehash: 37c877cc8562a9479535d9c6132e49e7c9b7e82f
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88831134"
---
# <a name="cmfcimagepaintareaimage_edit_mode-enumeration"></a>CMFCImagePaintArea::IMAGE_EDIT_MODE 列舉

指定您在 [影像編輯器] 對話方塊中用來修改影像的繪圖模式。

## <a name="syntax"></a>語法

```
enum IMAGE_EDIT_MODE
{
    IMAGE_EDIT_MODE_PEN = 0,
    IMAGE_EDIT_MODE_FILL,
    IMAGE_EDIT_MODE_LINE,
    IMAGE_EDIT_MODE_RECT,
    IMAGE_EDIT_MODE_ELLIPSE,
    IMAGE_EDIT_MODE_COLOR
};
```

## <a name="members"></a>成員

|名稱|描述|
|-|-|
|IMAGE_EDIT_MODE_PEN|用來繪製個別圖元。|
|IMAGE_EDIT_MODE_FILL|用來填滿在目前游標位置包含色彩的所有相鄰區域。|
|IMAGE_EDIT_MODE_LINE|用來繪製線條。|
|IMAGE_EDIT_MODE_RECT|用來繪製矩形。|
|IMAGE_EDIT_MODE_ELLIPSE|用來繪製橢圓形。|
|IMAGE_EDIT_MODE_COLOR|用來將目前的色彩設定為目前游標位置的色彩。|

### <a name="remarks"></a>備註

`CMFCImagePaintArea`和 `CMFCImageEditorDialog` 類別會使用這個列舉來設定目前的繪圖模式。 在 [影像編輯器] 對話方塊中，會使用繪圖模式和目前的色彩來修改圖片區域。 如需和的詳細資訊 `CMFCImagePaintArea` `CMFCImageEditorDialog` ，請參閱 [CMFCImagePaintArea 類別](../../mfc/reference/cmfcimagepaintarea-class.md) 和 [CMFCImageEditorDialog 類別](../../mfc/reference/cmfcimageeditordialog-class.md)。

當您使用 IMAGE_EDIT_MODE_COLOR 繪圖模式從影像中選取色彩時，架構會將目前的繪圖模式設定為 IMAGE_EDIT_MODE_PEN。

## <a name="requirements"></a>規格需求

**標頭：** afximagepaintarea。h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCImagePaintArea 類別](../../mfc/reference/cmfcimagepaintarea-class.md)<br/>
[CMFCImageEditorDialog 類別](../../mfc/reference/cmfcimageeditordialog-class.md)
