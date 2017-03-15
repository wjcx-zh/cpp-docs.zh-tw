---
title: "BEGIN_PROPERTY_SET_EX | Microsoft Docs"
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
  - "BEGIN_PROPERTY_SET_EX"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BEGIN_PROPERTY_SET_EX 巨集"
ms.assetid: c95e7fab-edce-47b8-b282-200e53a2ea8a
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# BEGIN_PROPERTY_SET_EX
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

標記在屬性集對應設定之屬性的開頭。  
  
## 語法  
  
```  
  
BEGIN_PROPERTY_SET_EX(  
guid  
, flags )  
```  
  
#### 參數  
 `guid`  
 \[屬性 GUID。  
  
 `flags`  
 \[您不想要公開的任何屬性集合的公開屬性的提供者的 **UPROPSET\_HIDDEN** 或 **UPROPSET\_PASSTHROUGH** 定義在提供者範圍之外。  
  
## 範例  
 請參閱 [BEGIN\_PROPSET\_MAP](../../data/oledb/begin-propset-map.md)。  
  
## 需求  
 **Header:** atldb.h  
  
## 請參閱  
 [OLE DB 提供者樣板的巨集](../../data/oledb/macros-for-ole-db-provider-templates.md)   
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者樣板架構](../../data/oledb/ole-db-provider-template-architecture.md)   
 [建立 OLE DB 提供者](../../data/oledb/creating-an-ole-db-provider.md)