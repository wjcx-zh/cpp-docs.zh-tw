---
title: "SyncLockT::~SyncLockT 解構函式 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::~SyncLockT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "~SyncLockT，解構函式"
ms.assetid: 9e14870d-017d-45fe-a3dc-cd86b6fa1c3a
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SyncLockT::~SyncLockT 解構函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
~SyncLockT();  
```  
  
## 備註  
 取消初始化 SyncLockT 類別的執行個體。  
  
 此解構函式也會解鎖目前 SyncLockT 執行個體。  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers::Details  
  
## 請參閱  
 [SyncLockT 類別](../windows/synclockt-class.md)