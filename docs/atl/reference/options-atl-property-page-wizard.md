---
title: "選項, ATL 屬性頁精靈 | Microsoft Docs"
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
  - "vc.codewiz.class.atl.ppg.options"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 屬性頁精靈, 選項"
ms.assetid: a7107779-b2ea-4f99-b84b-7f3e0c504bc8
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 選項, ATL 屬性頁精靈
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用此精靈頁面定義正在建立之屬性頁的執行緒模型和彙總 \(Aggregation\) 層次。  
  
 **執行緒模型**  
 指定屬性頁使用的執行緒模型。  
  
 如需詳細資訊，請參閱[指定專案的執行緒模型](../../atl/specifying-the-threading-model-for-a-project-atl.md)。  
  
|選項|描述|  
|--------|--------|  
|`Single`|屬性頁只在主要 COM 執行緒中執行|  
|**Apartment**|屬性頁可在任何單一執行緒 Apartment 中建立，  預設值。|  
  
 **Aggregation**  
 為您正在建立的屬性頁加入彙總支援。  如需詳細資訊，請參閱[彙總](../../atl/aggregation.md)。  
  
|選項|描述|  
|--------|--------|  
|**是**|建立可彙總的屬性頁|  
|**否**|建立無法彙總的屬性頁|  
|**Only**|建立只能透過彙總執行個體化的屬性頁|  
  
## 請參閱  
 [ATL 屬性頁精靈](../../atl/reference/atl-property-page-wizard.md)   
 [字串, ATL 屬性頁精靈](../../atl/reference/strings-atl-property-page-wizard.md)