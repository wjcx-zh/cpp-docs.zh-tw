---
title: "SyncLockT::IsLocked 方法 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::IsLocked"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IsLocked 方法"
ms.assetid: a81fea43-f99a-4708-812a-7fd6af500d3d
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SyncLockT::IsLocked 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
bool IsLocked() const;  
```  
  
## 傳回值  
 物件如果已鎖定SyncLockT物件，則為**true**，否則為 **false** 。  
  
## 備註  
 指示目前的SyncLockT物件是否擁有資源;也就是說 SyncLockT 物件已*被鎖定*。  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers::Details  
  
## 請參閱  
 [SyncLockT 類別](../windows/synclockt-class.md)