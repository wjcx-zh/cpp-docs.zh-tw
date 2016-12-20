---
title: "SRWLock::LockShared 方法 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::SRWLock::LockShared"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LockShared 方法"
ms.assetid: 9d826a5c-b6a2-4430-ac85-d5753cbca889
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SRWLock::LockShared 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在共用模式中取得一個 SRWLock 物件。  
  
## 語法  
  
```  
SyncLockShared LockShared();  
  
static SyncLockShared LockShared(  
   _In_ SRWLOCK* lock  
);  
```  
  
#### 參數  
 `lock`  
 為 SRWLock 物件的指標。  
  
## 傳回值  
 一個處於共用模式的 SRWLock 物件。  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [SRWLock 類別](../windows/srwlock-class.md)