---
title: "CreatorMap 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Details::CreatorMap"
  - "implements/Microsoft::WRL::Details::CreatorMap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreatorMap 結構"
ms.assetid: 94e40927-90c3-4107-bca3-3ad2dc4beda9
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CreatorMap 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 [!INCLUDE[cppwrl](../windows/includes/cppwrl_md.md)] 基礎結構，而且不是針對直接從程式碼中使用而設計。  
  
## 語法  
  
```  
struct CreatorMap;  
```  
  
## 備註  
 包含如何初始化，註冊和移除註冊物件。  
  
 CreatorMap 包含下列資訊:  
  
-   如何初始化，註冊和移除註冊物件。  
  
-   如何根據一個一般 COM 或 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] Factory 比較啟動資料。  
  
-   Factory 快取的資訊和伺服器名稱的介面。  
  
## Members  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[CreatorMap::activationId 資料成員](../windows/creatormap-activationid-data-member.md)|表示由一般 COM 類別 ID 或 [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] 名稱所識別的物件 ID。|  
|[CreatorMap::factoryCache 資料成員](../windows/creatormap-factorycache-data-member.md)|將指標儲存在 CreatorMap 的 factory 快取。|  
|[CreatorMap::factoryCreator 資料成員](../windows/creatormap-factorycreator-data-member.md)|建立指定之 CreatorMap 的 Factory。|  
|[CreatorMap::serverName 資料成員](../windows/creatormap-servername-data-member.md)|儲存 CreatorMap 的伺服器名稱。|  
  
## 繼承階層架構  
 `CreatorMap`  
  
## 需求  
 **標題:** module.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)