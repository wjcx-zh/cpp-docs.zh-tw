---
title: "FactoryCache 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Details::FactoryCache"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "FactoryCache 結構"
ms.assetid: 624544e6-0989-47f6-a3e9-edb60e1ee6d4
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# FactoryCache 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] 基礎結構，而且不是針對直接從程式碼中使用而設計。  
  
## 語法  
  
```  
struct FactoryCache;  
```  
  
## 備註  
 包含一個類別處理站的位置及一個可識別已註冊之 wrt 或 COM 類別物件的值。  
  
## Members  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[FactoryCache::cookie 資料成員](../windows/factorycache-cookie-data-member.md)|包含一個可識別已註冊的 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 或 COM 類別物件的值，並稍後用來解除註冊物件。|  
|[FactoryCache::factory 資料成員](../windows/factorycache-factory-data-member.md)|指向一個 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 或 COM Class Factory。|  
  
## 繼承階層架構  
 `FactoryCache`  
  
## 需求  
 **標題:** module.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)