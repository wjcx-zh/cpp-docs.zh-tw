---
title: "CriticalSectionTraits::Unlock 方法 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits::Unlock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Unlock 方法"
ms.assetid: 8fb382f5-6eda-407e-9673-71d77bda4962
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CriticalSectionTraits::Unlock 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

特製化 CriticalSection 範本，以便支援釋放指定的關鍵區段物件的擁有權。  
  
## 語法  
  
```  
inline static void Unlock(  
   _In_ Type cs  
);  
```  
  
#### 參數  
 `cs`  
 為關鍵區段物件的指標。  
  
## 備註  
 *Type* 修飾詞定義為 `typedef CRITICAL_SECTION* Type;`。  
  
 如需詳細資訊，請參閱\< LeaveCriticalSection 函式」中的「同步函式」Windows 應用程式開發介面文件的部分。  
  
## 需求  
 **標頭：**corewrappers.h  
  
 **命名空間:** Microsoft::WRL::Wrappers::HandleTraits  
  
## 請參閱  
 [CriticalSectionTraits 結構](../windows/criticalsectiontraits-structure.md)