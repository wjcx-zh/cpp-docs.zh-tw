---
title: "CMFCImagePaintArea Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCImagePaintArea"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCImagePaintArea class"
ms.assetid: c59eec22-f15a-4e58-8c4d-4a18a41f4452
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCImagePaintArea Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

提供可用來修改在影像編輯器對話方塊的影像的影像區域。  
  
## 語法  
  
```  
class CMFCImagePaintArea : public CButton  
```  
  
## Members  
  
### 公用建構函式  
  
|||  
|-|-|  
|名稱|描述|  
|[CMFCImagePaintArea::CMFCImagePaintArea](../Topic/CMFCImagePaintArea::CMFCImagePaintArea.md)|建構 `CMFCImagePaintArea` 物件。|  
|`CMFCImagePaintArea::~CMFCImagePaintArea`|解構函式。|  
  
### 公用方法  
  
|||  
|-|-|  
|名稱|描述|  
|[CMFCImagePaintArea::GetMode](../Topic/CMFCImagePaintArea::GetMode.md)|擷取目前的繪圖模式。|  
|[CMFCImagePaintArea::SetBitmap](../Topic/CMFCImagePaintArea::SetBitmap.md)|設定圖片區域的點陣圖影像。|  
|[CMFCImagePaintArea::SetColor](../Topic/CMFCImagePaintArea::SetColor.md)|設定目前的繪圖色彩。|  
|[CMFCImagePaintArea::SetMode](../Topic/CMFCImagePaintArea::SetMode.md)|設定目前的繪圖模式。|  
  
### 備註  
 這個類別並不適合直接從您的程式碼使用。  
  
 架構會使用這個類別會顯示在影像編輯器對話方塊的圖片區域。  如需影像編輯器對話方塊的詳細資訊，請參閱 [CMFCImageEditorDialog Class](../../mfc/reference/cmfcimageeditordialog-class.md)。  
  
## 範例  
 下列範例示範如何建構物件 `CMFCImagePaintArea` 類別，設定目前的繪圖色彩，設定目前的繪製模式，並設定圖片區域的點陣圖影像。  
  
 [!code-cpp[NVC_MFC_RibbonApp#37](../../mfc/reference/codesnippet/CPP/cmfcimagepaintarea-class_1.cpp)]  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CButton](../../mfc/reference/cbutton-class.md)  
  
 [CMFCImagePaintArea](../../mfc/reference/cmfcimagepaintarea-class.md)  
  
## 需求  
 **標題:** afximagepaintarea.h  
  
## 請參閱  
 [階層架構圖表](../../mfc/hierarchy-chart.md)   
 [類別](../../mfc/reference/mfc-classes.md)   
 [CMFCImageEditorDialog Class](../../mfc/reference/cmfcimageeditordialog-class.md)