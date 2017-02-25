---
title: "CD2DLayer 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxrendertarget/CD2DLayer"
  - "CD2DLayer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DLayer 類別"
ms.assetid: 2f96378e-66bb-40d1-9661-6afe324de3c1
caps.latest.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# CD2DLayer 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ID2D1Layer 的包裝函式。  
  
## 語法  
  
```  
class CD2DLayer : public CD2DResource;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CD2DLayer::CD2DLayer](../Topic/CD2DLayer::CD2DLayer.md)|建構 CD2DLayer 物件。|  
|[CD2DLayer::~CD2DLayer](../Topic/CD2DLayer::~CD2DLayer.md)|解構函式。  當正在終結 D2D 圖層物件時呼叫。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CD2DLayer::Attach](../Topic/CD2DLayer::Attach.md)|將現有的資源介面附加至物件|  
|[CD2DLayer::Create](../Topic/CD2DLayer::Create.md)|建立 CD2DLayer。  \(覆寫 [CD2DResource::Create](../Topic/CD2DResource::Create.md)\)。|  
|[CD2DLayer::Destroy](../Topic/CD2DLayer::Destroy.md)|終結 CD2DLayer 物件。  \(覆寫 [CD2DResource::Destroy](../Topic/CD2DResource::Destroy.md)\)。|  
|[CD2DLayer::Detach](../Topic/CD2DLayer::Detach.md)|將資源介面與其物件中斷連結|  
|[CD2DLayer::Get](../Topic/CD2DLayer::Get.md)|傳回 ID2D1Layer 介面|  
|[CD2DLayer::GetSize](../Topic/CD2DLayer::GetSize.md)|傳回轉譯目標的大小 \(以裝置獨立畫素為單位\)|  
|[CD2DLayer::IsValid](../Topic/CD2DLayer::IsValid.md)|檢查資源有效性 \(覆寫 [CD2DResource::IsValid](../Topic/CD2DResource::IsValid.md)\)。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CD2DLayer::operator ID2D1Layer\*](../Topic/CD2DLayer::operator%20ID2D1Layer*.md)|傳回 ID2D1Layer 介面|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CD2DLayer::m\_pLayer](../Topic/CD2DLayer::m_pLayer.md)|儲存 ID2D1Layer 物件的指標。|  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DLayer](../../mfc/reference/cd2dlayer-class.md)  
  
## 需求  
 **標頭檔：**afxrendertarget.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)