---
title: "Microsoft::WRL::Wrappers::Details 命名空間 | Microsoft Docs"
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
  - "implements/Microsoft::WRL::Details"
  - "internal/Microsoft::WRL::Details"
  - "async/Microsoft::WRL::Details"
  - "corewrappers/Microsoft::WRL::Wrappers::Details"
  - "client/Microsoft::WRL::Details"
  - "module/Microsoft::WRL::Details"
  - "event/Microsoft::WRL::Details"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Details 命名空間"
ms.assetid: 6d3f04ac-9b53-4a82-a188-a85309ec34a4
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Microsoft::WRL::Wrappers::Details 命名空間
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

支援 WRL 基礎結構，而且不是為了要直接從您的程式碼中使用而設計。  
  
## 語法  
  
```  
namespace Microsoft::WRL::Wrappers::Details;  
```  
  
## Members  
  
### 類別  
  
|名稱|描述|  
|--------|--------|  
|[SyncLockT 類別](../windows/synclockt-class.md)|表示可以取得資源的獨佔或共用擁有權的型別。|  
|[SyncLockWithStatusT 類別](../windows/synclockwithstatust-class.md)|表示可以取得資源的獨佔或共用擁有權的型別。|  
  
### 方法  
  
|名稱|描述|  
|--------|--------|  
|[CompareStringOrdinal 方法](../windows/comparestringordinal-method.md)|比較兩個指定的 `HSTRING` 物件，並傳回一個整數，指出它們在排序順序中的相對位置。|  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間：** Microsoft::WRL::Wrappers::Details  
  
## 請參閱  
 [Microsoft::WRL::Wrappers 命名空間](../windows/microsoft-wrl-wrappers-namespace.md)