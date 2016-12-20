---
title: "CD2DTextFormat 類別 | Microsoft Docs"
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
  - "afxrendertarget/CD2DTextFormat"
  - "CD2DTextFormat"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DTextFormat 類別"
ms.assetid: db194cec-9dae-4644-ab84-7c43b7164117
caps.latest.revision: 16
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CD2DTextFormat 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

IDWriteTextFormat 的包裝函式。  
  
## 語法  
  
```  
class CD2DTextFormat : public CD2DResource;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CD2DTextFormat::CD2DTextFormat](../Topic/CD2DTextFormat::CD2DTextFormat.md)|建構 CD2DTextFormat 物件。|  
|[CD2DTextFormat::~CD2DTextFormat](../Topic/CD2DTextFormat::~CD2DTextFormat.md)|解構函式。  當正在終結 D2D 文字格式物件時呼叫。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CD2DTextFormat::Create](../Topic/CD2DTextFormat::Create.md)|建立 CD2DTextFormat。  \(覆寫 [CD2DResource::Create](../Topic/CD2DResource::Create.md)\)。|  
|[CD2DTextFormat::Destroy](../Topic/CD2DTextFormat::Destroy.md)|終結 CD2DTextFormat 物件。  \(覆寫 [CD2DResource::Destroy](../Topic/CD2DResource::Destroy.md)\)。|  
|[CD2DTextFormat::Get](../Topic/CD2DTextFormat::Get.md)|傳回 IDWriteTextFormat 介面|  
|[CD2DTextFormat::GetFontFamilyName](../Topic/CD2DTextFormat::GetFontFamilyName.md)|取得字型家族名稱的複本。|  
|[CD2DTextFormat::GetLocaleName](../Topic/CD2DTextFormat::GetLocaleName.md)|取得地區設定名稱的複本。|  
|[CD2DTextFormat::IsValid](../Topic/CD2DTextFormat::IsValid.md)|檢查資源有效性 \(覆寫 [CD2DResource::IsValid](../Topic/CD2DResource::IsValid.md)\)。|  
|[CD2DTextFormat::ReCreate](../Topic/CD2DTextFormat::ReCreate.md)|重新建立 CD2DTextFormat。  \(覆寫 [CD2DResource::ReCreate](../Topic/CD2DResource::ReCreate.md)\)。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CD2DTextFormat::operator IDWriteTextFormat\*](../Topic/CD2DTextFormat::operator%20IDWriteTextFormat*.md)|傳回 IDWriteTextFormat 介面|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CD2DTextFormat::m\_pTextFormat](../Topic/CD2DTextFormat::m_pTextFormat.md)|IDWriteTextFormat 的指標。|  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DTextFormat](../../mfc/reference/cd2dtextformat-class.md)  
  
## 需求  
 **標頭檔：**afxrendertarget.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)