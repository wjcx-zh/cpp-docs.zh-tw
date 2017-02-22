---
title: "CreatorMap::factoryCreator 資料成員 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "module/Microsoft::WRL::Details::CreatorMap::factoryCreator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "factoryCreator 資料成員"
ms.assetid: c9aac363-8f38-4cfd-9605-1e6ac74c5097
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# CreatorMap::factoryCreator 資料成員
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
HRESULT (*factoryCreator)(  
   unsigned int* currentflags,  
   const CreatorMap* entry,  
   REFIID iidClassFactory,  
 IUnknown** factory);  
```  
  
## 參數  
 `currentflags`  
 [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) 列舉值其中之一。  
  
 `entry`  
 CreatorMap。  
  
 `iidClassFactory`  
 Class Factory 的介面 ID。  
  
 `factory`  
 當作業完成時，class factory 的位址。  
  
## 傳回值  
 如果成功，則為 S\_OK，否則，則為表示錯誤的 HRESULT。  
  
## 備註  
 建立 CreatorMap 指定的 factory。  
  
## 需求  
 **標題:** module.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [CreatorMap 結構](../windows/creatormap-structure.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)