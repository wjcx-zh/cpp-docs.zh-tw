---
title: "_com_ptr_t 擷取器 | Microsoft Docs"
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
  - "_com_ptr_t::operatorInterface&"
  - "operatorInterface*"
  - "operatorInterface&"
  - "_com_ptr_t::operatorbool"
  - "_com_ptr_t.operator->"
  - "_com_ptr_t.operator*"
  - "_com_ptr_t::operator->"
  - "_com_ptr_t::operator*"
  - "_com_ptr_t.operatorInterface&"
  - "_com_ptr_t.operatorbool"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "& 運算子, 使用特定物件"
  - "* 運算子, 使用特定物件"
  - "-> 運算子, 使用特定物件"
  - "擷取器"
  - "擷取器, _com_ptr_t 類別"
  - "運算子 *"
  - "運算子 bool"
  - "運算子 Interface&"
  - "運算子 Interface*"
  - "operator&"
  - "operator*"
  - "operator->"
ms.assetid: 194b9e0e-123c-49ff-a187-0a7fcd68145a
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_ptr_t 擷取器
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 擷取封裝的 COM 介面指標。  
  
## 語法  
  
```  
  
      operator Interface*( ) const throw( );   
operator Interface&( ) const;   
Interface& operator*( ) const;   
Interface* operator->( ) const;   
Interface** operator&( ) throw( );   
operator bool( ) const throw( );  
```  
  
## 備註  
  
-   **operator Interface\***：傳回封裝的介面指標，可能是 **NULL**。  
  
-   **operator Interface&**：傳回封裝之介面指標的參考，並在指標為 **NULL** 時發出錯誤。  
  
-   **operator\***：允許在取值時將智慧型指標物件當做如實際封裝的介面使用。  
  
-   **operator\-\>**：允許在取值時將智慧型指標物件當做如實際封裝的介面使用。  
  
-   **operator&**：釋放所有封裝的介面指標，並以 **NULL** 取代，然後傳回封裝的指標位址。  這可讓智慧型指標透過傳址方式傳遞至具有 **out** 參數，會透過它傳回介面指標的函式。  
  
-   **operator bool**：允許在條件運算式中使用智慧型指標物件。  如果指標不是 **NULL**，這個運算子會傳回 **true**。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_com\_ptr\_t 類別](../cpp/com-ptr-t-class.md)