---
title: "CD2DMesh 類別 | Microsoft Docs"
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
  - "afxrendertarget/CD2DMesh"
  - "CD2DMesh"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DMesh 類別"
ms.assetid: 11a2c78a-1367-40e8-a34f-44aa0509a4c9
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CD2DMesh 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ID2D1Mesh 的包裝函式。  
  
## 語法  
  
```  
class CD2DMesh : public CD2DResource;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CD2DMesh::CD2DMesh](../Topic/CD2DMesh::CD2DMesh.md)|建構 CD2DMesh 物件。|  
|[CD2DMesh::~CD2DMesh](../Topic/CD2DMesh::~CD2DMesh.md)|解構函式。  當正在終結 D2D 網狀物件時呼叫。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CD2DMesh::Attach](../Topic/CD2DMesh::Attach.md)|將現有的資源介面附加至物件|  
|[CD2DMesh::Create](../Topic/CD2DMesh::Create.md)|建立 CD2DMesh。  \(覆寫 [CD2DResource::Create](../Topic/CD2DResource::Create.md)\)。|  
|[CD2DMesh::Destroy](../Topic/CD2DMesh::Destroy.md)|終結 CD2DMesh 物件。  \(覆寫 [CD2DResource::Destroy](../Topic/CD2DResource::Destroy.md)\)。|  
|[CD2DMesh::Detach](../Topic/CD2DMesh::Detach.md)|將資源介面與其物件中斷連結|  
|[CD2DMesh::Get](../Topic/CD2DMesh::Get.md)|傳回 ID2D1Mesh 介面|  
|[CD2DMesh::IsValid](../Topic/CD2DMesh::IsValid.md)|檢查資源有效性 \(覆寫 [CD2DResource::IsValid](../Topic/CD2DResource::IsValid.md)\)。|  
|[CD2DMesh::Open](../Topic/CD2DMesh::Open.md)|開啟母體擴展的網狀。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CD2DMesh::operator ID2D1Mesh\*](../Topic/CD2DMesh::operator%20ID2D1Mesh*.md)|傳回 ID2D1Mesh 介面|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CD2DMesh::m\_pMesh](../Topic/CD2DMesh::m_pMesh.md)|ID2D1Mesh 的指標。|  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DMesh](../../mfc/reference/cd2dmesh-class.md)  
  
## 需求  
 **標頭檔：**afxrendertarget.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)