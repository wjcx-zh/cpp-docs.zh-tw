---
title: "CriticalSection::Lock 方法 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::CriticalSection::Lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Lock 方法"
ms.assetid: 37cb184c-e13c-49ef-b6a0-13908a956414
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CriticalSection::Lock 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

等候指定的關鍵區段物件的擁有權。  在授與呼叫執行緒釋出 Mutex 時，函式會傳回。  
  
## 語法  
  
```  
SyncLock Lock();  
  
   static SyncLock Lock(  
   _In_ CRITICAL_SECTION* cs  
);  
```  
  
#### 參數  
 `cs`  
 使用者指定的關鍵區段物件。  
  
## 傳回值  
 可以用來啟動目前的關鍵區段的鎖定物件。  
  
## 備註  
 第一 **Lock** 函式會影響目前的關鍵區段物件。  第二 **Lock** 函式影響一個使用者指定的關鍵區段。  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [CriticalSection 類別](../windows/criticalsection-class.md)