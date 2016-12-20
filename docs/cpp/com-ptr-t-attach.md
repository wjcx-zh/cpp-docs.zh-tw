---
title: "_com_ptr_t::Attach | Microsoft Docs"
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
  - "_com_ptr_t::Attach"
  - "_com_ptr_t.Attach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Attach 方法"
  - "COM 介面, attach 指標"
ms.assetid: 94c18e0a-06be-4ca7-bdaf-cd54ec0a645e
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_ptr_t::Attach
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 封裝這個智慧型指標類型的一般介面指標。  
  
## 語法  
  
```  
  
      void Attach(  
   Interface* pInterface   
) throw( );  
void Attach(  
   Interface* pInterface,  
   bool fAddRef   
) throw( );  
```  
  
#### 參數  
 `pInterface`  
 原始的介面指標。  
  
 `fAddRef`  
 如果為 **true**，則會呼叫 `AddRef`。  如果為 **false**，則 `_com_ptr_t` 物件會取得一般介面指標的擁有權，而不需呼叫 `AddRef`。  
  
## 備註  
  
-   **Attach\(**  `pInterface`  **\)** 不會呼叫 `AddRef`。  介面的擁有權會傳遞至這個 `_com_ptr_t` 物件。  此時會呼叫 **Release** 讓先前封裝之指標的參考計數遞減。  
  
-   **Attach\(**  `pInterface` **,**  `fAddRef`  **\)** 如果 `fAddRef` 為 **true**，則會呼叫 `AddRef`，讓封裝的介面指標參考計數遞增。  如果 `fAddRef` 為 **false**，則這個 `_com_ptr_t` 物件會取得一般介面指標的擁有權，而不需呼叫 `AddRef`。  此時會呼叫 **Release** 讓先前封裝之指標的參考計數遞減。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_com\_ptr\_t 類別](../cpp/com-ptr-t-class.md)