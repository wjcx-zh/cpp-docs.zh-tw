---
title: "CMFCImagePaintArea::IMAGE_EDIT_MODE 列舉 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IMAGE_EDIT_MODE Enumeration"
  - "CMFCImagePaintArea::IMAGE_EDIT_MODE Enumeration"
  - "CMFCImagePaintArea.IMAGE_EDIT_MODE Enumeration"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IMAGE_EDIT_MODE 列舉方法"
ms.assetid: e51db66a-fa1c-4766-9dac-a25b595f871a
caps.latest.revision: 15
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCImagePaintArea::IMAGE_EDIT_MODE 列舉
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定用於修改在影像編輯器對話方塊的影像的繪製模式。  
  
## 語法  
  
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
  
## 成員  
  
|||  
|-|-|  
|Name|說明|  
|`IMAGE_EDIT_MODE_PEN`|用來繪製個別像素。|  
|`IMAGE_EDIT_MODE_FILL`|用來填滿目前游標位置包含所有色彩的相鄰區域。|  
|`IMAGE_EDIT_MODE_LINE`|用來繪製線條。|  
|`IMAGE_EDIT_MODE_RECT`|用來繪製矩形。|  
|`IMAGE_EDIT_MODE_ELLIPSE`|用來繪製橢圓形。|  
|`IMAGE_EDIT_MODE_COLOR`|用來設定目前色彩到色彩包含在目前的游標位置。|  
  
### 備註  
 `CMFCImagePaintArea` 和 `CMFCImageEditorDialog` 類別使用這個列舉型別來設定目前的繪製模式。  繪製模式與目前色彩用來修改在影像編輯器對話方塊的影像區域。  如需 `CMFCImagePaintArea` 和 `CMFCImageEditorDialog` 的詳細資訊，請參閱 [CMFCImagePaintArea Class](../../mfc/reference/cmfcimagepaintarea-class.md) 和 [CMFCImageEditorDialog Class](../../mfc/reference/cmfcimageeditordialog-class.md)。  
  
 當您選取色彩從使用影像繪製模式的 `IMAGE_EDIT_MODE_COLOR` ，這個架構設定目前繪圖模式為 `IMAGE_EDIT_MODE_PEN`。  
  
## 需求  
 **標題:** afximagepaintarea.h  
  
## 請參閱  
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)   
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCImagePaintArea Class](../../mfc/reference/cmfcimagepaintarea-class.md)   
 [CMFCImageEditorDialog Class](../../mfc/reference/cmfcimageeditordialog-class.md)