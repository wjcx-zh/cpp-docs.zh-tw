---
title: "CriticalSectionTraits 結構 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits::CriticalSectionTraits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CriticalSectionTraits 結構"
ms.assetid: c515a1b5-4eb0-40bc-9035-c4d9352c9de7
caps.latest.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 3
---
# CriticalSectionTraits 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

特製化 CriticalSection 物件支援一個無效的關鍵區段或函式以釋放關鍵區段。  
  
## 語法  
  
```  
struct CriticalSectionTraits;  
```  
  
## Members  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|`Type`|`typedef` 定義了一個指向這個關鍵區段的指標。  `Type`定義為：`typedef CRITICAL_SECTION* Type;`|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[CriticalSectionTraits::GetInvalidValue 方法](../windows/criticalsectiontraits-getinvalidvalue-method.md)|特製化 CriticalSection 範本，讓範本永遠無效。|  
|[CriticalSectionTraits::Unlock 方法](../windows/criticalsectiontraits-unlock-method.md)|特製化 CriticalSection 範本，以便支援釋放指定的關鍵區段物件的擁有權。|  
  
## 繼承階層架構  
 `CriticalSectionTraits`  
  
## 需求  
 **標題:** corewrappers.h  
  
 **命名空間:** Microsoft::WRL::Wrappers::HandleTraits  
  
## 請參閱  
 [Microsoft::WRL::Wrappers::HandleTraits Namespace](../windows/microsoft-wrl-wrappers-handletraits-namespace.md)