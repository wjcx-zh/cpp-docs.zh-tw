---
title: "CreatorMap::activationId 資料成員 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Details::CreatorMap::activationId"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "activationId 資料成員"
ms.assetid: 77518b76-6e6a-4b48-8e2e-a4c7c67769e0
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# CreatorMap::activationId 資料成員
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
union {   
   const IID* clsid;  
   const wchar_t* (*getRuntimeName)();  
} activationId;  
```  
  
## 參數  
 `clsid`  
 介面 ID。  
  
 `getRuntimeName`  
 擷取一個物件的視窗執行階段名稱的函式。  
  
## 備註  
 表示由一般 COM 類別 ID 或視窗執行階段名稱所識別的物件 ID。  
  
## 需求  
 **標題:** module.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [CreatorMap 結構](../windows/creatormap-structure.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)