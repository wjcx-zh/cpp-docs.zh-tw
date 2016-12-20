---
title: "CD2DLinearGradientBrush 類別 | Microsoft Docs"
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
  - "afxrendertarget/CD2DLinearGradientBrush"
  - "CD2DLinearGradientBrush"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DLinearGradientBrush 類別"
ms.assetid: d4be9ff9-0ea8-45e6-9b8d-f3bc5673cbac
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CD2DLinearGradientBrush 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ID2D1LinearGradientBrush 的包裝函式。  
  
## 語法  
  
```  
class CD2DLinearGradientBrush : public CD2DGradientBrush;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CD2DLinearGradientBrush::CD2DLinearGradientBrush](../Topic/CD2DLinearGradientBrush::CD2DLinearGradientBrush.md)|建構 CD2DLinearGradientBrush 物件。|  
|[CD2DLinearGradientBrush::~CD2DLinearGradientBrush](../Topic/CD2DLinearGradientBrush::~CD2DLinearGradientBrush.md)|解構函式。  當正在終結 D2D 線形漸層筆刷物件時呼叫。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CD2DLinearGradientBrush::Attach](../Topic/CD2DLinearGradientBrush::Attach.md)|將現有的資源介面附加至物件|  
|[CD2DLinearGradientBrush::Create](../Topic/CD2DLinearGradientBrush::Create.md)|建立 CD2DLinearGradientBrush。  \(覆寫 [CD2DResource::Create](../Topic/CD2DResource::Create.md)\)。|  
|[CD2DLinearGradientBrush::Destroy](../Topic/CD2DLinearGradientBrush::Destroy.md)|終結 CD2DLinearGradientBrush 物件。  \(覆寫 [CD2DGradientBrush::Destroy](../Topic/CD2DGradientBrush::Destroy.md)\)。|  
|[CD2DLinearGradientBrush::Detach](../Topic/CD2DLinearGradientBrush::Detach.md)|將資源介面與其物件中斷連結|  
|[CD2DLinearGradientBrush::Get](../Topic/CD2DLinearGradientBrush::Get.md)|傳回 ID2D1LinearGradientBrush 介面|  
|[CD2DLinearGradientBrush::GetEndPoint](../Topic/CD2DLinearGradientBrush::GetEndPoint.md)|擷取線形漸層的結束座標。|  
|[CD2DLinearGradientBrush::GetStartPoint](../Topic/CD2DLinearGradientBrush::GetStartPoint.md)|擷取線形漸層的開始座標。|  
|[CD2DLinearGradientBrush::SetEndPoint](../Topic/CD2DLinearGradientBrush::SetEndPoint.md)|設定線形漸層在筆刷座標空間中的結束座標。|  
|[CD2DLinearGradientBrush::SetStartPoint](../Topic/CD2DLinearGradientBrush::SetStartPoint.md)|設定線形漸層在筆刷座標空間中的開始座標。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CD2DLinearGradientBrush::operator ID2D1LinearGradientBrush\*](../Topic/CD2DLinearGradientBrush::operator%20ID2D1LinearGradientBrush*.md)|傳回 ID2D1LinearGradientBrush 介面|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CD2DLinearGradientBrush::m\_LinearGradientBrushProperties](../Topic/CD2DLinearGradientBrush::m_LinearGradientBrushProperties.md)|漸層的開始和結束點。|  
|[CD2DLinearGradientBrush::m\_pLinearGradientBrush](../Topic/CD2DLinearGradientBrush::m_pLinearGradientBrush.md)|ID2D1LinearGradientBrush 的指標。|  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 [CD2DGradientBrush](../../mfc/reference/cd2dgradientbrush-class.md)  
  
 [CD2DLinearGradientBrush](../../mfc/reference/cd2dlineargradientbrush-class.md)  
  
## 需求  
 **標頭檔：**afxrendertarget.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)