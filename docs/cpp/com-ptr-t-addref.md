---
title: "_com_ptr_t::AddRef | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_com_ptr_t::AddRef"
  - "_com_ptr_t.AddRef"
  - "AddRef"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddRef 方法 [C++], 介面指標"
ms.assetid: c104dac3-aad3-40bb-a298-75c6cd0e63a2
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_ptr_t::AddRef
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 在封裝的介面指標上呼叫 **IUnknown** 的 `AddRef` 成員函式。  
  
## 語法  
  
```  
  
void AddRef( );  
  
```  
  
## 備註  
 在封裝的介面指標呼叫 `IUnknown::AddRef`，如果指標是 **NULL** 則引發 `E_POINTER` 錯誤。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_com\_ptr\_t 類別](../cpp/com-ptr-t-class.md)