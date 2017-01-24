---
title: "CD2DGeometry 類別 | Microsoft Docs"
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
  - "CD2DGeometry"
  - "afxrendertarget/CD2DGeometry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DGeometry 類別"
ms.assetid: 3f95054b-fdb8-4e87-87f2-9fc3df7279ec
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CD2DGeometry 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ID2D1Geometry 的包裝函式。  
  
## 語法  
  
```  
class CD2DGeometry : public CD2DResource;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CD2DGeometry::CD2DGeometry](../Topic/CD2DGeometry::CD2DGeometry.md)|建構 CD2DGeometry 物件。|  
|[CD2DGeometry::~CD2DGeometry](../Topic/CD2DGeometry::~CD2DGeometry.md)|解構函式。  當正在終結 D2D 幾何物件時呼叫。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CD2DGeometry::Attach](../Topic/CD2DGeometry::Attach.md)|將現有的資源介面附加至物件|  
|[CD2DGeometry::CombineWithGeometry](../Topic/CD2DGeometry::CombineWithGeometry.md)|將這個幾何與指定的幾何合併，並將結果儲存在 ID2D1SimplifiedGeometrySink。|  
|[CD2DGeometry::CompareWithGeometry](../Topic/CD2DGeometry::CompareWithGeometry.md)|描述這個幾何與指定幾何之間的交集  這個比較是使用指定的簡維 \(Flattening\) 容錯來執行。|  
|[CD2DGeometry::ComputeArea](../Topic/CD2DGeometry::ComputeArea.md)|在幾何由指定的矩陣使用指定的容限進行轉換和簡維之後，計算該幾何的面積。|  
|[CD2DGeometry::ComputeLength](../Topic/CD2DGeometry::ComputeLength.md)|仿彿將每個區段展開成一條線的方式，計算幾何的長度。|  
|[CD2DGeometry::ComputePointAtLength](../Topic/CD2DGeometry::ComputePointAtLength.md)|在幾何由指定的矩陣使用指定的容限進行轉換和簡維之後，計算沿該幾何指定之距離位置上的點及正切向量。|  
|[CD2DGeometry::Destroy](../Topic/CD2DGeometry::Destroy.md)|終結 CD2DGeometry 物件。  \(覆寫 [CD2DResource::Destroy](../Topic/CD2DResource::Destroy.md)\)。|  
|[CD2DGeometry::Detach](../Topic/CD2DGeometry::Detach.md)|將資源介面與其物件中斷連結|  
|[CD2DGeometry::FillContainsPoint](../Topic/CD2DGeometry::FillContainsPoint.md)|表示在指定的簡維容限下，幾何所填滿的區域是否包含指定的點。|  
|[CD2DGeometry::Get](../Topic/CD2DGeometry::Get.md)|傳回 ID2D1Geometry 介面。|  
|[CD2DGeometry::GetBounds](../Topic/CD2DGeometry::GetBounds.md)||  
|[CD2DGeometry::GetWidenedBounds](../Topic/CD2DGeometry::GetWidenedBounds.md)|在幾何以指定的筆劃寬度及樣式加寬，並由指定的矩陣進行轉換之後，取得該幾何的界限。|  
|[CD2DGeometry::IsValid](../Topic/CD2DGeometry::IsValid.md)|檢查資源有效性 \(覆寫 [CD2DResource::IsValid](../Topic/CD2DResource::IsValid.md)\)。|  
|[CD2DGeometry::Outline](../Topic/CD2DGeometry::Outline.md)|計算幾何的外框，並將結果寫入至 ID2D1SimplifiedGeometrySink。|  
|[CD2DGeometry::Simplify](../Topic/CD2DGeometry::Simplify.md)|建立僅包含線條及 \(選擇性\) 三次方貝茲曲線的簡化版幾何，並將結果寫入 ID2D1SimplifiedGeometrySink。|  
|[CD2DGeometry::StrokeContainsPoint](../Topic/CD2DGeometry::StrokeContainsPoint.md)|根據指定的筆劃粗細、樣式和轉換，判斷幾何筆劃是否包含指定的點。|  
|[CD2DGeometry::Tessellate](../Topic/CD2DGeometry::Tessellate.md)|在幾何由指定的矩陣使用指定的容限進行轉換和簡維之後，建立一組涵蓋該幾何的順時針捲繞三角形。|  
|[CD2DGeometry::Widen](../Topic/CD2DGeometry::Widen.md)|在幾何由指定的矩陣使用指定的容限進行轉換和簡維之後，以指定的筆劃將幾何加寬，並將結果寫入 ID2D1SimplifiedGeometrySink。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CD2DGeometry::operator ID2D1Geometry\*](../Topic/CD2DGeometry::operator%20ID2D1Geometry*.md)|傳回 ID2D1Geometry 介面。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CD2DGeometry::m\_pGeometry](../Topic/CD2DGeometry::m_pGeometry.md)|ID2D1Geometry 的指標。|  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DGeometry](../../mfc/reference/cd2dgeometry-class.md)  
  
## 需求  
 **標頭檔：**afxrendertarget.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)