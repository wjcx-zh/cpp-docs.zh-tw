---
title: "SRWLockExclusiveTraits 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits::SRWLockExclusiveTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SRWLockExclusiveTraits 結構"
ms.assetid: 38a996ef-c2d7-4886-b413-a426ecee8f05
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# SRWLockExclusiveTraits 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述 SRWLock 類別在獨佔鎖定模式的通用特性。  
  
## 語法  
  
```  
struct SRWLockExclusiveTraits;  
```  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|`Type`|[SRWLOCK](../windows/srwlock-class.md) 類別的指標的同義資料表。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[SRWLockExclusiveTraits::GetInvalidValue 方法](../windows/srwlockexclusivetraits-getinvalidvalue-method.md)|擷取永遠無效的 SRWLockExclusiveTraits 物件。|  
|[SRWLockExclusiveTraits::Unlock 方法](../windows/srwlockexclusivetraits-unlock-method.md)|指定的 SRWLock 互斥物件的版本控制項。|  
  
## 繼承階層架構  
 `SRWLockExclusiveTraits`  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間:** Microsoft::WRL::Wrappers::HandleTraits  
  
## 請參閱  
 [Microsoft::WRL::Wrappers::HandleTraits Namespace](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)