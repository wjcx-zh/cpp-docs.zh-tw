---
title: "CD2DGradientBrush 類別 | Microsoft Docs"
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
  - "CD2DGradientBrush"
  - "afxrendertarget/CD2DGradientBrush"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DGradientBrush 類別"
ms.assetid: 5bf133e6-16b7-4e3a-845d-0ce63fafe5ec
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CD2DGradientBrush 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

CD2DLinearGradientBrush 和 CD2DRadialGradientBrush 類別的基底類別。  
  
## 語法  
  
```  
class CD2DGradientBrush : public CD2DBrush;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CD2DGradientBrush::CD2DGradientBrush](../Topic/CD2DGradientBrush::CD2DGradientBrush.md)|建構 CD2DGradientBrush 物件。|  
|[CD2DGradientBrush::~CD2DGradientBrush](../Topic/CD2DGradientBrush::~CD2DGradientBrush.md)|解構函式。  當正在終結 D2D 漸層筆刷物件時呼叫。|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CD2DGradientBrush::Destroy](../Topic/CD2DGradientBrush::Destroy.md)|終結 CD2DGradientBrush 物件。  \(覆寫 [CD2DBrush::Destroy](../Topic/CD2DBrush::Destroy.md)\)。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CD2DGradientBrush::m\_arGradientStops](../Topic/CD2DGradientBrush::m_arGradientStops.md)|D2D1\_GRADIENT\_STOP 結構的陣列。|  
|[CD2DGradientBrush::m\_colorInterpolationGamma](../Topic/CD2DGradientBrush::m_colorInterpolationGamma.md)|在漸層停駐點之間執行色彩插補所用的空間。|  
|[CD2DGradientBrush::m\_extendMode](../Topic/CD2DGradientBrush::m_extendMode.md)|在 \[0,1\] 正規化範圍之外的漸層行為。|  
|[CD2DGradientBrush::m\_pGradientStops](../Topic/CD2DGradientBrush::m_pGradientStops.md)|D2D1\_GRADIENT\_STOP 結構陣列的指標。|  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 [CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)  
  
## 需求  
 **標頭檔：**afxrendertarget.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)