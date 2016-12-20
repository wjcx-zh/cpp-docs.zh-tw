---
title: "HANDLETraits::GetInvalidValue 方法 | Microsoft Docs"
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
  - "corewrappers/Microsoft::WRL::Wrappers::HandleTraits::HANDLETraits::GetInvalidValue"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetInvalidValue 方法"
ms.assetid: e95d2cc1-e70f-463f-8ff0-183cdeac1138
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# HANDLETraits::GetInvalidValue 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示無效的控制代碼。  
  
## 語法  
  
```  
inline static HANDLE GetInvalidValue();  
```  
  
## 傳回值  
 永遠傳回 INVALID\_HANDLE\_VALUE。\(INVALID\_HANDLE\_VALUE 是由 Windows 所定義\)。  
  
## 需求  
 **標頭：**corewrappers.h  
  
 **命名空間:** Microsoft::WRL::Wrappers::HandleTraits  
  
## 請參閱  
 [HANDLETraits 結構](../windows/handletraits-structure.md)