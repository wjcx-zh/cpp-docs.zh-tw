---
title: "_bstr_t::Attach | Microsoft Docs"
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
  - "_bstr_t::Attach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Attach 方法"
ms.assetid: 8cad867e-40fc-435b-841f-0d412c2f58d3
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _bstr_t::Attach
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 將 `_bstr_t` 包裝函式連結至 `BSTR`。  
  
## 語法  
  
```  
  
      void Attach(  
   BSTR s  
);  
```  
  
#### 參數  
 *s*  
 要與 `_bstr_t` 變數產生關聯或指派給該變數的 `BSTR`。  
  
## 備註  
 如果 `_bstr_t` 先前已附加至另一個 `BSTR`，且其他 `_bstr_t` 變數都不會使用 `BSTR`，則 `_bstr_t` 將會清除 `BSTR` 資源。  
  
## 範例  
 如需使用 **Attach** 的範例，請參閱 [\_bstr\_t::Assign](../cpp/bstr-t-assign.md)。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_bstr\_t 類別](../cpp/bstr-t-class.md)