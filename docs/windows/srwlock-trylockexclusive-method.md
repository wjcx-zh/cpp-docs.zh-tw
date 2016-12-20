---
title: "SRWLock::TryLockExclusive 方法 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::SRWLock::TryLockExclusive"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "TryLockExclusive 方法"
ms.assetid: 661e8b19-3058-4511-8742-c9fbb90412c7
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SRWLock::TryLockExclusive 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

嘗試取得以獨佔模式目前或指定之 SRWLock 物件的 SRWLock 物件。  如果呼叫成功，呼叫執行緒取得鎖定的擁有權。  
  
## 語法  
  
```  
SyncLockExclusive TryLockExclusive();  
  
static SyncLockExclusive TryLockExclusive(  
   _In_ SRWLOCK* lock  
);  
```  
  
#### 參數  
 `lock`  
 為 SRWLock 物件的指標。  
  
## 傳回值  
 如果成功，則將 SRWLock 物件以獨佔模式和呼叫執行緒取得鎖定的擁有權。  否則，狀態無效的 SRWLock 物件。  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [SRWLock 類別](../windows/srwlock-class.md)