---
title: "CD2DGeometrySink 類別 | Microsoft Docs"
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
  - "afxrendertarget/CD2DGeometrySink"
  - "CD2DGeometrySink"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DGeometrySink 類別"
ms.assetid: e5e07f41-0343-4ab1-9d6b-8c62ed33c04a
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CD2DGeometrySink 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ID2D1GeometrySink 的包裝函式。  
  
## 語法  
  
```  
class CD2DGeometrySink;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CD2DGeometrySink::CD2DGeometrySink](../Topic/CD2DGeometrySink::CD2DGeometrySink.md)|從 CD2DPathGeometry 物件建構 CD2DGeometrySink 物件。|  
|[CD2DGeometrySink::~CD2DGeometrySink](../Topic/CD2DGeometrySink::~CD2DGeometrySink.md)|解構函式。  當正在終結 D2D 幾何接收物件時呼叫。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CD2DGeometrySink::AddArc](../Topic/CD2DGeometrySink::AddArc.md)|將單一弧形加入至路徑幾何|  
|[CD2DGeometrySink::AddBezier](../Topic/CD2DGeometrySink::AddBezier.md)|在目前點和指定的結束點之間建立一條三次方貝茲曲線。|  
|[CD2DGeometrySink::AddBeziers](../Topic/CD2DGeometrySink::AddBeziers.md)|建立三次方貝茲曲線序列，並將它們加入至幾何接收。|  
|[CD2DGeometrySink::AddLine](../Topic/CD2DGeometrySink::AddLine.md)|在目前點和指定的結束點之間建立線段，並將其加入至幾何接收。|  
|[CD2DGeometrySink::AddLines](../Topic/CD2DGeometrySink::AddLines.md)|使用指定的點建立線條序列，並將它們加入至幾何接收。|  
|[CD2DGeometrySink::AddQuadraticBezier](../Topic/CD2DGeometrySink::AddQuadraticBezier.md)|在目前點和指定的結束點之間建立一條二次方貝茲曲線。|  
|[CD2DGeometrySink::AddQuadraticBeziers](../Topic/CD2DGeometrySink::AddQuadraticBeziers.md)|將二次方貝茲線段序列加入做為單一呼叫中的陣列。|  
|[CD2DGeometrySink::BeginFigure](../Topic/CD2DGeometrySink::BeginFigure.md)|啟動位於指定點的新圖形。|  
|[CD2DGeometrySink::Close](../Topic/CD2DGeometrySink::Close.md)|關閉幾何接收|  
|[CD2DGeometrySink::EndFigure](../Topic/CD2DGeometrySink::EndFigure.md)|結束目前的圖形，並選擇性地關閉它。|  
|[CD2DGeometrySink::Get](../Topic/CD2DGeometrySink::Get.md)|傳回 ID2D1GeometrySink 介面。|  
|[CD2DGeometrySink::IsValid](../Topic/CD2DGeometrySink::IsValid.md)|檢查幾何接收有效性|  
|[CD2DGeometrySink::SetFillMode](../Topic/CD2DGeometrySink::SetFillMode.md)|指定用來判斷哪些點是在這個幾何接收所描述的幾何內部，以及哪些點是在外部的方法。|  
|[CD2DGeometrySink::SetSegmentFlags](../Topic/CD2DGeometrySink::SetSegmentFlags.md)|指定要套用到已加入至幾何接收之新區段的筆劃與聯結選項。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CD2DGeometrySink::operator ID2D1GeometrySink\*](../Topic/CD2DGeometrySink::operator%20ID2D1GeometrySink*.md)|傳回 ID2D1GeometrySink 介面。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CD2DGeometrySink::m\_pSink](../Topic/CD2DGeometrySink::m_pSink.md)|ID2D1GeometrySink 的指標。|  
  
## 繼承階層架構  
 [CD2DGeometrySink](../../mfc/reference/cd2dgeometrysink-class.md)  
  
## 需求  
 **標頭檔：**afxrendertarget.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)