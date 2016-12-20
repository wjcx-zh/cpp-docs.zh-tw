---
title: "CD2DRadialGradientBrush 類別 | Microsoft Docs"
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
  - "CD2DRadialGradientBrush"
  - "afxrendertarget/CD2DRadialGradientBrush"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DRadialGradientBrush 類別"
ms.assetid: 6c76d84a-d831-4ee2-96f1-82c1f5b0d6a9
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CD2DRadialGradientBrush 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ID2D1RadialGradientBrush 的包裝函式。  
  
## 語法  
  
```  
class CD2DRadialGradientBrush : public CD2DGradientBrush;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CD2DRadialGradientBrush::CD2DRadialGradientBrush](../Topic/CD2DRadialGradientBrush::CD2DRadialGradientBrush.md)|建構 CD2DLinearGradientBrush 物件。|  
|[CD2DRadialGradientBrush::~CD2DRadialGradientBrush](../Topic/CD2DRadialGradientBrush::~CD2DRadialGradientBrush.md)|解構函式。  當正在終結 D2D 放射狀漸層筆刷物件時呼叫。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CD2DRadialGradientBrush::Attach](../Topic/CD2DRadialGradientBrush::Attach.md)|將現有的資源介面附加至物件|  
|[CD2DRadialGradientBrush::Create](../Topic/CD2DRadialGradientBrush::Create.md)|建立 CD2DRadialGradientBrush。  \(覆寫 [CD2DResource::Create](../Topic/CD2DResource::Create.md)\)。|  
|[CD2DRadialGradientBrush::Destroy](../Topic/CD2DRadialGradientBrush::Destroy.md)|終結 CD2DRadialGradientBrush 物件。  \(覆寫 [CD2DGradientBrush::Destroy](../Topic/CD2DGradientBrush::Destroy.md)\)。|  
|[CD2DRadialGradientBrush::Detach](../Topic/CD2DRadialGradientBrush::Detach.md)|將資源介面與其物件中斷連結|  
|[CD2DRadialGradientBrush::Get](../Topic/CD2DRadialGradientBrush::Get.md)|傳回 ID2D1RadialGradientBrush 介面|  
|[CD2DRadialGradientBrush::GetCenter](../Topic/CD2DRadialGradientBrush::GetCenter.md)|擷取漸層橢圓形的中心。|  
|[CD2DRadialGradientBrush::GetGradientOriginOffset](../Topic/CD2DRadialGradientBrush::GetGradientOriginOffset.md)|擷取漸層原點相對於漸層橢圓形中心的位移|  
|[CD2DRadialGradientBrush::GetRadiusX](../Topic/CD2DRadialGradientBrush::GetRadiusX.md)|擷取漸層橢圓形的 X 半徑。|  
|[CD2DRadialGradientBrush::GetRadiusY](../Topic/CD2DRadialGradientBrush::GetRadiusY.md)|擷取漸層橢圓形的 Y 半徑。|  
|[CD2DRadialGradientBrush::SetCenter](../Topic/CD2DRadialGradientBrush::SetCenter.md)|在筆刷座標空間中指定漸層橢圓形的中心|  
|[CD2DRadialGradientBrush::SetGradientOriginOffset](../Topic/CD2DRadialGradientBrush::SetGradientOriginOffset.md)|指定漸層原點相對於漸層橢圓形中心的位移|  
|[CD2DRadialGradientBrush::SetRadiusX](../Topic/CD2DRadialGradientBrush::SetRadiusX.md)|在筆刷座標空間中指定漸層橢圓形的 X 半徑|  
|[CD2DRadialGradientBrush::SetRadiusY](../Topic/CD2DRadialGradientBrush::SetRadiusY.md)|在筆刷座標空間中指定漸層橢圓形的 Y 半徑|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CD2DRadialGradientBrush::operator ID2D1RadialGradientBrush\*](../Topic/CD2DRadialGradientBrush::operator%20ID2D1RadialGradientBrush*.md)|傳回 ID2D1RadialGradientBrush 介面|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CD2DRadialGradientBrush::m\_pRadialGradientBrush](../Topic/CD2DRadialGradientBrush::m_pRadialGradientBrush.md)|ID2D1RadialGradientBrush 的指標。|  
|[CD2DRadialGradientBrush::m\_RadialGradientBrushProperties](../Topic/CD2DRadialGradientBrush::m_RadialGradientBrushProperties.md)|筆刷漸層的中心、漸層原點位移以及 X 半徑和 Y 半徑。|  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 [CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)  
  
 [CD2DRadialGradientBrush](../../mfc/reference/cd2dradialgradientbrush-class.md)  
  
## 需求  
 **標頭檔：**afxrendertarget.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)