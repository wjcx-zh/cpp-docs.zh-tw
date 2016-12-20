---
title: "_com_ptr_t::QueryInterface | Microsoft Docs"
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
  - "_com_ptr_t::QueryInterface"
  - "_com_ptr_t.QueryInterface"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "QueryInterface 方法"
ms.assetid: d03292f1-6b02-40db-9756-8b0837a97319
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _com_ptr_t::QueryInterface
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 在封裝的介面指標上呼叫 **IUnknown** 的 `QueryInterface` 成員函式。  
  
## 語法  
  
```  
  
      template<typename _InterfaceType> HRESULT QueryInterface (  
   const IID& iid,  
   _InterfaceType*& p   
) throw ( );  
template<typename _InterfaceType> HRESULT QueryInterface (  
   const IID& iid,  
   _InterfaceType** p  
) throw( );  
```  
  
#### 參數  
 `iid`  
 介面指標的 **IID**。  
  
 `p`  
 原始介面指標。  
  
## 備註  
 在包含指定 **IID** 的封裝介面指標呼叫 **IUnknown::QueryInterface** 並在 `p` 傳回最後產生的原始介面指標。  這個常式會傳回 `HRESULT`，表示成功或失敗。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_com\_ptr\_t 類別](../cpp/com-ptr-t-class.md)