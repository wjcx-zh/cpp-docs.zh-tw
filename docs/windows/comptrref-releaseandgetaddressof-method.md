---
title: "ComPtrRef::ReleaseAndGetAddressOf 方法 | Microsoft Docs"
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
  - "client/Microsoft::WRL::Details::ComPtrRef::ReleaseAndGetAddressOf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ReleaseAndGetAddressOf 方法"
ms.assetid: 004aac42-e135-41ce-8d1d-4c5969d55004
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtrRef::ReleaseAndGetAddressOf 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
InterfaceType** ReleaseAndGetAddressOf();  
```  
  
## 傳回值  
 由要刪除的 ComPtrRef 物件所表示之介面的指標。  
  
## 備註  
 刪除目前 ComPtrRef 物件並傳回指標的指標的 ComPtrRef 由物件所表示的介面。  
  
## 需求  
 **標題:** client.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [ComPtrRef 類別](../windows/comptrref-class.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)