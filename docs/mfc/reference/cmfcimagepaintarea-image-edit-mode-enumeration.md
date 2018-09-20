---
title: 'Cmfcimagepaintarea:: Image_edit_mode 列舉 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- IMAGE_EDIT_MODE Enumeration
dev_langs:
- C++
helpviewer_keywords:
- IMAGE_EDIT_MODE Enumeration method [MFC]
ms.assetid: e51db66a-fa1c-4766-9dac-a25b595f871a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 913a87383e617f331043751c4e3089acac744c7f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46374640"
---
# <a name="cmfcimagepaintareaimageeditmode-enumeration"></a>CMFCImagePaintArea::IMAGE_EDIT_MODE 列舉

指定您用來修改影像編輯器 對話方塊中的影像繪圖模式。

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

|||
|-|-|
|名稱|描述|
|IMAGE_EDIT_MODE_PEN|用來繪製個別像素為單位。|
|IMAGE_EDIT_MODE_FILL|用來填滿所有相鄰區域包含在目前游標位置的色彩。|
|IMAGE_EDIT_MODE_LINE|用來繪製一條線。|
|IMAGE_EDIT_MODE_RECT|用來繪製矩形。|
|IMAGE_EDIT_MODE_ELLIPSE|用來繪製橢圓形。|
|IMAGE_EDIT_MODE_COLOR|用來設定目前色彩的色彩，在目前游標位置。|

### <a name="remarks"></a>備註

`CMFCImagePaintArea`和`CMFCImageEditorDialog`類別會使用這個列舉型別來設定目前的繪製模式。 繪製模式和目前色彩會用來修改影像編輯器 對話方塊中的 圖片 區域中。 如需詳細資訊`CMFCImagePaintArea`並`CMFCImageEditorDialog`，請參閱[CMFCImagePaintArea 類別](../../mfc/reference/cmfcimagepaintarea-class.md)並[CMFCImageEditorDialog 類別](../../mfc/reference/cmfcimageeditordialog-class.md)。

當您選取色彩，您可以從映像使用 IMAGE_EDIT_MODE_COLOR 繪圖模式時，架構會將目前的繪製模式設定為 IMAGE_EDIT_MODE_PEN。

## <a name="requirements"></a>需求

**標頭：** afximagepaintarea.h

## <a name="see-also"></a>另請參閱

[巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[階層架構圖表](../../mfc/hierarchy-chart.md)<br/>
[類別](../../mfc/reference/mfc-classes.md)<br/>
[CMFCImagePaintArea 類別](../../mfc/reference/cmfcimagepaintarea-class.md)<br/>
[CMFCImageEditorDialog 類別](../../mfc/reference/cmfcimageeditordialog-class.md)
