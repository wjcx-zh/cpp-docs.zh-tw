---
title: "SyncLockWithStatusT::SyncLockWithStatusT 建構函式 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::Details::SyncLockWithStatusT::SyncLockWithStatusT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SyncLockWithStatusT，建構函式"
ms.assetid: 5d2fb820-ae1b-495f-8084-ebb4fecc3104
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SyncLockWithStatusT::SyncLockWithStatusT 建構函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
SyncLockWithStatusT(  
   _Inout_ SyncLockWithStatusT&& other  
);  
  
explicit SyncLockWithStatusT(  
   typename SyncTraits::Type sync,  
   DWORD status  
);  
```  
  
#### 參數  
 `other`  
 對其他物件的 SyncLockWithStatusT rvalue 參考。  
  
 `sync`  
 對另一個 SyncLockWithStatusT 物件的參考。  
  
 `status`  
 `other` 參數或 `sync` 參數的 [status\_](../windows/synclockwithstatust-status-data-member.md) 資料成員的值。  
  
## 備註  
 初始化 SyncLockWithStatusT 類別的新執行個體。  
  
 第一個建構函式會從另一個由`other`參數所指定的 SyncLockWithStatusT 物件初始化至目前的 SyncLockWithStatusT ，然後使另一個 SyncLockWithStatusT 物件失效。  第二個建構函式是 `protected`，並將目前的 SyncLockWithStatusT 物件初始化成為無效狀態。  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers::Details  
  
## 請參閱  
 [SyncLockWithStatusT 類別](../windows/synclockwithstatust-class.md)   
 [SyncLockWithStatusT::GetStatus 方法](../windows/synclockwithstatust-getstatus-method.md)