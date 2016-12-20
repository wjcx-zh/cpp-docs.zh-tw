---
title: "_com_ptr_t::Release | Microsoft Docs"
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
  - "_com_ptr_t.Release"
  - "_com_ptr_t::Release"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Release 方法"
ms.assetid: db448b34-0efa-4f02-b701-ad1ca3ae6ca5
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_ptr_t::Release
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 在封裝的介面指標上呼叫 **IUnknown** 的 **Release** 成員函式。  
  
## 語法  
  
```  
  
void Release( );  
  
```  
  
## 備註  
 在封裝的介面指標呼叫 `IUnknown::Release`，如果此介面指標是 **NULL** 則會引發 `E_POINTER` 錯誤。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_com\_ptr\_t 類別](../cpp/com-ptr-t-class.md)