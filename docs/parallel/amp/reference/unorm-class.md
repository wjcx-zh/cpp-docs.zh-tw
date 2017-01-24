---
title: "unorm 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "amp_short_vectors/Concurrency::graphics::unorm"
  - "amp/Concurrency::graphics::unorm"
dev_langs: 
  - "C++"
ms.assetid: bc30bd20-6452-4d5f-9158-3b11c4c16ed2
caps.latest.revision: 8
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# unorm 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

表示 unorm 數值。  每個項目都是範圍 \[0.0f， 1.0f\] 內的浮點數值。  
  
## 語法  
  
```  
class unorm;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[unorm::unorm 建構函式](../Topic/unorm::unorm%20Constructor.md)|多載。  預設建構函式。  初始化為 0.0f。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|unorm::operator\-\- 運算子。||  
|unorm::operator float 運算子|轉換運算子  轉換 unorm 數值成一浮點數值。|  
|unorm::operator\*\= 運算子。||  
|unorm::operator\/\= 運算子。||  
|unorm::operator\+\+ 運算子。||  
|unorm::operator\+\= 運算子。||  
|unorm::operator\= 運算子。||  
|unorm::operator\-\= 運算子。||  
  
## 繼承階層架構  
 `unorm`  
  
## 需求  
 **標頭:** amp\_short\_vectors.h  
  
 **命名空間:**  Concurrency::graphics  
  
## 請參閱  
 [Concurrency::graphics 命名空間](../../../parallel/amp/reference/concurrency-graphics-namespace.md)