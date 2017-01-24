---
title: "SyncLockT::Unlock 方法 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::Unlock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Unlock 方法"
ms.assetid: e21110a2-03dd-4073-9c3f-73b99e39f405
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SyncLockT::Unlock 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
void Unlock();  
```  
  
## 備註  
 資源的釋放控制項是由目前物件 SyncLockT 持有，如果有的話。  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers::Details  
  
## 請參閱  
 [SyncLockT 類別](../windows/synclockt-class.md)