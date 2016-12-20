---
title: "SRWLockSharedTraits::Unlock 方法 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits::Unlock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Unlock 方法"
ms.assetid: 33cdead9-1900-4094-b18e-38fcf1a0bd28
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SRWLockSharedTraits::Unlock 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定的 SRWLock 互斥物件的版本控制項。  
  
## 語法  
  
```  
inline static void Unlock(  
   _In_ Type srwlock  
);  
```  
  
#### 參數  
 `srwlock`  
 為 SRWLock 物件的控制代碼。  
  
## 傳回值  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間:** Microsoft::WRL::Wrappers::HandleTraits  
  
## 請參閱  
 [SRWLockSharedTraits 結構](../windows/srwlocksharedtraits-structure.md)