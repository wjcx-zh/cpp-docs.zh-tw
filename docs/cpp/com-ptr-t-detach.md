---
title: "_com_ptr_t::Detach | Microsoft Docs"
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
  - "_com_ptr_t::Detach"
  - "_com_ptr_t.Detach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Detach 方法"
ms.assetid: 0652053e-af37-44e9-a278-2522212ebfed
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_ptr_t::Detach
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 擷取和傳回封裝的介面指標。  
  
## 語法  
  
```  
  
Interface* Detach( ) throw( );  
  
```  
  
## 備註  
 擷取和傳回封裝的介面指標，然後將封裝的指標儲存區清除為 **NULL**。  這麼做會從封裝中移除介面指標。  您可以決定是否要在所傳回的介面指標上呼叫 **Release**。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_com\_ptr\_t 類別](../cpp/com-ptr-t-class.md)