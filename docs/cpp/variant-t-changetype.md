---
title: "_variant_t::ChangeType | Microsoft Docs"
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
  - "_variant_t::ChangeType"
  - "_variant_t.ChangeType"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ChangeType 方法"
  - "VARIANT 物件"
  - "VARIANT 物件, ChangeType"
ms.assetid: 829d2eeb-3338-4a88-9dce-0ca145f47aac
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# _variant_t::ChangeType
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 將 `_variant_t` 物件的類型變更為指定的 **VARTYPE**。  
  
## 語法  
  
```  
  
      void ChangeType(  
   VARTYPE vartype,  
   const _variant_t* pSrc = NULL   
);  
```  
  
#### 參數  
 `vartype`  
 這個 `_variant_t` 物件的 **VARTYPE**。  
  
 `pSrc`  
 要轉換之 `_variant_t` 物件的指標。  如果這個值是 **NULL**，表示轉換已經完成。  
  
## 備註  
 此成員函式會將 `_variant_t` 物件轉換為指定的 **VARTYPE**。  如果 `pSrc` 為 **NULL**，表示轉換已完成，否則便會從 `pSrc` 複製此 `_variant_t` 物件，然後再進行轉換。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [\_variant\_t 類別](../cpp/variant-t-class.md)