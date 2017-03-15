---
title: "SyncLockT::SyncLockT 建構函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockT::SyncLockT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SyncLockT，建構函式"
ms.assetid: 713dfd9f-7369-4d86-b4a0-8b32c184d89b
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# SyncLockT::SyncLockT 建構函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
SyncLockT(  
   _Inout_ SyncLockT&& other  
);  
  
explicit SyncLockT(  
   typename SyncTraits::Type sync = SyncTraits::GetInvalidValue()  
);  
```  
  
#### 參數  
 `other`  
 對另一個 SyncLockT 物件的 rvalue 參考。  
  
 `sync`  
 對另一個 SyncLockWithStatusT 物件的參考。  
  
## 備註  
 初始化 SyncLockT 類別的新執行個體。  
  
 第一個建構函式會以由參數 `other`指定的另一個 SyncLockT 物件來初始化目前的 SyncLockT 物件，然後使另一個 SyncLockT 物件失效。  第二個建構函式是 `protected`，並將目前的 SyncLockT 物件初始化成為無效狀態。  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers::Details  
  
## 請參閱  
 [SyncLockT 類別](../windows/synclockt-class.md)