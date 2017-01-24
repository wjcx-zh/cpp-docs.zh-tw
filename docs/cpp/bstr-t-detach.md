---
title: "_bstr_t::Detach | Microsoft Docs"
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
  - "_bstr_t::Detach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Detach 方法"
ms.assetid: cc8284bd-f68b-4fff-b2e6-ce8354dabf8b
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _bstr_t::Detach
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 傳回 `_bstr_t` 所包裝的 `BSTR`，並將 `BSTR` 與 `_bstr_t` 中斷連結。  
  
## 語法  
  
```  
  
BSTR Detach( ) throw;  
  
```  
  
## 傳回值  
 `_bstr_t` 包裝 `BSTR`。  
  
## 範例  
 請參閱 [\_bstr\_t::Assign](../cpp/bstr-t-assign.md)，了解使用 **Detach** 的範例。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_bstr\_t 類別](../cpp/bstr-t-class.md)