---
title: "out_of_memory 類別 | Microsoft Docs"
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
  - "amprt/Concurrency::out_of_memory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "out_of_memory 類別"
ms.assetid: 3aa7e682-8f13-4ae6-9188-31fb423956e4
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# out_of_memory 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

因為缺少系統或裝置記憶體導致方法失敗時，所擲回的例外狀況。  
  
## 語法  
  
```  
class out_of_memory : public runtime_exception;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[out\_of\_memory::out\_of\_memory 建構函式](../Topic/out_of_memory::out_of_memory%20Constructor.md)|初始化 `out_of_memory` 類別的新執行個體。|  
  
## 繼承階層架構  
 `exception`  
  
 `runtime_exception`  
  
 `out_of_memory`  
  
## 需求  
 **標頭:**  amprt.h  
  
 **命名空間：**並行  
  
## 請參閱  
 [Concurrency 命名空間 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)