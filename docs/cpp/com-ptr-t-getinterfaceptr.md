---
title: "_com_ptr_t::GetInterfacePtr | Microsoft Docs"
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
  - "_com_ptr_t::GetInterfacePtr"
  - "_com_ptr_t.GetInterfacePtr"
  - "GetInterfacePtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetInterfacePtr 方法"
ms.assetid: 55e3e2c7-c939-48b5-a905-4b9cbefeea7e
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_ptr_t::GetInterfacePtr
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 傳回封裝的介面指標。  
  
## 語法  
  
```  
  
      Interface* GetInterfacePtr( ) const throw( );   
Interface*& GetInterfacePtr() throw();  
```  
  
## 備註  
 傳回封裝的介面指標，可能為 **NULL**。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_com\_ptr\_t 類別](../cpp/com-ptr-t-class.md)