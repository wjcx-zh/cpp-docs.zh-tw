---
title: "_variant_t::Detach | Microsoft Docs"
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
  - "_variant_t::Detach"
  - "_variant_t.Detach"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Detach 方法"
  - "VARIANT 物件"
  - "VARIANT 物件, detatch"
ms.assetid: c348ac08-62cf-4657-a16f-974a79c12158
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _variant_t::Detach
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 中斷連結封裝的 **VARIANT** 物件與這個 `_variant_t` 物件。  
  
## 語法  
  
```  
  
VARIANT Detach( );  
  
```  
  
## 傳回值  
 封裝的 **VARIANT**。  
  
## 備註  
 擷取並傳回封裝的 **VARIANT**，然後清除這個 `_variant_t` 物件而不將其終結。  此成員函式會將 **VARIANT** 從封裝移除，並將此 `_variant_t` 物件的 **VARTYPE** 設定為 `VT_EMPTY`。  您可以呼叫 [VariantClear](http://msdn.microsoft.com/zh-tw/28741d81-8404-4f85-95d3-5c209ec13835) 函式來釋放傳回的 **VARIANT**。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_variant\_t 類別](../cpp/variant-t-class.md)