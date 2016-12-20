---
title: "CD2DSolidColorBrush 類別 | Microsoft Docs"
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
  - "CD2DSolidColorBrush"
  - "afxrendertarget/CD2DSolidColorBrush"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DSolidColorBrush 類別"
ms.assetid: d4506637-acce-4f74-8a9b-f0a45571a735
caps.latest.revision: 16
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CD2DSolidColorBrush 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ID2D1SolidColorBrush 的包裝函式。  
  
## 語法  
  
```  
class CD2DSolidColorBrush : public CD2DBrush;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CD2DSolidColorBrush::CD2DSolidColorBrush](../Topic/CD2DSolidColorBrush::CD2DSolidColorBrush.md)|多載。  建構 CD2DSolidColorBrush 物件。|  
|[CD2DSolidColorBrush::~CD2DSolidColorBrush](../Topic/CD2DSolidColorBrush::~CD2DSolidColorBrush.md)|解構函式。  當正在終結 D2D 實心筆刷物件時呼叫。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CD2DSolidColorBrush::Attach](../Topic/CD2DSolidColorBrush::Attach.md)|將現有的資源介面附加至物件|  
|[CD2DSolidColorBrush::Create](../Topic/CD2DSolidColorBrush::Create.md)|建立 CD2DSolidColorBrush。  \(覆寫 [CD2DResource::Create](../Topic/CD2DResource::Create.md)\)。|  
|[CD2DSolidColorBrush::Destroy](../Topic/CD2DSolidColorBrush::Destroy.md)|終結 CD2DSolidColorBrush 物件。  \(覆寫 [CD2DBrush::Destroy](../Topic/CD2DBrush::Destroy.md)\)。|  
|[CD2DSolidColorBrush::Detach](../Topic/CD2DSolidColorBrush::Detach.md)|將資源介面與其物件中斷連結|  
|[CD2DSolidColorBrush::Get](../Topic/CD2DSolidColorBrush::Get.md)|傳回 ID2D1SolidColorBrush 介面|  
|[CD2DSolidColorBrush::GetColor](../Topic/CD2DSolidColorBrush::GetColor.md)|擷取純色筆刷的色彩|  
|[CD2DSolidColorBrush::SetColor](../Topic/CD2DSolidColorBrush::SetColor.md)|指定這個純色筆刷的色彩|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CD2DSolidColorBrush::operator ID2D1SolidColorBrush\*](../Topic/CD2DSolidColorBrush::operator%20ID2D1SolidColorBrush*.md)|傳回 ID2D1SolidColorBrush 介面|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CD2DSolidColorBrush::m\_colorSolid](../Topic/CD2DSolidColorBrush::m_colorSolid.md)|筆刷純色。|  
|[CD2DSolidColorBrush::m\_pSolidColorBrush](../Topic/CD2DSolidColorBrush::m_pSolidColorBrush.md)|儲存 ID2D1SolidColorBrush 物件的指標。|  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 [CD2DSolidColorBrush](../../mfc/reference/cd2dsolidcolorbrush-class.md)  
  
## 需求  
 **標頭檔：**afxrendertarget.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)