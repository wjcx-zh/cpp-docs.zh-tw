---
title: "SRWLock::TryLockShared 方法 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockShared"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "TryLockShared 方法"
ms.assetid: 10cc198d-39a0-4d18-aa78-706744948668
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SRWLock::TryLockShared 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

嘗試為目前或指定之 SRWLock 物件在共用模式中取得一個 SRWLock 物件。  
  
## 語法  
  
```  
WRL_NOTHROW SyncLockShared TryLockShared();  
WRL_NOTHROW static SyncLockShared TryLockShared(  
   _In_ SRWLOCK* lock  
);  
```  
  
#### 參數  
 `lock`  
 為 SRWLock 物件的指標。  
  
## 傳回值  
 如果成功，則處於共用模式的 SRWLock 物件和呼叫執行緒將取得鎖定的擁有權。  否則，狀態無效的 SRWLock 物件。  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [SRWLock 類別](../windows/srwlock-class.md)