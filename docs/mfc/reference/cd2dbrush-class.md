---
title: "CD2DBrush 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CD2DBrush"
  - "afxrendertarget/CD2DBrush"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DBrush 類別"
ms.assetid: 0d2c0857-2261-48a8-8ee0-a88cbf08499a
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CD2DBrush 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ID2D1Brush 的包裝函式。  
  
## 語法  
  
```  
class CD2DBrush : public CD2DResource;  
```  
  
## Members  
  
### 受保護的建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CD2DBrush::CD2DBrush](../Topic/CD2DBrush::CD2DBrush.md)|建構 CD2DBrush 物件。|  
|[CD2DBrush::~CD2DBrush](../Topic/CD2DBrush::~CD2DBrush.md)|解構函式。  當正在終結 D2D 筆刷物件時呼叫。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CD2DBrush::Attach](../Topic/CD2DBrush::Attach.md)|將現有的資源介面附加至物件|  
|[CD2DBrush::Destroy](../Topic/CD2DBrush::Destroy.md)|終結 CD2DBrush 物件。  \(覆寫 [CD2DResource::Destroy](../Topic/CD2DResource::Destroy.md)\)。|  
|[CD2DBrush::Detach](../Topic/CD2DBrush::Detach.md)|將資源介面與其物件中斷連結|  
|[CD2DBrush::Get](../Topic/CD2DBrush::Get.md)|傳回 ID2D1Brush 介面|  
|[CD2DBrush::GetOpacity](../Topic/CD2DBrush::GetOpacity.md)|取得這個筆刷的不透明度|  
|[CD2DBrush::GetTransform](../Topic/CD2DBrush::GetTransform.md)|取得轉譯目標的目前轉換。|  
|[CD2DBrush::IsValid](../Topic/CD2DBrush::IsValid.md)|檢查資源有效性 \(覆寫 [CD2DResource::IsValid](../Topic/CD2DResource::IsValid.md)\)。|  
|[CD2DBrush::SetOpacity](../Topic/CD2DBrush::SetOpacity.md)|設定這個筆刷的不透明度|  
|[CD2DBrush::SetTransform](../Topic/CD2DBrush::SetTransform.md)|將指定的轉換套用至轉譯目標，並取代現有的轉換。  所有後續的繪製作業都會在轉換的空間中發生|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CD2DBrush::operator ID2D1Brush\*](../Topic/CD2DBrush::operator%20ID2D1Brush*.md)|傳回 ID2D1Brush 介面|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CD2DBrush::m\_pBrush](../Topic/CD2DBrush::m_pBrush.md)|儲存 ID2D1Brush 物件的指標。|  
|[CD2DBrush::m\_pBrushProperties](../Topic/CD2DBrush::m_pBrushProperties.md)|筆刷屬性。|  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
## 需求  
 **標頭檔：**afxrendertarget.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)