---
title: "CD2DTextLayout 類別 | Microsoft Docs"
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
  - "CD2DTextLayout"
  - "afxrendertarget/CD2DTextLayout"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DTextLayout 類別"
ms.assetid: 724bd13c-f2ef-4e55-a775-8cb04b7b7908
caps.latest.revision: 16
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CD2DTextLayout 類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

IDWriteTextLayout 的包裝函式。  
  
## 語法  
  
```  
class CD2DTextLayout : public CD2DResource;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[CD2DTextLayout::CD2DTextLayout](../Topic/CD2DTextLayout::CD2DTextLayout.md)|建構 CD2DTextLayout 物件。|  
|[CD2DTextLayout::~CD2DTextLayout](../Topic/CD2DTextLayout::~CD2DTextLayout.md)|解構函式。  當正在終結 D2D 文字配置物件時呼叫。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CD2DTextLayout::Create](../Topic/CD2DTextLayout::Create.md)|建立 CD2DTextLayout。  \(覆寫 [CD2DResource::Create](../Topic/CD2DResource::Create.md)\)。|  
|[CD2DTextLayout::Destroy](../Topic/CD2DTextLayout::Destroy.md)|終結 CD2DTextLayout 物件。  \(覆寫 [CD2DResource::Destroy](../Topic/CD2DResource::Destroy.md)\)。|  
|[CD2DTextLayout::Get](../Topic/CD2DTextLayout::Get.md)|傳回 IDWriteTextLayout 介面|  
|[CD2DTextLayout::GetFontFamilyName](../Topic/CD2DTextLayout::GetFontFamilyName.md)|複製指定位置之文字的字型家族名稱。|  
|[CD2DTextLayout::GetLocaleName](../Topic/CD2DTextLayout::GetLocaleName.md)|取得位於指定位置之文字的地區設定名稱。|  
|[CD2DTextLayout::IsValid](../Topic/CD2DTextLayout::IsValid.md)|檢查資源有效性 \(覆寫 [CD2DResource::IsValid](../Topic/CD2DResource::IsValid.md)\)。|  
|[CD2DTextLayout::ReCreate](../Topic/CD2DTextLayout::ReCreate.md)|重新建立 CD2DTextLayout。  \(覆寫 [CD2DResource::ReCreate](../Topic/CD2DResource::ReCreate.md)\)。|  
|[CD2DTextLayout::SetFontFamilyName](../Topic/CD2DTextLayout::SetFontFamilyName.md)|為指定之文字範圍內的文字設定以 Null 結束的字型家族名稱|  
|[CD2DTextLayout::SetLocaleName](../Topic/CD2DTextLayout::SetLocaleName.md)|設定指定之文字範圍內文字的地區設定名稱。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[CD2DTextLayout::operator IDWriteTextLayout\*](../Topic/CD2DTextLayout::operator%20IDWriteTextLayout*.md)|傳回 IDWriteTextLayout 介面|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CD2DTextLayout::m\_pTextLayout](../Topic/CD2DTextLayout::m_pTextLayout.md)|IDWriteTextLayout 的指標。|  
  
## 繼承階層架構  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DTextLayout](../../mfc/reference/cd2dtextlayout-class.md)  
  
## 需求  
 **標頭檔：**afxrendertarget.h  
  
## 請參閱  
 [類別](../../mfc/reference/mfc-classes.md)