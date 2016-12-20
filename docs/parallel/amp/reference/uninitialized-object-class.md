---
title: "uninitialized_object 類別 | Microsoft Docs"
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
  - "amprt/Concurrency::uninitialized_object"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "uninitialized_object 類別"
ms.assetid: 6ae3c4e8-64a6-4511-a158-03be197b63af
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# uninitialized_object 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

使用未初始化的物件時，所擲回的例外狀況。  
  
## 語法  
  
```  
class uninitialized_object : public runtime_exception;  
  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[uninitialized\_object::uninitialized\_object 建構函式](../Topic/uninitialized_object::uninitialized_object%20Constructor.md)|初始化 `uninitialized_object` 類別的新執行個體。|  
  
## 繼承階層架構  
 `exception`  
  
 `runtime_exception`  
  
 `uninitialized_object`  
  
## 需求  
 **標頭:**  amprt.h  
  
 **命名空間：**並行  
  
## 請參閱  
 [Concurrency 命名空間 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)