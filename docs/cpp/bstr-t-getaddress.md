---
title: "_bstr_t::GetAddress | Microsoft Docs"
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
  - "_bstr_t::GetAddress"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetAddress 方法"
ms.assetid: 09bc9180-867e-4ee5-b22a-8339dc663142
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _bstr_t::GetAddress
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 釋放任何現有字串並傳回新配置字串的位址。  
  
## 語法  
  
```  
  
BSTR* GetAddress( );  
  
```  
  
## 傳回值  
 由 `_bstr_t` 包裝的 `BSTR` 指標。  
  
## 備註  
 `GetAddress` 會影響所有共用 `BSTR` 的 `_bstr_t` 物件。  一個以上的 `_bstr_t` 可以使用複製建構函式和 `operator=` 來共用 `BSTR`。  
  
## 範例  
 如需使用 `GetAddress` 的範例，請參閱 [\_bstr\_t::Assign](../cpp/bstr-t-assign.md)。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_bstr\_t 類別](../cpp/bstr-t-class.md)