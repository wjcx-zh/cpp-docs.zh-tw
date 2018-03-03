---
title: "Cmfcimagepaintarea:: Image_edit_mode 列舉 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IMAGE_EDIT_MODE Enumeration
dev_langs:
- C++
helpviewer_keywords:
- IMAGE_EDIT_MODE Enumeration method [MFC]
ms.assetid: e51db66a-fa1c-4766-9dac-a25b595f871a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 22e3b00bed830052c2abbc988152f4a14f1267ff
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
|`IMAGE_EDIT_MODE_PEN`|用來繪製個別像素為單位。|  
|`IMAGE_EDIT_MODE_FILL`|用來填滿所有相鄰區域包含在目前游標位置的色彩。|  
|`IMAGE_EDIT_MODE_LINE`|用來繪製一條線。|  
|`IMAGE_EDIT_MODE_RECT`|用來繪製矩形。|  
|`IMAGE_EDIT_MODE_ELLIPSE`|用來繪製橢圓形。|  
|`IMAGE_EDIT_MODE_COLOR`|用來設定目前色彩的色彩，在目前游標位置。|  
  
### <a name="remarks"></a>備註  
 `CMFCImagePaintArea`和`CMFCImageEditorDialog`類別來設定目前的繪圖模式使用這個列舉型別。 目前的色彩與繪圖模式可用來修改影像編輯器 對話方塊中的圖片區域。 如需有關`CMFCImagePaintArea`和`CMFCImageEditorDialog`，請參閱[CMFCImagePaintArea 類別](../../mfc/reference/cmfcimagepaintarea-class.md)和[CMFCImageEditorDialog 類別](../../mfc/reference/cmfcimageeditordialog-class.md)。  
  
 當您選取色彩從映像使用`IMAGE_EDIT_MODE_COLOR`繪圖模式，架構目前繪圖模式設定為`IMAGE_EDIT_MODE_PEN`。  
  
## <a name="requirements"></a>需求  
 **標頭：** afximagepaintarea.h  
  
## <a name="see-also"></a>請參閱  
 [巨集和全域變數](../../mfc/reference/mfc-macros-and-globals.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCImagePaintArea 類別](../../mfc/reference/cmfcimagepaintarea-class.md)   
 [CMFCImageEditorDialog 類別](../../mfc/reference/cmfcimageeditordialog-class.md)
