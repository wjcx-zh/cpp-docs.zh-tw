---
title: "SRWLockSharedTraits 結構 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockSharedTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SRWLockSharedTraits 結構"
ms.assetid: 709cb51e-d70c-40b6-bdb4-d8eacf3af495
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SRWLockSharedTraits 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在共用鎖定模式描述 SRWLock 類別的通用特性。  
  
## 語法  
  
```  
struct SRWLockSharedTraits;  
```  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|`Type`|[SRWLOCK](../windows/srwlock-class.md) 類別的指標的同義資料表。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[SRWLockSharedTraits::GetInvalidValue 方法](../windows/srwlocksharedtraits-getinvalidvalue-method.md)|擷取永遠無效的 SRWLockSharedTraits 物件。|  
|[SRWLockSharedTraits::Unlock 方法](../windows/srwlocksharedtraits-unlock-method.md)|指定的 SRWLock 互斥物件的版本控制項。|  
  
## 繼承階層架構  
 `SRWLockSharedTraits`  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間:** Microsoft::WRL::Wrappers::HandleTraits  
  
## 請參閱  
 [Microsoft::WRL::Wrappers::HandleTraits Namespace](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)