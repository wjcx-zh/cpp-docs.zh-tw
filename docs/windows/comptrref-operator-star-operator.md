---
title: "ComPtrRef::operator* 運算子 | Microsoft Docs"
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
  - "client/Microsoft::WRL::Details::ComPtrRef::operator*"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator* 運算子"
ms.assetid: 0287ca7a-4ce1-47f7-bab6-714fca3e04bb
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ComPtrRef::operator* 運算子
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
InterfaceType* operator *();  
```  
  
## 傳回值  
 ComPtrRef 對目前物件所表示之介面的指標。  
  
## 備註  
 擷取指標目前 ComPtrRef 物件所表示的介面。  
  
## 需求  
 **標題:** client.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## 請參閱  
 [ComPtrRef 類別](../windows/comptrref-class.md)   
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)