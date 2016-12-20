---
title: "CHAIN_PROPERTY_SET | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CHAIN_PROPERTY_SET"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHAIN_PROPERTY_SET 巨集"
ms.assetid: 2bcf6d7d-f4e5-480d-9140-1e32a0994c94
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CHAIN_PROPERTY_SET
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個巨集一起繫結屬性群組。  
  
## 語法  
  
```  
  
CHAIN_PROPERTY_SET(  
ChainClass   
)  
  
```  
  
#### 參數  
 *ChainClass*  
 \[in\] 繫結屬性的類別名稱。  這是已經含有對應的 ATL 專案精靈產生的類別 \(例如工作階段、命令或資料來源物件類別\)。  
  
## 備註  
 您可以將其他類別所設定的屬性加入至類別，然後直接從您的類別會存取屬性。  
  
> [!CAUTION]
>  盡量不要使用這個巨集。  不適當使用可能造成消費者在 OLE DB 一致性測試失敗。  
  
## 需求  
 **標頭：** atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板的巨集](../../data/oledb/macros-for-ole-db-provider-templates.md)