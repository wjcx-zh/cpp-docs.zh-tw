---
title: "CD2DResource 類別 | Microsoft Docs"
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
  - "afxrendertarget/CD2DResource"
  - "CD2DResource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DResource 類別"
ms.assetid: 34e3ee18-aab6-4c39-9294-de869e1f7820
caps.latest.revision: 18
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CD2DResource 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

抽象類別，提供介面以建立和管理 D2D 資源，例如筆刷、圖層和文字。  
  
## 語法  
  
```  
class CD2DResource : public CObject;  
```  
  
## Members  
  
### 受保護的建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CD2DResource::CD2DResource](../Topic/CD2DResource::CD2DResource.md)|建構 CD2DResource 物件。|  
|[CD2DResource::~CD2DResource](../Topic/CD2DResource::~CD2DResource.md)|解構函式。  當正在終結 D2D 資源物件時呼叫。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CD2DResource::Create](../Topic/CD2DResource::Create.md)|建立 CD2DResource。|  
|[CD2DResource::Destroy](../Topic/CD2DResource::Destroy.md)|終結 CD2DResource 物件。|  
|[CD2DResource::IsValid](../Topic/CD2DResource::IsValid.md)|檢查資源有效性|  
  
### 受保護的方法  
  
|名稱|描述|  
|--------|--------|  
|[CD2DResource::IsAutoDestroy](../Topic/CD2DResource::IsAutoDestroy.md)|核取自動終結旗標。|  
|[CD2DResource::ReCreate](../Topic/CD2DResource::ReCreate.md)|重新建立 CD2DResource。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CD2DResource::m\_bIsAutoDestroy](../Topic/CD2DResource::m_bIsAutoDestroy.md)|資源將會由擁有者 \(CRenderTarget\) 終結|  
|[CD2DResource::m\_pParentTarget](../Topic/CD2DResource::m_pParentTarget.md)|父 CRenderTarget 的指標\)|  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
## 需求  
 **標頭檔：**afxrendertarget.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)