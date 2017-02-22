---
title: "CD2DPathGeometry 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxrendertarget/CD2DPathGeometry"
  - "CD2DPathGeometry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DPathGeometry 類別"
ms.assetid: 686216eb-5080-4242-ace5-8fa1ce96307c
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CD2DPathGeometry 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ID2D1PathGeometry 的包裝函式。  
  
## 語法  
  
```  
class CD2DPathGeometry : public CD2DGeometry;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CD2DPathGeometry::CD2DPathGeometry](../Topic/CD2DPathGeometry::CD2DPathGeometry.md)|建構 CD2DPathGeometry 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CD2DPathGeometry::Attach](../Topic/CD2DPathGeometry::Attach.md)|將現有的資源介面附加至物件|  
|[CD2DPathGeometry::Create](../Topic/CD2DPathGeometry::Create.md)|建立 CD2DPathGeometry。  \(覆寫 [CD2DResource::Create](../Topic/CD2DResource::Create.md)\)。|  
|[CD2DPathGeometry::Destroy](../Topic/CD2DPathGeometry::Destroy.md)|終結 CD2DPathGeometry 物件。  \(覆寫 [CD2DGeometry::Destroy](../Topic/CD2DGeometry::Destroy.md)\)。|  
|[CD2DPathGeometry::Detach](../Topic/CD2DPathGeometry::Detach.md)|將資源介面與其物件中斷連結|  
|[CD2DPathGeometry::GetFigureCount](../Topic/CD2DPathGeometry::GetFigureCount.md)|擷取路徑幾何中的圖形數目。|  
|[CD2DPathGeometry::GetSegmentCount](../Topic/CD2DPathGeometry::GetSegmentCount.md)|擷取路徑幾何的線段數目。|  
|[CD2DPathGeometry::Open](../Topic/CD2DPathGeometry::Open.md)|擷取用以將圖形及線段填入路徑幾何的幾何接收。|  
|[CD2DPathGeometry::Stream](../Topic/CD2DPathGeometry::Stream.md)|將路徑幾何的內容複製到指定的 ID2D1GeometrySink。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CD2DPathGeometry::m\_pPathGeometry](../Topic/CD2DPathGeometry::m_pPathGeometry.md)|ID2D1PathGeometry 的指標。|  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DGeometry](../../mfc/reference/cd2dgeometry-class.md)  
  
 [CD2DPathGeometry](../../mfc/reference/cd2dpathgeometry-class.md)  
  
## 需求  
 **標頭檔：**afxrendertarget.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)