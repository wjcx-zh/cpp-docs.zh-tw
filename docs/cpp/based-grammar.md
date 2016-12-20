---
title: "__based 文法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "基底定址"
ms.assetid: a68ff750-c7fa-4c0c-8d5f-2df76e4686c5
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __based 文法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定的  
 基底位址在您需要精確控制配置物件的區段時很實用 \(靜態和動態架構資料\)。  
  
 在 32 位元和 64 位元編譯中可接受的唯一基底位址形式是「以指標為基礎」，這種形式定義的類型會包含相對於 32 位元或 64 位元基底或以 `void` 為基礎的 32 位元或 64 位元位移。  
  
## 文法  
 *based\-range\-modifier*：  
 **\_\_based\(**  *base\-expression*  **\)**  
  
 *base\-expression*：  
 *based\-variablebased\-abstract\-declaratorsegment\-namesegment\-cast*  
  
 *based\-variable*：  
 *識別項*  
  
 *based\-abstract\-declarator*：  
 *abstract\-declarator*  
  
 *base\-type*：  
 *type\-name*  
  
## END Microsoft 特定的  
  
## 請參閱  
 [Based 指標](../cpp/based-pointers-cpp.md)