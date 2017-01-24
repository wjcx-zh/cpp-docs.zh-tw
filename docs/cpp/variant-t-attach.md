---
title: "_variant_t::Attach | Microsoft Docs"
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
  - "_variant_t::Attach"
  - "_variant_t.Attach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Attach 方法"
  - "VARIANT 物件"
  - "VARIANT 物件, attach"
ms.assetid: 2f02bd08-2306-4477-aa88-d2a5dee2b859
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _variant_t::Attach
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 將 **VARIANT** 物件附加至 `_variant_t` 物件。  
  
## 語法  
  
```  
  
      void Attach(  
   VARIANT& varSrc   
);  
```  
  
#### 參數  
 *varSrc*  
 要附加至這個 `_variant_t` 物件的 **VARIANT** 物件。  
  
## 備註  
 透過封裝方式取得 **VARIANT** 的擁有權。  這個成員函式會釋放所有現有的已封裝 **VARIANT**，然後複製提供的 **VARIANT**，並將其 **VARTYPE** 設定為 `VT_EMPTY`，確保只有 `_variant_t` 解構函式能夠釋放其資源。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_variant\_t 類別](../cpp/variant-t-class.md)