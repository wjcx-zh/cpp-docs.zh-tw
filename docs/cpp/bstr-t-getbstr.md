---
title: "_bstr_t::GetBSTR | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "GetBSTR"
  - "_bstr_t::GetBSTR"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetBSTR 方法"
ms.assetid: 0c62ff16-4433-4183-a03c-d5a0a9b731ef
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# _bstr_t::GetBSTR
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 指向由 `_bstr_t` 所包裝之 `BSTR` 的開頭。  
  
## 語法  
  
```  
  
BSTR& GetBSTR( );  
  
```  
  
## 傳回值  
 由 `_bstr_t` 所包裝之 `BSTR` 的開頭。  
  
## 備註  
 `GetBSTR` 會影響所有共用 `BSTR` 的 `_bstr_t` 物件。  一個以上的 `_bstr_t` 可以使用複製建構函式和 `operator=` 來共用 `BSTR`。  
  
## 範例  
 如需使用 `GetBSTR` 的範例，請參閱 [\_bstr\_t::Assign](../cpp/bstr-t-assign.md)。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_bstr\_t 類別](../cpp/bstr-t-class.md)