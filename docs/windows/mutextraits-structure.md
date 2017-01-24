---
title: "MutexTraits 結構 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits::MutexTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MutexTraits 結構"
ms.assetid: 6582df80-b9ba-4892-948f-d572a3b23d54
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MutexTraits 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義 [Mutex](../windows/mutex-class1.md) 類別的通用特性。  
  
## 語法  
  
```  
struct MutexTraits : HANDLENullTraits;  
  
```  
  
## Members  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[MutexTraits::Unlock 方法](../windows/mutextraits-unlock-method.md)|釋放共用資源的獨佔控制權。|  
  
## 繼承階層架構  
 `HANDLENullTraits`  
  
 `MutexTraits`  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間:** Microsoft::WRL::Wrappers::HandleTraits  
  
## 請參閱  
 [Microsoft::WRL::Wrappers::HandleTraits Namespace](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)