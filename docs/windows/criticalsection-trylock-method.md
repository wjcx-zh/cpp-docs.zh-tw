---
title: "CriticalSection::TryLock 方法 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::CriticalSection::TryLock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "TryLock 方法"
ms.assetid: 504bb87c-2cd0-4f54-b458-b3efb9789053
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CriticalSection::TryLock 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

嘗試以不封鎖的方式進入關鍵區段。  如果呼叫成功，則呼叫執行緒會取得關鍵區段的擁有權。  
  
## 語法  
  
```  
SyncLock TryLock();  
  
static SyncLock TryLock(  
   _In_ CRITICAL_SECTION* cs  
);  
```  
  
#### 參數  
 `cs`  
 使用者指定的關鍵區段物件。  
  
## 傳回值  
 非零的值，如果關鍵區段已成功進入或目前執行緒已經擁有關鍵區段。  如果為零，另一個執行緒已經擁有關鍵區段。  
  
## 備註  
 第一 **TryLock** 函式會影響目前的關鍵區段物件。  第二 **TryLock** 函式影響一個使用者指定的關鍵區段。  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：**Microsoft::WRL::Wrappers  
  
## 請參閱  
 [CriticalSection 類別](../windows/criticalsection-class.md)